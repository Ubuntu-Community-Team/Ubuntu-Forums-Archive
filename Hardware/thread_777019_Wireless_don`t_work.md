---
title: "Wireless don`t work"
date: 2008-05-01
forum: Hardware
---

### Post by Nicolasto on 2008-05-01
Hi, 
I just installed Ubuntu 8.04 on an [ Acer Travelmate 660]("http://www.acersupport.com/notebook/html/tm660.html"), but I can't activate wireless, on Ubuntu 7.10 it worked.
Can somebody help me?
Sorry for my English:oops:

---

### Post by ajmorris on 2008-05-01
hi there, could you please give us some information about what wireless card you are running? :)

(paste output of sudo lspci)

also, can you paste the outputs of sudo ifconfig and sudo iwconfig


AJ

---

### Post by Nicolasto on 2008-05-01
> **ajmorris said:**
> hi there, could you please give us some information about what wireless card you are running? :)

(paste output of sudo lspci)

also, can you paste the outputs of sudo ifconfig and sudo iwconfig


AJ
Here are the results of lspci
```
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:02.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:04.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
02:06.0 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:06.1 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)

```

Here of sudo ifconfig:
```
nicola@nicola-laptop:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:c0:9f:26:fa:1d  
          inet addr:192.168.1.5  Bcast:192.168.1.7  Mask:255.255.255.248
          inet6 addr: fe80::2c0:9fff:fe26:fa1d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20317 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19605 errors:0 dropped:0 overruns:0 carrier:0
          collisions:49 txqueuelen:1000 
          RX bytes:8689856 (8.2 MB)  TX bytes:9624767 (9.1 MB)
          Interrupt:11 

eth1      Link encap:Ethernet  HWaddr 00:04:23:59:05:c5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0x6000 Memory:e0206000-e0206fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2919 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2919 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:132825 (129.7 KB)  TX bytes:132825 (129.7 KB)

```
and here of sudo iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
Now I'm connected with Lan cable

---

### Post by Nicolasto on 2008-05-01
I do not know how but now I can enable wireless and works!

---

### Post by Nicolasto on 2008-05-02
I'm so an idot! It was enough press the button of the wireless to turn on it!! A friend of mine had the same problem and we have them two hours to seek a solution to then discover that just press a button!

---

### Post by subzero316 on 2008-05-02
lol..hm it wont have been an issue if the light worked

---

