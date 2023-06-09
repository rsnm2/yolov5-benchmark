# Benchmarking YOLOv5

## Benchmark DeepSparse

Install:
```
pip install deepsparse-nightly[yolo]==1.5.0.20230420
```

Download image:
```bash
wget -O basilica.jpg https://raw.githubusercontent.com/neuralmagic/deepsparse/main/src/deepsparse/yolo/sample_images/basilica.jpg
```

Run the following for usage:

```bash
python3 benchmark-deepsparse.py --help
```

Runs at batch=1:
```bash
OMP_NUM_THREADS=1 python3 benchmark-deepsparse.py  --do_engine --model_path zoo:cv/detection/yolov5-x6/pytorch/ultralytics/voc/pruned75_quant-none --img_sz 1280
```

Runs at batch=32:
```bash
OMP_NUM_THREADS=1  python3 benchmark-deepsparse.py --do_engine --model_path zoo:cv/detection/yolov5-x6/pytorch/ultralytics/voc/pruned75_quant-none --img_sz 1280 --batch_size 32 --iterations 5
```

## Benchmark YOLOv5

Clone the Ultralytics repo.

```bash
git clone https://github.com/ultralytics/yolov5.git
cd yolov5
pip install -r requirements.txt
cd ..
```

Download image:
```bash
wget -O basilica.jpg https://raw.githubusercontent.com/neuralmagic/deepsparse/main/src/deepsparse/yolo/sample_images/basilica.jpg
```

Run the following for usage:

```bash
python3 benchmark-pytorch.py --help
```

Runs at batch=1:
```bash
python3 benchmark-pytorch.py --do_model --model_name yolov5x6 --img_sz 1280
```

Runs at batch=16:
```bash
python3 benchmark-pytorch.py --do_model --model_name yolov5x6 --img_sz 1280 --batch_size 16 --iterations 5
```
