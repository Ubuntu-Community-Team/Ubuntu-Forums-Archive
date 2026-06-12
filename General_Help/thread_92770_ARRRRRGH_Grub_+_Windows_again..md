---
title: "ARRRRRGH Grub + Windows again."
date: 2005-11-20
forum: General Help
---

### Post by rebo on 2005-11-20
Yes I know what you must be thinking not another Grub problem.

Im sorry but ive looked at every tutorial and every possible setup from using the map commands , noverify and such

Situation:: Want to tripple boot XP x64 and Ubuntu

Computer has 2 HDD, one SATA and one IDE. All 3 OSes are on the SATA drive.  Yes i know this is crazy but there we go.

Ubuntu installed with an option in grub to goto ntldr, this brings up my old menu and I can choose from x64 and XP. However the XP link does not work and reboots, i dont thjink it can find the startup file.

So ideally i want to either

(a) boot directly into XP or x64 from Grub, or
(b) re-enable the XP in ntldr

Here is my device.map

(hd0) /dev/hda
(hd1) /dev/sda

Ive tried many combinations of maps and unhides such but none seem to 
work.


fdisk p's

 /dev/hda1 * 1 9728 78140128+ 7 HPFS/NTFS

 Device Boot Start End Blocks Id System
/dev/sda1 * 1 6374 51199123+ 7 HPFS/NTFS
 /dev/sda2 6375 25699 155228062+ f W95 Ext'd (LBA)
/dev/sda3 25700 30401 37768815 83 Linux
 /dev/sda5 6375 12748 51199123+ 7 HPFS/NTFS
/dev/sda6 12749 25496 102398278+ e W95 FAT16 (LBA)
 /dev/sda7 25497 25699 1630566 82 Linux swap / Solaris

Please help i want to throw my computer out the window.

THankyou/

---

### Post by KnottyMan on 2005-11-20
Does your motherboard support changing the boot order so sata would be first?  Sometimes you have to set it to SCSI...

I have my Windows (98, XP) booting out of grub as it saves time picking through submenus.

brb  :)

---

### Post by veloct on 2005-11-20
try this:

title Microsoft Windows XP 1
#:2 <-- type: 0 => linux, 1 => windows, 2 => other
title           Microsoft Windows XP 1
root            (hd1,0)
makeactive
chainloader     +1

title Microsoft Windows XP 2
#:2 <-- type: 0 => linux, 1 => windows, 2 => other
title           Microsoft Windows XP 2
root            (hd1,4)
makeactive
chainloader     +1

Just add these and add # to the rest of your windows stuff so in case this doesn't work we can go back and reinstate it.

---

### Post by KnottyMan on 2005-11-20
Yeah, veloct beat me to it.  Should do the trick.  It's not crazy to have the all the OSes on the same drive.  It's actually harder I think to spread it across multiple devices.  Although with grub magic, "harder" is relative.  :)

---

### Post by aberry7670 on 2005-11-20
Try this link:

[http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html](http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html)

---

### Post by rebo on 2005-11-20
Thanks for your help everyone but im going to reformat and try the whole thing again.

Thanks anyways.

---

### Post by Xogun on 2005-12-14
[QUOTE=rebo]Thanks for your help everyone but im going to reformat and try the whole thing again.

Thanks anyways.[/QUOTE]

How did it go?
Im curious cuz i also have Win xp, XP x64 and Ubuntu on the same HDD, when i installed the ubuntu the windows xp x64 option doesnt work.

Any ideias?

---

