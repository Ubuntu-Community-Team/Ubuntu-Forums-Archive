---
title: "Compaq SATA HD upgrade problem"
date: 2007-07-27
forum: Hardware &amp; Laptops
---

### Post by maikunari on 2007-07-27
Hi All, 

I was recently given a Compaq Presario SR1130NX with a broken hard drive. 
I bought a new Hitachi SATA drive to put into it but it is not recognized on the bios
or by Ubuntu when I try to install it.

I'm not sure if the problem is that I need to update the bios (Award BIOS 3.03 2/09/2004) or what?
Does anyone have any suggestions as to what the problem might be?

Thanks very much!
Mike

---

### Post by logos34 on 2007-07-27
> I was recently given a Compaq Presario SR1130NX with a broken hard drive.
I bought a new Hitachi SATA drive to put into it but it is not recognized on the bios
or by Ubuntu when I try to install it.

I'm not sure if the problem is that I need to update the bios (Award BIOS 3.03 2/09/2004) or what?
Does anyone have any suggestions as to what the problem might be?

Yep, flash the bios with the update (08/'05).  

You might also check Hitachi website for a firmware update for the drive (especially if this is a sataII drive-for  backward compatibility with the sata I controller on your board)

[http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=228&lc=en&cc=us&dlc=en&product=425917&lang=en](http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=228&lc=en&cc=us&dlc=en&product=425917&lang=en)

---

### Post by maikunari on 2007-07-27
Thank you logos34,
About flashing the bios, would [this]("http://ubuntuforums.org/showthread.php?t=318789&highlight=update+bios") be the best method to use? The computer doesn't have a floppy drive but I have another computer running fiesty I could use to make the boot CD. 

your help is much appreciated!

---

### Post by logos34 on 2007-07-27
well, I'm familiar with [this version of the howto]("http://doc.gwos.org/index.php/Flash_Bios"), but use your link because it looks like it's been updated for Feisty (i.e. feisty archive for unzip tool).  I haven't flashed a bios using the CD method, only via floppy diskette and using winflash .exe from the Windows desktop.

---

### Post by maikunari on 2007-07-27
Sorry to take so long to get back, hopefully someone can help me with this next problem.
I've followed the steps in the above tutorial to make the boot cd to flash the bios, but when I log in to Freedos I get an error when I try to run the flash program "AFLASH.EXE" it says
 "can't find the bios' hook"

anyone have any clue what I should do?

Thanks!

---

