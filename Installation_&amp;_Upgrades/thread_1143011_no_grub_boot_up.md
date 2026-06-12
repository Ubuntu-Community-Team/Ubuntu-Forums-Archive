---
title: "no grub boot up"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by hockman5 on 2009-04-29
ok, after my jaunty failed I decided to do a fresh 8.10 install. I had installed the Wubi(??) version of jaunty first and then went for the desktop version of 8.10. After install, my windows boot.ini
had the choice of windows or ubuntu. When I select ubuntu and then hit escape, I only have the option to boot into the Wubi version. What happened to my 8.10 install. So then I wanted to clean all of this up, so I uninstalled the Jaunty Wubi version but it still left in it my windows boot. So I edited the boot.ini to remove it.
I ran the 8.10 live CD and entered the GRUB shell. I did the options to reinstall grub and rebooted, but grub still is not active. It only boots to windows now. I think that it reinstalled GRUB on the wrong disk. I have three hard drives, how do I get grub to use the correct MBR disk? How do I know which one is the correct disk to use? I know it is the disk that has WinXP on it.

---

### Post by hockman5 on 2009-04-29
Well I decided to do another fresh install. It finished and rebooted straight to winxp. Still no way to boot to ubuntu

---

### Post by hockman5 on 2009-04-30
After doing a fresh Jaunty install, I got grub back....Solved

---

