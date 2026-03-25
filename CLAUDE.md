# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## 프로젝트 개요

빌드 도구, 패키지 매니저, 서버가 필요 없는 단순 정적 프론트엔드 프로젝트입니다. 모든 코드는 단일 파일에 존재합니다.

## 실행 방법

`index.html`을 브라우저에서 직접 열면 됩니다. 빌드 과정이나 `npm install` 없이 바로 실행 가능합니다.

## 아키텍처

**`index.html`** — `<style>`과 `<script>` 블록이 인라인으로 포함된 단일 자급자족 파일.

- **데이터**: 스크립트 상단의 `quotes` 배열 (`{ text, author }` 객체 목록, 현재 15개).
- **상태**: `currentIndex`가 현재 표시 중인 명언의 인덱스를 추적.
- **진입점**:
  - `showNext()` — `currentIndex`를 순환 증가시켜 다음 명언 표시.
  - `showRandom()` — 현재 항목과 중복되지 않는 무작위 인덱스 선택.
  - `updateDisplay(index)` — 두 함수가 공통으로 호출하는 실제 DOM 업데이트 함수.
- **전환 효과**: `.quote-card`에 `fade-out` 클래스를 추가 → 350ms 후 내용 교체 및 클래스 제거 (opacity + translateY 애니메이션).
- **외부 의존성**: Google Fonts(`Noto Serif KR`, `Noto Sans KR`)만 사용. 나머지는 순수 HTML/CSS/JS.
