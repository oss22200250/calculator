Calculator
---
<img src="Logotype primary.png" width="60%" height="60%" />

Created with *create-react-app*. See the [full create-react-app guide](https://github.com/facebookincubator/create-react-app/blob/master/packages/react-scripts/template/README.md).



Try It
---

[sortizm.github.io/calculator](https://sortizm.github.io/calculator/)



Install
---

`npm install`



Usage
---

`npm start`


ㅡㅡ 여기까지 기본 리드미 파일 내용 ㅡㅡ


## 1 Project Structure
주요 파일 2-3개의 역할

index.js가 코드의 시작점.
가상 컴포넌트를 웹 브라우저의 html 문서에 연결해줌.
- ReactDOM.render(...); 코드를 통해서 뼈대만 있는 순수 html 파일 내부의 <div id="root"> 태그 안에 끼워넣음

App.js가 전체 흐름 통제.
화면을 조립하고 계산 데이터 중앙 관리.
- state를 통해서 현재 계산기에 입력된 숫자, 연산 상태 기억
- handleClick 함수를 통해 사용자가 버튼을 누를 때 calculate 함수를 실행하여 결과를 상태로 업데이트
- render 안에 <Display/>와 <ButtonPanel/> 통해 하나의 계산기로 화면 조립


## 2 React Component
주요 컴포넌트 1-2개의 역할

Display 컴포넌트는 계산기 화면창을 보여줌
- 스스로 계산하거나 상태를 가지지 않는다. total과 operations 속성을 받아 화면에 렌더링함

ButtonPanel 컴포넌트는 키패드 컨테이너
- 여러 Button 컴포넌트들 줄을 맞춰 5개의 행으로 묶어 배치하는 역할
- 부모 App.js와 자식 Button.js 사이를 이어줌


## 3 Code Analysis
코드 1개(5-15줄) 선택하여 동작 원리 설명

calculate.js 내부 분석
분석할 코드
export default function calculate(obj, buttonName) {
  if (buttonName === "AC") {
    return RESET_OBJ;
  } else if (buttonName === "=") {
    return operate(obj.operations);
  } else {
    return { operations: (obj.operations || "") + buttonName }
  }
}

- 이 코드는 사용자가 계산기의 어떤 버튼을 눌렀느냐(buttonName)에 따라서 앱 상태 obj가 어떻게 변할지 결정하는 역할
- 사용자가 초기화 버튼 AC를 누르면 빈 상태(RESET_OBJ) 반환하여 화면을 지움
- = 버튼을 누르면 지금까지 입력된 obj.operations를 operate 함수로 넘겨 계산 수행
- 그 외 숫자나 기호 누르면 기존 수식 뒤에 글자를 그대로 이어 붙여 새로운 상태로 반환