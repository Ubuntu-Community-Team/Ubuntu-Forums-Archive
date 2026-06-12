---
title: "MBR does not have ubuntu."
date: 2009-07-03
forum: Installation &amp; Upgrades
---

### Post by richlyn9 on 2009-07-03
I have two HDD the first one has WIN XP and also has Ubuntu 8.10 and the second HDD has ubuntu 9.04 with a large space kept for data.
I had issues with the WIN XP so i reinstalled it.
And when i booted with a Ubuntu Live CD to rewrite MBR it simply does not find "stage1"

What i did is
sudo grub
find /grub/stage1

It returns with  "error 15 stage1 not found"

I went and explored manually and tried to open stage1 which gave another error saying it cannot be opened"

I got thinking what could the reason be  and hence i disconnected the drive o which WIN XP is and pluged the second HDD cable and it said "no bootable devices found" i booted to a live CD and tried doing the same as above but no change in situation.

could some one help me with this and i was also thinking perhaps i could made a seperate HDD partition for the MBR so that its not effected whatever i do with the OS and could boot with both of the drives independently..any ideas if this can be done?

---

### Post by swerdna on 2009-07-03
Try this: find /boot/grub/stage1 (or /boot/grub/menu.lst)

And re opening "stage1": it's not a text file.

---

### Post by richlyn9 on 2009-07-08
Windows was giving me and error with the explorer.exe after a lot of mulling i reinstallaed WIN XP and this rewrote MBR and did not detect Ubuntu. I reinstalled Ubuntu 904 fromatting the / partition amd mounting the data partition to home.I also created a 7MB dedicated grub partition and chose the advanced op-tion on step 7 to install bood loder to the dedicated grub partition.
After al this when i reboot windows loads automatically without detecting ubuntu.
Is there something else that io should do or something i havent done right.I want to multi boot using a dedicated grub

The WIN XP is on sda1 and Ubuntu is on sdb1 (two diffreenet hard drives)
futher after i biooted using a live Cd and at grub prompt find /sbin/init returns "error15 file not found"

---

### Post by richlyn9 on 2009-07-09
futhermore when i boot in with a live CD and mount grub partition i see that there is only one directory wich is lost and found without any file in it.

---

