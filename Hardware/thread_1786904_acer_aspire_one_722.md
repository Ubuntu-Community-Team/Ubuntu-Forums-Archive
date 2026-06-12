---
title: "acer aspire one 722"
date: 2011-06-20
forum: Hardware
---

### Post by dwaldie on 2011-06-20
Hello, i am having problems with sound on this laptop running ubuntu 11.04.  Sound works but when I plug in headphones sound still comes out of the speakers as well as the headphones.  Does anyone know how to fix this.

Thank you,
David

---

### Post by zzarko on 2011-07-18
I don't have a solution to your problem, as a matter of fact I have exact the same one. I tried various solutions for 522 model, but none of them worked for me. Did you have any luck with this?

---

### Post by zzarko on 2011-07-22
The solution for other Acer laptop, but with the same chipset, worked for me:
[http://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/783582](http://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/783582)

deb file from that page enables jack-sense and internal microphone (you'll need to mute/unmute it from sound preferences).

---

### Post by zzarko on 2011-07-24
I mostly managed to solve all my problems with Ubuntu on 722. You can find what I did at:
[http://ubuntuforums.org/showthread.php?t=1811178](http://ubuntuforums.org/showthread.php?t=1811178)

---

