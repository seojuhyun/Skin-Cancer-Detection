# 🧠 Vision Transformer (ViT) for Skin Cancer Detection  

이 프로젝트는 논문 *"An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale (ICLR, 2021)"* 에서 제안된 Vision Transformer(ViT) 아키텍처를 기반으로, ISIC 2024 피부암 데이터셋에서 양성(Benign) / 악성(Malignant) 피부 병변을 분류하기 위한 모델을 구현한 과제입니다.

  <div align= 'center'>
  <img width="632" alt="image" src="https://github.com/user-attachments/assets/ec8a1aac-51dd-49cf-9d31-7eaeb1bed23d" />
  </div>




## 📁 Dataset

- **ISIC 2024 - Skin Cancer Detection with 3D-TBP**  
  https://challenge2024.isic-archive.com/
- 클래스: `benign (양성)` / `malignant (악성)`
  
[benign (양성)]

<p align="center">
  <img src="https://github.com/user-attachments/assets/73b92ce5-4d03-4043-aee1-b713189ae4cc" width="100">
  <img src="https://github.com/user-attachments/assets/1c45cb61-4c05-41e9-b23f-6cde032ca908" width="100"/>
</p>



[malignant (악성)]
  
<p align="center">
  <img src="https://github.com/user-attachments/assets/114ff4ec-7f65-44fd-b0ca-b4366b9922de" width="100">
  <img src="https://github.com/user-attachments/assets/45e67cdf-4469-4e42-ba3d-fcdcf41ecbaf" width="100"/>
</p>


- 입력 이미지 크기: `288 × 288`
- 데이터 불균형 존재 → Train Class Count: {0: 240,389,  1: 246}
 



## 🧠 Model Architecture

- **Backbone**: Vision Transformer (ViT)
- Patch Size: `18`
- Channel: `3`
- Embedding Size: `128`
- Image Size: `288 × 288`
- Depth (Transformer Layers): `8`
- Number of Classes: `2`


## 🔹 주요 구성 요소

- **Patch & Position Embedding**
- **Multi-Head Self-Attention**
  - Num Heads: `8`
  - Q/K/V Shape: `torch.Size([32, 8, 257, 16])`
- **Transformer Encoder**
  - Embedding Size: `128`
  - Feedforward Expansion: `×4`



## 🏋️‍♂️ Training Configuration

- Batch Size: `64`
- Loss Function: CrossEntropyLoss
- Evaluation Metric: AUC-ROC, Precision, Recall, F1-score



## 📊 Results

- **AUC-ROC**: `0.92`
- **Accuracy**: `0.99`
- **Recall**: `0.63`
- **Precision, F1-score**는 낮은 편 (이상 클래스 비율 0.001로 인한 영향)
- 전체적으로 정상/이상 구분을 잘 학습함

> ⚠️ 이상 클래스에 대한 민감도(Recall)는 63%로 양호하지만, 데이터 불균형으로 인해 Precision 및 F1-score는 상대적으로 낮음.



## 🔹 More Details

<div align= 'center'>  
  <img width="677" alt="스크린샷 2025-07-02 오후 1 44 13" src="https://github.com/user-attachments/assets/af287246-9082-48fa-a669-fee1326c1bee" />
  <img width="676" alt="스크린샷 2025-07-02 오후 1 44 59" src="https://github.com/user-attachments/assets/feb27549-1edc-4a93-94d3-2705751f06ec" />
</div>



## 📚 References

- Dosovitskiy, Alexey, et al.  
  *An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale.*  
  ICLR, 2021. [arXiv:2010.11929](https://arxiv.org/abs/2010.11929)

- Vaswani, Ashish, et al.  
  *Attention is All You Need.*  
  NeurIPS, 2017.


