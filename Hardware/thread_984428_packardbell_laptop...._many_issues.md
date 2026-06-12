---
title: "packardbell laptop.... many issues"
date: 2008-11-16
forum: Hardware
---

### Post by Snappo on 2008-11-16
I've been trying to get ubuntu running on my packard bell for a while now (I want Windows gone!). I've had many issues including no support for wireless or my intel video chip. I bought a dongle to use with my laptop which works fine on my two dell desktops. I installed a fresh copy of hardy and ended up with a 600x800 resolution as usual and weird errors when the laptop is booted (pnp bios stuff). I'm not too worried about my wireless but my video card has to work. So I thought these issues may have been solved in 8.10 but now I can't even connect to my wired network it looks as if it is connecting then just says "disconnected".

> 



To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

snappo@Snappo-Linux:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:06.0 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 02)
snappo@Snappo-Linux:~$ 

EASYNOTE R1005


The most important thing for now would be connecting to my network so I could continue to trouble shoot the other problems.

---

### Post by hydo1 on 2009-05-05
i have the easynote r1004 and i cant get the vidoe card working

---

