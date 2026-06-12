---
title: "Please help with GRUB entries for multi-boot USB stick"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by darkod on 2009-11-04
Hello.

The idea is not new but so far I was not able to find any good how-to.

Since my netbook does not have optical drive I have a USB stick for installation purposes. And since that stick is 8GB I thought why not put all the versions of 9.10 on it, plus some Win7.

Ideally, it would be:
Ubuntu Desktop 32bit
Ubuntu Desktop 64bit
Ubuntu Netbook Remix
Windows 7 32bit
Windows 7 64bit

The total should fit on 8GB stick. But I am not experienced enough to create the boot/startup menu where you select which one you want and then for that installation to actually start (and work). :p

Using Windows so far I managed to format the stick with FAT32 and using GRUB4DOS to make it bootable. That was the easy part.

I have no clue how to organize the commands in menu.lst to achieve launching of the installation process of the selected OS. Most documents about grub and menu.lst just cover the entries for booting off your HDD which isn't the case here.

To make things even more complicated, if possible, I would like all three Ubuntu distros to start with the menu which offers just running them as live CD, not with the installation directly.

Assuming all of the above is possible, could someone give me a hand with the grub entries how to achieve this? As an idea, it is pretty "simple". You would just need commands to launch the setup.exe of the Win7 (I guess) and the main menu of the Ubuntu distros. But I can not do this myself.

Any advice is welcomed. Cheers.

---

### Post by Mighty_Joe on 2009-11-04
Have a look at [this post]("http://ubuntuforums.org/showthread.php?t=1205798"), but keep in mind you can use the UUID of a device instead of the device name, since the device name can change.

---

### Post by darkod on 2009-11-04
Thanks. I read the post and other stuff googling around. I think I found a way to make this work but will have to check later after I convince my girlfriend to give me back the ubuntu netbook. :lolflag:

One question though.

The standard grub entry for Windows is:
title Windows
rootnoverify (sd0,0)
chainloader +1

I guess the UUID which is better to use like you advised needs to replace the rootnoverify line. How? Something like:
rootnoverify UUID="####" or
rootnoverify=UUID="####" or something else?

Thanks for all the help.

---

