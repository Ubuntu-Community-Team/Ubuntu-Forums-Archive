---
title: "Installation on SD card"
date: 2009-08-14
forum: Installation &amp; Upgrades
---

### Post by elmosim2 on 2009-08-14
I recently got a dell mini 9 netbook with windows XP on it.  (it was refurbished and cheaper than buying with Ubuntu).  

Anyway, it only has 8GB of internal flash storage and I keep running out of space.  I bought a 16GB SD card in hopes that I could install right on the card.  

I can't seem to even get an ext* file system on the card at all.  When I'm in the Ubuntu install that's on the internal flash it doesn't even recognize that there's an SD card at all (using gparted).  

Short question is simply, can this even be done?  

If not, could I use symlinks for the important directories to link them to the SD card maybe?  (I'm not sure if that's even what symlinks do).

Thanks in advance for anyone's input!

---

### Post by stlsaint on 2009-08-14
im not sure if thats possible...havent really researched it yet but i wouldnt recommend it because should you lose that SD card you will not be able to boot into your system! have you considered getting a bigger hdd!!

---

### Post by elmosim2 on 2009-08-14
The SD card I was planning on permanently leaving in my system.  As for more internal storage, a hard drive isn't even an option as the slot for the flash in there right now is 1.8 inches.  I would love to upgrade the size of that but have you seen the prices of flash storage?  It's still pretty steep.

---

### Post by spiffydudex on 2009-08-14
Correct me if I am wrong, but I think SDHC is a hardware element to the card reader and is not software driven. It might not recognize it because the card reader does not support an SDHC card.

---

### Post by Nakken on 2010-12-19
I will recommend installing on a MicroSD, that way you can easily present the MicroSD to any pc as a standard usb memorystick, or as a SD card using a 2$ converter. 

I am running a full installation from MicroSD, not pendrivelinux.com. 

Simply create a bootable memorystick as described at [www.pendrivelinux.com](www.pendrivelinux.com) and use that pendrive to create a full installation on the MicroSD. I use a 8gb card. 

I have an Aspire 1810TZ and did not believe that the Bios supported booting from SD, but it does, and I have removed the harddrive. 

When traveling I dont bring a pc if someone else does, just the MicroSD.

---

### Post by C.S.Cameron on 2010-12-19
I have done both persistent install and Full install to SD HC cards and my EEE PC runs great from either.

As long as your BIOS can see the card as a HDD it should be possible.

---

