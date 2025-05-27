# NAVER CLOUD CAMP 정보보안 3기 3조 NOCHULBAN (3차 프로젝트)
## 공개 출처 기반 수집 파일에 대한 악성코드 탐지 시스템 개발
<div align="center">
  <img src="https://github.com/user-attachments/assets/a3819795-5724-472c-a233-5d41daca6ed9" width="500"/>
</div>

## 프로젝트 개요
본 프로젝트는 공개 저장소(S3 버킷 등)에서 수집된 문서를 대상으로 개인정보 포함 여부를 자동 탐지하고, 발견된 개인정보를 블러 처리하여 비식별화하는 시스템을 개발하는 것을 목표로 합니다.
OCR을 통하여 비정형 문서에서도 개인정보를 탐지하며, 탐지된 부분을 자동 비식별화합니다.

## 주요 기능
- 파일 확장자 기반 처리(텍스트 파싱 or 이미지화)
- OCR 및 정규표현식 기반 개인정보 탐지
- OpenCV 기반 개인정보 블러 처리
- 탐지 및 처리 결과 저장


## 사용 기술
- Python 3.10
- OpenCV, re(정규표현식)
- NAVER CLOVA OCR
-	MySQL
  
## 디렉터리 구조
```
ncb/
├── connectDatabase.py       # DB 연결 및 쿼리 처리
├── convertDoc.py            # 문서 파일(PDF, DOC, XLS 등) 이미지 변환
├── ocrProcess.py            # OCR 수행 및 개인정보 탐지
├── infoBlur.py              # 탐지된 개인정보 블러 처리 (OpenCV)
├── requirements.txt         # 의존성 목록
```

## 실행 방법 (api key 추가 필요)
```
# 가상환경 생성 및 실행(python 3.10)
source venv/bin/activate

# 패키지 설치
pip install -r requirements.txt

# 파이프라인 실행
python ocrProcess.py
```

## 데이터베이스 구성
- normal_docs : 저장소에서 수집된 파일 메타 정보 (경로, 이름, 크기 등)
<div align="center">
  <img width="945" alt="스크린샷 2025-05-27 오전 9 40 40" src="https://github.com/user-attachments/assets/22701cc2-2cf1-46e2-8115-c14c4ff68d7f" />
</div>

## 시스템 흐름도
[normal_docs 불러오기] → [확장자 기반 처리] → [OCR + GPT 개인정보 탐지] → [블러 처리]
