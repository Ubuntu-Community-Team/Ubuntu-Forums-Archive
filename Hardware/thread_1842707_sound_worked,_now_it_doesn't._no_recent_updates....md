---
title: "sound worked, now it doesn't. no recent updates..."
date: 2011-09-12
forum: Hardware
---

### Post by marcdjr on 2011-09-12
I am pretty new to ubuntu and linux in general, so many of the technical terminal solutions to sound card issues ar over my head.

I ran in a terminal:
lspci -v | less

and saw two audio devices:
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Defini
tion Audio (rev 06)
01:00.1 Audio device: nVidia Corporation GF106 High Definition Audio Controller 
(rev a1)


I do not know if I need to refer to ALSA list, which I did, but was unsure what was what.

also, saw in another [thread]("http://ubuntuforums.org/showthread.php?t=1721701") a command and ran it:
wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh

[Here is that link.]("http://www.alsa-project.org/db/?f=3c8f7e300acaac81a418099bea34d85bfafcc64f")

Any suggestions?

---

### Post by mastablasta on 2011-09-12
which version of Ubuntu?

---

### Post by marcdjr on 2011-09-12
> **mastablasta said:**
> which version of Ubuntu?

Ubuntu 11.04

---

### Post by marcdjr on 2011-09-12
Don't know what changed, but in the process of booting between os's, it works again.

The weird part is that I rebooted like 20 times between now and when it stopped?

---

