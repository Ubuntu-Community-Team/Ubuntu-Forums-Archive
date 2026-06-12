---
title: "Poblem seeing FAT32 partiton on separate drive"
date: 2005-05-08
forum: Hardware &amp; Laptops
---

### Post by mcescher on 2005-05-08
I am having trouble "seeing" a FAT32 partiton I created on my separate Windows drive.
I created the partiton to be able to write files downloaded in Ubuntu and also be able to see them when in Windows.

Can any one tell me how to mount/see this specific partiton in Ubuntu (in gory detail please) so that I can write data to it?

I have tried the official user guide mounting a FAT partiton with no luck. I don't know where to go to have access to this partiton.

---

### Post by alastair on 2005-05-08
The first thing I would do is use "fdisk" to list the partitions on teh relevant drive e.g.

fdisk -l /dev/hda

where /dev/hda is primary master IDE. 

You might see something similar to :

```

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
 
   Device Boot    Start       End    Blocks   Id  System
/dev/hda1   *         1      4865  39078081    c  Win95 FAT32 (LBA)

```

So - /dev/hda1 (partition 1) is FAT.

To mount :

1) make a place to mount it :

sudo mkdir /media/windows

2) mount it :

sudo mount -t vfat /dev/hda1 /media/windows


Then ... you should read about mounting automatically (/etc/fstab), and permissions etc.

---

### Post by voidlogic on 2005-06-06
i agree, I have done that before to preform data recovery for Windows boxes, it worked well.

---

### Post by jsuen on 2005-06-08
[QUOTE=voidlogic]i agree, I have done that before to preform data recovery for Windows boxes, it worked well.[/QUOTE]
 just set it up on my slave drive (xp/hoary) properly just based on this thread and this link here:
[http://ubuntuguide.org/#automountfat](http://ubuntuguide.org/#automountfat)

great! also made a symbolic link for the windows folder on my desktop 

cheers :)

---

