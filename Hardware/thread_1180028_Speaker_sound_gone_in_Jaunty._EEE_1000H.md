---
title: "Speaker sound gone in Jaunty. EEE 1000H"
date: 2009-06-06
forum: Hardware
---

### Post by nielsek on 2009-06-06
I used to have speaker sound in Jaunty, but since the one time that i plugged in my headphones, the speakers are dead. Now its only my headphones that works.

I dual boot with xp and there is no sound problems there.

---

### Post by nielsek on 2009-06-06
Okay so i solved it in some weird way:p

i added

[PHP]options snd-hda-intel index=0 model=basic  [/PHP]

to the end of my "/etc/modprobe.d/alsa-base.conf" file, and rebooted.
After the reboot i got some more sound options to play with but it didn't help,
so i removed it again and rebooted, and now it workes.

---

### Post by hbayar_morph on 2010-12-30
I had exactly same problem. So followed your guide, but i didn't had to delete again. 

thanks

---

