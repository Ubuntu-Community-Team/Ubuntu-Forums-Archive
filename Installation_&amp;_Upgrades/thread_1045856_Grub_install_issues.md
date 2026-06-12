---
title: "Grub install issues"
date: 2009-01-20
forum: Installation &amp; Upgrades
---

### Post by getnripped on 2009-01-20
Okay i was running windows 7 beta on a dual boot (big mistake) and when I removed the partition it also removed my grub menu that I had installed while W7 was on there. So when i run 
```
sudo grub
grub setup (hd0)

```
I get an error. no such file exists... any thoughts?

---

### Post by Will4 on 2009-01-20
you shoul boot from your live CD, i guess you have Ubuntu, and after it opens start a terminal and type


sudo grub
find /boot/grub/stage1

after getting the answer ex: (hd0,2) 

root (hd0,2) 
setup (hd0)

he will tell you at the end of the text (Done...)
after that press ESC to exit and save.

then reboot and may be you will have to edit your boot again before you really boot

press 'e' to edit the boot comands and be sure you change the boot sequence for the one you got before ex: (hd0,2)

---

### Post by getnripped on 2009-01-20
I do the prescribed and I receive the same error. I fear that I need to re-install ubuntu all together.

---

### Post by Will4 on 2009-01-20
Hey buddy,

I dont want to be advising to reinstall all the time, but reinstalling would for sure solve the problem. 
I was trying to give you a short cut to solution!!

---

