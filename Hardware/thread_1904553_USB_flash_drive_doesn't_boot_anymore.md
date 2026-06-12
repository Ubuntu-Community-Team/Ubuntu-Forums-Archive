---
title: "USB flash drive doesn't boot anymore"
date: 2012-01-05
forum: Hardware
---

### Post by velja27 on 2012-01-05
I have previously used USB flash drive to boot various distros, during which time I had Ubuntu 10.04 installed. But recently I wanted to install other distros and check them out that way. And then I wanted to dual boot Bodhi Linux and openSUSE 12.1, which failed miserably. openSUSE didn't appear in the GRUB and after fiddling with the graphics drivers on Bodhi it too didn't want to boot. So after many fails at "reviving" Bodhi, I decided to delete it and openSUSE and install another distro. It ended up being Fuduntu. In the end i was not satisfied with it and i tried to make a bootable usb drive, which I did using unetbootin(as with all previous bootable usb drives). But now the usb drive didn't want to boot, so naturally I tried it on my laptop and it booted just fine. I have checked all possible options in BIOS, switching them off and on with each unsuccessful boot.
And somehow after all that I managed to have two GRUBs installed, one 1.97 beta on one hard disk (sda) and a 0.99 or something on another (sdb).
The USB drive in question is Kingston DT108, 16GB, FAT32. I have tried ext2 also, both of which have worked but neither does now.

So I ask you these two questions, can you help me get rid of the GRUB 0.99 on sdb and help me fix my desktop so it can boot USB drives again?

And sadly no, it's not possible to just burn a disk because I get busybox with newer distros, because of the elderly disk drive.

---

### Post by velja27 on 2012-01-05
For some reason or the other I tried again. Reformatted the usb drive to ext2, made it bootable and it works now. The only thing left now is the GRUB question, but i realize now that it might not be suitable for the subforum I placed it in.

---

