---
title: "Radeon vs FGLRX drivers"
date: 2007-08-07
forum: Hardware &amp; Laptops
---

### Post by Elvish Legion on 2007-08-07
If I install (or atempt to) the open source drivers (I have an xpress 200 ATI card...I'm almost postive it'll work) will I still get 3d accel? If not it isn't a HUGE deal (I mostly play NWN and baldurs gate 2, nothing that really takes heavy 3d) Just curious

---

### Post by stchman on 2007-08-07
> **Elvish Legion said:**
> If I install (or atempt to) the open source drivers (I have an xpress 200 ATI card...I'm almost postive it'll work) will I still get 3d accel? If not it isn't a HUGE deal (I mostly play NWN and baldurs gate 2, nothing that really takes heavy 3d) Just curious

I have a Radeon XPress 200M on my laptop and the restricted driver works well.  I have 3D acceleration (tested it using glxgears and fglxgears).  Mind you the 200M is not a 3d power house but will run Google Earth and some old school 3D games.

---

### Post by JamesDS on 2007-08-07
Could someone help me install these restricted drivers for my Radeon Xpress 200M ?  When I click the 'Restricted Drivers Manager', it says I don't have any hardware which requires them - but I do have the same graphics card as the posters above.

---

### Post by stchman on 2007-08-07
> **JamesDS said:**
> Could someone help me install these restricted drivers for my Radeon Xpress 200M ?  When I click the 'Restricted Drivers Manager', it says I don't have any hardware which requires them - but I do have the same graphics card as the posters above.

All I did was go to the restricted driver manager and click to enable it.  I had to reboot the machine and all worked fine.

Give me a uname -a and paste here and an lspci as well.

You need the proper kernel to support ATI based cards.

---

### Post by JamesDS on 2007-08-07
```
uname -a

Linux jamesds 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux
```

```

lspci

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

---

### Post by stchman on 2007-08-07
> **JamesDS said:**
> ```
uname -a

Linux jamesds 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux
```

```

lspci

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

We have very similar laptops.  Mine is a Celeron M processor yours appears to be an Athlon 64.

I just checked the enable on the restricted driver for ATI and rebooted.  If I remember correctly I had to try a couple of times to enable the driver but it worked.

You are running the proper kernel as well.  Try again.

---

### Post by JamesDS on 2007-08-07
OK, I've got a Compaq V5115EU.  I'll keep trying, just it says "Your hardware doesn't need any restricted drivers".  Need I add a repository or tick a box somewhere?

---

### Post by stchman on 2007-08-07
> **JamesDS said:**
> OK, I've got a Compaq V5115EU.  I'll keep trying, just it says "Your hardware doesn't need any restricted drivers".  Need I add a repository or tick a box somewhere?

No, when I installed Ubuntu on my laptop all I did was check the enable box in the restricted drivers section.  First time I tried it would not take, but I tried again and it worked.

---

### Post by Elvish Legion on 2007-08-10
How would Igo about installing the open source drivers? I can't seem to find the documentation

---

