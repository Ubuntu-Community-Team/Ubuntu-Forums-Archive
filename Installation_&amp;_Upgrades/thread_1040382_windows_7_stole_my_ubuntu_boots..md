---
title: "windows 7 stole my ubuntu boots."
date: 2009-01-15
forum: Installation &amp; Upgrades
---

### Post by waxxed on 2009-01-15
Ok here's the deal. Downloaded windows 7 beta for testing and whatnot. Thought it would be cool.

Ive got two harddrives.. 

Harddrive A - Ubuntu / XP dual boot with grub as boot
Harddrive B - newly installed windows 7

I did what I thought was a "clean" install onto my B harddrive, but it actually re-wrote the boot manager on the A harddrive...
allowing XP to boot and windows 7 to boot.. from harddrive A

so just a fair warning. gonna have to re-load grub methinks.

anyone have any trouble re-loading grub, allowing to boot xp / w7 / ubuntu?

Waxxed

---

### Post by HighCommander540 on 2009-01-15
The same thing happened to me, when I tried to dual-boot Windows XP and Ubuntu 8.10.
 
It is a very simple thing to fix. All you need to do is simply boot using a Live disc or if you can get your Ubuntu install to boot do that.
 
Start a terminal session.
 
Then use the following commands to reinstall GRUB.
 
1. sudo grub
2. root (hd0, 0) - This refers to your Ubuntu partition install. For you it is on your first harddrive and probably on partition 0. If you don't know which partition it is do step 3 otherwise go to step 4.
3. find /boot/grub/stage1 - You will get something like (hd0, 1) - Use this for the root command.
4. setup (hd0, 0) - Or whatever your partition is.
5. quit
6. Reboot and remove your live CD.

---

