---
title: "Problem with adding an Ultra ATA IDE Card with 2 Storage Drives"
date: 2005-07-18
forum: Hardware &amp; Laptops
---

### Post by SogniX on 2005-07-18
Ubuntu does not like my Adaptec Ultra ATA card with 2 storage drives (no OSs).
Here's my setup:


IDE1 : HDD1 = Windows XP
       HDD2 = Ubuntu

IDE2 : DVD Drive
       CDRW Drive

Adaptec PCI Ultra ATA Card with:
IDE1 :  120 GB HDD - Storage
        120 GB HDD - Backups
 


I installed and am able to boot into Ubuntu without the Adaptec card in. But the moment I put it in, Ubuntu freaks out and gives me a kernel panic, with a line that says :

VFS: Can't find ext3 filesystem on dev hdb1.

So I assume that with the adaptec card in - my secondary hard drive got moved to a different virtual location. Question is, where? And how do I fix it? :(

Thanks for any info.

---

### Post by SogniX on 2005-07-18
I am booting off of the live cd, chroot into the ubuntu installation, I edit the /boot/grub/menu.lst file to point to the correct drive, and do grub-install /dev/hda but get an error about stage1 file not being able to be read correctly. 

I've read somewhere that bios antivirus protection might do that, so I disabled it and still no luck.

Now what? reinstall? :(

---

### Post by steven_ellis on 2005-07-19
Ok when you boot off the Live CD can you get the details on the hard drive order as discovered by Linux.

Sounds like Linux is treating your Ultra ATA card as ide0, and ide1, and your onboard as ide2, ide3.

I've had similar problems with selected IDE cards which is really annoying.

What you can try is to tell your bios to boot from SCSI or RAID and see if that help

Steve

---

### Post by SogniX on 2005-07-19
You are right, now that I look closer to what it's doing that's exactly it! The ATA Card is taking priority! Gah!!! 

I don't think the motherboard has options as far as booting from a ATA/RAID card, but I'll play around with it. 

Maybe I can just put the Ubuntu drive into the IDE channel where it'll find it. Not really what I wanted to do but, if it works I'll be happy. :p

---

### Post by SogniX on 2005-07-20
Incase anyone is wondering,
I solved the problem by putting all the hard drives on the ATA Card with the OS Drives in Channel 1, and the storage drives in Channel 2 (altho the storage drives should work on either the motherboard or ata card). I reinstalled the OS and it worked fine from there.

---

