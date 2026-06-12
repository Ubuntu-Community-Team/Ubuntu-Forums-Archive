---
title: "Remove a secondary OS"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by Xelfox on 2009-10-29
Hi there I have 3 OS's installed on my computer I am running ubuntu 9.04 and am upgrading tonight. I don't know how to remove the other two on my machine can someone please help me out

Thanks.

---

### Post by mark44magnum on 2009-10-29
Hi, what i would do is backup your important information onto a usb then do a complete fresh install, that way you get to format your harddrive and wipe the two other os from your system,and as a bonus,you get a nice fresh install..:p

---

### Post by chrisplymouth on 2009-10-29
You are upgrading your 9.04 system? I would definitely backup your data if that is your intention.

Fire up a terminal and type in "sudo apt-get install gparted" Gparted may already be installed but you never know! 

System > Administration > Partition editor.

This program will show you how your hard drive is organised. If Ubuntu 9.04 is on the first partition, you may be able to get away with removing the other partitions.

On the flip side, if your Ubuntu partition is not the first partition, you may as well do a fresh install.

Can you post a screenshot of the gparted window?

---

### Post by Xelfox on 2009-10-31
Thanks for your advice guys worked like a charm!

---

