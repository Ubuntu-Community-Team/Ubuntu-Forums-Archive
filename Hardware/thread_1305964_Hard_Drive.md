---
title: "Hard Drive"
date: 2009-10-30
forum: Hardware
---

### Post by RumboPumbo on 2009-10-30
Hello,
I have a hard drive which is corrupt and not booting (Windows Hard Drive) it hasn't been used in a while (about 4 years) so all the information on there isn't needed (already checked just in case), i now want to see if i can make it work again by re formatting it, i know you can with windows but i dont know how to re format when using Linux, any guidence?
Thanks in advance

---

### Post by hal10000 on 2009-10-30
use gparted for partitioning and formatting
```
sudo apt-get install gparted
```

---

### Post by sickly on 2009-10-30
what do you want to fomat it to?
for example:
open a terminal:
unmount the drive: 
 
sudo umount /dev/sdb1
 
format it in fat32:
 
sudo mkfs.vfat /dev/sdb1
 
 
( /dev/sda1 ) is my drive path, and probly wont be the same for yours. Hope this helps

---

### Post by RumboPumbo on 2009-10-30
I am wanting the hard drive to be wiped clean basically so there is no data left on

---

### Post by sickly on 2009-10-30
The above commands i listed will wipe it clean in a format of FAT32. You need to find out what format you want it in.

---

### Post by coffeecat on 2009-10-30
> **RumboPumbo said:**
> I am wanting the hard drive to be wiped clean basically so there is no data left on

Yes, that's fine, but what do you want to do with the drive then? You mention re-formatting, but you have to reformat by creating one or more partitions with a filesystem - or re-formatting an existing partition.

One poster has told you about Gparted which will do everything you want and more. Another has told you how to create a drive with a single FAT partition. But you need to be more specific with what the drive is for in order to get specific advice.

Another point - reformatting a drive will rewrite the partition table but will not erase any data on the drive. Most files and data will still be recoverable (until they are overwritten) with forensic software or even tools available in the Ubuntu repositories. So if you have private data you want irretrievably erased, you will need to use a tool such as shred.

---

### Post by amjjawad on 2009-11-01
> **RumboPumbo said:**
> Hello,
I have a hard drive which is corrupt and not booting (Windows Hard Drive) it hasn't been used in a while (about 4 years) so all the information on there isn't needed (already checked just in case), i now want to see if i can make it work again by re formatting it, i know you can with windows but i dont know how to re format when using Linux, any guidence?
Thanks in advance


Do you mean the data is corrupted and you just need to format it to make it usable? or you mean it's not working at all?

---

