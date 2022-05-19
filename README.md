개발환경

Java 15 
jdk1.8.0_202
apache-tomcat-8.5.7.7

--Project File 소개--

--구조--

 Mvc Model2

--백단--

Front Controller > 각 Controller로 이동시킴 (Servlet이용) >Dao에서 기능담당 Vo(Dto)에 객체에 담아 저장 및 쿼리(DB연동 JDBC) > Jsp이동

DBmanager 생성하여 메소드 불러서 사용(Dao혹은 Controller)

--화면단--

MainPage  >  Home.jsp 

--Home.jsp 구조--

Css를 갖고 있으며, include를 통해 모듈화 진행하여, 독립적으로 개발이가능 (협업에 용이함. 또한 소스코드를 바로 노출 하지 않는 장점!)

Join,Login 등 기능에 대해서는 rightMenu(우측화면 Contents 부분)을 제외한 부분이 변경되지 않게 동일한 CSS및 HTML구조 차용!
(화면전환되지 않는 듯한 효과를 낼 수 있음.)

--Class 소개--

--Controller--
FrontController	기능 :	최초 index에서 무조건 이곳으로 이동함! 각 Controller 분기해주는 효과 split사용하여 주소 잘라서 Servlet이동!
HomeController	기능:	메인화면에 띄워주어야 할 부분들 처리 및 세션의 유무에 따른 처리
JoinController	기능:	가입기능수행 Dao로 이동시켜서 쿼리문 실행
LoginController	기능:	로그인 화면에서 받아온 Parameter 받아서 Dao에서 쿼리기능 처리 할 수 있게 해줌!
MypageController	기능:	개인정보 수정 기능을 위해 Dao로 보내줌! 현재는 쿼리문도 같이 있음 수정예정!

--Model--
JoinDao		기능:회원가입에 필요한 쿼리(insert)후 JoinController로 리턴
LoginDao		기능:로그인 시에 jsp에서 입력받은 Parameter 이용해서 다시 Vo에 저장 후 세션에 저장!
MemberLogic	기능:객체를 생성하여 Member객체, 메서드들(위의 Dao기능들) 싱글톤 활용하여 하려고 했던 잔재

--vo--
DBManager	기능:JDBC 연결 기능 close 메서드를 만들어두어 연결을 끊을 떄의 편리를 도모함(메서드 불러와서 DB연결종료)
Member		기능:VO(DTO)로써 객체로써 DB와의 연결하기 위해 사용

--구현 완료한 기능--

1.메인페이지 접속
  1)index이동시 n초후 자동으로 페이지이동 기능구현

  2)메인페이지 HTML CSS작업

  3)상단메뉴바에서의 기능 3가지
    (1)로그인기능
    (2)로그아웃기능
    (3)회원가입기능
    (4)회원정보수정기능(일부)

--기존 사이트보다 개선된 점--
상단으로 nav(네비게이션바)를 옮겨서 조금더 보편적인 사용감(UX)
불필요한  Css를 줄여서 깔끔한 느낌
구조적으로 보편적이지 않은(많은 사이트에서 사용하지 않는)UI구조를 개선
  Ex)상단바의 위치,Footer 위치에 와야할 부분이 최상단에 와있는 구조 등

--수정보완사항--
CSS에서 bar(상하로 내-려가는)의 모양을 가려주는 기능 보완해야함
HTML구조가 원본 사이트와 약간 상이함
전체적인 기능의 완성이 덜 되었음
수정시 select 기능으로 입력 받아야 할 부분이 input text 형식으로 되어있는 부분 등

--작성시 어려웠던점--
Session에 값을 담아서 jsp에서 불러와서 전체적으로 로그인한 사람 한 사람의 Session값을 받아와서
jsp내에서 사용해야 했는데 최초에 null Point Exception이 계속 나와서 처리해 주는데 애를 먹었음.
  - 최초 null대신 ""(공백문자)로 치환해주어 해결!

Css와 HTML작성에 익숙하지 않아 헤매었는데 프로젝트 작성중에 익숙해짐.

설계미숙으로 인해 많은 오류 발생
  -많은 공부가 필요해보임


--기타 전달하고 싶은 사항--

면접관 님들 께서 코드를 직접 보기 힘드실 테니 실행화면을 캡쳐해서 첨부해 드립니다. 기능이 구현된 부분은 캡쳐해 놓았습니다.
또한 혹시나 필요 할 것 같아 노트북도 들고 갈테니 궁금하신점이 있으시면 말씀해 주십시오. 감사합니다.


