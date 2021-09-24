# Meeting History

- 2021/09/18 회의 내용

  - 내용 : 팀을 정하고, 9/21(화)까지 조사해올 기능 정리

    - < 규민/석준 : 공간 >
    - 다른 팀의 공간으로 이동하는 기능
    - 작품 등록
    - 참가자 등록 (발표자/내부인/외부인/교수 등)
    - 방명록 작성
    - 최근 뉴스/기술/논문 등 띄워주기

    < 재광/보민 : 전시 (1) >

    - 유튜브 재생
    - 포스터 전시 (이미지 또는 문서, 누르면 확대)
    - 실시간 라이브

    < 재형/종인/지희 : 전시(2) >

    - 피드백 (댓글/추천/조회수)
    - 정렬 순서 설정
    - 지도교수 연구실 링크 연결

<hr>

- 2021/09/21 회의 내용

- 내용 : 기능 조사내용 발표
- < 규민/석준 : 공간 >

  - 다른 팀의 공간으로 이동하는 기능
    - 가능
    - [docs](https://docs.vrchat.com/docs/vrc_portalmarker)
    - [youtube](https://www.youtube.com/watch?v=vfJiyDoCFng)
  - 작품 등록, 참가자 등록, 방명록

    - 애매함 (DB연동 및 등록 과정들이 쉽지 않아보임)
    - [youtube 키패드, 암호](https://www.youtube.com/watch?v=mSnLzyRe2Mk)
    - [youtube world 트리거](https://www.youtube.com/watch?v=y7mKZqgmmck)

  - 최근 뉴스/기술/논문 등 띄워주기

    - 현재는 가능( docs에서 현재 가능하지만, 추후 삭제될 수 있다고함 )
    - [docs](https://docs.vrchat.com/docs/vrc_webpanel)

- < 재광/보민 : 전시 (1) >

  - 라이브 스트리밍

    - [VRC_SyncVideoStream](https://docs.vrchat.com/docs/vrc_syncvideostream)
      : VRC에서 제공하는 component. 다만 유튜브 스트리밍을 예시로 들어서 해당 component를 이용하여 웹캠 송출이 가능한지는 모름.

  - 유튜브 재생

    - [UdonSyncPlayer](https://gongdolhoon.tistory.com/entry/UnityVR-Chat-SDK-10-Video-Player)
      : 유튜브 재생, 라이브 스트리밍 모두 가능한 prefab
    - [jetdogs prefabs](https://github.com/jetdog8808/JetDogs-Prefabs)
      : 위와 같은 기능 제공하는 prefab

  - 포스터 전시 (이미지 또는 문서, 누르면 확대)

    - [VRC_Panorama](https://docs.vrchat.com/docs/vrc_panorama)
      : 이미지 기반 슬라이드쇼. 이게 제일 현실적?
    - [Unity Asset Store](https://assetstore.unity.com/packages/tools/gui/pdf-renderer-32815?locale=ko-KR)
      : PDF renderer가 있는데 유료인거 보니 못쓸듯
    - [VRC_BookBuilder](https://booth.pm/ja/items/1786695)
      : PDF를 책처럼 보여주는 asset..?

  - 실시간 라이브 - VRChat 내부에선 보통 가상 아바타를 사용해서 그런지 webcam 사용법이 잘 안 나옴. Webcam을 이용해 face/body tracking하는 게 가능하니 webcam 사용도 가능하지 않을까 추측 중… vrc_syncvideostream 사용해서 웹캠을 송출 가능한지도 알아봐야함. - UdonSyncPlayer는 prefab이라서 유튜브 재생, 라이브스트리밍 둘 다 지원하는 것 같고
    VRC_SyncVideoPlayer는 component라 유튜브 재생만 가능하고 라이브스트리밍 하려면 VRC_SyncVideoStream을 따로 써야하는 것으로 추정

- < 재형/종인/지희 : 전시(2) >

  - 피드백 (댓글/추천/조회수)
    - SDK에서 제공하는 컴포넌트가 딱히 존재하지 않는다. 하려면 직접 firebase같은 DB 필요할듯. (추천이나 조회수까지는 가능할듯, 댓글은 힘들어보인다)
  - 정렬 순서 설정
    - sort layer가 unity로 component에 레이어 번호를 붙여서 sort 가능.
    - 좋아요 숫자로 정렬시에는, DB연동해서 하면 될듯
  - 지도교수 연구실 링크 연결
    - VRCWebPanel로 가능했었다. but 보안상의 이유로 삭제
    - 미리 준비해둔 정보를 올려주는 식으로 올려주는 방안이 있을 수 있음.

<hr>

- 2021/09/24 회의 내용

  - 내용 : 기능 정리 및 역할분배, 보고서 작성 내용 정리

  - 지난 회의때 정하지 않은 문제

    - Q. 작품 개수를 정해야하는가?

      - A. https://cs.skku.edu/gp/exhibition/211 60개 이상

    - Q. 방을 몇 개 만들어야 하는가?

      - A. AI/웹/etc로 나눠서 3개, 내부에서 (논문/작품) 으로 나눌 수 있음

    - Q. 방의 크기가 작품 개수에 따라 변하는가?

      - A. 가변적으로는 불가능, 미리 사이즈 정해서 만들기로함

    - Q. 작품 등록은 관리자만 가능하게 설정하는가?
      - A. YES, 이상한 작품들이 올라갈 수 있기때문

  - 기능 정리

    | 분류 |                                 필수                                  |                           보류                            |
    | :--: | :-------------------------------------------------------------------: | :-------------------------------------------------------: |
    | 기능 | A. 참가자 등록, 방명록, 피드백<br>B. 포스터전시, 유튜브재생, 공간이동 | 라이브 스트리밍, 뉴스 띄워주기, 지도교수 연구실 링크 연결 |

  - 역할 분담
    | 팀 | 보민, 재광 | 종인, 지희 ,재형 | 석준, 규민 |
    | :--: | :-----------------------------------------------------------: | :-------------------------------------------------------: |:-------------------------------------------------------: |
    | 기능 | 월드 디자인, 제안서, 보고서 |포스터전시, 유튜브재생, 공간이동, 보고서 | 참가자 등록, 방명록, 피드백, 보고서 |
