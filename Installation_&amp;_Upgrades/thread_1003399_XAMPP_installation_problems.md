---
title: "XAMPP installation problems"
date: 2008-12-06
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2008-12-06
I have installed XAMP
when I run 
muf@muf-desktop:~/Desktop$ sudo /opt/lampp/lampp start
[sudo] password for muf: 
Starting XAMPP for Linux 1.6.8a...
XAMPP: XAMPP-Apache is already running.
XAMPP: Another MySQL daemon is already running.
XAMPP: Another FTP daemon is already running.
XAMPP for Linux started.
I think another server is occupying the port 80 ???
when I [http://localhost/](http://localhost/)
I se in browser this "It works!" I want to find the witch server is causing it.
 I run netstat -l

muf@muf-desktop:~/Desktop$ netstat -l
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 localhost:mysql         *:*                     LISTEN     
tcp        0      0 *:tproxy                *:*                     LISTEN     
tcp        0      0 *:1234                  *:*                     LISTEN     
tcp        0      0 *:ftp                   *:*                     LISTEN     
tcp        0      0 localhost:ipp           *:*                     LISTEN     
tcp6       0      0 ip6-localhost:47304     [::]:*                  LISTEN     
tcp6       0      0 [::]:www                [::]:*                  LISTEN     
tcp6       0      0 [::]:https              [::]:*                  LISTEN     
udp        0      0 *:bootpc                *:*                                
udp        0      0 *:mdns                  *:*                                
udp        0      0 *:55547                 *:*                                
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node   Path
unix  2      [ ACC ]     STREAM     LISTENING     16895    /var/run/sdp
unix  2      [ ACC ]     STREAM     LISTENING     30537    @/var/run/hald/dbus-M2yZKvF7rK
unix  2      [ ACC ]     STREAM     LISTENING     50152    /tmp/orbit-muf/linc-34ef-0-185baf02e6dfb
unix  2      [ ACC ]     STREAM     LISTENING     18053    @/tmp/dbus-y4wUkMnYAa
unix  2      [ ACC ]     STREAM     LISTENING     83678    /tmp/orbit-muf/linc-3525-0-138c1365901c7
unix  2      [ ACC ]     STREAM     LISTENING     16913    @/org/bluez/audio
unix  2      [ ACC ]     STREAM     LISTENING     17165    @/tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     81757    /opt/lampp/logs/cgisock.14259
unix  2      [ ACC ]     STREAM     LISTENING     30540    @/var/run/hald/dbus-vQDq7zyTnR
unix  2      [ ACC ]     STREAM     LISTENING     15475    /var/run/mysqld/mysqld.sock
unix  2      [ ACC ]     STREAM     LISTENING     17166    /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     18038    /tmp/ssh-DtHihh5833/agent.5833
unix  2      [ ACC ]     STREAM     LISTENING     18155    /tmp/.esd-1000/socket
unix  2      [ ACC ]     STREAM     LISTENING     18158    /tmp/pulse-muf/native
unix  2      [ ACC ]     STREAM     LISTENING     18207    /tmp/orbit-muf/linc-1737-0-4f5306b41d2aa
unix  2      [ ACC ]     STREAM     LISTENING     18443    /tmp/orbit-muf/linc-1735-0-7530fb2b4966d
unix  2      [ ACC ]     STREAM     LISTENING     14991    /var/run/acpid.socket
unix  2      [ ACC ]     STREAM     LISTENING     18477    /tmp/seahorse-NMIMBy/S.gpg-agent
unix  2      [ ACC ]     STREAM     LISTENING     18501    /tmp/.ICE-unix/5833
unix  2      [ ACC ]     STREAM     LISTENING     18524    /tmp/orbit-muf/linc-16c9-0-6f77554e65c4
unix  2      [ ACC ]     STREAM     LISTENING     18714    /tmp/orbit-muf/linc-1779-0-ae5201a2205b
unix  2      [ ACC ]     STREAM     LISTENING     18719    /tmp/keyring-MQJsxl/socket
unix  2      [ ACC ]     STREAM     LISTENING     18721    /tmp/keyring-MQJsxl/ssh
unix  2      [ ACC ]     STREAM     LISTENING     18723    /tmp/keyring-MQJsxl/socket.pkcs11
unix  2      [ ACC ]     STREAM     LISTENING     18784    /tmp/orbit-muf/linc-177d-0-69224fb05dde4
unix  2      [ ACC ]     STREAM     LISTENING     18845    /tmp/orbit-muf/linc-177e-0-6f288ae98a402
unix  2      [ ACC ]     STREAM     LISTENING     18975    /tmp/orbit-muf/linc-1785-0-47332e1127f0c
unix  2      [ ACC ]     STREAM     LISTENING     19057    /tmp/orbit-muf/linc-1787-0-609a1463a86bb
unix  2      [ ACC ]     STREAM     LISTENING     19172    /tmp/orbit-muf/linc-1789-0-7a2fdcfc95edc
unix  2      [ ACC ]     STREAM     LISTENING     19327    /tmp/orbit-muf/linc-17ab-0-47e62d3447f9d
unix  2      [ ACC ]     STREAM     LISTENING     19380    /tmp/orbit-muf/linc-173e-0-6988c99682f62
unix  2      [ ACC ]     STREAM     LISTENING     19430    /tmp/orbit-muf/linc-17b5-0-3adc7a68f3b6a
unix  2      [ ACC ]     STREAM     LISTENING     19609    /tmp/orbit-muf/linc-17c5-0-652c50f5cc25
unix  2      [ ACC ]     STREAM     LISTENING     19634    /tmp/orbit-muf/linc-17c1-0-75fffae515d48
unix  2      [ ACC ]     STREAM     LISTENING     20260    /tmp/orbit-muf/linc-17da-0-30da6d525182
unix  2      [ ACC ]     STREAM     LISTENING     20312    /tmp/orbit-muf/linc-17d0-0-117f44363cb5a
unix  2      [ ACC ]     STREAM     LISTENING     20325    /tmp/orbit-muf/linc-17d7-0-6aa2c46342492
unix  2      [ ACC ]     STREAM     LISTENING     20349    /tmp/orbit-muf/linc-17e2-0-f08578f58130
unix  2      [ ACC ]     STREAM     LISTENING     20390    /tmp/orbit-muf/linc-17ea-0-4b0b9f46d2575
unix  2      [ ACC ]     STREAM     LISTENING     35304    /tmp/orbit-muf/linc-3011-0-5c6f197aa9fce
unix  2      [ ACC ]     STREAM     LISTENING     15292    /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     17121    /var/run/gdm_socket
unix  2      [ ACC ]     STREAM     LISTENING     15341    /var/run/avahi-daemon/socket
unix  2      [ ACC ]     STREAM     LISTENING     46325    /var/run/cups/cups.sock

---

