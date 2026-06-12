---
title: "HDD problems with using + installing Ubuntu Server (8.10)"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by fonsoy on 2009-04-27
Hello,

Some weeks ago I decided to try Ubuntu as OS for that old PC that I found. The first time, I was able to install Ubuntu just fine ... until I got troubles with booting. GRUB was able to load, however later on in the boot process, the server announces the following:
"SRST failed. 06x04 <some text that I forgot>
SRST failed. <and then two other integers with a x between them>"
This made the boot process more or less fail I guess, because I got caught in some shell where I was the root: initramfs. Remarkeably, typing exit resumed the boot process, but sometimes the initramfs shell triggered again and I was back where I was; I had to type it multiple times now and then.
Those were the problems I HAD.

Now, I was pretty fed up with the error, and I reinstalled ubuntu, and during the installation process, the HDD is not detected. The disk is a WD1200J, and it used to run windows (and Ubuntu Server) perfectly fine. I tried all the IDE connectors. During the installation process I'm getting stuck in a menu where I HAVE to choose a HDD driver, it won't operate without. I have googled for ages, and I can't seem to find what driver I need.

Now here comes my question. What is the problem? I have put the hd in another computer and checked it for bad sectors/errors, it gave none.

I still suspect the hard disk though. Please share your thoughts with me :)
EDIT:
I checked the harddisk and used several cables and connectors, the harddisk is well over 50 degrees centigrade.

---

