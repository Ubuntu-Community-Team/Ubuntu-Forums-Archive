---
title: "Please help."
date: 2009-08-04
forum: Installation &amp; Upgrades
---

### Post by tad214 on 2009-08-04
[B]Hello,
I just upgraded my 8.04, to 8.10, so i can upgrade to 9.0. I was told i had to update one at a time till i got up to the newest version. Anyway, that is not a problem. The problem is, when i upgraded to 8.10, i now have no wireless options. When i click on my network window in the task bar, the drop down menu has all the options i need, however, they are greyed out. The only option that can be clicked on, is the vpn configuration. I just need my plain wireless network that i have always used.  I want to finish updating to 9.0 but i can't get online with it.  P.S. I ran a couple of commands that might help someone to be to help me. The results are posted below. Thanks in advance for the help. Have a blessed day. [COLOR="Red"]Dale[/COLOR] 

[COLOR="red"]For command lspci:[/COLOR]

00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4L/
ICH4M)
USB UHCI
Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4L/
ICH4M)
USB UHCI
Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4L/
ICH4M)
USB UHCI
Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4M)
USB2 EHCI Controller
(rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4M)
LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4M)
IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4L/
ICH4M)
AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4L/
ICH4M)
AC'97 Modem
Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go5200 64M] (rev a1)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401 100BaseT
(rev 01)
02:01.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
02:01.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE1394
Controller
02:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection
(rev 05)

[COLOR="red"]For command iwconfig:[/COLOR]

root@dalelaptop:~#
iwconfig
lo no wireless extensions.
eth0 no wireless extensions.
eth1 unassociated ESSID:"cheers wireless"
Mode:Managed Channel=0 Access Point: NotAssociated
Bit Rate:0 kb/s TxPower=
20 dBm Sensitivity=8/0
Retry limit:7 RTS thrff
Encryption key ff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
pan0 no wireless extensions.
root@dalelaptop:~#

Thank you again for all the help. Dale[/B]

---

### Post by Tux118 on 2009-08-04
That sounds strange. Have you checked if it is stable yet? If it isn't stable, those bugs like that are perfectly normal so you should wait until it becomes stable. If it is, I'm sorry, I can't help you.

---

### Post by Yanatsu on 2009-08-04
My advice would be to upgrade to 9.04 on a wired connection and hope it comes back-It does support more WiFi hardware, or at least it's the first release that has supported mine without drivers.
Also, did you install Ubuntu on this computer yourself or did it come with it? If it came with it, it may have had drivers installed on it-look it up. Or maybe you put drivers on yourself?

---

### Post by ugm6hr on 2009-08-04
Couple more details might help find the problem:

```
lshw -class network
lsmod
```

The Intell 2200 should use the ipw2200 driver - I know Intel restructured their drivers, so perhaps there is another driver conflicting with ipw2200.

---

### Post by tad214 on 2009-08-05
**Hi, Ok, thanks, i will try this.**

---

