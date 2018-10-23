# TestClassification
Test Classification on 5 classes.

## Getting Started

The problem consists in classifying images of shirts into 5 different classes according to the type of sleeves.

### Prerequisites

Install Kera with Tensorflow backend.
Download the dataset and copy it to the notebook path.

## Running the tests

The solution is based on the fine tuning of VGG16 network, pretrained on imagenet, with the dense layers adapted for this particular task.

Tha dataset is splitted into training and validation set, keeping the number of samples for class (500) the same for each class. This is done with image transformations for increasing the samples for that classes with less elements. The remaining images are used for validation.
The images are loaded in batches using keras api applying data augmentation.

The training uses early stopping to avoid overfitting and the best result are achieved after 6 epoch. A checkpoint callback is used to save only the weight that decrease the validation loss.
The best weights are renamed as 'weights.hdf5' and loaded to make a brief evaluation ok the results.
In particular, the test reach an accuracy of 0.93.

```
No of errors = 123/1754

Confusion Matrix=    [[334   3  14   2   0]
                     [ 17 443   1   0  17]
                     [ 37   2 322   1   2]
                     [  1   5   2 232   8]
                     [  2   1   2   6 300]]
```
