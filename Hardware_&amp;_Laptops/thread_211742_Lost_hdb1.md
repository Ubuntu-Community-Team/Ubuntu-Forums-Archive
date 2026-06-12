---
title: "Lost hdb1"
date: 2006-07-08
forum: Hardware &amp; Laptops
---

### Post by Guns90 on 2006-07-08
I had originally installed and was using Breezy. I wanted a bigger hd, so I bought a new one, installed it, and downloaded and installed Dapper on it. I moved the Breezy hd over to hdb1. I couldn't mount hdb1 because it was being viewed as 'not a removeable data device'. I followed the how to at [http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html) and the hdb1 disappeared, but a 'storage' file appeared in the 'computer' window. I have looked through all the files in the 'storage' folder, but I cannot find any of the files I had on hdb1.  I'm lost.  I would appreciate it very much if someone could help me. Thanks

---

### Post by coffeecat on 2006-07-09
A couple of questions first. Did you just want to copy some files across from your old Breezy partition, or did you want to create a dual Breezy/Dapper boot? If the latter you'll be needing to edit the Breezy fstab among other things.

Leaving that aside for now, if you just want to do a once-only copy of some files, boot up with the Dapper live CD and it should mount both hard drives, and you will be able to copy the files across. But if you need long term access to the Breezy partition, then some detective work is needed because if you've followed the linked howto correctly it should all work.

OK then. Did you add a hdb1 line to fstab? Suggest you post your fstab. Did you do the chown and chmod lines, and did you change 'marie' to your own username and group? If you did all that correctly and it still doesn't work then I can suggest a different hdb1 line for fstab from that in the howto and which works for me. I'll wait to see what you post before posting it.

---

### Post by Guns90 on 2006-07-16
Sorry it took so long to get back on this.  Family stuff, ya know?  Anyway, I just went back and followed all the directions in the howto again.  The only thing that was differant this time was that the storage directory was already there (and recognized).  Here is what I currantly have on my fstab..

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1 /storage ext3 defaults 0 0

Oh, I forgot to answer your question.  I simply want to transfer all the data (documents, pictures, music, etc.) that I have on hdb1 over to hda1, and then be able to store new data on hdb1.

---

