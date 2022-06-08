# Publishing Commerce
LGHV 미디어커머스 퍼블리싱 프로젝트  

## 디렉토리 구조 (예시)
```
+-- [assets]
+----- [fonts] - 폰트
+----- [images] - 이미지
+----- [scss] - scss
+-------- base.scss - 초기화
+-------- common.scss - base, layout, components 를 import 후 사용
+-------- layout.scss - 앱의 warapping 및 header footer 등
+-------- components.scss - 공통모듈
+-------- config.scss - mixins, variables, functions ...
+-------- home.scss - 홈 (각 페이지 별 scss)
+-- [pages] - 각 페이지별 분리 (나르미/재플린 section 구조와 동일)
+----- [splash]
+-------- splash.html 
```
<br/>

## Coding conventions

### 기본 rule
- 클래스와 id는 하이픈 사용 div class="class-name", div id="id-name"
- 공통 요소(버튼, 아이콘, 모듈) 및 기본 스타일(color, font 등)은 mixin 과 variable 로 처리
- section, aside, header, div 등 Tag는 강제하지 않지만 최대한 시맨틱하게 사용
- css는 클래스로만 선언 (div class="ex" - O, div id="ex" - X)
- css 클래스명은 의미적으로 선언 ex) .contents-footer-area (o) .ct-ft-a (x)
- css 속성은 레이아웃 관련, 우선 선언
   - position: relative;
   - display: flex;
   - width: 100%;
   - height: 100%;
   - font-size: 1.8rem;
   - color: #000;
   - background-color: #f00;
- float 속성 사용 X, flexbox(flex) 레이아웃으로 구성
<br/>

## navigation 적용을 위한 rule
- 활성화 / 포커스가 될 노드는 아래와 같은 구조로 퍼블리싱 (기존 Alaska 방식)
- 해당 페이지에서 활성화 될 수 있는 영역 selector: '._active' (스타일링 클래스로 사용하지 않고 활성화 영역에 대한 컨센서스만 맞추기 위해 사용됨)
- 활성화 된 부모 영역 selector : '.active'
- 활성화 된 포커스 selector : '.active .focus'
- 활성화 되지 않은 포커스 selector : '.focus' (시나리오 상 selected 효과가 필요한 경우에만 사용)
```
<ul class="home-list active _active" id="home-list"> <!-- 활성화 될 수 있는 영역이며 활성됨. -->
    <li class="focus">item1</li> <!-- 현재 활성화된 영역의 포커스 아이템 -->
    <li>item2</li>
    <li>item3</li>
</ul>

<div class="home-category _active" id="home-category"> <!-- 활성화 될 수 있는 영역. 현재 활성 안됨 -->
    <div>홈</div>
    <div>월정액관</div>
    <div class="focus">영화/해외</div> <!-- 활성화 되지 않은 영역의 포커스 아이템 -->
    <div>TV방송</div>
</div>
```

<br/>

## 이미지 처리
- 이미지는 png X2(두배 크기) 사용 (포스터 등 운영 이미지 제외)
- 배포 전 용량 최적화 https://tinypng.com/
```
.list-item {
    position: relative;
    padding-left: 15px;
    &::before {
        contents: '';
        position: absolute;
        top: 0;
        bottom: 0;
        left: 12px;
        width: 4px;
        height: 4px;
        margin: auto 0;
        border-radius: 50%;
        background-color: #666;
    }
}
```

<br/>

## 버전관리
- <em>HTML, CSS는 개발과 동일하게 최신으로 유지</em>
    - 퍼블리싱에서 수정 후 개발 전달
    - 개발에서 직접수정 X