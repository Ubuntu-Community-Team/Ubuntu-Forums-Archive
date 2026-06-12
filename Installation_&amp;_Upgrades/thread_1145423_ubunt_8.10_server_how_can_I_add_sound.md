---
title: "ubunt 8.10 server: how can I add sound?"
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by 8200 on 2009-05-01
Hi guys.

I am trying to use an pretty old notebook with ubuntu 8.10 i386 server installing just the stuff I need:
xorg fvwm-crystal hal gcc xpdf openoffice vlc ...


Everything works fine but I am missing sound.


What packages are necessary for sound? (maybe linux-sound-base alsa-base alsa-utils)



Thanks!

---

### Post by 8200 on 2009-05-02
A little success: I installed alsa (linux-sound-base alsa-base alsa-utils) and sound works on console (Strg+alt+F1).

But when I startx (which starts fvwm-crystal) it seems that I have no permission to connect to the soundcard.
Starting alsa-mixer in fvwm-crystal I get this error:
   > alsamixer: function snd_ctl_open failed for default: No such file or directory
But it does work with "sudo alsamixer" so I there is something wrong with the permissions?


Why does it work on console but not in fvwm-crystal?

---

### Post by 8200 on 2009-05-02
Thanks to this helping thread: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)


I solved the problem by adding my user to the audio group (as it is written in the thread).

---

