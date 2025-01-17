# 업무에 바로쓰는 HTML5/CSS3

## 환경구성
- 최신 웹브라우저 및 확장 프로그램 설치
  - visbug, tota11y, web developer, headingsmap, open wax
- Visual Studio Code  설치 및 확장 프로그램 설치
  - live server, auto rename tag, auto close tag
- [node 설치](https://nodejs.org/ko/) : LTS 버전
- [git 설치](https://git-scm.com/) : 최신 버전

## Git 버전 관리
- [강사 저장소 Fork](https://github.com/seulbinim/webcafeHTML5)
- Fork한 저장소를 컴퓨터(Local)로 [Clone](https://github.com/shinupl/webcafeHTML5.git)  
```bash
git clone https://github.com/shinupl/webcafeHTML5.git
```  

- 변경이력 및 상태 확인
```bash
git status
```  

- Index Area 영역으로 이동(WD -> Commit 대기열로)
```bash
git add <파일명>  -> 파일 선택 
git add . --------> 전체 파일
```  

- 확정본 생성(대기열 -> commit)
```bash
git commit -m "커밋 메시지(무엇을 바꾸었는지)"
```

- remote 저장소로 백업(웹으로 전달)
```bash
git push origin main
```

- 변경 이력 조회(로그 확인/add나 commit 후 확인)
```bash
git log --oneline
```

## html tag 입력방법
- div.group.group$*3
- div.group.group$*3{group}
- li.no$*4>a[href="/"]+em.up[aria-lable=""]  
```css
<li class="no1">
  <a href="/"></a>
  <em class="up" aria-lable=""></em>
</li>
<li class="no2">
  <a href="/"></a>
  <em class="up" aria-lable=""></em>
</li>
<li class="no3">
  <a href="/"></a>
  <em class="up" aria-lable=""></em>
</li>
<li class="no4">
  <a href="/"></a>
  <em class="up" aria-lable=""></em>
</li>
```

## 레이아웃 구성
- 레이아웃을 위해 마크업을 변경하는건 안좋음
- 마크업은 콘텐츠 기준, 뷰 기준이 아님
- 구조를 보고 누구를 선택할 지 생각해 css를 넣어야됨
- 눈에 보이는 기준이 아닌 사용자 순서에 따라 합리적인 순서로 마크업하기
- 배경 컬러를 사용해 영역을 보면서 코드를 생각하면 좋음

- 단축 표기법은 속성 값을 이해하고 적절히 사용하기


- display : flex
  - flex-direction 속성으로 row 또는 column 방향을 지정할 수 있음  
    (flex-direction 메인축과 교차축이 결정)
  - flex 컨테이너와 flex 아이템이 가질 수 있는 속성이 다름  

- float 속성
  - linebox 안에서 왼쪽 또는 오른쪽 배치
  - normal flow를 벗어나 화면에 떠있는 형태  --->  부모가 높이를 잃게됨
  - float 요소의 부모에게 display: flow-root(상위 개채)를 지정해 float 개체의 높이를 부모가 읽어들일 수 있도록 할 수 있음  
  - overflow: hidden, clear: both는 flow-root를 대신해 float 이슈를 해결 할 수 있지만  
    영역이 넘어가면 잘려 보이기 때문에 수정에 용이하지 않음
  - float는 width 값이 맞지 않으면 left, right를 적절하게 사용해도 정렬이 안되, width 값을 잘 계산해 진행

- 세로값은 auto 또는 min-height
- margin과 padding(내부 포함)은 적절하게 사용  
  (margin도 박스 값에 투명하게 보일 뿐, 박스에 포함되기 때문)
- order : 순서를 설정할 수 있다. 모든 아이템은 0이 기본 -1이 되면 가장 앞으로 나오게 됨

- body *, body *::before, body *::after ---> 반응형 시 (타켓 명확하게)
- *, *::before, *::after ---> 고정 형 (전체에 해당되기 때문에 속도에 문제를 줄 수있다.)

- ul.member-service>li*>sapn[aria-hidden="true"]{:}+a[href='/']

- li.no$4*>a[href="/"]+em.up[aria-lable=""]

aria-hidden="true" : 보이스로 읽을 때 읽지 않는다

position absolute ---> 유연하지 못하다. 변경되면 좌표를 변경해야한다.

flex는 margin 사용이 아니고 gap

display: none;은 사라질 수있지만 콘텐츠가 없는 상태

메뉴 배치 시 li를 inline-block을 사용하면 공백이 나오게되 레이아웃 설정 시 부적절

배치나 크기에 영향을 주는 부분들은 상속 X
꾸미는 요소들은 상속 O

가상요소는 가상 박스가 생성 -> 딱 콘텐츠의 영역만

@ : 선언할때 사용

css 파일을 나눠서 하면 좋지만 성능이 떨어짐, 배포할때는 하나로 합쳐서 해야됨

focus-visible ---> 키보드 상태에서만

페이지 이동이면 링크 / 이동이 없으면 버튼

required -> 필수라는걸 알려줌

## a태그 사용
- 새창 열리게 할 시 target="" neneoopr, noreferrer를 꼭 넣어줘야함
```css
<a href="https://validator.w3.org/" target="_blank"  
  title(마우스 오버했을 때 나오는 툴팁 속성)="마크업 유효성 검사 사이트로 이동(새창)"  
  rel="noopener noreferrer"(보안을 위해)>W3C Markup Validation</a>
```
- a태그 텍스트 말고 공백에도 마우스 오버했을 때 바뀌거나, 링크 넘어가게 하려면 a를 block요소로 만들면 됨

<section> 에서 사양이 낮은 버전에서는 fieldset이 꼭 필요
       
          <fieldset> : display 가급적 값을 변경하는걸 추천하지 않는다


그로우 0 슈링크 1

- 공통 모듈을 따로 유틸리트 파일을 만듬
- 딱 제어할 수 있는 부분은 유니크하게 id를 사용

- css sprite 패턴 : 이미지 한장에 아이콘을 넣어 위치를 바꿔 보여주는것  
- IR : padding, text-indent(첫줄 들여쓰기, 첫줄 내여쓰기), position 글자를 밖으로 보내는거
- aria-label 키보드 리딩이 되지만, 화면에 노출이 안되 편리  
  (overflow, padding등으로 밀 필요가 없다.)
  
  
  
  headingsmap
  openwax
  tota11y for chrome
  visbug
  web developer
