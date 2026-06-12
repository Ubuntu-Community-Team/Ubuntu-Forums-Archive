---
title: "quad boot problem &gt; now 2 /boot's!"
date: 2008-08-17
forum: General Help
---

### Post by nlz on 2008-08-17
I already had Ubuntu 8.04 (three different kernels) and 64studio on my PC, but i needed to make a repository CD for our radio station, so I installed Ubuntu 7.10, and then I did something stupid, I didn't 'tell' the installer that I had a seperate boot partition, so now there is a whole new boot loader on the last partition (sda7) how can I undo this? I understand how i can add Ubuntu 7.10 to my normal boot (by editing menu.lst and copying the kernel etc), but i don't know how to let the computer now he should use the old GRUB  (or /boot)

For clarity

sda1 /boot
sda2 /swap
sda3 /Ubuntu 8.04
sda4 /home Ubuntu 8.04
sda5 / 64Studio
sda6 /home 64studio
sda7 /Ubuntu 7.10 (including /home and the SECOND BOOT)

Should i maybe use the gparted liveCD to flag sda1 as boot device or something?

---

### Post by Elfy on 2008-08-17
You can use the livecd to reinstall grub or use supergrub and tell it which to use, it's what you would need to do if windows had overwritten grub - follow that. Information for both is here

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by caljohnsmith on 2008-08-17
Since you know which partition you want Grub to use for its config files, just boot a Live CD, open a terminal, and do the following:
```
sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```
What that does is reinstall Grub to the MBR, but it will now point to sda1 (or (hd0,0) in Grub's World) for all its config files, including menu.lst of course.

---

