---
title: "Can't boot Ubuntu from external HD"
date: 2009-08-05
forum: Installation &amp; Upgrades
---

### Post by FScheltens on 2009-08-05
Hello all,

i have been trying fruitlessly for the last two days now to install Ubuntu on a Toshiba 1TB external hard disk that is connected by USB and get my pc to boot from it. I have read a number of webpages, and I have done:
- set boot order in my bios to pick cdrom and usb hdd first
- tried installing Ubuntu from the live CD with internal HD disconnected
- tried building a new initrd file with usb drivers in the module file. (As in [this thread]("http://ubuntuforums.org/showthread.php?t=80811"), which is unfortunately from 2005. )
- just today i tried [this guide]("http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/") on a 10 GB FAT32 partition with the 4 GB Casper-rw file. During the "makeboot.bat" file being executed, i got an error saying: "not a removable drive. press -f to force."  I edited the -f into the .bat file and the file ldlinux.sys appeared in the root directory of the drive.

About the only thing i haven't tried yet is getting the alternate version of the Ubuntu 9.04 cd, which i'm downloading at the moment. 

Does anyone know if you need to install Ubuntu from the CD onto a fat32 partition rather than a ext3 partition for it to work with an external hd? If anyone else has a good suggestion or can tell me what I'm doing wrong i would really appreciate it because I'm running out of ideas!](*,)

p.s. Someone on another forum i wrote on said he had zero problems getting it to work on a pc with windows Vista. I run windows XP on my main pc, which afaik uses a different bootloader. Does this make any difference ?

---

### Post by presence1960 on 2009-08-05
what happens when you try to install via Live CD? Do you get errors, black screen, etc? You have given very little info for us to see what may be going on. Be more specific please.

P.S. an ubuntu install does not work on FAT. A bootable Ubuntu media is formatted FAT32. Such as I have, I made my Ubuntu iso into a bootable usb stick, which is formatted FAT32. I use that to install Ubuntu, it is way faster than installing from a Live CD.

---

### Post by FScheltens on 2009-08-06
The problem was that my pc would not boot linux off of an external HD connected by USB. However, yesterday evening i had an epiphany and found out why:

It was because motherboard, a Gigabyte GA-EP35-DS3R, has really CRAPPY support for usb drives!
First off, you can only boot usb-drives connected to the BACK of the motherboard, i.e. to the ports soldered on the motherboard. The usb-ports in the front of my case DONT WORK. (For booting, they work fine in any OS).
Secondly, in bios you can set the order of boot-devices, but you can also set the order of Hard disk Boot Priority, where you select WHICH harddisk is booted from, kinda like this one: [IMG]http://i558.photobucket.com/albums/ss25/FScheltens/bios2.jpg[/IMG]

Now, when you hook up an usb drive its added to the bottom of this list. I have been able to reproduce the following:

I connected the usb-drive, i moved the USB drive to the top of the list, and rebooted. My pc started linux just like it was supposed to. Then i turned off my usb drive, rebooted, and windows started up. all good.
I then turned on the usb drive again, and lo and behold: WINDOWS. Turns out that the usb drive got put back on the list, ON THE BOTTOM! In other words, this motherboard will NEVER automatically boot up from an external HD!
The only way around this is to press F12 to bring up the list of boot devices during boot, or to go into the bios and change the order of harddisks in the list shown above.
Now just today i installed Ubuntu 9.04 from the alternate CD, installed grub on the external HD, and everything worked the first time. IF you plug it into the back and hit F12 .... I spent TWO DAYS trying to get this to work ](*,)
In addition to that, Linux caused a problem with my raid-array, which i set in bios.
I have two harddisks hooked up to my intel ICHR9, which contain two arrays, a raid-1 for my OS and a raid-0 for other files.
Linux saw these as two separate harddisks, and after that, windows did too ! In the intel application, my first harddisk was listed as part of the raid 1 array, and the second disk as a non-raid array.
Fortunately i rebooted again a little later, and everything worked as before again. I had backups of a lot of files on the raid-0 array anyway, but im still going to install dmraid on the external hd, using my OLD pc.

Anyway, im off now to post a not so pleasant message on the local gigabyte support forum. I'm more than a little PISSED that i spent so much time on something that for most other people works the first time in just an hour or so ...

p.s. i installed Ubuntu into an EXT3 partition on my USB harddisk, worked perfectly.

---

### Post by presence1960 on 2009-08-06
At least you know what the problem is now. Due to poor USB boot support you may have to live with hitting F12 to change the boot order when you want Ubuntu on the USB drive. Hopefully you can find a workaround with that mobo.

---

