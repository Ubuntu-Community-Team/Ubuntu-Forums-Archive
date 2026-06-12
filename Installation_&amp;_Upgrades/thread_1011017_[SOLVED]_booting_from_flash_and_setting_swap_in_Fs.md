---
title: "[SOLVED] booting from flash and setting swap in Fstab"
date: 2008-12-14
forum: Installation &amp; Upgrades
---

### Post by speed32219 on 2008-12-14
I have installed 8.04 and 8.10 to a 4 GB flash drive.  It works great except for it being a little slow sometimes.  It could be I have a cheap flash drive and I am looking for a fast 8 GB currently, but I also have a question.  

Ques: Can I change the swap partition in Fstab (which is only 266 MB now and I have 1.5 GB system ram) to a installed hard disk?  Like setting up a 3 GB swap, I think my system slowing down sometimes may be due to the swap.

---

### Post by logos34 on 2008-12-14
sure, you can change it.  Just make a new /swap on the hdd with gparted, then edit /etc/fstab

but i doubt the slow down is due to swap SIZE--1.5 gb is plenty ram, you probably never need to use swap with that much.  But if it does use swap, then a swap on the usb would be slower

---

### Post by speed32219 on 2008-12-14
Thank you.  Worked great.  Now I wonder if I could just put in 8-16GB of Ram and set up a ram disk with the OS.

---

