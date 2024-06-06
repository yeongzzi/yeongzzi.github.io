---
title: "이상한 문자 만들기"
excerpt: "map+for문"

categories:
  - Categories2
tags:
  - [tag1, tag2]

permalink: /categories2/이상한 문자 만들기/

toc: true
toc_sticky: true

date: 2024-06-06
last_modified_at: 2024-06-06
---

**문제 설명**
문자열 s는 한 개 이상의 단어로 구성되어 있습니다. 각 단어는 하나 이상의 공백문자로 구분되어 있습니다. 각 단어의 짝수번째 알파벳은 대문자로, 홀수번째 알파벳은 소문자로 바꾼 문자열을 리턴하는 함수, solution을 완성하세요.

**제한 사항**
문자열 전체의 짝/홀수 인덱스가 아니라, 단어(공백을 기준)별로 짝/홀수 인덱스를 판단해야합니다.
첫 번째 글자는 0번째 인덱스로 보아 짝수번째 알파벳으로 처리해야 합니다.

**입출력 예**
| s | return |
| --- | --- |
| "try hello world" | "TrY HeLlO WoRlD" |

**입출력 예 설명**
"try hello world"는 세 단어 "try", "hello", "world"로 구성되어 있습니다. 각 단어의 짝수번째 문자를 대문자로, 홀수번째 문자를 소문자로 바꾸면 "TrY", "HeLlO", "WoRlD"입니다. 따라서 "TrY HeLlO WoRlD" 를 리턴합니다.

---

- 오류원인: 단어가 아니라 문자열 전체로 상정하여 for문을 사용했기 때문
- 해결방법: 배열로 바꿔 맵핑한 다음 for문을 사용하여 각 단어를 순회했다. 순회한 결과를 변수에 담아 return

---

내 풀이
```tsx
function solution(s) {
    let arr = s.split(" "); // 공백을 기준으로 문자열을 나눈다.
    let transformedWords = arr.map(word => {
        // word = arr[0] , try
        let transformed = ''; // 변환된 단어를 저장할 변수
        for (let j = 0; j < word.length; j++) {
            // "t" 
            if (j % 2 === 0) {
                transformed += word[j].toUpperCase();
            } else {
                transformed += word[j].toLowerCase();
            }
        }
        return transformed; 
        // 변환된 단어를 반환. 각 단어가 변환된 순서대로 반환된다.
    });
    return transformedWords.join(" "); // 변환된 단어가 들어있는 배열을 공백으로 결합
}

```
