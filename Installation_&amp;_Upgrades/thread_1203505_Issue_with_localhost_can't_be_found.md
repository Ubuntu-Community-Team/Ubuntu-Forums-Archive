---
title: "Issue with localhost can't be found"
date: 2009-07-03
forum: Installation &amp; Upgrades
---

### Post by ml41782 on 2009-07-03
HI , 
I'm running 9.04. This box is collecting solar and wind data and displays the data in a personal web page.  The IP of the box 192.168.1.50 . The box that the information is on is 1.10. There are no printers inviolved here or ties to a windows network.  This is just a standalone box. running appache2.2 , MySql 5.0 and adobe AIR. It also runs a weather program as well for added info to the web page. 

I had read a post of some one with a similar problem everything they were looking at looked like it was correct. 

Some time between patch upgrades since going to version 9 I have had issues with Mysql and now another program runnning properly. The programs are failling to find "localhost". I have looked in the local hosts table /etc/hosts and it is there. 

I do see I have some line errors that I need to fix at layer 2. That wouldn't stop localhost 

otg1017@Webserver:~$ nslookup localhost
Server:        4.2.2.2
Address:    4.2.2.2#53

** server can't find localhost: NXDOMAIN

why is it I can't see it in an nslookup but I can ping it...

otg1017@Webserver:~$ ping localhost
PING localhost (127.0.0.1) 56(84) bytes of data.
64 bytes from Webserver (127.0.0.1): icmp_seq=1 ttl=64 time=0.073 ms
64 bytes from Webserver (127.0.0.1): icmp_seq=2 ttl=64 time=0.074 ms
64 bytes from Webserver (127.0.0.1): icmp_seq=3 ttl=64 time=0.072 ms
64 bytes from Webserver (127.0.0.1): icmp_seq=4 ttl=64 time=0.071 ms
64 bytes from Webserver (127.0.0.1): icmp_seq=5 ttl=64 time=0.075 ms
64 bytes from Webserver (127.0.0.1): icmp_seq=6 ttl=64 time=0.068 ms


otg1017@Webserver:~$ cat /etc/hosts
127.0.0.1       localhost
192.168.1.50    Webserver
192.168.1.10    webbox
# The following lines are desirable for IPv6 capable hosts
# ::1     ip6-localhost ip6-loopback
# fe00::0 ip6-localnet
# ff00::0 ip6-mcastprefix
# ff02::1 ip6-allnodes
# ff02::2 ip6-allrouters
# ff02::3 ip6-allhosts
otg1017@Webserver:~$ 

otg1017@Webserver:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:04:5a:76:44:eb  
          inet addr:192.168.1.50  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::204:5aff:fe76:44eb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:813411 errors:36 dropped:0 overruns:36 frame:36
          TX packets:0 errors:485093 dropped:0 overruns:0 carrier:969616
          collisions:0 txqueuelen:1000 
          RX bytes:541869711 (541.8 MB)  TX bytes:0 (0.0 B)
          Interrupt:10 Base address:0xec00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:180977 errors:0 dropped:0 overruns:0 frame:0
          TX packets:180977 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17517344 (17.5 MB)  TX bytes:17517344 (17.5 MB)

otg1017@Webserver:~$

---

