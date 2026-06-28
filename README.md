# my-first-harness

2인 팀으로 커밋 메시지를 생성하는 최소 하네스 프로젝트.

## 개요

Claude Code 에이전트 2개(author, reviewer)가 협업하여 Conventional Commits 형식의 커밋 메시지를 자동 생성한다.

```
author  →  초안 작성  →  _workspace/commit-draft.md
reviewer →  검토·판정  →  _workspace/review-report.md
```

판정이 REDO이면 author를 최대 2회 재호출하고, PASS이면 최종 메시지를 사용자에게 제시한다.

## 사용법

```bash
# 변경 사항을 스테이지한 뒤
git add <파일>

# 커밋 메시지 생성 스킬 실행
/commit-message
```

## 구조

```
.claude/
  agents/
    commit-msg-author.md    # 초안 작성 에이전트
    commit-msg-reviewer.md  # 검토 에이전트
  skills/
    commit-message/
      SKILL.md              # 2인 팀 워크플로 정의
_workspace/                 # 중간 산출물 (commit-draft.md, review-report.md)
CLAUDE.md                   # 프로젝트 규칙
```

## 규칙

- 커밋 메시지는 `type(scope): subject` 형식 (Conventional Commits)
- 중간 산출물은 `_workspace/` 에 저장
- 에이전트는 `.claude/agents/`, 스킬은 `.claude/skills/` 에 정의
