---
title: "Grub update"
date: 2009-07-30
forum: Installation &amp; Upgrades
---

### Post by Pogasu on 2009-07-30
Hello,

I have Ubuntu 8.04 with Windows XP... I will format the Windows unit and I dont know if after formating, the grub will remain the same.. I mean, if I could run Windows or Ubuntu like I did before the format or I should update the grub....

What should I do?

---

### Post by philcamlin on 2009-07-30
yes grub will still be there without the Windows Xp Professional option there :popcorn:

---

### Post by Pogasu on 2009-07-30
I dont understand. If I want to have Windows XP again (after formating), what should I do in order to have everything like before formating?

---

### Post by merlinus on 2009-07-31
Are you reinstalling xp, or formatting its partition?  If reinstalling, then you will have to reinstall grub afterwards, but that is quite simple.

---

### Post by Pogasu on 2009-07-31
Im formatting Windows partition and then reinstall it...
So, what I have to do is reinstall grub... using grub(hd0) ?

---

### Post by merlinus on 2009-07-31
Boot from live cd, open a terminal, and enter these commands, one at a time:

```
sudo grub
find /boot/grub/stage1 #you will get a response such as root (hd0,2)
root (hd0,2) #use the numbers from the previous command
setup (hd0)  #use the number from the previous command
quit 
```

and restart.

---

