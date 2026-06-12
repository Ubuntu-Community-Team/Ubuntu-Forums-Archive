---
title: "Audio issues with Ubuntu 9.10 64 bit"
date: 2009-12-09
forum: Hardware
---

### Post by timmick23 on 2009-12-09
I have just recently installed Ubuntu 9.10 64 bit on my HP Pavilion dv7 laptop. The installation worked smoothly and everything seems to be in place. There is just on issue, my audio driver, IDT, was not installed and whenever I try to listen to music through headphones, the audio comes through both the headphones and speakers. I wouldn't have noticed this if a friend of mine hadn't mentioned it to me. Also when I shutdown or restart the computer, a static like sound comes through the speakers. Everything works perfect on my Windows partition. Help from anyone would be greatly appreciated. Thank you in advance.

---

### Post by darkksyde. on 2009-12-09
Does it say in hardware drivers that it can install an audio driver?

---

### Post by timmick23 on 2009-12-09
No. It doesn't. It's like the audio works but it plays from both the headphones and speakers when I try to listen to something.

---

### Post by markbuntu on 2009-12-10
These sort of problems are very hardware specific. There is a lot of solutions here, including some for the DV7. You could also try checking or unchecking some of the switches in the alsa-mixer (the gnome-alsamixer is handy for this).

[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

---

### Post by veehexx on 2009-12-11
just like to say thanks for this info markbuntu.

i had issues on the HP DC7800 (USDT) and the internal speaker not working.
the app you suggested made the internal speaker work (output was muted!)

however, i now have the same issue as the OP (ubuntu 9.10 x86)- audio goes through both the internal speaker and headphones when plugged in (front ports).

---

### Post by timmick23 on 2009-12-12
Thanks markubuntu. I will try this out. It is weird how the audio doesn't work for some strange reason. I also had this issue with the older version of Ubuntu. I stopped using Ubuntu because I kept having audio issues.

---

