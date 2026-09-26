# Eclipse Marketplace 등록

## 1. 업데이트 사이트 공개

이번 변경사항과 `docs/`를 GitHub의 main 브랜치에 커밋하고 푸시합니다.
저장소 **Settings → Pages → Build and deployment**에서 다음을 선택합니다.

- Source: **Deploy from a branch**
- Branch: **main**
- Folder: **/docs**

Save 후 Pages 배포가 끝날 때까지 기다립니다. 아래 주소가 실제로 열려야 다음 단계로 진행할 수 있습니다.

- 소개: https://pinnpublic.github.io/code-recorder-eclipse/
- 설치 저장소: https://pinnpublic.github.io/code-recorder-eclipse/updates/
- 메타데이터: https://pinnpublic.github.io/code-recorder-eclipse/updates/content.xml
- 아티팩트 목록: https://pinnpublic.github.io/code-recorder-eclipse/updates/artifacts.xml

업데이트 사이트는 디렉터리 목록 화면이 없어도 됩니다. content.xml, artifacts.xml과 그 안의 JAR 파일에 접근할 수 있어야 합니다.

## 2. 공개 주소로 설치 확인

Eclipse의 **Help → Install New Software… → Add…**에서 설치 저장소 주소를 입력합니다.
기본 설치 옵션을 유지한 상태로 Code Recorder 0.3.5 설치와 재시작, 녹화 및 내보내기를 확인합니다.
기존 Eclipse 플랫폼 구성 요소를 교체하거나 다운그레이드하는 설치 계획이 나오면 진행하지 말고 원인을 확인합니다.

로컬 빌드·패키지 검사는 공개 URL에서의 설치 확인을 대신하지 않습니다.

## 3. Marketplace에 등록

https://marketplace.eclipse.org/ 에 Eclipse 계정으로 로그인하여 새 솔루션 등록 화면을 엽니다.
등록 화면의 실제 필드에 맞춰 다음 값을 사용합니다.

| 항목 | 값 |
|---|---|
| 이름 | Code Recorder for Eclipse |
| 짧은 설명 | Record code edits and file changes in Eclipse and export them as JSON. |
| 웹사이트 | https://github.com/pinnpublic/code-recorder-eclipse |
| 업데이트 사이트 | https://pinnpublic.github.io/code-recorder-eclipse/updates/ |
| 소스 저장소 | https://github.com/pinnpublic/code-recorder-eclipse |
| 문의·이슈 | https://github.com/pinnpublic/code-recorder-eclipse/issues |
| Feature ID | dev.coderecorder.feature |
| 설치 가능한 p2 IU ID | dev.coderecorder.feature.feature.group |

Feature ID를 묻는 필드와 p2 설치 단위 ID를 묻는 필드를 구분합니다.
라이선스는 저장소 LICENSE의 실제 조건과 일치시킵니다.
지원 환경은 검증한 Eclipse 버전만 선택합니다. 다른 STS 버전까지 호환된다고 등록하지 않습니다.

설명 예시:

> Code Recorder captures code edits and file changes in Eclipse and exports recordings as .coderec.json files. Select a project or folder, configure excluded paths and file extensions, and start recording. Unsaved edits are recorded. Use Stop / Export to finish the recording.

등록 후 Marketplace 클라이언트에서도 설치 항목과 설치 결과를 확인합니다.

## 새 버전 배포

빌드 및 업데이트 사이트 패키징 후 `scripts/prepare-marketplace.ps1 -Version 새버전`으로 docs/updates를 갱신합니다.
docs/index.html의 표시 버전도 맞춘 뒤 커밋하고 푸시합니다.

## 공식 안내

- [GitHub Pages 공개 소스 설정](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site)
- [Eclipse 소프트웨어 설치](https://help.eclipse.org/latest/topic/org.eclipse.platform.doc.user/tasks/tasks-127.htm)
