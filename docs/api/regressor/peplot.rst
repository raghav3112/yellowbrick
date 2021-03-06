.. -*- mode: rst -*-

Prediction Error Plot
=====================

A prediction error plot shows the actual targets from the dataset against the predicted values generated by our model. This allows us to see how much variance is in the model. Data scientists can diagnose regression models using this plot by comparing against the 45 degree line, where the prediction exactly matches the model.

=================   ==============================
 Visualizer           :class:`~yellowbrick.regressor.prediction_error.PredictionError`
 Quick Method         :func:`~yellowbrick.regressor.prediction_error.prediction_error`
 Models               Regression
 Workflow             Model Evaluation
=================   ==============================

.. plot::
    :context: close-figs
    :alt: Prediction Error plot on the Concrete dataset using a linear model

    from sklearn.linear_model import Lasso
    from sklearn.model_selection import train_test_split

    from yellowbrick.datasets import load_concrete
    from yellowbrick.regressor import PredictionError

    # Load a regression dataset
    X, y = load_concrete()

    # Create the train and test data
    X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

    # Instantiate the linear model and visualizer
    model = Lasso()
    visualizer = PredictionError(model)

    visualizer.fit(X_train, y_train)  # Fit the training data to the visualizer
    visualizer.score(X_test, y_test)  # Evaluate the model on the test data
    visualizer.show()                 # Finalize and render the figure

Quick Method
------------
The same functionality can be achieved with the associated quick method ``prediction_error``. This method will build the ``PredictionError`` object with the associated arguments, fit it, then (optionally) immediately show the visualization.

.. plot::
    :context: close-figs
    :alt: Prediction Error plot on the Concrete dataset using a linear model

    from sklearn.linear_model import Lasso
    from sklearn.model_selection import train_test_split

    from yellowbrick.datasets import load_concrete
    from yellowbrick.regressor import prediction_error

    # Load a regression dataset
    X, y = load_concrete()

    # Create the train and test data
    X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

    # Instantiate the linear model and visualizer
    model = Lasso()
    visualizer = prediction_error(model, X_train, y_train, X_test, y_test)

API Reference
-------------

.. automodule:: yellowbrick.regressor.prediction_error
    :members: PredictionError, prediction_error
    :undoc-members:
    :show-inheritance:
    :noindex: