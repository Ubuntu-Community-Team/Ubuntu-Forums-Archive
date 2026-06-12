---
title: "Ubuntu remix on a external hard drive"
date: 2009-10-22
forum: Installation &amp; Upgrades
---

### Post by Dannyst on 2009-10-22
Helo,

I have just bought a:

WD Passport Essential Portable 320GB 2.5" USB2.0 white

Now i want to instal ubuntu remix on it so i can boot from my acer aspire one laptop. I have followd the instruction on this url:

[https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles)

I have downloaded win32 disk manager but when i try to find the new hard drive to instal ubuntu remix the drive letter isn't in the list??? When I start the program i get an error 8. and when i trie to refresh the drives i get the same error.

I have checked and standard the new hard drive is formated in fat 32 what is needed for installing ubuntu remix. I'am trying to install it from windows vista.I have already tried it with an other usb and it worked perfect so the problem is the hard drive. I don't have any idea what could be the problem here. please help me with this.Thanks

Best regards

Daniël

---

### Post by dstew on 2009-10-22
I am not sure exactly what you are trying to do. The instruction page you link to is for creating a bootable USB with a Live CD-type system. Usually, the reason you do this, is to use the Live USB system to install onto hard drives. The Live USB system is not very useful as an operating system, because it is not persistent. That is, it does not retain installed programs, settings etc.

I think you really want to install a regular Ubuntu system onto your USB hard drive, so you can install programs, and save documents and pictures on it. If so, can try to install the .img file on the external drive, boot the external drive, and then install to the external drive from the live system.

Getting your Vista system to recognize the external drive's file system, that is a Windows problem that I can't help you with. Maybe you have to instruct it to recognize the drive, like the mount command in Linux, but I don't know. Or, like the old "Map Network Drive" in XP. But you probably have to ask Windows people about it.

---

### Post by dandnsmith on 2009-10-22
It looks as if the instructions have changed since I used them - perhaps the image files have too.

When I followed the then recommended procedure (via linux route), the usb stick ended up as a single partition 1GB drive - odd, since it was actually a 4GB stick.
I'm not the only one with that experience. Later there appeared a way to correct the apparent size (in some cases).

Perhaps you got off lightly - you might have been concerned and mystified to end up with a 1GB drive, instead of 320GB.

---

