<div align="center">

# 스FIN크스 · SphinX

### Last gate. That's me — the Sphinx. Pull up if you bad.

**스핑크스는 답을 알려주지 않습니다. 질문을 합니다.**

<br/>

![Status](https://img.shields.io/badge/status-in%20progress-D99A2B?style=flat-square)
![Stage](https://img.shields.io/badge/stage-private%20beta-122B4E?style=flat-square)
![Year](https://img.shields.io/badge/2026-FinTech-4ADE80?style=flat-square)

</div>

---

## 무엇을 만드는가

금융상품 계약 **직전**에 서는 판매 게이트입니다.

판매자가 설명을 마치면 시스템이 상품설명서에서 뽑은 위험항목마다 고객에게 묻습니다. 고객이 자기 말로 답하고, 그 답이 이해로 인정되는지를 재고, **이해가 서지 않으면 계약으로 넘어가지 않습니다.**

서명란에 이름을 받는 것과 고객이 이해했는지 확인하는 것은 다릅니다. 불완전판매 분쟁에서 지금 남는 증거는 대개 앞쪽입니다.

## 두 가지를 갈라 둡니다

```
AI    이 발화가 항목을 이해한 것인가     →  측정값 (등급 · 근거 인용 · 신뢰도)
룰    이 측정값으로 계약을 열어도 되나    →  판정  (통과 · 보완 · 보류)
```

**모델이 판정하지 않습니다.** 게이트 판정은 선언적 룰 파일이 만들고, 모델 출력은 그 룰의 입력일 뿐입니다. 그래서 *"왜 막혔는가"* 에 발화한 룰 이름으로 답할 수 있고, 같은 발화가 어제와 오늘 다른 등급을 받으면 그건 고칠 버그입니다.

근거 없는 판정은 아예 만들어지지 않습니다. 발화 인용과 루브릭 조항이 비면 생성자가 예외를 던집니다.

## 어떻게 일하는가

**왜 그렇게 했는지가 남습니다.** 배선·계약 결정이 전수로 한 파일에, 원칙급 결정 8건이 ADR 로 있습니다. 자기 영역을 고치기 전에 그 절을 먼저 읽습니다. 결정이 바뀌면 기존 문서를 고치지 않고 새 기록을 얹습니다 — *"그때 무엇을 정했나"* 를 나중에도 읽을 수 있어야 합니다.

**테스트가 구현과 비슷한 규모입니다.** 코드 파일(`.java`·`.py`·`.ts`) 기준으로 구현 27,561줄, 테스트 31,356줄입니다. 선언적 룰 파일을 구현으로 세면 이 문장은 뒤집히므로 세는 규칙을 같이 적습니다.

**주장에는 실측을 붙입니다.** 리뷰에서 *"그럴 것이다"* 는 근거가 아닙니다. 고친 자리에 변이를 넣어 그물이 실제로 우는지 확인하고, **0건을 검사하고도 통과하는 그물**을 따로 잡습니다. 검사가 눈을 감은 채 초록인 것이 검사가 없는 것보다 나쁩니다.

**파일마다 소유자가 있습니다.** 남의 영역은 건드리지 않고, 모듈 간 계약을 바꿀 때는 그 계약을 쓰는 사람을 전원 부릅니다.

## 역이용을 코드가 막습니다

집계된 이해도 데이터는 *"설득하기 쉬운 고객"* 목록이 될 수 있습니다. 그래서 그것을 소비할 수 있는 역할을 **아예 만들지 않았습니다.**

권한을 주지 않는 것과 줄 수 있는 대상이 없는 것은 운영 압박이 들어왔을 때 다르게 작동합니다. 역할이 없으면 부여하려면 코드를 고쳐야 하고, 그 변경은 PR 에 남습니다.

## 팀

2026 금융 AI Challenge · 4인

<div align="center"> <table> <tr> <td align="center" width="160"> <a href="https://github.com/gitIt-sehyeon"> <img src="https://github.com/gitIt-sehyeon.png" width="90" height="90" alt="정세현"/> </a> </td> <td align="center" width="160"> <a href="https://github.com/yoonjiseok"> <img src="https://github.com/yoonjiseok.png" width="90" height="90" alt="윤지석"/> </a> </td> <td align="center" width="160"> <a href="https://github.com/junseo2323"> <img src="https://github.com/junseo2323.png" width="90" height="90" alt="오준서"/> </a> </td> <td align="center" width="160"> <a href="https://github.com/hd0rable"> <img src="https://github.com/hd0rable.png" width="90" height="90" alt="강희진"/> </a> </td> </tr> <tr> <td align="center"><b>정세현</b></td> <td align="center"><b>윤지석</b></td> <td align="center"><b>오준서</b></td> <td align="center"><b>강희진</b></td> </tr> <tr> <td align="center"><a href="https://github.com/gitIt-sehyeon">@gitIt-sehyeon</a></td> <td align="center"><a href="https://github.com/yoonjiseok">@yoonjiseok</a></td> <td align="center"><a href="https://github.com/junseo2323">@junseo2323</a></td> <td align="center"><a href="https://github.com/hd0rable">@hd0rable</a></td> </tr> </table> </div>

| | 무엇을 소유하나 |
|---|---|
| [윤지석](https://github.com/yoonjiseok) | 채점·오해 탐지·질문 생성 — `ai-service` |
| [강희진](https://github.com/hd0rable) | API·상태머신·게이트 판정·PII 경계 — `server/api`·`core` |
| [정세현](https://github.com/gitIt-sehyeon) | 불변 기록·접근 정책·시뮬레이터·평가 — `evidence`·`security`·`eval` |
| [오준서](https://github.com/junseo2323) | 화면 8종·인프라·배포 — `web`·CI |
