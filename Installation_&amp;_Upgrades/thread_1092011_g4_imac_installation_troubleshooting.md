---
title: "g4 imac installation troubleshooting"
date: 2009-03-09
forum: Installation &amp; Upgrades
---

### Post by Slappey on 2009-03-09
Hi, I'm trying to install ubuntu on my g4 imac, using the 8.10 ppc alternate cd, when i get to the step where it is supposed to mount the cdrom drive, it can't find the drivers for it. Does anyone know what i'm doing wrong, or where i can find the drivers? 

Thanks, 
~ Teh Slapz

---

### Post by Neo_The_User on 2009-03-09
What exact error? Could be a kernel problem.

---

### Post by Slappey on 2009-03-10
i'm away from it now, but it said something about an uncommon device, and asked me if i would like to install the driver from a floppy, or from a device module.

*edits*

You may need to load additional CD-ROM drivers from a driver floppy.
If you have such a floppy available now, put it in the drive, and continue. Otherwise, you will be given the option to manually select CD-ROM modules.

Load CD-ROM drivers from a driver floppy? (Yes/No)"

When i hit "no", i get the following message:

"Your CD-ROM drive may be an old mitsumi or another non-IDE, non-SCSI CD-ROM drive. In that case you should choose which module to load and the device to use. If you don't know which module and device are needed, look for some documentation or try a network installation instead of a CD-ROM installation.

Manually select a CD-ROM module and device? (Yes/No)"

When i hit yes, i get a selection of different modules to choose from:
none
cdrom

---

### Post by Neo_The_User on 2009-03-10
Try device module.

---

### Post by Slappey on 2009-03-10
i did, it had the default path /dev/cdrom
i pressed enter, and it just failed. Is there a more specific path that I should enter?

---

### Post by avtolle on 2009-03-10
This problem is discussed at the Apple Users Forum (apparently, a small glitch in the installer on the 8.10 alternate install disk). See [http://ubuntuforums.org/showthread.php?t=964904](http://ubuntuforums.org/showthread.php?t=964904) and follow it closely (the first few posts, IIRC). It works; I have two G4 Cubes, and following the directions got 8.10 installed. Be prepared to manually edit your /etc/X11/sorg.conf file, BTW; you might check on said forum for some further information and assistance. Good luck.

---

### Post by Slappey on 2009-03-10
> **avtolle said:**
> This problem is discussed at the Apple Users Forum (apparently, a small glitch in the installer on the 8.10 alternate install disk). See [http://ubuntuforums.org/showthread.php?t=964904](http://ubuntuforums.org/showthread.php?t=964904) and follow it closely (the first few posts, IIRC). It works; I have two G4 Cubes, and following the directions got 8.10 installed. Be prepared to manually edit your /etc/X11/sorg.conf file, BTW; you might check on said forum for some further information and assistance. Good luck.
lol, i've always wanted a cube, but can't find em anywhere :)

thanks, i'll try it out tonight when i get back, and i'll post an update tomorrow.

Thanks for your help, and I hope it works!

---

### Post by Neo_The_User on 2009-03-10
try setting the device to /dev/scd0 or /dev/sr0. Try both. If it still doesn't work, try /dev/dvd, then try /media/cdrom0 then /media/cdrom1 then... im out.

---

### Post by Slappey on 2009-03-11
ok, so the instuctions in the other topic worked, but it turns out my download had some corrupted files, so i gotta download it again. :/ thanks for the help tho, it didn't seem to have any other problems.

---

