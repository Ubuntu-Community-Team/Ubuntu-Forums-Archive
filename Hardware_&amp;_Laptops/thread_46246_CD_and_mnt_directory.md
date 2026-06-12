---
title: "CD and mnt directory"
date: 2005-07-03
forum: Hardware &amp; Laptops
---

### Post by Omnios on 2005-07-03
I have a slight problem. I have a cd and a cdrw they work ok off the menue. WHen trying to check the cd in synaptic I got errors that it couldn't assess the cd. Anyways later I checked my mnt folder and it was empty. The thing is I remember checking my media and mount folders a long time ago and mnt was not empty. I also had the same problem with wine which I havent reinstalled yet. This game is wearing thin time to pull out the hatchet and learn to repair it otherwise its "Reformat". 

 Im trying to migrate to Linux with XP as my second os but this is wearing thin as I already have two reformats so far in about 4 months. Hopefully this can get repaired with the communitys help.

---

### Post by dickohead on 2005-07-03
[QUOTE=Omnios]I have a slight problem. I have a cd and a cdrw they work ok off the menue. WHen trying to check the cd in synaptic I got errors that it couldn't assess the cd. Anyways later I checked my mnt folder and it was empty. The thing is I remember checking my media and mount folders a long time ago and mnt was not empty. I also had the same problem with wine which I havent reinstalled yet. This game is wearing thin time to pull out the hatchet and learn to repair it otherwise its "Reformat". 

 Im trying to migrate to Linux with XP as my second os but this is wearing thin as I already have two reformats so far in about 4 months. Hopefully this can get repaired with the communitys help.[/QUOTE]
 Is there anything in the CD drive when you are trying to access it?

---

### Post by Omnios on 2005-07-03
I can access a cd from Gnome and it is there in media but missing in the mount file. What is happening is it seems that apps like synaptic cannot access the cd even when there is a cd in the drive. ALso I have two cd's and that may be causing a problem with the mount file being empty. I also had the cd in th master cd.

---

### Post by dickohead on 2005-07-04
[QUOTE=Omnios]I can access a cd from Gnome and it is there in media but missing in the mount file. What is happening is it seems that apps like synaptic cannot access the cd even when there is a cd in the drive. ALso I have two cd's and that may be causing a problem with the mount file being empty. I also had the cd in th master cd.[/QUOTE]
 I also have two CD/DVD-ROM drives... so I'd like to think that's not the problem, I'll make an assumption that neither drive works and you have got BIOS and Jumpers set correctly? Sometimes they don't always mount to /mnt/cdrom1, i have encountered a lot of Linux systems, especially lately, where they have their own folders like /media or /devices - dumb question - have you checked them?

---

### Post by Omnios on 2005-07-04
Um one thing I just i just added a vfet partition drive right before this happened to fstab. I remember hearing something similar to this but can't find the post.

---

### Post by Omnios on 2005-07-05
Bump.

 Um I r4ealy need help with this my cdrom is spooling for like over a min and it already cooked one of my CD's 

Note: If your cd is acting funny and keeps spooling for minuts do not eject it till it stops spooling. " I cooked one of my Ubuntu CD's fortunatly I have another one!"

---

### Post by dickohead on 2005-07-05
[QUOTE=Omnios]Bump.

 Um I r4ealy need help with this my cdrom is spooling for like over a min and it already cooked one of my CD's 

Note: If your cd is acting funny and keeps spooling for minuts do not eject it till it stops spooling. " I cooked one of my Ubuntu CD's fortunatly I have another one!"[/QUOTE]
 Remove the vfat partition, reboot and see if the drive works? If not - then it's not you adding the vfat partition - the only way you're going to sovle this is with some trial and error - if you have two CD-ROMs, remove one - see if the machine picks it up - if so it could be Jumper/BIOS issue, if not - try the toher drive. then try replacing the cable to one cd drive at a time, just keep replacing things till you find out if it's hardware or software. If after al of that - then if nothing still works you will know for sure that it's Linux, which leaves me not knowing how to help you.... perhaps a driver issue?

---

### Post by rjwood on 2005-07-29
[QUOTE=dickohead]Remove the vfat partition, reboot and see if the drive works? If not - then it's not you adding the vfat partition - the only way you're going to sovle this is with some trial and error - if you have two CD-ROMs, remove one - see if the machine picks it up - if so it could be Jumper/BIOS issue, if not - try the toher drive. then try replacing the cable to one cd drive at a time, just keep replacing things till you find out if it's hardware or software. If after al of that - then if nothing still works you will know for sure that it's Linux, which leaves me not knowing how to help you.... perhaps a driver issue?[/QUOTE]
 I have a similar problem. I can play cd's but cannot have permission to access the cdrom. I am trying to create a vertual h.d. and need to point the teminal to the cdrom and it won't let me. any suggestions

---

