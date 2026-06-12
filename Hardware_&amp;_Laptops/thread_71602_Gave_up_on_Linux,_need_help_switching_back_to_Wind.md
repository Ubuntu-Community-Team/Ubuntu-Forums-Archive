---
title: "Gave up on Linux, need help switching back to Windows."
date: 2005-10-03
forum: Hardware &amp; Laptops
---

### Post by jgclark123 on 2005-10-03
Hey, all.  

First off, I have an old Gateway computer with an AMD Athlon 1100 MHz, 256 MB of 133 MHz SDRAM, an NVIDIA 5200 (or something) video card, a SoundBlaster Live! sound card, and a 10 GB hard drive (my 40 GB hard drive died of a virus or a static or something).  

I tried Ubuntu Linux and liked it a lot, but I had that sound issue everyone else with a SoundBlaster Live! sound card seems to be complaining about.  In trying to fix it, I updated the Linux headers.  According to my local amateur Linux geeks, that was bad.  Now I can't boot Ubuntu, reinstall Ubuntu, or even install Windows (my ultimate goal).  

Also, the computer is the family's, so Ubuntu was supposed to be a temporary fix until we found another Windows XP Professional disc.  (Something was wrong with the old one.)

Thanks in advance for all of the help!  I hope to use Linux more in the future.

---

### Post by matthew on 2005-10-03
I wish you well.

---

### Post by mlomker on 2005-10-03
> Now I can't boot Ubuntu, reinstall Ubuntu, or even install Windows (my ultimate goal). 

Why is that?  XP is usually easy to install.  You boot up to the CD and it walks you through everything.

---

### Post by aysiu on 2005-10-03
Follow these instructions:

[http://support.microsoft.com/default.aspx?scid=kb;en-us;314458](http://support.microsoft.com/default.aspx?scid=kb;en-us;314458)

---

### Post by jgclark123 on 2005-10-04
[QUOTE=mlomker]Why is that?  XP is usually easy to install.  You boot up to the CD and it walks you through everything.[/QUOTE]
Yeah, I know.  The first time I tried it, it worked up until the partition manager.  I opted to delete the E: partition created by Ubuntu, and almost immediately I got the Blue Screen of Death.  It told me to restart, and I did.  Now I can't get that far anymore because it freezes during the install, and I need to hold the power button for 4 seconds (cut the power directly) to turn it off.

---

### Post by jgclark123 on 2005-10-04
> **aysiu]Follow these instructions:
[url]http://support.microsoft.com/default.aspx?scid=kb said:**
> 
Thanks a bunch.  I'll give that a try.  I think I have an old Windows 98 SE boot disk.  If not, I can just make an MS-DOS boot disk at another computer.

---

### Post by urbandryad on 2005-10-04
[QUOTE=jgclark123]Yeah, I know.  The first time I tried it, it worked up until the partition manager.  I opted to delete the E: partition created by Ubuntu, and almost immediately I got the Blue Screen of Death.  It told me to restart, and I did.  Now I can't get that far anymore because it freezes during the install, and I need to hold the power button for 4 seconds (cut the power directly) to turn it off.[/QUOTE]


I got that problem with Ubuntu. The problem is that a REGULAR Ubuntu install doesn't seem to be able to OVERWRITE a previous install. You have to install using expert mode, which I'm sure somebody here can guide you through. Then you'll be able to install no prob, thats how I did it when I had to reinstall and it kept crashing during partition. ^^

Good luck!

---

### Post by Claudia Park on 2005-10-04
Sounds like you still have a virus kicking around on the Hard drive, and the is not Linux's fault. The only solution is to re-format the Hard drive and start over again.

Claudia

---

### Post by Claudia Park on 2005-10-04
I know it isn't recommended, but can windows be instally after Liunx was installed? I partitioned the Hard drive to make space for it. I need to access my scanner and I am having trouble editing pictures (lack of experience) with the program provided...the pictures grow instead of shrinking in file size. It's hilariously funny, I bring the size down from 20" x20" to a normal 8x 12" and the file size doubles!  I know, I know, I am not using the program properly...so if I could stop laughing long enough,mayber I'll get it right?

Claudia

---

### Post by brentoboy on 2005-10-04
[QUOTE=Claudia Park]I know it isn't recommended, but can windows be instally after Liunx was installed? 
[/QUOTE]

Sure, just install windows. (be careful not to kill any of your linux partitions in the process.

The reason it isnt recommended is that windows conveniently overlooks the other oses, and doesnt offer to let you boot them. You will have to use your install CD to restore your boot loader after you install windows.  You might want to search around for some instructions on doing that, Im sure there is a walkthrough somewhere.

---

### Post by Claudia Park on 2005-10-04
Thanks.
I am planing to use win98se, it's one of the better windows...less of a control freaker. I formated the partition as FAt32, and I wanted copy the windows setup there, boot from a floppy and install it that way...then use my CD to restore the boot? I am seaching for a "walk through" as I type

Thanks

---

### Post by Gezzer on 2005-10-04
after booting with the win98se boot floppy
1st menu
start with cd-rom support

when at the A> write
fdisk
press enter

option 3 delete partitions
then option 4 delete non dos partitions

delete all non dos partitions
then option 3 again delete logical, extended, primary

do this for all the partitions on the drive

then use option 1 to setup a primary and any extended, logical partitions that u require

restart (with boot floppy in the drive)

at the A> write
format C:
press enter

insert 98se cd the drive will be 1 letter passed the ram drive

at the A> write
X: (replace with cd drive letter)
press enter

at the X: write
setup
press enter
follow the yellow brick road from there ...

---

### Post by Claudia Park on 2005-10-05
Thanks Steve,
I had a mess left over from my previous WinXP, and when I ran fdisk, it reported my linux as extended dos, and only 2 G of hard disk left for windows...duh!

Anyway, I ran fdisk, deleted everything (nothing worth saving) and booted with the XP install disk, partitioned the HD, installed windows on the second partition at the end of the HD, shut down. I rebooted with Linux, and installed Linux on the front end, with the "boot" and EVERYTHING is running smooth. My partitions are FAT.

I can access my scanner with XP and run AVG anti-virus if the need arises(it would be windows that caused it for sure!).  As soon as I figure out how to adapt this flatbed scanner on Linux, windows will probably never be accessed. This laptop is on warranty so I still "must" have XP installed...which is stupid. 

The scanner is showing up on the Device tool, but I can't acces it. I have to learn more scripting in Linux to change my options.

Take care,
Claudia

---

### Post by Sirin on 2005-10-05
> **aysiu]Follow these instructions:
[url]http://support.microsoft.com/default.aspx?scid=kb said:**
> 
Yup, it's definitely Microsoft to have a guide on that. :rolleyes:

---

