# Fork 기록 (yenalee04/superpowers)

[obra/superpowers](https://github.com/obra/superpowers)를 포크해 비개발자 업무에 맞게 고친 저장소다.

| | |
|---|---|
| 원본 | https://github.com/obra/superpowers (MIT, `LICENSE` 참고) |
| 포크한 날 | 2026-10-01 |
| 포크 시점 원본 커밋 | `8ca22db` (Release v6.4.2) |

원본에 PR을 보내지 않는다. 원본 `AGENTS.md`가 포크 전용 변경은 PR로 받지 않는다고 적어 두었다.

## 바꾼 것

원칙: 스킬 폴더는 지우지 않는다. 스킬끼리 서로 가리키고 있어서(예: `writing-plans`가 `executing-plans`를, `writing-skills`가 `test-driven-development`를 가리킴) 지우면 남은 스킬이 깨진다. 덧붙이는 내용은 파일 맨 끝에 둔다.

| 바꾼 것 | 파일 | 이유 |
|---|---|---|
| 직접 호출 전용으로 표시 (`name:` 아래에 `disable-model-invocation: true` 한 줄) | `dispatching-parallel-agents`, `executing-plans`, `finishing-a-development-branch`, `requesting-code-review`, `subagent-driven-development`, `systematic-debugging`, `test-driven-development`, `using-git-worktrees`, `using-superpowers`의 `SKILL.md` | 개발 전용이거나, 이미 쓰는 다른 스킬과 겹치거나(`tdd`, `diagnosing-bugs`), 너무 자주 끼어드는 스킬(`using-superpowers`는 모든 답변 전에 스킬을 부르게 함). 필요하면 `/이름`으로 직접 부를 수 있다. |
| description 교체 | `skills/brainstorming/SKILL.md` | 원본은 창작 작업 전 반드시 쓰라고 되어 있어 작은 일에도 끼어든다. 목표가 아직 정해지지 않은 새 설계일 때만 쓰도록 좁혔다. |
| 맨 끝에 `## Fork customization (yenalee04)` 단락 추가 | `verification-before-completion`, `receiving-code-review`, `writing-plans`, `writing-skills`의 `SKILL.md` | 근거 인용과 추정 표기, 묻기 전에 조사, 계획 저장 위치와 예상 시간, 스킬 description 규칙과 평가 같은 내 작업 규칙을 넣었다. |
| `FORK.md` (이 파일) | 새로 만듦 | 원본 주소, 바꾼 것, 업데이트 받는 법을 한곳에 남기기 위해 |

## 아직 못 한 것

- **세션 시작 훅 끄기**: `hooks/hooks.json`이 창을 열 때마다 `hooks/session-start`를 실행해 `using-superpowers` 내용을 주입한다. 내 PC는 훅 때문에 멈춘 기록이 있어 끄려 했으나, 2026-10-01 Claude의 자동 안전장치가 훅 설정 수정을 막았다. 끄기 전에는 내 Claude에 설치하지 않는다.

## 원본 업데이트 받기

1. https://github.com/yenalee04/superpowers 에서 **Sync fork** → **Update branch**.
2. 충돌이 나면 내 PC에서 해결한다.
   ```
   git fetch upstream
   git merge upstream/main
   git push origin main
   ```
3. 받은 뒤 확인할 것
   - 위 9개 스킬의 `disable-model-invocation: true` 줄이 그대로 있는지
   - `brainstorming`의 description이 내 버전인지
   - 4개 스킬 맨 끝의 `## Fork customization (yenalee04)` 단락이 그대로 있는지
   - 원본에 **새 스킬**이 생겼는지. 새 스킬은 기본으로 자동 호출되니 쓸지 정한다.

## 지킬 것

- **공개 저장소다.** 회사 이름, 브랜드, SKU, 숫자 등 회사 정보는 넣지 않는다.
- 원본(`upstream`)에는 push하지 않는다. 내 PC 설정에서 push 주소를 막아 두었다(`NO_PUSH_TO_UPSTREAM`).
