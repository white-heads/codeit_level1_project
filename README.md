# 경구약제 이미지 객체 검출 프로젝트
## [kaggle]코드잇 스프린트 AI 엔지니어링 2기 초급 프로젝트
이번 프로젝트의 목표는 사진 속에 있는 최대 4개의 알약의 이름(클래스)과 위치(바운딩 박스)를 검출하는 것입니다.

white heads(1팀)

## 디렉토리 아키텍쳐
```
my_object_detection_project/
├── README.md
│
├── EDA.ipynb
│
├── config/
│   ├── baseline.yaml             # YOLOv8_base 하이퍼파라미터 설정 파일
│   ├── exp.yaml                  # YOLOv8_exp 하이퍼파라미터 설정 파일
│   ├── data.yaml                 # YOLO 모델에 들어가는 train/val/test 경로
│   │                             # 및 classes, np 정의한 YAML
│   └── path.yaml                 # path에 대해 설정한 파일
│
├── utils/                        # 각종 유틸리티 코드
│   ├── data_utils.ipynb          # 데이터 로드, 분할, 증강 관련 함수
│   └── split_data.ipynb          # train, val 파일 분리
├── models/
│   ├── yolo/                     # YOLO best model 스크립트
│   │   ├── YOLOv8.ipynb          # YOLOv8 모델 스크립트   
│   │   └── yolov11.ipynb
│   └── pretrained/               # 미리 학습된(pretrained) 백본(backbone) 가중치
│       ├── yolov8n.pt
│       ├── yolov8s.pt
│       └── yolo11n.pt
├── experiments/                  # 실험용(다양한 하이퍼파라미터 실험) 폴더
│   ├── name1/                    # 팀원 1
│   │   ├── hyparameter.yaml      # 실험 파라미터 저장
│   │   ├── results              # 실험 결과(결과 그래프)
│   │   └── best_model.pt         # 베스트 모델 가중치
│   ├── name2/                    # 팀원 2
│       └── …
└── results/                      # 베스트 모델 학습 결과 폴더
    ├── predict/
    └── train/
        ├── exp_1
        ├── exp_2
        └── …
```

## 사용한 데이터
원본 데이터 출처: Ai Hub 경구약제 이미지 데이터를 가공
추가 데이터 출처: Ai Hub에 있는 데이터중 원본 데이터 속 73개의 클래스만 포함하고 있는 데이터를 추가
train_images - 훈련 데이터(이미지)
train_annotations - 훈련 데이터(annotation)
test_images - 테스트 데이터(이미지)
