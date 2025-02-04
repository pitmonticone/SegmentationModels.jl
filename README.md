# SegmentationModels

[![Stable](https://img.shields.io/badge/docs-stable-blue.svg)](https://maxfreu.github.io/SegmentationModels.jl/stable)
[![Dev](https://img.shields.io/badge/docs-dev-blue.svg)](https://maxfreu.github.io/SegmentationModels.jl/dev)
[![Build Status](https://github.com/maxfreu/SegmentationModels.jl/workflows/CI/badge.svg)](https://github.com/maxfreu/SegmentationModels.jl/actions)

The aim of this package is to provide functionality similar to https://github.com/qubvel/segmentation_models.pytorch. Pull requests are very welcome.


## Supported Architectures
- UNet

## Supported Backbones
- VGG
- ResNet
- ResNeXt
- MobileNetv1-3

A subset of the classifiers in [Metalhead.jl](https://github.com/FluxML/Metalhead.jl) is supported. 
Pre-training is supported as far as its supported there.

## Supported Features
- Using pretrained models
- Setting the number of output classes
- Changing the number of input layers, e.g. to ingest multispectral images
- Setting the final activation


## Usage

```julia
using Flux
using SegmentationModels

data = rand(Float32, 256, 256, 8, 1) |> gpu
unet = UNet(8,1; init_channels=16, stages=4) |> gpu  # returns unet with simple double-conv backbone as a placeholder

# or
unet = UNet(ResNet50(;pretrain=true); num_classes=1337, input_channels=4) |> gpu

unet(data)
```

## ToDo
- Add other segmentation architectures
- Flesh out docs
- Flesh out tests
