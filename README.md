# 🚀 LG Aimers AI 모델 경량화 해커톤

본 프로젝트는 **EXAONE-4.0-1.2B** 모델을 대상으로 성능($PerfNorm$)과 속도($SpeedNorm$)의 균형을 최적화하는 LLM 경량화를 목표로 합니다.

---

## 🛠 1. 개발 환경 (Environment)

### **시스템 요구사항**
* **Python 버전:** `3.11.14` (반드시 일치 권장)
* **로컬 가속:** macOS(CPU) 또는 Linux(CUDA) 지원
* **평가 서버 스펙:** L4 GPU (22.4GiB VRAM), 6 vCPU, 28GB RAM

### **로컬 환경 구축 순서**

1. **저장소 클론**
   ```bash
   git clone <your-repository-url>
   cd Aimers-Hackathon
   ```

2. **Python 3.11.14 가상환경 생성 (pyenv 사용 권장)**
    ```Bash
    pyenv local 3.11.14
    python -m venv .venv
    source .venv/bin/activate  # Windows: .venv\Scripts\activate
    ```

3. **기본 도구 업데이트 및 PyTorch 설치**

    ```Bash
    pip install --upgrade pip setuptools wheel
    # 로컬 CUDA 환경에 따라 설치 (예: CUDA 12.4)
    pip install torch==2.9.0 --extra-index-url [https://download.pytorch.org/whl/cu124](https://download.pytorch.org/whl/cu124)
    ```

4. **필수 라이브러리 설치**

    ```Bash
    pip install -r requirement.txt
    ```


## 📊 2. 평가 및 규칙 (Rules)

### **최종 스코어 산식**
최종 점수는 성능과 속도를 5:5 비율로 반영합니다.

<img width="1166" height="84" alt="image" src="https://github.com/user-attachments/assets/74c080c1-b220-4ff2-8d7b-1f3d6ab66636" />


* **성능 ($PerfNorm$):** 기본 모델 대비 성능 유지 비율
* **속도 ($SpeedNorm$):** 기본 모델 대비 토큰당 추론 시간 감소 비율

### **제한 사항** 
* **전체 실행 시간:** 20분 이내 (모델 로드 ~ 추론 완료 포함)
* **제출 용량:** 압축 파일 10GB 이하 (압축 해제 후 32GB 이하)
* **제출 형식:** 허깅페이스 표준 형식의 가중치 및 설정 파일만 포함 (submit.zip)

## 📂 3. 프로젝트 구조 (Directory Structure)

    2026_AIMERS/
    ├── open/
    │   ├── base_model/   # 원본 EXAONE 모델 (수동 다운로드 필요)
    │   ├── model/        # 양자화 완료된 모델 저장 폴더
    │   └── [Baseline].ipynb  # 메인 실험 코드
    ├── results/          # 실험 히스토리 (성능 결과 저장)
    ├── requirement.txt   # 패키지 의존성
    └── README.md

## 🤝 4. 협업 규칙
1. (Collaboration)브랜치 전략: 개별 실험은 feature/기법명-이름 브랜치에서 진행합니다.
2. 코드 관리: 모델 파일(.safetensors)과 가상환경(.venv)은 절대 Push 하지 않습니다.
3. 결과 기록: results 폴더에 실험 날짜와 스코어($PerfNorm$, $SpeedNorm$)를 기록하여 공유합니다.

