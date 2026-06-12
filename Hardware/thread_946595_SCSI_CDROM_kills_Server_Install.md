---
title: "SCSI CDROM kills Server Install"
date: 2008-10-13
forum: Hardware
---

### Post by clay.michaels on 2008-10-13
I am trying to install 8.04 Server on an old DataGeneral AViiON 3700 (or it might be a 3400, it is not clearly marked)

I can boot from the CD, but when the installer tries to search for a common CDROM drive, it fails. I had the same problem with the USB install. I tried installing an IDE CDROM drive, and I could boot from that but then the installer craps out in the same place. 

My question is basically:
How come I can boot from a CDROM drive, and yet the installer can't see the drive its sitting in? Seems crazy to a novice like me.

Thanks in Advance

Specs:
4x PIII 
2 GB RAM
A 16-bit wide LSI SCSI controller on MB w/ CDROM
A 32-bit wide LSI SCSI controller on MB unused
A Mylex DAC 960 PCI SCSI add-in controller attached to the backplane 5x HDD
ATA controller w/ Floppy drive
A PCI Fibre-Channel card for my SAN (not set up yet)

---

### Post by scratman on 2008-10-13
Same place everytime?  Hmmm, have you checked the md5 checksum?
Might be worth burning it again.

---

### Post by clay.michaels on 2008-10-13
Tried 2 different CDs (both Ubuntu Server) and I also tried the USB install. (Different download)

I will check the checksums, but I don't think that is it. 

Thanks, either way

---

### Post by clay.michaels on 2008-10-14
Nope, as I suspecterd, they summed out fine. 

Any other Ideas?

---

### Post by clay.michaels on 2008-10-25
I still haven't found a solution.
Anyone?

---

