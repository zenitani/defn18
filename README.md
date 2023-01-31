# Deep Flare Net (DeFN) TensorFlow 2 version

Seiji Zenitani,
Research Center for Urban Safety and Security, Kobe University, Japan

Originally developed by
Komei Sugiura,
National Institute of Information and Communications Technology, Japan
https://github.com/komeisugiura/defn18.git

## 0. License

* BSD 3-Clause Clear License

## 1. Requirements

* Ubuntu 22.04 LTS
* Python 3.9
  * numpy, pandas, scikit-learn (sklearn)
  * tensorflow 2

## 2. Install

* In the following procedure, `~/work` is assumed to be used as a working directory.

```
$ cd ~/work/
$ git clone https://github.com/zenitani/defn18.git
$ cd defn18
$ pip3 install tensorflow
[ $ pip3 install tensorflow numpy pandas sklearn ]
```

## 3. Download data

* Visit `http://wdc.nict.go.jp/IONO/wdc/solarflare/index.html` and download `defn_feature_database_v1_pl.zip`.

```
$ cd ~/work/
$ mv defn_feature_database_v1_pl.zip ./
$ unzip defn_feature_database_v1_pl.zip
(password is required)
$ cp defn_feature_database_v1/defn_input_database/charval2017X_*.csv.gz ./defn18/data/
```

## 4. Run

```
$ cd ~/work/defn18/src
$ ./deepflarenet.py
```

* The following result will be shown. This means that TSS=0.8024 is obtained by using a pretrained model.

`[008000]Acc: Tra=0.8345, Val=0.8584, Tes=0.8584, MaxVal=0.8584(0.8584), TSS=0.8024`

## 5. Training DeFN from scratch

Modify `src/deepflarenet.py`.

* Uncomment the following line to train the model
`# net1.train_model(update_interval=100)`

* Uncomment the following line to save the trained model. Current model is overwritten.
`# net1.save_model(myflag.outfile_model)`

* Comment the following two lines out, if you don't like to load the model
```
net1.load_model(myflag.infile_model)
net1.show_training_status(epoch=8000)
```

## A. References

1. N. Nishizuka, K. Sugiura, Y. Kubo, M. Den, and M. Ishii, "Deep Flare Net (DeFN) Model for Solar Flare Prediction", The Astrophysical Journal, Vol. 858, Issue 2, 113 (8pp), 2018. DOI: 10.3847/1538-4357/aab9a7

# Local Variables:
# coding: utf-8
# End:
