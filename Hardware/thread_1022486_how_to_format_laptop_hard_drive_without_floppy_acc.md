---
title: "how to format laptop hard drive without floppy access"
date: 2008-12-26
forum: Hardware
---

### Post by luke0927 on 2008-12-26
OK so i have a new laptop hard drive and im actually going to install windows on it first but maybe ubuntu could fix the problem the laptop does not have a floppy so i can not load a boot disk to format it and make it bootable....if i add the drive as a secondary to my ubuntu workstation is there a way i can format it so windows ill see it and i can make it pick it up?  

Can ubuntu find the drive if i just format it as say an NTFS drive?

when i normally install a drive in my desktop i boot to floop and use fdisk  the do a format c: /s

thanks for the help!

---

### Post by luke0927 on 2008-12-26
man i love linux even though im a newbie i just found a program gparted and it looks like i can get it running with this.

---

### Post by Racecar56 on 2008-12-26
Is this solved? If it is, mark it solved.

---

### Post by albinootje on 2008-12-26
> **luke0927 said:**
> man i love linux even though im a newbie i just found a program gparted and it looks like i can get it running with this.
You can actually skip using gparted, because Ubuntu can do the resizing for you during the installation.

And it's a good idea to first install Windows, and then Linux, because then your boot-menu will be working well right away (And Windows want its boot-files on a primary partition on the first disk I've read.)
Installing first Linux and then Windows will end up with having to fix the boot-menu.

Good luck, have fun!

---

