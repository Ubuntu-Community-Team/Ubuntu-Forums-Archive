---
title: "HOW-TO: Install Ubuntu on a PC with an ABIT AB9 mobo"
date: 2010-07-18
forum: Hardware
---

### Post by duncan_bayne on 2010-07-18
[From my blog post [Installing Ubuntu on a PC with an ABIT AB9 mobo](http://www.fluidscape.co.nz/node/208)]

This one was a right bastard; the machine wouldn't boot off USB, CD-ROM support was wonky as a result of the ancient BIOS, bugs in said BIOS caused Ubuntu to hang every few minutes, and I didn't have a Windows installation.

The solution in brief: install FreeDOS and copy the BIOS flash utility onto that partition using the Ubuntu live CD.

The details:

[LIST=1]
[*]go into BIOS Setup and load fail-safe defaults
[*]if you don't have a floppy drive, make sure BIOS knows that, or things will become a little confused when you try to boot FreeDOS
[*]download and burn the full [FreeDOS ISO](http://www.freedos.org/freedos/files/)
[*]download the latest [AB9 BIOS](http://www.abit.com.tw/page/uk/download/download_bios_detail.php?pFILE_TYPE=Bios&pMAIN_TYPE=Motherboard&pTITLE_ON_SCREEN=AB9&pSOCKET_TYPE=LGA775) update and put it on a USB flash disk
[*]install FreeDOS onto the hard drive (yes, really - issues with CDROM support on early AB9 BIOS releases means that this is the best way)
[*]boot off the FreeDOS live CD, and edit C:\FDCONFIG.SYS to remove the phrase "TUNS" from the end of the SHELLHIGH directive (see [here](http://www.mail-archive.com/freedos-user@lists.sourceforge.net/msg07938.html) for the reason)
[*]boot using your Ubuntu live CD, and copy the BIOS flash utility from the USB keychain to the FreeDOS partition; you may have to attempt this multiple times as the old AB9 BIOS will be causing Linux to crash randomly but frequently
[*]reboot into FreeDOS in safe mode (either from the live CD or the startup menu) and run the BIOS flash utility
[*]when prompted by the BIOS flash utility, hit F1 and the machine will reboot
[*]BIOS will then complain about a CMOS checksum error; press DEL to enter BIOS setup and load optimized defaults, disable the floppy drive (unless you have one), and set the first boot device to be the CD-ROM
[*]boot from the Ubuntu live CD and install Ubuntu
[*]go and put some more home-brew in the fridge
[/LIST]
In hindsight, I probably could have got away with just creating a FAT16 partition, putting the BIOS flash utility there, then booting from the FreeDOS live CD.  That said I'm enjoying having FreeDOS on my machine; it's very retro :-)

---

### Post by cascade9 on 2010-07-18
Nice work. 

I would have just done it the old fashioned way with a floppy, but I'm lazy :)

---

### Post by duncan_bayne on 2010-07-18
Thanks :-)  And oh yeah, the machine had no floppy drive and I had no access to one to install.

---

