# Docker image for Fooocus: Focus on prompting and generating

## Installs

* Ubuntu 22.04 LTS
* CUDA 11.8
* Python 3.10.12
* [Fooocus](
  https://github.com/lllyasviel/Fooocus) 2.1.860
* Torch 2.1.0
* xformers
* [runpodctl](https://github.com/runpod/runpodctl)
* [croc](https://github.com/schollz/croc)
* [rclone](https://rclone.org/)

## Available on RunPod

This image is designed to work on [RunPod](https://runpod.io?ref=2xxro4sy).
You can use my custom [RunPod template](
https://runpod.io/gsc?template=ileyo7dtpj&ref=2xxro4sy)
to launch it on RunPod.

## Running Locally

### Install Nvidia CUDA Driver

- [Linux](https://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html)
- [Windows](https://docs.nvidia.com/cuda/cuda-installation-guide-microsoft-windows/index.html)

### Start the Docker container

```bash
docker run -d \
  --gpus all \
  -v /workspace \
  -p 3000:3001 \
  -p 8888:8888 \
  -e JUPYTER_PASSWORD=Jup1t3R! \
  roomber/fooocus:latest
```

You can obviously substitute the image name and tag with your own.

### Ports

| Connect Port | Internal Port | Description |
|--------------|---------------|-------------|
| 3000         | 3001          | Fooocus     |
| 8888         | 8888          | Jupyter Lab |

### Environment Variables

| Variable           | Description                                  | Default   |
|--------------------|----------------------------------------------|-----------|
| JUPYTER_PASSWORD   | Password for Jupyter Lab                     | Jup1t3R!  |
| DISABLE_AUTOLAUNCH | Disable Web UIs from launching automatically | (not set) |
| PRESET             | Fooocus Preset (anime/realistic)             | (not set) |

## Logs

Fooocus creates a log file, and you can tail the log instead of
killing the service to view the logs.

| Application | Log file                      |
|-------------|-------------------------------|
| Fooocus     | /workspace/logs/fooocus.log   |

For example:

```bash
tail -f /workspace/logs/fooocus.log
```