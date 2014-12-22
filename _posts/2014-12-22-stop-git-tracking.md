---
layout: post
title: "git에서 특정 파일 트래킹을 잠시 멈추는 방법 (설정 파일 등)"
description: "mysql 콘솔에서 데이터베이스를 생성할 때, ‘-‘ (대쉬) 가 먹지 않아 문제가 생긴 경우가 있었다. git repository 소스의 프로퍼티 설정값에 나타나있는 DB명과 일치시킬 수 없는 문제가 발생한 것이다."
date: 2014-12-22 22:19:00
categories: tech git
---
mysql 콘솔에서 데이터베이스를 생성할 때, ‘-‘ (대쉬) 가 먹지 않아 문제가 생긴 경우가 있었다. git repository 소스의 프로퍼티 설정값에 나타나있는 DB명과 일치시킬 수 없는 문제가 발생한 것이다.

다시 툴을 켜서 프로퍼티대로 새 DB를 만들기가 귀찮아서, 파일의 DB명을 수정해서 테스트하니 브랜치 변경이나 커밋때마다 사람을 귀찮게 한다. 
로컬 빌드환경을 맞출 때도 이런 일이 종종 있을 것이다.

그렇다고 이걸 잠시 삭제할 수도 없고.. 이럴 때 내가 원하는 동안만 파일 트래킹을 하지 않으려면 다음과 같이 한다.

> git update-index *—assume-unchanged [path]*

반대로 다시 추적을 시작하려면 이렇게 한다.

> git update-index **—no***-assume-unchanged [path]*

.idea 디렉토리라던지 아예 추적이 필요 없는 것들은 .gitignore로 빼버리면 된다.

### 추적 제외된 파일을 보고 싶으면
> git ls-files -v | grep “\^[[:lower:]]"

제외된 것은 소문자로 표시되어 있다. 알파벳이 궁금하면 링크 참고 - [git-ls-files][ls-files]

[ls-files]:http://git-scm.com/docs/git-ls-files