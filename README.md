# four-team

![hexa](https://user-images.githubusercontent.com/88864456/133198600-1aac2164-16a5-4024-b415-774202b3a422.png)


# 1. 서비스 시나리오 

##    A.	기능적 요구사항

####    고객이 메뉴를 주문한다
####    고객이 결제한다
####    결제가 되면 주문 내역이 상점에 전달된다
####    상점 주인은 주문내역을 확인하여 메뉴를 접수하고 배송을 시작한다.
####    고객이 주문을 취소할 수 있다
####    주문이 취소되면 배송을 취소한다.
####    메뉴가 취소되면 결제를 취소한다.
####    고객이 주문상태를 중간중간 조회한다.
####    주문상태가 바뀔 때 마다 카톡으로 알림을 보낸다.


    B.	비기능적 요구사항

      i.	트랜잭션

        결제가 되지 않은 주문건은 아예 거래가 성립되지 않아야 한다. Sync 호출

        주문이 취소되어도 가게주인이 접수하여 배송을 시작한 주문인 경우 주문 취소는 원복되어야 한다. Saga(보상 트랜잭션)


      ii.	장애격리

        배송 기능이 수행되지 않더라도 주문, 결제는 받을 수 있어야 한다. Async (event-driven), Eventual Consistency

        결제시스템이 과중되면 사용자를 잠시동안 받지 않고 결제를 잠시후에 하도록 유도한다. Circuit breaker, fallback


      iii.	성능

        고객이 자주 확인할 수 있는 주문상태를 마이페이지(프론트엔드)에서 확인할 수 있어야 한다. CQRS

        주문상태가 바뀔때마다 카톡 등으로 알림을 줄 수 있어야 한다. Event driven

