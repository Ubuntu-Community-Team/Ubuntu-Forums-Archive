---
title: "Radeon 9600 Pro - only 60FPS?"
date: 2010-12-25
forum: Hardware
---

### Post by adam993 on 2010-12-25
Hello!
I booted LiveCD version of Ubuntu 10.10 and I checked the glxgears results. Terminal shows only 60FPS, I can't enable transparency.
Hardware:
Athlon 2.0GHz
1GB RAM
Gigabyte GA-K8U (ULI 1689)
Radeon 9600 Pro (driver radeon, of course)
On Ubuntu 10.04 I've more than 2000FPS.
What's wrong?
*bump*

---

### Post by adam993 on 2010-12-26
*bump*

---

### Post by Decatf on 2010-12-26
Run it with:
[B]vblank_mode=0 glxgears

[/B]

---

### Post by adam993 on 2010-12-29
> 
ATTENTION: default value of option vblank_mode overridden by environment.
ATTENTION: default value of option vblank_mode overridden by environment.
8463 frames in 5.0 seconds = 1692.432 FPS
8560 frames in 5.0 seconds = 1711.909 FPS
7493 frames in 5.0 seconds = 1498.400 FPS
8704 frames in 5.0 seconds = 1740.787 FPS
8556 frames in 5.0 seconds = 1711.103 FPS
8551 frames in 5.0 seconds = 1710.059 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 57212 requests (57212 known processed) with 0 events remaining.

On LiveCD mode, I stopped the processing.
Without  vblank_mode=0:
> 
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
301 frames in 5.0 seconds = 60.171 FPS
301 frames in 5.0 seconds = 60.023 FPS
301 frames in 5.0 seconds = 60.016 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 2078 requests (2077 known processed) with 0 events remaining.

lspci:
> 
00:00.0 Host bridge: ALi Corporation M1689 K8 Northbridge [Super K8 Single Chip]
00:01.0 PCI bridge: ALi Corporation AGP8X Controller
00:02.0 PCI bridge: ALi Corporation M5249 HTT to PCI Bridge
00:03.0 ISA bridge: ALi Corporation M1563 HyperTransport South Bridge (rev 70)
00:03.1 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:0e.0 IDE interface: ALi Corporation M5229 IDE (rev c7)
00:0e.1 Mass storage controller: ALi Corporation ULi 5289 SATA (rev 10)
00:0f.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0f.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0f.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0f.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary)
02:07.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
02:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

and also:
> 
direct rendering: Yes

system: Linux ubuntu 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686 GNU/Linux
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.10
Release:    10.10
Codename:    maverick

---

