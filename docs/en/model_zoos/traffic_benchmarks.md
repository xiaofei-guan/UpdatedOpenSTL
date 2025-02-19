# Traffic Prediction Benchmarks

**We provide benchmark results of spatiotemporal prediction learning (STL) methods on popular traffic prediction datasets. More STL methods will be supported in the future. Issues and PRs are welcome!**

<details open>
<summary>Currently supported spatiotemporal prediction methods</summary>

- [x] [ConvLSTM](https://arxiv.org/abs/1506.04214) (NeurIPS'2015)
- [x] [PredRNN](https://dl.acm.org/doi/abs/10.5555/3294771.3294855) (NeurIPS'2017)
- [x] [PredRNN++](https://arxiv.org/abs/1804.06300) (ICML'2018)
- [x] [E3D-LSTM](https://openreview.net/forum?id=B1lKS2AqtX) (ICLR'2018)
- [x] [MIM](https://arxiv.org/abs/1811.07490) (CVPR'2019)
- [x] [CrevNet](https://openreview.net/forum?id=B1lKS2AqtX) (ICLR'2020)
- [x] [PhyDNet](https://arxiv.org/abs/2003.01460) (CVPR'2020)
- [x] [MAU](https://openreview.net/forum?id=qwtfY-3ibt7) (NeurIPS'2021)
- [x] [PredRNN.V2](https://arxiv.org/abs/2103.09504v4) (TPAMI'2022)
- [x] [SimVP](https://arxiv.org/abs/2206.05099) (CVPR'2022)
- [x] [SimVP.V2](https://arxiv.org/abs/2211.12509) (ArXiv'2022)
- [ ] [TAU](https://arxiv.org/abs/2206.12126) (CVPR'2023)

</details>

<details open>
<summary>Currently supported MetaFormer models for SimVP</summary>

- [x] [ViT](https://arxiv.org/abs/2010.11929) (ICLR'2021)
- [x] [Swin-Transformer](https://arxiv.org/abs/2103.14030) (ICCV'2021)
- [x] [MLP-Mixer](https://arxiv.org/abs/2105.01601) (NeurIPS'2021)
- [x] [ConvMixer](https://arxiv.org/abs/2201.09792) (Openreview'2021)
- [x] [UniFormer](https://arxiv.org/abs/2201.09450) (ICLR'2022)
- [x] [PoolFormer](https://arxiv.org/abs/2111.11418) (CVPR'2022)
- [x] [ConvNeXt](https://arxiv.org/abs/2201.03545) (CVPR'2022)
- [x] [VAN](https://arxiv.org/abs/2202.09741) (ArXiv'2022)
- [x] [IncepU (SimVP.V1)](https://arxiv.org/abs/2206.05099) (CVPR'2022)
- [x] [gSTA (SimVP.V2)](https://arxiv.org/abs/2211.12509) (ArXiv'2022)
- [x] [HorNet](https://arxiv.org/abs/2207.14284) (NeurIPS'2022)
- [x] [MogaNet](https://arxiv.org/abs/2211.03295) (ArXiv'2022)

</details>


## TaxiBJ Benchmarks

We provide traffic benchmark results on the popular [TaxiBJ](https://arxiv.org/abs/1610.00081) dataset using $4\rightarrow 4$ frames prediction setting. Metrics (MSE, MAE, SSIM, pSNR) of the final models are reported in three trials. Parameters (M), FLOPs (G), and V100 inference FPS (s) are also reported for all methods. All methods are trained by Adam optimizer with Cosine Annealing scheduler (5 epochs warmup and min lr is 1e-6) and **single GPU**.

### **STL Benchmarks on TaxiBJ**

For a fair comparison of different methods, we report final results when models are trained to convergence. We provide config files in [configs/taxibj](https://github.com/chengtan9907/OpenSTL/configs/taxibj).

| Method       |  Setting | Params |  FLOPs | FPS |   MSE  |  MAE  |  SSIM  |  PSNR |   Download   |
|--------------|:--------:|:------:|:------:|:---:|:------:|:-----:|:------:|:-----:|:------------:|
| ConvLSTM-S   | 50 epoch | 14.98M | 20.74G |  46 | 0.3358 | 15.32 | 0.9836 | 39.73 | model \| log |
| E3D-LSTM\*   | 50 epoch | 50.99M | 98.19G |  60 | 0.3421 | 14.96 | 0.9842 | 39.92 | model \| log |
| MIM          | 50 epoch |  49.2M |  1858G |  39 | 0.3110 | 14.96 | 0.9847 | 39.88 | model \| log |
| PredRNN      | 50 epoch | 23.66M | 42.40G |  22 | 0.3194 | 15.31 | 0.9838 | 39.79 | model \| log |
| PredRNN++    | 50 epoch | 38.40M | 62.95G |  15 | 0.3348 | 15.37 | 0.9834 | 39.76 | model \| log |
| PredRNN.V2   | 50 epoch | 23.67M | 42.63G |  22 | 0.3834 | 15.55 | 0.9826 | 39.75 | model \| log |
| SimVP+IncepU | 50 epoch | 13.79M | 3.61G |  533 | 0.3282 | 15.45 | 0.9835 | 39.72 | model \| log |
| SimVP+gSTA-S | 50 epoch |  9.96M | 2.62G | 1217 | 0.3246 | 15.03 | 0.9844 | 39.95 | model \| log |

### **Benchmark of MetaFormers on SimVP**

Similar to [Moving MNIST Benchmarks](#moving-mnist-benchmarks), we benchmark popular Metaformer architectures on [SimVP](https://arxiv.org/abs/2211.12509) with training times of 50-epoch. We provide config files in [configs/taxibj/simvp](https://github.com/chengtan9907/OpenSTL/configs/taxibj/simvp/).

| MetaFormer       |  Setting | Params | FLOPs |  FPS |   MSE  |  MAE  |  SSIM  |  PSNR |   Download   |
|------------------|:--------:|:------:|:-----:|:----:|:------:|:-----:|:------:|:-----:|:------------:|
| IncepU (SimVPv1) | 50 epoch | 13.79M | 3.61G |  533 | 0.3282 | 15.45 | 0.9835 | 39.72 | model \| log |
| gSTA (SimVPv2)   | 50 epoch |  9.96M | 2.62G | 1217 | 0.3246 | 15.03 | 0.9844 | 39.95 | model \| log |
| ViT              | 50 epoch |  9.66M | 2.80G | 1301 | 0.3171 | 15.15 | 0.9841 | 39.89 | model \| log |
| Swin Transformer | 50 epoch |  9.66M | 2.56G | 1506 | 0.3128 | 15.07 | 0.9847 | 39.89 | model \| log |
| Uniformer        | 50 epoch |  9.52M | 2.71G | 1333 | 0.3268 | 15.16 | 0.9844 | 39.89 | model \| log |
| MLP-Mixer        | 50 epoch |  8.24M | 2.18G | 1974 | 0.3206 | 15.37 | 0.9841 | 39.78 | model \| log |
| ConvMixer        | 50 epoch |  0.84M | 0.23G | 4793 | 0.3634 | 15.63 | 0.9831 | 39.69 | model \| log |
| Poolformer       | 50 epoch |  7.75M | 2.06G | 1827 | 0.3273 | 15.39 | 0.9840 | 39.75 | model \| log |
| ConvNeXt         | 50 epoch |  7.84M | 2.08G | 1918 | 0.3106 | 14.90 | 0.9845 | 39.99 | model \| log |
| VAN              | 50 epoch |  9.48M | 2.49G | 1273 | 0.3125 | 14.96 | 0.9848 | 39.95 | model \| log |
| HorNet           | 50 epoch |  9.68M | 2.54G | 1350 | 0.3186 | 15.01 | 0.9843 | 39.91 | model \| log |
| MogaNet          | 50 epoch |  9.96M | 2.61G | 1005 | 0.3114 | 15.06 | 0.9847 | 39.92 | model \| log |

<p align="right">(<a href="#top">back to top</a>)</p>
