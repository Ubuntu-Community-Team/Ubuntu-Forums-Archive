---
title: "Ubuntu 8.10 no sound on ASUS PRO72SL"
date: 2009-07-03
forum: Installation &amp; Upgrades
---

### Post by jrouane on 2009-07-03
Hello

I'm a new user who tries to install Ubuntu on my new computer. Dual boot with Windows XP.
I installed the 8.10 : all work fine except sound.
I have tried to upgrade to 9.04 : the sound works with, but the rest is catastrophic : the computer freezes entirely on the desktop lauch 3 time on 4, and when no freezes no network. Worse if I boot with Windows, the network is also losted (wire and wireless) and very difficult to repair.
I have tested the 9.04 for 3 days : very impossible to use my computer with.
So I re-installed the 8.10.
And since 2 days I am trying to obtain the sound with the 8.10.
I have update the Asla driver following this thread [http://ubuntuforums.org/showthread.php?p=6589810#post6589810 ]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810")
no result
Are my devices ok ?
```

>:~$ aplay -l
**** Liste des PLAYBACK périphériques ****
carte  0: SIS966 [HDA SIS966], périphérique 0 : ALC663 Analog [ALC663 Analog]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
carte  0: SIS966 [HDA SIS966], périphérique 1 : ALC663 Digital [ALC663 Digital]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
```Sorry for my english I'm french

Help me please

---

### Post by jrouane on 2009-07-04
I resolved this issue by myself.

I modified /etc/modprobe.d/alsa-base and append the line at the end:

options snd-hda-intel model=m51va

My sound card works fine with this option

edit : microphone doesn't work

edit2 : with
options snd-hda-intel model=g71v
the microphone works

---

