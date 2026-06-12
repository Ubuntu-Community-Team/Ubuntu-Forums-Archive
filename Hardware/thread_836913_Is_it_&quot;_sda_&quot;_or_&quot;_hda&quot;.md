---
title: "Is it &quot; sda &quot; or &quot; hda&quot;"
date: 2008-06-22
forum: Hardware
---

### Post by sofasurfer on 2008-06-22
I was using a sata HD but now have added an ata HD. I reinstalled Ubuntu on the ata HD and intend to use the sata HD for backup.

In trying to learn how to mount the sata to my system I used gparted to see what the hard drives are recognized as. I see that I have 3 drives listed. They are...

/dev/scd0  (unallocated, size 512 bytes, 0 used).  
/dev/sda (my backup drive, 233 gig). 
/dev/sdb (ubuntu, /dev/sdb).

Questions...
What is the scd0?
Why does the Ubuntu drive show up as /sdb? Isn't sd(x) a sata designation? Shouldn't an ata device show up as /dev/hd(x)?

---

### Post by chungy on 2008-06-22
/dev/scd0 is the optical drive.  I don't know why GParted lists it, but ignore it.

as for the /dev/sdX thing, that's just the designation for SCSI *and* SATA (also USB drives, for some reason...).  I would say you should know which disk is which by the sizes...

---

