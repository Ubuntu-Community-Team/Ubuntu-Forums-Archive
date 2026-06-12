---
title: "graphics gone dodgy in edgy"
date: 2007-01-21
forum: Hardware &amp; Laptops
---

### Post by cmacis on 2007-01-21
I just upgraded from dapper to edgy hoping that it might solve this problem, but it has acutally gotten worse. ](*,) 

Currently my laptop (spec/data sheet available here:[http://www.fujitsu-siemens.co.uk/Resources/72/1031346079.pdf](http://www.fujitsu-siemens.co.uk/Resources/72/1031346079.pdf)) is using the default graphics drivers, which work, but not very well. Scrolling in firefox is slow and jumpy and gaming is something that happens to other people. I tried  dpkg-reconfigure xserver-xorg to use the via drivers (which someone said should work for unichrome cards, which is what the data sheet claims is in my laptop) but on restart I get the error message that no visual device was found, so I have to restore the default settings. 

Here is the output from lspci, which I think shows that PCI:1:0:0 is the screen (well, that's what the program to change the settings thinks it is anyway)
00:00.0 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:06.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
**01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01)**

Should I be doing something different than calling it "default video driver" and accepting all defaults? Does anyone else have this laptop and has managed to get this working?

Also Dapper made the RHS of my touchpad act like a scrollwheel, but edgy has taken that away from me. Does anyone know how to return it to it's scrollwheely goodness?

---

### Post by cmacis on 2007-01-22
Help, anyone, please. Or I may have to return to windows. :o

---

### Post by cmacis on 2007-01-22
Sorted, thanks to [https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome) . Even got my scroll-wheel emulation working automatically. Not tested games yet but back in term so I don't have time for games.

---

