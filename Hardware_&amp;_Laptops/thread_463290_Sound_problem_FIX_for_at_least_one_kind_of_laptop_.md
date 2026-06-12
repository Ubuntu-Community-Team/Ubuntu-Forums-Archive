---
title: "Sound problem FIX for at least one kind of laptop (Toshiba Satellite P100)"
date: 2007-06-03
forum: Hardware &amp; Laptops
---

### Post by Dutchy on 2007-06-03
[http://ubuntuforums.org/showthread.php?t=290485](http://ubuntuforums.org/showthread.php?t=290485)

This was my problem and was fix by 

[http://www.linuxquestions.org/questions/showthread.php?p=2773589#post2773589](http://www.linuxquestions.org/questions/showthread.php?p=2773589#post2773589)
(i posted a small change to the howto for ubuntu in the 11th post)

For other laptop models, to see if this thing works too, i suggest checking the gentoo wiki
I found that it was needed for my model there too (well actually from the alsa mailing list)
[http://gentoo-wiki.com/HARDWARE_Toshiba_Satellite_P100#Audio](http://gentoo-wiki.com/HARDWARE_Toshiba_Satellite_P100#Audio)

---

### Post by rebel14 on 2007-07-11
That looks quite similar to the steps I followed to fix the sound on my Toshiba Satellite P100-332 indeed. Unfortunately I still had no sound using headphones, though the speakers were being muted correctly when I would plug in the headphones. 

Today I found the fix for the headphones as well. In /etc/modprobe.d/alsa-base just add this line at the bottom or replace any existing identical line:
options snd-hda-intel model=stack3

---

