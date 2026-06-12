---
title: "Sony Vaio VGN-TX5XN"
date: 2008-12-26
forum: Hardware
---

### Post by Bedev on 2008-12-26
1)Version Of Ubuntu : 8.10 
2)Type Of Hardware : Sony Vaio VGN-TX5XN

Installation went amazingly smooth but graphics (OpenGL ?) are not good in eg Google Earth.  IN XMBC video is fair but the whole system blocks when I press pause.

I think that the issue is that I have a Intel GMA 950 in the system.  Searched for a solution but that seems not that simple...

Main purpose of the machine is to use XBMC but without solution to this I have to consider another solution...

Can somebody help me ?

---

### Post by pytheas22 on 2008-12-26
Yes, unfortunately I think that the Intel 950 cards have some issues.  If you could please post the output of this command, I'll try to help:
```

lspci -nn
```

---

### Post by Bedev on 2008-12-27
Here it is, thanks !

00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 02)
02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
06:04.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
06:04.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller [104c:803a]
06:04.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]
06:08.0 Ethernet controller [0200]: Intel Corporation PRO/100 VM Network Connection [8086:1093] (rev 02)

---

### Post by pytheas22 on 2008-12-27
I think that this [bug report]("https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/177492") is relevant to your problem.  It seems that there are some major revisions in progress with the Intel Linux video drivers, and the default configuration may not be the most efficient.

One user says that opening his /etc/X11/xorg.conf file and adding these options to the 'device' section yielded better performance on Ubuntu 8.10:

```
Option "MigrationHeuristic" "greedy"
Option "ExaNoComposite" "false"
Option "ExaOptimizeMigration" "true"
```

Does that help?

Also, do desktop effects work smoothly?

Finally, have you run XBMC on this machine under Windows just to verify that your graphics card is capable of handling it well?  Intel video is not made for super-intense stuff, remember; it could be the case that the device is just not powerful enough for what you're trying to do, driver issues aside.

---

