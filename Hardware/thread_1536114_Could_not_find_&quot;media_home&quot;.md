---
title: "Could not find &quot;/media/_home&quot;"
date: 2010-07-21
forum: Hardware
---

### Post by whoboo on 2010-07-21
I get that when trying to open the CD-R via Places.  Where is it coming from and how do I get rid of it ?  

My CD is still not writing, though it goes through all the motions.  I have tried the suggestions in the ATAPI.README.setup file.  That just seemed to lock things up so restart wouldn't even function.

Any ideas will be appreciated.

---

### Post by whoboo on 2010-07-22
I commented out this line in /etc/fstab and the "Could not find ..." message went away:

 /dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0


still have the sr0 error problem and no writing to cd ...  verrry annoying ...

help, please ...

---

