# Image Classifier

## Description
Part 1 of the project involves implementing an image classifier that is trained on a flower data set. There are 102 different types of flowers, where there are ~20 images per flower to train on.

Part 2 involves converting the classifier into an application that can be used for any images. GPU processing is recommended, although the application will also work without GPU processing, albeit slower.

## Date
Download/extract/place the training [download link](http://www.robots.ox.ac.uk/~vgg/data/flowers/102/index.html) dataset in the following folder structure:

~~~~~~~
        project
          |-- codes
          |-- data
               |--- train
                    |-- class 1
                    |-- class 2
                    |-- etc
               |-- valid
                    |-- class 1
                    |-- class 2
                    |-- etc
               |-- test
                    |-- class 1
                    |-- class 2
                    |-- etc
~~~~~~~


## How To Run It
Part 1: Run Image Classifier Project.ipynb

Part 2: Run train.py to train a new network on a data set. Run predict.py to predict image class from an image.

The train.py file accepts the following arguments:
```bash
default arguments:
  data_dir          set directory of the training images
optional arguments:
  -h, --help         show this help message and exit
  --save_dir         set directory to save checkpoints
  --arch             choose network architecture
  --learning_rate    set learning rate
  --hidden_unit      set number of hidden units per network layer
  --epochs           set number of training epochs
  --gpu              use gpu processing
```

For example, to train the network with images located at the path ../aipnd-project/flowers using the AlexNet network architecture with a learning rate of 0.01, 256 hidden units and 1 epoch of training time:

```bash
python train.py --arch alexnet --learning_rate 0.01 --hidden_units 256 --epochs 1 --gpu ../aipnd-project/flowers
```

The predict.py file accepts the following arguments:
```bash
default arguments:
  /path/to/image     path of a single image
  checkpoint         checkpoint of saved model
optional arguments:
  -h, --help         show this help message and exit
  --top_k            return top K most likely classes
  --category_names   use a mapping of categories to real names
  --gpu              use gpu processing
```

For example, to predict the top 5 classes of the image located at the path ../aipnd-project/flowers/test/10/image_07090.jpg using a mapping of categories to real names located at the path ../aipnd-project/cat_to_name.json and using gpu processing:

```bash
python predict.py --top_k 5 --category_names ../aipnd-project/cat_to_name.json --gpu ../aipnd-project/flowers/test/10/image_07090.jpg checkpoint.pth
```