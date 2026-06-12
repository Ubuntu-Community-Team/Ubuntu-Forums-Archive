---
title: "Ubuntu 12.04, 600 x 480 resolution,  mercury motherboard driver needed."
date: 2013-10-13
forum: Hardware
---

### Post by wheelchairman on 2013-10-13
Hi,
Just installed ubuntu 12.04. Monitor - SAMSUNG SyncMaster 943NWX. Resolution - 600 x 480 only. Motherboard Mercury. 
Please help restore resolution to 1280 x 1024. Thanks.
regards,
wheekchairman.

---

### Post by varunendra on 2013-10-14
I don't have much idea about video resolution issues, but it may help if you post the exact video card/chip and driver it is using. The output of the following should give us both -
```
lspci -nnk | grep -iA2 vga
```

And have you checked the "Additional Drivers" program to see if there is a suggestion to download a proprietary driver?

---

### Post by wheelchairman on 2013-12-31
Subsystem: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub [8086:2770]
	Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller [0300]: Intel Corporation 82945G/GZ Integrated Graphics Controller [8086:2772] (rev 02)
	Subsystem: Intel Corporation 82945G/GZ Integrated Graphics Controller [8086:2772]
	Kernel modules: intelfb, i915

Sorry, in frustration I have uninstalled Ubuntu. Hoping that someone like u would help reinstalled again with problem persisiting. Please help.

---

### Post by Bucky Ball on 2013-12-31
Yea, reinstalling is not going to do anything different so if the install is fine just leave it at that. ;)

Have you gone to the display settings and changed it there??? You should get a selection.

Not on Ubuntu at the moment but Settings>Display or something like that should get you there. Select resolution. Additional Drivers are possibly not required for this resolution (and could give rise to a whole bunch of other issues). 

Try the obvious first.

---

### Post by wheelchairman on 2013-12-31
'LapTop' button is ON with editing disabled. Resolution displays as 1280 x 1024. But the actual display screen width is 3 inches smaller.

---

