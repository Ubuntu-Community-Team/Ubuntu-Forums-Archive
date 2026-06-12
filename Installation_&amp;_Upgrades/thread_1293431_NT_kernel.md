---
title: "NT kernel"
date: 2009-10-17
forum: Installation &amp; Upgrades
---

### Post by darkodelta on 2009-10-17
i have install XP and Linux Ubuntu 9.04,and later Windows 7 i remove Windows 7 but my NT kernel Boot loader don't show on start up...How do i get it back ?:confused:

---

### Post by swerdna on 2009-10-17
Run gparted in Ubuntu and use "manage flags" to set to bootable the partition that contains boot.ini (usually sda1).

Then with the windows xp install cd go to the end --> repair --> run fixmbr


Then you'll boot to windows xp.

Is that what you wanted?

---

### Post by darkodelta on 2009-10-17
Well i can't boot linux...thats problem it set to windows is default end its starting windows on startup...but can i set linux from gparted?
Thanks

---

### Post by darkodelta on 2009-10-17
i have gparted on cd i can start him on computer star up as boot cd...then what?to show me boot loader on starup so i can choose OS

---

### Post by swerdna on 2009-10-17
I thought you wanted your NT bootloader to show on startup. Booting Linux is a different problem. You need help from a Grub guru now to reinstall Grub code in the master boot record, accessing menu.lst in the boot folder of Linux.

---

### Post by darkodelta on 2009-10-17
well how to access linux boot folder?i tried to access from a liveCD but it says that i don't have an authorization for that file...how to edit menu.lst ?:confused:

---

### Post by darkodelta on 2009-10-17
i solved problem thanks for help :)

---

### Post by swerdna on 2009-10-17
All right then, if no guru will help you, I'll try -- do this:
Boot the Ubuntu cd.
Open a Gnome terminal window.
Run this command: ```
sudo grub
```
Run this command: ```
find /boot/grub/menu.lst
```
That will return the partition number in a form like (hd0,2). It won't be exactly that, something like that.
Run this command (using your version of (hd0,2): ```
root (hd0,2)
```
Run this command:```
setup (hd0)
```
Run this command:```
quit
```
Run this command:```
reboot
```

---

### Post by swerdna on 2009-10-17
I just noticed -- while I was typing, you solved it. Good for you.

How did you solve it?

---

### Post by darkodelta on 2009-10-18
i type those cods in terminal as you type in that last reply i found them on web by googleing but tnx. for all you gave me idea :)

---

