---
title: "Backside of duplex print output mirrored"
date: 2009-07-21
forum: Hardware
---

### Post by drds on 2009-07-21
Help! I am new to Ubuntu Linux (second week), I think it is really great, but am having problems with my printer, a Konica Minolta 5430DL. I got the rpm driver from Minolta used alien to convert it to deb and installed the package.  It works fine unless, I use the duplex option, the the backside comes out mirrored about the vertical.

The solution may be the PPD file. It contains an instruction **[SIZE=2]cupsFlipDuplex: true[/SIZE]**
I have tried changing this to false and modifying the printer with the new PPD file, but this hasn't worked I have also tried **cupsBackSide** with flipped and rotated, but nothing seems to stop the mirroring. 

Any ideas? Is therer something else I need to do like restarting the OS, or putting the PPD file somewhere other than the desktop, or using sudo or gksudo or something, i have tried modifying the printer from the printer window and also the cups web interface or local:631.

Any help very much appreciated, thanks. 

 I am using Ubuntu 9.0.4

---

