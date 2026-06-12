---
title: "Font display problems, primarily in Firefox"
date: 2013-01-09
forum: Hardware
---

### Post by gwilson on 2013-01-09
I'm having font display problems which seem to be only noticeable in Firefox. Looks like horizontal white lines through letters (missing sections of individual letters). I have a Sony Vaio VGN-N130G laptop with 1.5 GB Ram and the following graphics chip. I read about font problems in Firefox 17 and went back to Firefox 15 and still have the problem.

Anyone have a solution or suggestion?  Thanks.

Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller 

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: Sony Corporation Device 8212
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Region 0: Memory at dc180000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

---

### Post by ajgreeny on 2013-01-09
[LIST=1]
[*]Try a new profile by renaming the hidden ~/.mozilla folder in your home.
[*]Start FF in safe mode with command ```
firefox --safe-mode
``` to see if that solves the problem.   If it does you will need to start it normally and disable your extensions/add-ons one by one until you find the culprit.
[*]Look at the font settings in FF Preferences->Content and change your current settings.
[/LIST]

---

### Post by jaddle on 2013-02-21
I have the same issue - it's not just in firefox though. I've seen it show up in just about every program. Especially firefox, thunderbird and xfce4-terminal - but those are the three that I'm using 99% of the time, so it's not surprising.

I have a thinkpad with the same graphics chip as the original poster, so maybe that has to do with the issue?

EDIT:
Some more googling led me to this bug: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/745608](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/745608)

Good news is that it looks like it might be fixed in 13.04! Until then, you can work around the issue with a /etc/X11/xorg.conf containing

```
Section "Device"
    Identifier "Intel"
    Driver "intel"
    Option "DebugWait" "true"
EndSection
```

I haven't tried that yet (requires a reboot) but from the replies in the bug report, it seems that it will fix it.

---

