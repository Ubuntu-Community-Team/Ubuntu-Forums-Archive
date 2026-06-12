---
title: "Connecting M Audio M Track USB Interface (Newbie to Linux UBUNTU)"
date: 2016-02-07
forum: Hardware
---

### Post by iyerarv on 2016-02-07
I am a complete newbie to Ubuntu / Linux and am trying to connect my M Audio MTRACK USB interface.

Even if there is a thread that explains this from scratch, please do direct me to it. Thanks in advance.

---

### Post by Lasakro on 2016-02-20
I just grabbed my M-Track out of the closet and before hooking it up found your question here. There doesn't seem to be any info about it's use with Ubuntu from my quick search but here are reports of success here with other distros:
[https://linuxmusicians.com/viewtopic.php?t=11131](https://linuxmusicians.com/viewtopic.php?t=11131)

How have you made out?

So far I found that alsamixer detects "M-Track" and lsusb detects "Midiman". Now I've uninstalled PulseAudio to run JACK2 (jackdbus), ALSA to JACK bridges with calf plug-in's on Ubuntu Studio. When plugging my USB and Audio out from the M-Track my speakers are sensing the connections but it looks like the input of the M-Track is still out to lunch. When I find a solution I'll report back.

Oh, a link about Ubuntu Studio being compatible with M-T:
[https://help.ubuntu.com/community/UbuntuStudio/SupportedHardware](https://help.ubuntu.com/community/UbuntuStudio/SupportedHardware)

Also a 2 month old here with Linux, BTW....and lovin' it!

---

