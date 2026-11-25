# 장유 맛집 탐험대 — GitHub Pages 설치

```
github 저장소 (이 폴더 전체를 올림)
├─ index.html            ← 앱 화면
├─ config.js             ← 앱스스크립트 웹앱 주소 한 줄만 고치면 됨
├─ manifest.webmanifest  ← 홈 화면에 앱처럼 추가
├─ icons/                ← 아이콘 (svg·png)
├─ .nojekyll
└─ apps-script/          ← GitHub에 안 올려도 됨. 구글 스크립트에 붙여 넣을 3개 파일
   ├─ Code.gs
   ├─ Index.html
   └─ appsscript.json
```

## 1단계. 구글 앱스스크립트 (서버)
1. script.google.com → 새 프로젝트
2. `Code.gs` 내용을 통째로 붙여 넣기
3. 파일 추가(＋) → HTML → 이름 `Index` → `apps-script/Index.html` 내용 붙여 넣기
4. **appsscript.json 넣기**: 왼쪽 ⚙ 프로젝트 설정 → **"appsscript.json" 매니페스트 파일 표시** 체크 →
   편집기로 돌아와 `appsscript.json` 이 보이면 `apps-script/appsscript.json` 내용으로 통째로 교체
5. 함수 `setup` 실행 → 권한 승인 (시트·사진 폴더 자동 생성)
6. 배포 → 새 배포 → 유형 **웹 앱** → 실행: **나** / 액세스: **모든 사용자** → 배포
7. 나오는 웹 앱 주소(`https://script.google.com/macros/s/…/exec`) 복사

✔ 배포 확인: 웹 앱 주소 끝에 `?ping=1` 을 붙여 열었을 때 `{"ok":true,... "version":"2026-11-25-f","hasPost":true}` 가 보이면 새 코드가 적용된 것입니다. 앱 화면이 그대로 나오면 아직 옛 버전입니다.

※ 나중에 `Code.gs`를 고치면 배포 → 배포 관리 → 수정 → **새 버전**으로 다시 배포해야 반영됩니다.

## 2단계. GitHub (화면)
1. `config.js` 를 열어 `apiUrl` 에 위 웹 앱 주소 붙여 넣기
2. 저장소를 만들고 `index.html`, `config.js`, `manifest.webmanifest`, `icons/`, `.nojekyll` 올리기
3. 저장소 Settings → Pages → Branch: `main` / `/ (root)` → Save
4. 잠시 후 `https://<내계정>.github.io/<저장소>/` 로 접속

휴대폰에서 이 주소를 열고 "홈 화면에 추가"를 누르면 아이콘이 깔립니다.

## 참고
- 업로드·수정·삭제 비밀번호는 `Code.gs`의 `adminPw_()` 안(7008)에 있습니다. 구글 쪽에만 있으니 GitHub 저장소가 공개여도 노출되지 않습니다.
- `apps-script/` 폴더에는 비밀번호가 든 `Code.gs`가 있으므로 **GitHub에는 올리지 마세요.**
- 앱스스크립트 웹 앱 주소로 직접 접속해도 같은 앱이 열립니다.
