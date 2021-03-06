---
layout:   post
title:    OSI 7계층 (OSI 7 Layer)
author:   Kimtaeng
tags: 	  Network OSI7
description: Open System Interconnection 7 Layer
category: Network
comments: true
---

# OSI 7 계층이란 무엇일까?

정보처리기사 시험에서도, IT 회사 필기 또는 면접 전형에서도 가끔 등장하죠! OSI 7 계층에 대해서 알아봅시다. <br/> 
네트워크 상에서 여러 대의 컴퓨터가 데이터를 주고 받으려면 이들을 서로 연동할 수 있도록 표준화된 인터페이스를 지원해야 합니다.

국제 표준화 기구인 ISO(International Standard Organization)가 확립한 OSI(Open System Interconnection) 7계층은
개방화된 데이터 통신 환경에서 사용하는 계층적 구현 모델의 표준입니다.

<img class="post_image" src="{{ site.baseurl }}/img/post/2018-02-17-network-osi-7-layer-1.png" width="740" height="400" alt="OSI 7 계층"/>

이름처럼 7개의 계층으로 구성되어 있으며, 각 계층마다 수행하는 역할이 다릅니다.<br/>
임의의 호스트에서 실행되는 계층 N 모듈은 상대 호스트의 계층 N 모듈과 논리적으로 통신하며
이를 N 프로토콜이라고 합니다. 동일 계층에 위치한 통신 양단은 같은 프로토콜을 사용하여 통신하기 때문에
동료 프로세스(Peer Process)라고 하지요.

한 호스트에서 위아래로 이웃하는 계층에 위치한 모듈 사이에는 인터페이스가 정의되어 접근 방법을 제한하며,
상위 계층에서는 하위 계층의 인터페이스를 통해 하위 계층의 서비스를 이용합니다.

또한, 송신 호스트에서 데이터를 전달할 때는 동료 프로세스에서 직접 전달하는 것이 아니라 하위 계층에 서비스를 요청하고
이 요청은 최하위에 위치한 물리 계층까지 반복하게 됩니다.

반대로 수신 호스트에서는 상위 계층으로 데이터가 전달되면서 프로토콜 기능이 동작합니다.
각 계층의 동료 프로세스가 직접 통신하는 형태를 보이지만, 실제로는 항상 물리 계층을 통해 데이터가 전송됩니다.

그럼 각 계층 별로 특징을 알아볼까요?

<br/>

# 물리 계층(Layer 1)

물리적 매체를 통해서 데이터 비트를 전송하기 위해 요구되는 기능들을 정의하며
케이블, 연결 장치 등 전송에 필요한 두 장치 간의 실제 접속과 같은 기계적, 전기적 특성에 대한 규칙을 정의합니다.

전송단위 : 비트(Bit)
프로토콜 : RS-232C 등
장비 : 허브, 리피터

<br/>

# 데이터 링크 계층(Layer 2)

두 개의 개방 시스템들 간의 효율적이고 신뢰성있는 정보 전송을 할 수 있도록 하며
오류의 검출과 회복을 위한 오류 제어 기능을 수행합니다.
또한, 송신측과 수신측의 속도 차이를 해결하기 위해 흐름 제어(stop-and-wait & sliding window 방식으로 처리할 수 있는 패킷의 양보다 많은 경우)
기능을 하며 프레임의 시작과 끝을 구분하기 위한 프레임의 동기화 기능을 수행합니다.

전송단위 : 프레임(Frame)
프로토콜 : 이더넷, MAC, PPP 등
장비 : 브릿지, 스위치

<br/>

# 네트워크 계층(Layer 3)

다중 네트워크 링크에서 발신지로부터 목적지까지 전달할 책임을 가집니다.
이전 계층인 데이터 계층은 노드 vs 노드 전달을 감독하는 것이고
네트워크 계층은 시작점에서 목적지까지 성공적으로 전달되도록 하는 역할을 수행합니다.

전송단위 : 패킷(Packet)
프로토콜 : IP, ICMP 등
장비 : 라우터, L3 스위치

<br/>

# 전송 계층(Layer 4)

전체 메시지를 종단 vs 종단(End-to-End, 발신지에서 목적지)간 제어와 에러를 관리합니다.
패킷의 전송이 유효한지 확인하고 전송에 실패된 패킷을 다시 보내는 것과 같은 신뢰성있는 통신을 보장합니다.
주소 설정, 오류 및 흐름 제어, 다중화를 수행합니다.

전송단위 : 세그먼트(Segment)
프로토콜 : TCP, UDP 등
장비 : 게이트웨이, L4 스위치

<br/>

# 세션 계층(Layer 5)
 
양 끝단의 응용 프로세스가 통신을 관리하기 위한 방법을 제공합니다.
동시송수신(Duplex), 반이중(Half-Duplex), 전이중(Full-Duplex) 방식의 통신과 함께
체크 포인팅과 유후, 종료, 다시 시작 과정 등을 수행합니다.
통신 세션을 구성하며 포트 번호를 기반으로 연결합니다.

프로토콜 : NetBIOS, SSH, TLS

<br/>

# 표현 계층(Layer 6)

응용 계층으로부터 받은 데이터를 하위 계층인 세션 계층에 보내기 전에 통신에 적당한 형태로 변환하고
세션 계층에서 받은 데이터는 응용 계층에 맞게 변환하는 역할을 수행합니다.
코드 변환, 구문 검색, 데이터 압축 및 암호화 등의 기능을 담당합니다.

프로토콜 : JPG, MPEG, SMB, AFP

<br/>

# 응용 계층(Layer 7)

응용 프로세스와 직접 관계하여 일반적인 응용 서비스를 수행합니다.
응용 프로세스 간의 정보 교환, 전자메일, 파일전송 등의 서비스를 제공합니다.

프로토콜 : DNS, FTP, HTTP

