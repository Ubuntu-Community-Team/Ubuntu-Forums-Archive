---
title: "Accidentally formatted my FAT32 HDD into ext3"
date: 2008-09-13
forum: General Help
---

### Post by sa-mejia on 2008-09-13
Help!  

In the process of backing up my data from my old external HDD to a new one, I accidentally formatted it.  

The old HDD was in FAT32, and I formatted it into ext3 (using gparted).

I tried to recover my filesystem with TestDisk, but it did not work 

(I tried following the steps posted in [http://www.cgsecurity.org/wiki/Data_Recovery_Examples#Recovery_of_reformated_partition](http://www.cgsecurity.org/wiki/Data_Recovery_Examples#Recovery_of_reformated_partition) and [http://ubuntuforums.org/archive/index.php/t-560209.html](http://ubuntuforums.org/archive/index.php/t-560209.html), 
but it seems to me that this only works when you format a FAT32 into ntsc, or vice versa.

Does any one know whether it is theoretically possible to recover my original filesystem?  

If so, any idea of how is this practically attainable?

Thanks for any kind of help. 

Santiago.

---

### Post by Bucky Ball on 2008-09-13
If you've formatted the disk where the data was, it is unlikely. You now have a blank disk. Are you wanting to recover the data?

Run this in a terminal with your drives plugged in and switched on:

**sudo fdisk -l**

Post the results here.

Alternatively, if you can see your external drive on the desktop, it is mounted and ready to go. Double clicking it will tell you what is on there.

---

### Post by sa-mejia on 2008-09-13
Yes.  What I have now is a blank disk.

And... if it is not possible to recover the file system, I will, in fact, try to recover the data.


The relevant result of fdisk (that is, the HDD in question):

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3d51c552

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321   83  Linux

---

### Post by Sef on 2008-09-13
Check out [Trinity Rescue Kit]("http://trinityhome.org/Home/index.php?wpid=1&front_id=12").

---

### Post by Gannon8 on 2008-09-13
Or photorec. That will look even in the free space.
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

---

### Post by sa-mejia on 2008-09-14
> **Sef said:**
> Check out [Trinity Rescue Kit]("http://trinityhome.org/Home/index.php?wpid=1&front_id=12").

From what I have read in [http://trinityhome.org](http://trinityhome.org), it seems that what I need is to use TestDisk.  However, as I said, it did not work for me.  

Do you think that if I put down the output of TestDisk, you might be able to help me?

---

### Post by sa-mejia on 2008-09-14
> **Gannon8 said:**
> Or photorec. That will look even in the free space.
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

My cherished dream would be to restore the file system (if that is how it is called).  That is, what I would like to have is some magic utility that restores not only a raw and disorered list of files, but also as much as it can from the file structure.

Anyways, I gave it photorec a try (in a disk image that I created as soon as I could) but many archives seem to be merely corrupted.  There are many .doc and .pdf which simply do not open.  Not to mention that it could not retreive any of my .avi, mpg, wmv.  foremost worked better, but it is still far from what I would like to have.  

Do you know if, perhaps altering something in the advance options, I can have more luck with photorec?

Thanks.

---

### Post by sa-mejia on 2008-09-24
bump

---

