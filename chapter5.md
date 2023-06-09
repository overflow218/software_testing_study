# 5강. 속성 기반 테스트

일단 속성 기반 테스트를 보고 드는 생각은 요 부분은 뭐 한번 본다고 알 수 있는 부분이 아니고 여러번 반복적인 연습을 통해서 내것으로 체화시켜야하는 부분의 지식이라는 것이다.
이전까지 명세기반 테스팅과 구조적 테스팅에서 코드 커버리지개념을 다뤘다. 뭐가 되었든지 주어진 명세서 혹은 코드를 분석하고 내가 직접 예제 입력을 만들어냈어야했다. 속성 기반 테스트는 다르다. 이건 들어갈 수 있는 값의 범위와 그걸 어떻게 만드는지를 정해주고 나면은 테스팅 프레임워크가 알아서 그 범위내에서 무작위로 인풋을 만들어서 테스팅을 진행하는 방법이다. 예를 들어 1 ~ 5까지의 수를 받으면 false, 5 초과 10이하의 수를 받으면 true, 나머지는 에러가 나는 프로그램이 있다고 해보자. 그러면 1≤ x ≤ 5, 5 < x ≤ 10, x < 1, 10 < x 이렇게 만드는 방법을 명시적으로 적어준후 저기서 뽑아서 테스팅을 진행하도록 할 수 있다. 이건 간단한 예제지만 복잡한 경우에는 컴퓨터가 이해할수있는 저런 시나리오를 만들어야 하는데 그게 쉽지 않다. 그리고 사용하는 언어의 테스팅 프레임워크를 잘 알고 있어야 거기 기능을 여러가지 가져다가 조합해서 사용할 수 있다.
복잡하긴하지만 성능은 아주 확실하다. 그렇기 때문에 꼭 내 무기로 만들도록 하자.

### 연습문제

1. 예시 기반 테스트와 속성 기반 테스트의 주요 차이점은 무엇인가?
   1. 위에도 적어놨듯이 구획을 나누고 분석하는건 두 테스트 모두 동일하다. 다만 그 구간별로 들어갈 입력값을 내가 직접 정하는지 아니면 컴퓨터가 정해진 범위내에서 무작위로 만들어주는지가 둘의 차이점이다.
2. 전달된 문자열이 회문(거꾸로 읽는거랑 그냥 읽는거랑 같은 문자열)이면 참, 아니면 거짓을 반환하는 프로그램이 있다. 속성 기반 테스트를 통해 테스트할 수 있는 속성은 무엇인가? 또 이러한 테스트를 구현하는 방법을 기술하라.
   1. 문자열이 널일때, 빈문자열일때 예외처리해주고 그 이외에는 랜덤한 길이를 가지는 문자열을 만들어준다. 이걸 뒤집어서 두개가 같은지 비교하고 테스트 오라클을 만든다. 그런다음에 프로그램에 문자열을 넣어서 같은 결과가 나오는지 확인한다
3. 퍼지 테스트 또는 퍼징이 무엇인지 알아보자. 속성 기반 테스트와 퍼징의 차이는 무엇인가?
   1. 퍼징은 무작위로 인풋을 만들어내는 random testing의 한 종류이다. 속성 기반 테스트도 무작위로 만들어내는 것이 맞지만 이건 정해진 범위와 규칙내에서 무작위로 만들어내는 것이다. 반면에 퍼징은 진짜 무작위다. 그래서 제대로 프로그램을 타겟할 확률이 많이 떨어진다.
