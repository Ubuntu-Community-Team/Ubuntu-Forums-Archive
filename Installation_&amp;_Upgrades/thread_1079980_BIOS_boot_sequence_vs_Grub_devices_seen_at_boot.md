---
title: "BIOS boot sequence vs Grub devices seen at boot"
date: 2009-02-24
forum: Installation &amp; Upgrades
---

### Post by Browser_ice on 2009-02-24
I need to confirm something.

If my BIOS boot sequence is setup as :
1-CD
2-Floppy
3-USB key
4-HD-A
5-HD-B

and I boot the PC with a CD + USB Key

then Grub will label the CD as hd00, USB=hd01, HD-A=hd02, HD-B=hd03 ?

In other words the first device Grub sees according to that BIOS list will be marked as hd00, the second device it sees will be hd01 and so on ?

---

### Post by cybergalvez on 2009-02-25
> **Browser_ice said:**
> I need to confirm something.

If my BIOS boot sequence is setup as :
1-CD
2-Floppy
3-USB key
4-HD-A
5-HD-B

and I boot the PC with a CD + USB Key

then Grub will label the CD as hd00, USB=hd01, HD-A=hd02, HD-B=hd03 ?

In other words the first device Grub sees according to that BIOS list will be marked as hd00, the second device it sees will be hd01 and so on ?

I don't think thats the way it works, your bios will try to boot from the cd, floppy usb and then HDA in that order. If it finds bootable media then the bios is happy and will try to boot, no grub is involved if you boot from the cd or usb.  Grub will only count the HS';s so hd1 is your hsa and hd2 is your hdb

---

### Post by caljohnsmith on 2009-02-25
> **Browser_ice said:**
> 
then Grub will label the CD as hd00, USB=hd01, HD-A=hd02, HD-B=hd03 ?

In other words the first device Grub sees according to that BIOS list will be marked as hd00, the second device it sees will be hd01 and so on ?
You are correct in that Grub on start up sees the order of drives as your BIOS boot order, but Grub does not label the drives as you have them; the floppy drive would be (fd0), the CD would be (cd0), and all other USB/IDE/SATA drives are labeled as (hdX); so in your case, the USB drive would be (hd0), HD-A would be (hd1), and HD-B would be (hd-2), since that is how you have those drives in your BIOS boot order. :)

---

