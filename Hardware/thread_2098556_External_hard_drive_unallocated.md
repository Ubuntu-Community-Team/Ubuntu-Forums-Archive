---
title: "External hard drive: unallocated"
date: 2012-12-27
forum: Hardware
---

### Post by Ck.asdf on 2012-12-27
I'm not sure if this is the right forum, but I figure it's a good start.

I had to use my external hard drive enclosure for another hard drive than the one normally in there, and after I put the hard drive back in, I went to get some data off of it.  I plugged it into the enclosure, plugged the enclosure into the computer, and nothing happened, no drives mounted.  

In gparted, the entire drive is listed as "unallocated."  I cannot remember the file system structure, but I had one ext4 partition with a Linux OS on it, another ext4 partition for the majority of my files, and an NTFS partition for Windows backup.

Any thoughts on bringing back the filesystem and the files?

---

### Post by ahallubuntu on 2012-12-27
Give testdisk a try, see if it can find anything on there.

---

### Post by Ck.asdf on 2012-12-27
Thanks for the suggestion.  Out of curiosity, I connected it to the computer it had originally been connected to via eSATA, and the data actually shows.  But connected to my new computer via USB, it doesn't.  The new one has the UEFI boot stuff, the old one doesn't; could this have any effect on the drive, even though I don't boot to it?  Alternatively, could the difference in plugging it in via USB vs eSATA have made any difference? 

Anyway, if I do have any problems in retreiving the data, I'll definitely give the software you mentioned a look.

---

