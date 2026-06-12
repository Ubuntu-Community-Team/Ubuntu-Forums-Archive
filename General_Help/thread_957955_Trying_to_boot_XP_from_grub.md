---
title: "Trying to boot XP from grub"
date: 2008-10-24
forum: General Help
---

### Post by maestrobwh1 on 2008-10-24
I just got an Asus EEE-Box and I also had an eee-pc.  I cloned the sd card I installed on the eee-pc onto another and stuck it in the sd card slot, and well, I love Linux... specifically Ubuntu, as it booted right up to my desktop.  

I set BIOS to boot from the sd card because I prefer Ubuntu about 95% of the time.

I want to boot the Windows OS on the internal drive but not have to go through pressing this and that while the computer boots to get the boot menu.

I added to my menu.lst

title Windows
rootnoverify (hd0,0)
makeactive
chainloader +1

but I get error 13.  I assume that the internal drive is 0,0 because when I run ubuntu, and use grub find, it locates /boot/grub/stage1 being (hd1,0)

Do I need to add

title Windows
[B]map (hd0) (hd1)
map (hd1) (hd0)[/B]
rootnoverify (hd0,0)
makeactive
chainloader +1

I thought that one would only add these lines if XP was moved to the slave position.

then do

sudo update-grub

or should I just so 

sudo update-grub without doing the "map" thing.

I don't want to botch the fact that I can actually boot from both drives separately.  I realize that as long as I don't actually enter the grub program and issue a setup (hdx) command, this most likely could not happen anyway.

---

