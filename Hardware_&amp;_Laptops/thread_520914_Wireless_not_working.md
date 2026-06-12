---
title: "Wireless not working?"
date: 2007-08-08
forum: Hardware &amp; Laptops
---

### Post by cameron1 on 2007-08-08
Hi, my wireless isn't working when I'm on Ubuntu but it works when I boot into Vista. 

Also in Ubuntu I can go wired into the router, but I prefer Wireless.

Any advice?

---

### Post by solar george on 2007-08-08
What is the make/model of your wireless adaptor?

Can you post the output of,
```
lspci
```

---

### Post by cameron1 on 2007-08-09
> **solar george said:**
> What is the make/model of your wireless adaptor?

Can you post the output of,
```
lspci
```

It's a dell.

I'm not sure where I can find that info, but heres some info I found in network connection in Vista.

Dell Wireless 1500 Draft 802.11n WLAN Mini-Card

---

### Post by EXCiD3 on 2007-08-09
You need to open a terminal (console) and type: ```
lspci
```

You will probably need to use ndiswrapper to install the drivers for that card, as they are not supported out of the box with Ubuntu. Unfortunately the new wireless 802.11n cards don't have great support yet, use an ndiswrapper tutorial and see if you can modify it to use YOUR drivers instead of the ones on the howto...good luck. This will certainly be a learning experience for you ;)

---

### Post by cameron1 on 2007-08-10
> **EXCiD3 said:**
> You need to open a terminal (console) and type: ```
lspci
```

You will probably need to use ndiswrapper to install the drivers for that card, as they are not supported out of the box with Ubuntu. Unfortunately the new wireless 802.11n cards don't have great support yet, use an ndiswrapper tutorial and see if you can modify it to use YOUR drivers instead of the ones on the howto...good luck. This will certainly be a learning experience for you ;)

Where do I type that lol

Thanks for your help,

Cameron

---

### Post by ugm6hr on 2007-08-10
> **cameron1 said:**
> Where do I type that lol


Look at the link in my signature about "Code entries"

---

### Post by cameron1 on 2007-08-20
Srry for the long awaited response. What I did was since I can't get on the interent with the laptop i'm trying to get the wireless tow rok on, I pasted the output of the comamnd, into a text editor then saved it, and put it on a USB, then put it on this desktop, which I'll upload. 

I think you have to open it on a linux computer, cause of the file format.

Thanks for your help again

here is the link to download the file.

[http://www.mediafire.com/?bhml4mds1bx](http://www.mediafire.com/?bhml4mds1bx)

ps the output o that commmand was a big list of drivers that have been installed it looked like, it was pretty long list. Thanks.

---

### Post by ntlam on 2007-08-21
can you go to your window to check your wireless card? the information about it would help

---

### Post by solar george on 2007-08-21
```
0b:00.0 Network controller: Broadcom Corporation Unknown device 4328 (rev 01)
```

Looks like a BCM43xx type card,

Try using ndiswrapper

```
sudo aptitude install ndisgtk
```

This will install ndiswrapper and ndisgtk (a gui for ndiswrapper), and use it to install your wireless cards (windows) drivers.

---

### Post by cameron1 on 2007-08-21
> **solar george said:**
> ```
0b:00.0 Network controller: Broadcom Corporation Unknown device 4328 (rev 01)
```

Looks like a BCM43xx type card,

Try using ndiswrapper

```
sudo aptitude install ndisgtk
```

This will install ndiswrapper and ndisgtk (a gui for ndiswrapper), and use it to install your wireless cards (windows) drivers.

Alright, I'm going to school in about 10 minutes I'll try this the second I get back.

Thanks,
Cameron

---

### Post by rajashokkumar on 2007-08-24
Hi,


Even I  am facing the same issue , not able to get connectd through the wireless card but I am able to connect through wired card. 

Even i tried to update the following still not working.
administrator@ubuntu:~/ashok$ sudo aptitude install ndisgtk


NOTE : When i try to connect through wireless it says connected but not able to browse i am getting server not found error for all website.

Please see the requested above details in my laptop(Dell)

administrator@ubuntu:~/ashok$ cat /etc/issue
Ubuntu 7.04 \n \l

administrator@ubuntu:~/ashok$ lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 [Mobility FireGL 9000] (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5702X Gigabit Ethernet (rev 02)
02:01.0 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:01.1 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
03:00.0 Ethernet controller: Atheros Communications, Inc. AR5006X 802.11abg NIC (rev 01)
administrator@ubuntu:~/ashok$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:14:BF:7C:5E:BC  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:875 (875.0 b)  TX bytes:7858 (7.6 KiB)

eth0      Link encap:Ethernet  HWaddr 00:0B:DB:DB:BE:87  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1675 errors:0 dropped:0 overruns:0 frame:1
          TX packets:1405 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1634802 (1.5 MiB)  TX bytes:182414 (178.1 KiB)
          Interrupt:11 

eth0:avah Link encap:Ethernet  HWaddr 00:0B:DB:DB:BE:87  
          inet addr:169.254.9.238  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:992 errors:0 dropped:0 overruns:0 frame:0
          TX packets:992 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:78740 (76.8 KiB)  TX bytes:78740 (76.8 KiB)

wifi0     Link encap:UNSPEC  HWaddr 00-14-BF-7C-5E-BC-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:114505 errors:0 dropped:0 overruns:0 frame:27298
          TX packets:4690 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:9485594 (9.0 MiB)  TX bytes:205186 (200.3 KiB)
          Interrupt:11 

administrator@ubuntu:~/ashok$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:15 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signa il level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:108938  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

administrator@ubuntu:~/ashok$ 



Thanks in advance,
-Ashok.

---

