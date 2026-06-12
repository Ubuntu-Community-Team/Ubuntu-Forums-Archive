---
title: "i need help with my cd drive"
date: 2009-09-11
forum: Hardware
---

### Post by benp1987 on 2009-09-11
i wasn't sure were to put this but i just installed 9.4 i had 8.4 and 8.10 all work with my cd drive now on this version it says unable to mount and it will freeze when i eject the cd is there anything i can do to fix this? ... thanks a bunch

---

### Post by ghostborg on 2009-09-11
It sounds like Ubuntu is having a problem with the media- from the fact that it recognized a disc. Maybe try medibuntu [https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu"), you know those endless things that need to be installed for anything to work. I don't remember having to edit any config files just enabling/installing all that proprietary stuff.

Good Luck

---

### Post by benp1987 on 2009-09-11
im not sure if its reading at all i kno it has my dvd ram drive listed but it wont open anything when i pop a disc in spins for  a min nothing pops up i click the cd drive and it says unable to mount if i eject 20secs later it freezes the system and i have to push the power button :-(

---

### Post by ghostborg on 2009-09-11
Sorry forgot the freeze part. Still try Mediabuntu , maybe it will load some needed files particular to your drive.
Install Ubuntu-restricted-extras


Make sure you have run updates. 
Leave your drive model on this board for more knowledgeable people.
Try a complete power down.
Try unpluggind drive, boot ubuntu, shutdown, plug back in, boot again.
Try another drive if possible.

My system has from the root a subfolder /media with a folder cdrom0 and a link cdrom to cdrom0.
/media/cdrom
and
/media/cdrom0 

Take a breath and I'm sure someone helpful will be along shortly.

---

### Post by aatyler on 2009-09-11
Just to add, I'm experiencing a similar problem. When I boot up my system I can put a cd in my drive and it will be read just fine. Once I try to umount or eject the drive, the cddrive gets stuck endlessly reading the disc. When I try commands like 'eject' or 'sudo eject' on the terminal I get errors about either device busy, input/output error on device, or no media present. In order for the cdrom drive to work correctly after that I have to completely power down my laptop and reboot. My laptop is:

ASUS M50VM-B1 I'm not sure exactly which drive it has, and I'm not exactly sure how to tell, either. Thanks for your time.

---

### Post by benp1987 on 2009-09-12
i went back to windows vista wich solved my prob thanks for the replies

---

### Post by benp1987 on 2009-09-12
i couldnt resist so i tryed again with a program i found on the ubuntu website called wubi and for some off reason it downloaded the 64 bit version and my cd drive works!!!! im excited i love ubuntu :-)

---

