---
title: "Can´t find ide flashdisk, and ata disk becomes sda?"
date: 2007-11-15
forum: Hardware &amp; Laptops
---

### Post by kragsterman on 2007-11-15
Hi!
 Ubuntu 7.10, running an old  hp vectra vl 400, PIII 866. Systemis installed at master on primary ide-channel.
Anyway, I´m using flashdrives quite exstensively, and in this case an ide flashdisk, directly in the sekundary ide-channel. The drive shows nicely in bios/setup, but when ubuntu booted I can´t find it anywhere. Of coarse I tried fdisk, but it only show /dev/sda1, 2 och 3, etc. No other /dev/?. I even tried parted, but with same result. Checked the hardware monitor, but didn´t find anything there either. There is nothing wrong with the drive, I tried it in other systems(rhel, fedora, window§), and it works well. Something else I have thought about, is why the primary ide drive shows up as /dev/sda, instead of /dev/hda? When I lock in the hardware monitor it shows up under scsi//scsi/ata, which maybe is why, but why is it under scsi? It was also registred under /proc/scsi/scsi/ata. Why? Greatful for help and aspects of this. Rgrds JK

---

### Post by fatespeaks on 2007-11-17
On Ubuntu 7.10 my IDE (PATA) shows up as /dev/sda as well.  I found this post while investigating.  My best guess is that Ubuntu is now using libATA for IDE controllers.  Perhaps your IDE flashdisk is not supported by libATA?

---

