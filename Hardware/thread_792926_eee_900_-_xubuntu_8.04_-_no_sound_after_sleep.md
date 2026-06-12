---
title: "eee 900 - xubuntu 8.04 - no sound after sleep"
date: 2008-05-13
forum: Hardware
---

### Post by ShaqArif on 2008-05-13
Hi,

hoping someone can help me with this problem...

Basically, sound is working fine for me, on my eee, until I suspend using Fn+F1.  Coming back from sleep, the sound refuses to work either through headphones or speaker.  I've tried to do a /etc/init.d/alsautils restart, which says that alsa has been restarted, but sound still doesn't work.  Logging out to the gdm and back in again doesn't help either - it has to be a cold reboot and then the sound is OK again.

Anybody else come across this problem, and know of a solution?

Thanks!

Shaq

---

### Post by mempman on 2008-05-13
While your linux system is "sleeping," are yo accessing other installed OS on your system?

---

### Post by ShaqArif on 2008-05-13
Hi mempman,

no, I removed the Xandros OS so that Ubuntu is the only OS on the system now.

Thanks,

Shaq

---

### Post by ShaqArif on 2008-05-14
Seems that issue can be resolved by executing the following:

>sudo alsa force-reload

Many thanks to jogloran on the eeeuser forums for this solution.

---

