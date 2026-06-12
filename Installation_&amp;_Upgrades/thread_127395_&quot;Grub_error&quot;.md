---
title: "&quot;Grub error&quot;"
date: 2006-02-08
forum: Installation &amp; Upgrades
---

### Post by windowsnewbie on 2006-02-08
So after I installed Ubuntu from the CD, it told me to remove the CD from the drive and the computer restarted.
After proceeding past the BIOS page, I get to a black screen that says:

GRUB Loading stage1.5.


GRUB loading, please wait. . .
Error 18


Any ideas what I should do?

Thanks! :(

---

### Post by hod139 on 2006-02-08
This seems to be a common problem. A quick search in the forums for "grub error 18" found *lots* of pages. In addition, check out this page [http://wiki.linuxquestions.org/wiki/GRUB]("http://wiki.linuxquestions.org/wiki/GRUB")
which has a discussion on Error 18:
> 
***Error 18**: Selected cylinder exceeds maximum supported by BIOS*
This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB on others.). In more practical terms this means the BIOS is unable to start executing the kernel because the kernel is not located within the block it can access at boot up time. 
**  This can be circumvented** by creating a boot partition at the beginning of the disk that is completely within the first 1023 cylinders of the harddrive. This partition will contain the kernel. 

(emphasis mine).

So, it looks like you need to do an expert install and set up a boot partition, instead of installing grub on the MBR.

---

### Post by TheGreenSchnizits on 2006-02-08
What is the best way to do this once you are installed?

---

### Post by hod139 on 2006-02-08
I was just doing a little more searching on error 18 because it seems there isn't an easy solution howto. Everything I've read says this:
> Try an update for your BIOS and/or move your boot partition to the front neither of which are easy tasks for a novice.

> 
What is the best way to do this once you are installed?

I'm not sure how to do this once ubuntu is installed.
It is easiest to create a /boot partition during the install process. At the partition disks screen, you can choose manual, and create a small boot parition at the beginning of the drive (hopefully you don't have windows there because then I don't know what to do). Then at the grub install screen, you will have to tell it install in this partition.

I'm off to bed now, but I'll try and do some research tomorrow on a guide for creating a boot partition using the ubuntu installer. Or maybe I"ll get lucky and someone else will post a solution while I sleep.

---

### Post by windowsnewbie on 2006-02-08
Is it possible for me to completely ignore Ubuntu and go back to Windows?
All my files are in there.
I installed Ubuntu onto a separate hard drive on the computer.

---

### Post by TheGreenSchnizits on 2006-02-08
hod139
-thanks for reply
 I can always re-install. I normally never put my boot in / normally I create a small partition for it. I was going to do that when I installed but I found the custom install partion setup in Ubuntu to be a pain, and was in a hurry. Probably I was to impatient to learn it, so now I pay the price. I am a long time Mandrake / MAndriva user, so this was a new exp. for me. I will probably try and boot to a live CD distro, use qtparted to rezise my / directory and create a boot and then reboot into ubuntu again. I think this will work , if not I will reinstall.

windowsnewbie-
what version of windows are you using? do you mean you set this up dual boot and want to get rid of grub, or something else? If you just want your windows boot sector back, and you have XP, or 2000 you can boot from the windows CD, press R for the recovery console when it asks (looks like it will install, loads a bunch of drivers etc, but eventually you will see the option to select R)
This will put you in the recovery console, log into your windows partition, (usually 1, and administrator and password)  then type FIXMBR and yes at prompt. That will give you a new master boot record for windows and should work. 

Note this all depends on how you installed ubuntu and windows together, etc.

thanks folks. off to find one of my Mepis CD's to boot into

---

### Post by windowsnewbie on 2006-02-08
I run Windows XP SP2 Home edition; it was factory-installed on an HP Pavilion computer.

I cannot access the HP Recovery partition using F10 or the Windows Safe Mode on F8.  It directly loads grubs and displays Error 18.  The only thing I could access are:  reinstalling Ubuntu 4 times and F1 into BIOS configuration.

---

### Post by TheGreenSchnizits on 2006-02-09
so you need to boot with a windows xp cd, I will look around for another way to do this, this is the way I use. You just need your windows master boot record back, and you will be booting into windows again.

---

