# 증강 기법에 따른 자연어 생성 성능 비교 웹 애플리케이션

## 소개
이 프로젝트는 증강 기법에 따른 자연어 생성 성능 비교 웹 애플리케이션입니다.
기본 모델은 KoGPT2 모델을 사용합니다.

사용한 데이터 셋인 소상공인 고객 주문 질의 데이터셋은 다음 링크에서 다운받을 수 있습니다.
https://aihub.or.kr/aihubdata/data/view.do?currMenu=115&topMenu=100&aihubDataSe=data&dataSetSn=102

1. 증강 기법은 다음과 같습니다.
- Synonym Replacement : 단어를 비슷한 의미를 가진 단어로 대체
- Random Insertion : 단어를 문장 중간에 무작위로 삽입
- Random Swap : 단어를 문장 중간에 무작위로 교환
- Random Deletion : 단어를 문장 중간에 무작위로 삭제

2. 성능 지표는 다음과 같습니다.
- Perplexity : 언어 모델이 테스트 데이터(참조 텍스트)를 얼마나 잘 예측하는지 나타내는 척도이다 / 성능이 높을수록 낮은 값
- BLEU : 기계 번역에서 흔히 쓰이며, 생성 번역문과 참조 번역문 간의 n-그램 매칭 정도에 초점을 둔다
- ROUGE : 요약 분야에서 주로 사용하며, 참조 요약문과의 n-그램, 단어나 구문 수준의 겹침 정도를 측정한다
- METEOR : BLEU의 보완책으로, 단순 n-그램 매칭을 넘어 형태소 분석, 동의어 매칭 등을 고려한다
- CHRF : 문자 단위 n-그램 일치도를 통해 다양한 언어 형식 변화를 더 유연하게 반영한다

3. TSNE 시각화를 통해 데이터셋을 시각화합니다.
- 증강 데이터 셋과 기본 데이터 셋을 비교하여 증강 데이터셋의 신뢰도를 확인합니다.

4. 증강된 데이터셋 예시를 확인할 수 있으며, 증강된 데이터셋을 다운로드 받을 수 있습니다.

5. 증강된 데이터셋으로 fine-tuning된 모델을 통해 채팅을 주고받을 수 있습니다.

## 시작하기

### 필요 조건
- Python 3.7 이상
- Flask

### 설치 방법
1. 이 저장소를 클론합니다.  
```bash
git clone https://github.com/seyun0714/HW5.git
cd HW5
```

2. 가상 환경을 만들고 활성화합니다.
```bash
python -m venv venv
source venv/Scripts/activate
```

3. 필요한 패키지를 설치합니다.   
```bash
pip install -r requirements.txt
```

## 사용 방법
애플리케이션을 실행하려면 다음 명령어를 사용하세요:
```bash
python app.py
```

애플리케이션은 기본적으로 `http://localhost:5000`에서 실행됩니다.

## 주요 기능
- **홈페이지**: 기본 라우트로 접속 시 파일 업로드 페이지로 이동합니다.
- **파일 업로드**: 파일 업로드 페이지에서 파일을 업로드하고 대시보드로 이동합니다.
- **데이터셋 증강**: 업로드한 파일을 증강하여 데이터셋을 생성합니다.
- **대시보드**: 대시보드 페이지에서 데이터셋 증강 및 시각화 결과를 확인할 수 있습니다.
- **데이터셋 시각화**: perplexity, BLEU, ROUGE, METEOR, CHRF, TSNE 등을 시각화합니다.
- **데이터셋 다운로드**: 증강된 데이터셋을 다운로드합니다.
- **모델 테스트**: 증강된 데이터셋으로 fine-tuning된 모델을 통해 채팅을 주고받을 수 있습니다.

## 기술 스택
- **Frontend**: HTML, CSS, JavaScript, Bootstrap, d3.js
- **Backend**: Flask