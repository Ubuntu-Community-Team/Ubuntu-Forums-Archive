---
title: "No sound on Asus G51VX"
date: 2011-03-05
forum: Hardware
---

### Post by TwiggLe on 2011-03-05
So this is my first time using Linux ever. 
I installed the newest Ubuntu 64bit. 

One thing though is I know my headphone jack is stuck in the "on" position. Cause with Windows i have to change a registery setting to force the speakers on and it also leaves the headphone jack on also.

Here's my info from Alsa incase that's needed.
[http://www.alsa-project.org/db/?f=bddc6287041c7563496908133a3746eab3df513b](http://www.alsa-project.org/db/?f=bddc6287041c7563496908133a3746eab3df513b)

---

### Post by Yellow Pasque on 2011-03-05
Googling around, I found someone who said this:
> This worked on my Asus G51VX:
Edit your /etc/modprobe.d/alsa-base.conf: gksu gedit /etc/modprobe.d/alsa-base.conf
Add this line at the end of your file: options snd-hda-intel model=m51va position_fix=0
Reboot.
[http://www.linlap.com/wiki/asus+g50v](http://www.linlap.com/wiki/asus+g50v)

Other options for the codec:
```
ALC662/663/272
==============
  3stack-dig	3-stack (2-channel) with SPDIF
  3stack-6ch	 3-stack (6-channel)
  3stack-6ch-dig 3-stack (6-channel) with SPDIF
  6stack-dig	 6-stack with SPDIF
  lenovo-101e	 Lenovo laptop
  eeepc-p701	ASUS Eeepc P701
  eeepc-ep20	ASUS Eeepc EP20
  ecs		ECS/Foxconn mobo
  m51va		ASUS M51VA
  g71v		ASUS G71V
  h13		ASUS H13
  g50v		ASUS G50V
  asus-mode1	ASUS
  asus-mode2	ASUS
  asus-mode3	ASUS
  asus-mode4	ASUS
  asus-mode5	ASUS
  asus-mode6	ASUS
  asus-mode7	ASUS
  asus-mode8	ASUS
  dell		Dell with ALC272
  dell-zm1	Dell ZM1 with ALC272
  samsung-nc10	Samsung NC10 mini notebook
  auto		auto-config reading BIOS (default)

```

---

### Post by Yellow Pasque on 2011-03-05
I noticed that the alsa script lists your lappy as a g60vx. If the above fix doesn't work, you can also try
```
options snd-hda-intel model=asus-mode3
```
[http://ubuntuforums.org/showthread.php?p=9174385](http://ubuntuforums.org/showthread.php?p=9174385)

---

### Post by toccata015 on 2011-06-25
Thanks, Temüjin! 
Your fix worked perfectly for the headphone jack on my Asus G51VX. The second fix, that is.

Cheers!

---

### Post by lidex on 2011-06-26
Nice work 'T'

---

