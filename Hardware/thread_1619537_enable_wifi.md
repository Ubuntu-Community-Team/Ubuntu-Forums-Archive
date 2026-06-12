---
title: "enable wifi"
date: 2010-11-11
forum: Hardware
---

### Post by Cnfys on 2010-11-11
Hello,

First off all, i'm completely  new to linux.
I've just installed xubuntu 10.10 and everything works fine except the wifi.
I'm googleling for 5 houres now but i stil didn't find a solution.
First off all, my laptop is a medion 97600 and my network card is ipw2200.
The laptop has got a button to enable or disable wifi. 
But this button doesn't work in xubunu, so i can't enable my wifi.
Can anyone tell me what i should do to enable it ?

Thx in advance,
Greetz Cnfys

---

### Post by Fafler on 2010-11-12
It should work with the ipw2200 driver, which is included in Ubuntu.

I haven't really used Xubuntu enough to know how wireless networks work. Is there a network applet on the panel? 

Try opening a terminal and post the outputs of:

```
modprobe ipw2200
ifconfig -a
```

---

### Post by Cnfys on 2010-11-12
> **Fafler said:**
> It should work with the ipw2200 driver, which is included in Ubuntu.

I haven't really used Xubuntu enough to know how wireless networks work. Is there a network applet on the panel? 

Try opening a terminal and post the outputs of:

```
modprobe ipw2200
ifconfig -a
```

this is whats comes out:

```
 dien@dien:~$ sudo modprobe ipw2200
[sudo] password for dien: 
dien@dien:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0a:e4:b9:b0:71  
          inet addr:192.168.0.199  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:e4ff:feb9:b071/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2198 errors:29 dropped:36 overruns:29 frame:0
          TX packets:1664 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3097160 (3.0 MB)  TX bytes:160809 (160.8 KB)
          Interrupt:18 Base address:0x3000 

eth1      Link encap:Ethernet  HWaddr 00:16:6f:ad:0b:fe  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0xe000 Memory:b8000000-b8000fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:92 errors:0 dropped:0 overruns:0 frame:0
          TX packets:92 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7280 (7.2 KB)  TX bytes:7280 (7.2 KB) 
```Would switching to ubuntu be a solution?
edit: It isn't. I just tried running ubuntu with a cd and i had the same problem

---

### Post by Cnfys on 2010-11-12
> **Fafler said:**
> . Is there a network applet on the panel? 


Yes there is, It sais i have wired connection but wifi is disabled.

---

