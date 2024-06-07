<h1 align="center">
  <br>
  CLIPAG: Towards Generator-Free Text-to-Image Generation
  <br>
</h1>
<p align="center">
  <a href="https://royg27.github.io/">Roy Ganz</a> •
  <a href="https://elad.cs.technion.ac.il/">Michael Elad</a>
</p>
<p align="center">
[WACV 2024] Official Code Repository of <a href="https://arxiv.org/abs/2306.16805">CLIPAG: Towards Generator-Free Text-to-Image Generation</a>.
</p>

> **Abstract:** *Perceptually Aligned Gradients (PAG) refer to an intriguing property observed in robust image classification models, wherein their input gradients align with human perception and pose semantic meanings. While this phenomenon has gained significant research attention, it was solely studied in the context of unimodal vision-only architectures. 
In this work, we extend the study of PAG to Vision-Language architectures, which form the foundations for diverse image-text tasks and applications. Through an adversarial robustification finetuning of CLIP, we demonstrate that robust Vision-Language models exhibit PAG in contrast to their vanilla counterparts.
This work reveals the merits of CLIP with PAG (CLIPAG) in several vision-language generative tasks. Notably, we show that seamlessly integrating CLIPAG in a "plug-n-play" manner leads to substantial improvements in vision-language generative applications.  Furthermore, leveraging its PAG property, CLIPAG enables text-to-image generation without any generative model, which typically requires huge generators.*

## Table of Contents
- [Boosting CLIPDraw](#boosting-clipdraw)
- [Generator-Free Text-to-Image Generation](#generator-free-text-to-image-generation)
- [CLIPAG Pretrained Model](#clipag-pretrained-model)
- [Citation](#citation)

## Boosting CLIPDraw
The entire code for enhancing CLIPDraw using CLIPAG is contained in a single self-contained colab notebook - `CLIPAG+CLIPDraw.ipynb`.

<p align="center">
  <img src="https://github.com/royg27/CLIPAG/blob/main/CLIPDraw.png" height="300">
</p>

## Generator-Free Text-to-Image Generation
Our text-to-image generation framework is in `CLIPAG_T2I.ipynb`.

<p align="center">
  <img src="https://github.com/royg27/CLIPAG/blob/main/CLIPAG_T2I.png" height="400">
</p>

## CLIPAG Pretrained Model
The provided notebooks contain download instructions and code for our pretrained model, supported by the open-clip library. For simplicity, the model weights are available here - [CLIPAG_ViTB32.pt](https://zenodo.org/records/10446026/files/CLIPAG_ViTB32.pt). 
To load the pretrained model, use the following code snippet:
```python
import open_clip

model, preprocess_train, preprocess_test = open_clip.create_model_and_transforms(
    'ViT-B/32',
    pretrained='CLIPAG_ViTB32.pt',
    precision="amp",
    device="cuda"
)

tokenizer = open_clip.get_tokenizer('ViT-B-32')
model.eval()
```
## Citation
If you find this code or our model useful for your research, please consider citing it.

```bibtex
@inproceedings{ganz2024clipag,
    title={CLIPAG: Towards Generator-Free Text-to-Image Generation},
    author={Ganz, Roy and Elad, Michael},
    booktitle={Proceedings of the IEEE/CVF Winter Conference on Applications of Computer Vision},
    pages={3843--3853},
    year={2024}
}
