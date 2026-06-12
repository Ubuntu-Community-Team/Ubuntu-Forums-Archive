---
title: "no sound - asus laptop"
date: 2008-10-01
forum: Hardware
---

### Post by SESF0908 on 2008-10-01
Hi, my laptop is Asus F80L-T5550, i install ubuntu 8.04, the first time i start the computer, i don't hear anything, no sound at all, is this a bug? help, please.

---

### Post by Cuogar on 2008-10-01
I also am having a "no sound" issue with my ASUS M51S series laptop. any ideas on how to get this resolved?

---

### Post by sX_ on 2008-10-01
Try to install OSS [https://help.ubuntu.com/community/OpenSound]("https://help.ubuntu.com/community/OpenSound").

---

### Post by markbuntu on 2008-10-01
Try this sound troubleshooting guide:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by fireoftroy on 2008-11-02
With the M51S, try adding two lines to /etc/modprobe.d/alsa-base:

options snd-hda-intel enable=1 index=0 model=lenovo
alias snd-card-0 snd-hda-intel

Basically the drivers in 8.04 are based on intel sound cards, but lenovo has taken over their hardware line, so these two lines resolved that issue for me.  With 8.10, the sound seems to work out-of-the-box.  I'm having a few issues with WOW run via Wine, but all Ubuntu based programs seem to have no problems.

---

