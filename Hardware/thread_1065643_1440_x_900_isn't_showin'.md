---
title: "1440 x 900: isn't showin'"
date: 2009-02-10
forum: Hardware
---

### Post by Deuz Ex Machina on 2009-02-10
Hiya folks, just put intrepid ibex on my sony vaio vgn-fe550g. Unfortunately I can't seem to get the native 1440 x 900 display working, if anyone could possibly help some, I'd be grateful. Step by step instructions would be great, I don't have any graphics card, just the onboard intel. Tried finding on the site some similar issues, but the people who posted had nvid @.@ 

```
L Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

```

```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

:popcorn:

---

### Post by Deuz Ex Machina on 2009-02-10
Haha, anyone?

---

### Post by Deuz Ex Machina on 2009-02-10
More info sort of?

```
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
	Subsystem: Sony Corporation Device [104d:81ef]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at d0100000 (32-bit, non-prefetchable) [size=512K]
	Region 1: I/O ports at 1800 [size=8]
	Region 2: Memory at b0000000 (32-bit, prefetchable) [size=256M]
	Region 3: Memory at d0180000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>
	Kernel modules: intelfb

00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
	Subsystem: Sony Corporation Device [104d:81ef]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Region 0: Memory at 54000000 (32-bit, non-prefetchable) [disabled] [size=512K]
	Capabilities: <access denied>

```

---

### Post by Deuz Ex Machina on 2009-02-10
Also, Im not sure if this information would help, but when running the live cd of LInux Mint, I do get the native 1440 x 900

---

### Post by martinbaselier on 2009-02-10
can't find the right setting at the moment. You should be able to find it in man xorg.conf

---

### Post by avrilrox on 2009-02-10
You can edit the resolutions by editing your /etc/X11/xorg.conf file.

I can't remember exactly what the syntax is and i'm not running Ubuntu right now... I'm experiencing some issues.

---

### Post by avrilrox on 2009-02-10
Make sure you read[ this]("http://ubuntuforums.org/showthread.php?t=83973")

---

### Post by Deuz Ex Machina on 2009-02-12
Ah hey so, I haven't tried that option yet on manually changing the xorg, but I will soon enough. Here's the weird part tho, before I installed ubuntu on this laptop I was running at 1440 x 900, ok well now when I log into my media center I have two different display types for my monitor, the plug and play option and some default. Anyway, the second option the default doesn't have 1440 x 900 but several resolutions higher then that I never had before. Such as like 1680x1050 never had that before tho. Also the media center and the xp have been split as if they were two different operating systems. When I start it in xp it leads me to a help screen in restoring the media center xD And only the media center is the actual OS I was using prior. Which I just found odd. Anyway, thank you so far for the help, Im not sure if I should even mess around with the xorg if my plug and play settings for the media center im using now is stalled at 1280 X 800 

if anyone has more info feel free to sure. Wondering if it has anything to do with the intel accelerated graphics chip thats in the laptop.

---

### Post by densou on 2009-02-14
first, you need to edit these lines onto your xorg.conf:
```
Section "Device"
        Identifier 	"intel"
        Driver     	"intel"
EndSection

Section "Screen"
        Identifier 	"Default Screen"
	Device 		"intel"
EndSection
```

How to set 1440x900:
[http://www.x.org/wiki/Projects/XRandR](http://www.x.org/wiki/Projects/XRandR)

---

