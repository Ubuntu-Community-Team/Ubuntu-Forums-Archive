---
title: "Permissions on USB drive"
date: 2015-03-08
forum: Hardware
---

### Post by ubuntubrian on 2015-03-08
I struggled for hours to format a flash drive (FAT32) so I could add some pix to it and view them with a Pico projector. I used gparted to format the drive yet I could not add files without superuser permissions. Needless to say the projector could not view the files. After many attempts with gparted, disk utility and googling my fingers raw I finally decided to just mount the drive on my wife's macbook, run the disk utility and repair. 
The drive worked like a charm. I could add pix and view them.
My question is, is there or why is there not a simple way to do the same with Ubuntu?

Thanks

---

### Post by weatherman2 on 2015-03-08
I did this yesterday in Ubuntu with Gparted.  It was easy and took about 30 seconds to make a FAT32 partition on the flash drive and format it.  My GPS could read it without issue.

You do need "superuser" (sudo) privileges in Ubuntu to run Gparted, but that's a simple matter of typing your password once.

I didn't see exactly what you were doing, but may I suggest you were creating not a FAT32 partition but an ext4 (Linux) partition?  That's the default partition type in Gparted, unless you choose "FAT32" from the drop-down list.  There are no special permissions for FAT32.  If you successfully create such a partition in Ubuntu, any user can write to it.

---

### Post by coldraven on 2015-03-09
> I did this yesterday in Ubuntu with Gparted.  It was easy and took about  30 seconds to make a FAT32 partition on the flash drive and format it.   My GPS could read it without issue.
Same here, no problems any time that I have created a FAT32 usb stick or card. I've been using gparted for about five years now.

---

