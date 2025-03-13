# 🍚 코매칭 ver3.5 (Backend) (개인프로젝트)

> 학교 동아리 축제 기간에 새내기들에게 동아리를 홍보하기 위해 제작된 밥친구 매칭 서비스의 백엔드 서버입니다.

## 🖥 프로젝트 소개

**코매칭 ver3.5**는 학교 동아리 축제 기간에 새내기들과 기존 동아리 구성원을 연결하여 밥친구를 매칭하는 웹 기반 서비스입니다. 개인 프로젝트로 제작되었으며, 본 문서는 백엔드 개발 내용을 중점적으로 다루고 있습니다.

## 🚀 주요 기능

- **사용자 인증**: 카카오 OAuth 로그인 및 JWT를 통한 안전한 사용자 인증 처리
- **매칭 서비스**: 사용자의 입학 연도, 나이 등 정보를 기반으로 최적의 밥친구를 자동 매칭
- **회원 정보 관리**: 회원 가입 및 프로필 정보 관리 기능 제공
- **자동화 배포**: Render 플랫폼을 활용한 CI/CD 파이프라인 구축
- 
---

## 🛠️ Tech Stack

<p align="center">
  <!-- Node.js -->
  <img src="https://img.shields.io/badge/-Node.js-339933?style=flat-square&logo=Node.js&logoColor=white" width="120" />
  <!-- Express -->
  <img src="https://img.shields.io/badge/-Express-000000?style=flat-square&logo=Express&logoColor=white" width="120" />
  <!-- MongoDB -->
  <img src="https://img.shields.io/badge/-MongoDB-47A248?style=flat-square&logo=MongoDB&logoColor=white" width="120" />
  <!-- Mongoose -->
  <img src="https://img.shields.io/badge/-Mongoose-880000?style=flat-square&logo=Mongoose&logoColor=white" width="120" />
</p>

<p align="center">
  <!-- JavaScript -->
  <img src="https://img.shields.io/badge/-JavaScript-F7DF1E?style=flat-square&logo=JavaScript&logoColor=black" width="120" />
  <!-- JWT -->
  <img src="https://img.shields.io/badge/-JWT-000000?style=flat-square&logo=JSON%20web%20tokens&logoColor=white" width="120" />
  <!-- Passport -->
  <img src="https://img.shields.io/badge/-Passport-34E27A?style=flat-square&logo=Passport&logoColor=white" width="120" />
  <!-- Kakao -->
  <img src="https://img.shields.io/badge/-Kakao%20OAuth-FFCD00?style=flat-square&logo=Kakao&logoColor=3C1E1E" width="120" />
</p>

<p align="center">
  <!-- Render -->
  <img src="https://img.shields.io/badge/-Render-46E3B7?style=flat-square&logo=Render&logoColor=white" width="120" />
  <!-- GitHub -->
  <img src="https://img.shields.io/badge/-GitHub-181717?style=flat-square&logo=GitHub&logoColor=white" width="120" />
  <!-- dotenv -->
  <img src="https://img.shields.io/badge/-dotenv-ECD53F?style=flat-square&logo=dotenv&logoColor=black" width="120" />
  <!-- Cors -->
  <img src="https://img.shields.io/badge/-CORS-CC6699?style=flat-square&logoColor=white" width="120" />
</p>

---

### ⚡ 기술 스택 설명

- **Node.js & Express**: 백엔드 서버와 RESTful API 구성
- **MongoDB & Mongoose**: NoSQL 데이터베이스 관리
- **JWT (JSON Web Token)**: 사용자 인증 토큰 생성 및 검증
- **Passport & Kakao OAuth**: 카카오 계정을 이용한 소셜 로그인 인증
- **Render**: CI/CD 및 자동 배포 서비스
- **dotenv & Cors**: 환경 변수 관리 및 교차 출처 리소스 공유 처리


## 🗃 프로젝트 구조

```
├── config
│   ├── db.js         # MongoDB 연결 설정
│   ├── jwt.js        # JWT 생성 및 검증
│   └── passport.js   # Passport OAuth 설정
│
├── models
│   └── User.js       # 사용자 정보 스키마 정의
│
├── routes
│   ├── auth.js       # 인증 관련 라우팅
│   ├── matching.js   # 매칭 기능 라우팅
│   └── user.js       # 사용자 정보 관련 라우팅
│
├── scripts           # DB 초기화 및 테스트 데이터 추가 스크립트
│
├── .env              # 환경 변수 파일
├── package.json
└── server.js         # 서버 시작 파일
```

## 🚩 설치 및 실행 방법

### 1. 프로젝트 클론

```bash
git clone https://github.com/<your-username>/comatching-backend.git
cd comatching-backend
```

### 2. 의존성 설치

```bash
npm install
```

### 3. 환경 변수 설정 (.env 파일)

```env
PORT=5000
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret
FRONTEND_URL=https://your-frontend-url.com
```

### 4. 서버 실행

```bash
npm run dev
```

## 📌 API 엔드포인트

| Method | URL                             | Description                      |
|--------|---------------------------------|----------------------------------|
| GET    | /auth/kakao                     | 카카오 로그인 페이지 리다이렉트        |
| GET    | /auth/kakao/callback            | 카카오 로그인 인증 콜백 처리           |
| GET    | /auth/logout                    | 사용자 로그아웃 처리                |
| GET    | /auth/is-first-login            | 사용자의 첫 로그인 여부 확인          |
| POST   | /auth/signup                    | 사용자 회원가입 및 정보 업데이트       |
| GET    | /api/matching                   | 사용자 매칭 요청                   |
| GET    | /api/matching/matched-users     | 매칭된 사용자 목록 조회              |

## 🔐 인증 방식

- **카카오 OAuth**를 사용한 소셜 로그인
- 로그인 성공 시 JWT 기반의 accessToken을 발급하고 쿠키에 저장
- 이후 요청마다 JWT 토큰의 유효성을 검사하여 보안 유지

## 🎯 데이터 모델

### 사용자(User)

- kakaoId: String
- admissionYear: String
- age: String
- hobby: Array[String]
- comment: String
- contactFrequency: String
- contact_id: String
- major: String
- mbti: String
- song: String
- isFirstLogin: Boolean
- isFirstMatch: Boolean
- matchedUsers: Array[ObjectId(User)]

## 🚧 CI/CD 배포 과정

- Render 플랫폼을 활용하여 자동화된 CI/CD 구축
- GitHub 저장소와 연동되어 커밋마다 자동 빌드 및 배포 수행
- HTTPS 및 SSL 인증서를 자동 제공하여 보안성 보장



## 📚 공부한 내용

- [Render란?](https://ojspp41.tistory.com/81)
- [JWT토큰](https://ojspp41.tistory.com/80)
- [카카오 로그인](https://ojspp41.tistory.com/79)
- [몽고디비 추가 자동화](https://ojspp41.tistory.com/78)
- [MongoDB, Mongoose](https://ojspp41.tistory.com/77)
- [등록 API](https://ojspp41.tistory.com/76)
- [서버 URL 및 엔드포인트](https://ojspp41.tistory.com/75)
- [Passport](https://ojspp41.tistory.com/74)
- [$ne와 $nin](https://ojspp41.tistory.com/73)
- [node.js 카카오 로그인](https://ojspp41.tistory.com/72)
- [Node.js 모듈 시스템 개요](https://ojspp41.tistory.com/71)
- [User 총 개수 조회 기능 (/api/participations) 정리](https://ojspp41.tistory.com/70)

