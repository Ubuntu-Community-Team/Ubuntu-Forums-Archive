---
title: "No wired connection on ubuntu 9.04"
date: 2009-06-09
forum: Installation &amp; Upgrades
---

### Post by vicalanis on 2009-06-09
Hello everyone, this is my first post here,so bear with me :)
I'd really love to switch from XP so I tried Ubuntu: I installed it on my other drive,and everything works OK (audio,video,etc) But (and its a huge but) I cannot establish my Internet connection. I have an ethernet cable with an automatic IP address, so I don't need username and password. There's a little animation when establishing the connection,but at the end,the result is the same: "Wired connection disconnected" or something like that...Here's my ifconfig result:

ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:18:f3:ab:2b:3a  
          inet6 addr: fe80::218:f3ff:feab:2b3a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:152 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10460 (10.4 KB)  TX bytes:3888 (3.8 KB)
          Interrupt:20 Base address:0xb800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

I tried deleting  my "Auto eth0" connection,restarted the PC and tried to establish it again...( did not work) 
Please help me...I fell in love with Ubuntu and really want to use it permanently.

EDIT: and sorry if my post is not in the right section, just move it then
And thank in advance...even for reading it.

---

### Post by LeapingLeapord on 2009-06-09
Have you checked your patch cable?

---

### Post by vicalanis on 2009-06-09
The cable is OK...I have no trouble connecting to the Internet on XP

---

### Post by vicalanis on 2009-06-09
So? Anyone came up with a solution yet ? Sorry for being impatient :)

---

### Post by vicalanis on 2009-06-11
Bump...

---

### Post by Goodlooking on 2009-10-21
I also have been having htese problems, I just bought my Compaq Avo with Ubuntu installed and I get the same error messages as the first comment.
Altho, the Ubuntu@ubuntu:~$ is actually user@user:~$. HELPP

ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:18:f3:ab:2b:3a  
          inet6 addr: fe80::218:f3ff:feab:2b3a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:152 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10460 (10.4 KB)  TX bytes:3888 (3.8 KB)
          Interrupt:20 Base address:0xb800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

---

### Post by Iowan on 2009-10-21
[This]("http://ubuntuforums.org/showthread.php?t=1156441") was my problem/solution.

---

### Post by Goodlooking on 2009-10-21
> **Iowan said:**
> [This]("http://ubuntuforums.org/showthread.php?t=1156441") was my problem/solution.

I have looke dthrew the thread and can't find an answer, I am really new at computer period, I have used widows foreva and still have no dea what to do with them, I don't know what al the commands are for, I have tried entering some of them, such as the previous one, Next step would be?

Thanks btw for your time, I am getting really irritated with not being abe to use my new Laptop.

---

