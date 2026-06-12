---
title: "Will not boot to install"
date: 2006-01-06
forum: Installation &amp; Upgrades
---

### Post by brucecassidy on 2006-01-06
Firstly im a noob so be gentle 
I have tried to look though the forums to see if i can get the help i need but no i cant find it.
i hve had redhat installed on my other pc which i needed a boot disk to install it i have now decided that i want ubuntu but i cant get the dam thing to do any thing i have a intel p3 pc and have no idea why its not installing is there a specific boot dist or am i just being dumb

help please

ps im not installing it on this pc but a spare i have so i only want it to have ubuntu no other os

---

### Post by ramaswamyps on 2006-01-06
what do u have now?
ubuntu 5.10 cd?
downloaded iso file?
have u set the bios to boot from cdrom?
give us more details of ur hardware.
everybody is learning everyday
:) :)

---

### Post by brucecassidy on 2006-01-06
ubuntu 5.10 - yes
downloaded iso - the what 
have u set the bios to boot from cdrom - yes

Hardware 
pIII prossesor 663mhz 256mb ram
30gb hard drive
that all i can think off

---

### Post by Nightwind on 2006-01-06
[QUOTE=brucecassidy]ubuntu 5.10 - yes
downloaded iso - the what 
have u set the bios to boot from cdrom - yes

Hardware 
pIII prossesor 663mhz 256mb ram
30gb hard drive
that all i can think off[/QUOTE]
This computer that you are trying to install 5.10 on has it ever booted from the CD? Some of the older machine are a pain in that aspect and refuse no matter what you have it set to boot from in the BIOS.

---

### Post by brucecassidy on 2006-01-06
I have been able to boot from the cd i have installed fedora core 4 and redhat before and they both booted up, i have also (spit) booted up a window$ Xp disk.
Could i be useing the wrong version i know you can get them for mac's and power pc' i chose the x86 version, i had the same problem when i was trying to install gentoo which was my first choice

---

### Post by Nightwind on 2006-01-06
It sounds like to me that you picked the right ISO I believe I386 would be correct as that's what I used.
I did learn that even if I have managed to boot from a  CD before sometimes for reason known ONLY to the computer gods it won't on other CDS.
What O.S  if any is currently installed on the machine in question?
Sorry for all the questions but I am trying to narrow things down so perhaps I can help you. I am new  to 5.10 as well but I normally figure things out. If you want some one with more experience to help you I am sure they will.

---

### Post by brucecassidy on 2006-01-06
i have red hat 9.0 i think, if that is true and it will only boot up from say red hat disks is there any way of changing it (open question)

---

### Post by Nightwind on 2006-01-06
[QUOTE=brucecassidy]i have red hat 9.0 i think, if that is true and it will only boot up from say red hat disks is there any way of changing it (open question)[/QUOTE]
Ok  you will have to remove Red Hat from the MBR using fdisk which if you have ever fdisked and formatted a hard drive you have a disk all ready that will do that.
Instructions: Insert floppy disk, reboot, when the DOS prompt comes up type: fdisk /mbr let it run, I normally reboot at after it's done, then I continue to fdisk and reformat the hard drive.

---

