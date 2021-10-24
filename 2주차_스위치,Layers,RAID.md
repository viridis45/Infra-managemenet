1. 스위치
   1.  enables connected devices to share information and talk to each other.
   2. 패킷을 어느 쪽으로 보내는지 판단하는 기기. 어떤 정보를 가지고 이를 판단하느냐에 따라 layer가 나뉜다.
   3. stores mac address of devices, ASIC based
   4. types
      1. unmanaged : no config required
      2. managed : more secure
   5. layers
      1. L2
         1. 포트별 bandwidth가 부여되고 L2는 기기의 mac address를 알고있음
      2. L3 
         1. L2에 라우팅(IP) 기능이 있는 스위치. 
         2. TCP/IP
            1. IP : 패킷 통신 방식의 인터넷 프로토콜
            2. TCP : 전송 조절 프로토콜
               1. 3 way handshake
                  1. 송신자가 수신자에게 SYN을 날려 통신가능한지 확인. Port가 열려있어야 함
                  2. 수신자가 송신자보루터 SYN을 받고 'SYN/ACK'로 화답
                  3. 송신자가 이를 받고 ACK를 날려 전송 시작을 알림
         3. 다른 IP들이 목적지를 제대로 찾도록 도움
      3. L4 : Transport Layer
         1.  load balancer
         2. 외부에서 오는 모든 요청을 받아 해당 서버로 나누어줌
         3. 모든 요청은 스위치의 공인IP로 보내지고 스위치가 할당하여 각 서버로 전달
         4. 
      4. L7 : Application Layer
         1. HTTP, DNS, FTP등에 간섭하여 로드밸런싱, 헤더에 정보삽입
         2. L4가 전달자 역활이었으면 L7은 중개자 역할(Proxy)
   
2. RAID, (RAID 0,1,4,5,6,1+0, 0+1)

   1. Redundant Array of Inexpensive Disks
   2. 여러 개의 디스크를 연결하여 고성능의 디스크처럼 작동하게 만들기
   3. HDD : high speed spinning parts -> fail rate of 2.5% // SDD : 0.5%
   4. RAID의 종류
      1. RAID 0 (Stripping, 분산저장)
         1. 데이터를 여러 디스크에 분산저장하여 스피드는 빠르나 안정성이 떨어짐
            1. 6 array는 데이터유실률이 13.5% 라고
         2. 서버 cache저장 등 데이터 유실에 걱정 없을 시 사용
      2. RAID 1 (Mirroring, 복사저장)
         1. 2개 한묶음으로 하여 복사본도 저장 -> array's failure시 복구가능
         2. 읽기는 빠르나 쓰기는 느리고 용량은 두 배로 차지
      3. RAID 4
         1. 최소 2 개의 디스크에 분산저장
      4. RAID 5/6 (stripping + Distributed Parity)
         1. 최소 3 개의 드라이브 필요
         2. 데이터를 여러 개의 디스크에 분산저장 한 후 parity정보를 마지막 하나에 저장
            1. 데이터량을 보고 분산해야 하므로 이를 수행하는  deicated 하드웨어 필요
         3. 읽기에는 빠르나 쓰기에는 느림
      5. RAID 0+1 / 1+0
         1.  Striping then mirroring / Mirroring then stripping
         2. mirroring 먼저하느냐 striping 먼저 하느냐의 차이
         3. 1+0의 경우 mirroring 먼저 하므로 손실된 데이터만 복원 가능하나 0+1은 그룹으로 나뉜 데이터 전체를 복원해야 함

3. Failover

   1. 장애 시 예비 시스템으로 전환하여 사용

4. Fallback

   1. 장애발생 시 장애발생 이전 저장해두었던 상태로 돌아가기

      

5. 출처

   1. [RAID]([Almost Everything You Should Know About RAID | Steadfast](https://www.steadfast.net/blog/almost-everything-you-need-know-about-raid))
   2. [RAID]([Riad 0, Raid 1, Raid 10, .. : 네이버블로그 (naver.com)](https://blog.naver.com/kanglae77/220609327442))
   3. [failover/failback]([What’s the Difference Between Failover and Failback? | Rubrik](https://www.rubrik.com/insights/the-difference-between-failover-and-failback))