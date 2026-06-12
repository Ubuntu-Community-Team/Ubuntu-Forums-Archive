---
title: "Can't mount CDs"
date: 2009-07-12
forum: Hardware
---

### Post by iamgoose on 2009-07-12
Ubuntu 9.04 new installation, first on this hardware. Can't mount data CDs or play audio CDs. Dell Latitude D505 with IDE CDROM. I think fstab sees it as a SCSI device (because of "scd0"?

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

For data CDs: "Unable to mount location, no media in the drive"
For audio CDs: ...nothing at all. 

Thanks in advance!

---

### Post by wojox on 2009-07-12
Add a line for it in /etc/fstab like so:


/dev/scd0 /media/cdrom0 iso9660,udf user,noauto,exec,utf8 0 0
/dev/sr0 /media/cdrom0 iso9660,udf user,noauto,exec,utf8 0 0

---

### Post by iamgoose on 2009-07-12
After adding the additional line and restarting, the file browser could read the volume name of the CD and display it in file brower, but I still can't access it. Any other ideas? Thanks!

---

### Post by iamgoose on 2009-07-12
Correction to my last post. I can now successfully mount data CDs after editing fstab as suggested. I still can't see or play audio CDs. Any suggestions?

---

