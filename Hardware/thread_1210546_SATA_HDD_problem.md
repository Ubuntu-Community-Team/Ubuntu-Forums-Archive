---
title: "SATA HDD problem"
date: 2009-07-11
forum: Hardware
---

### Post by Sopranosmainman on 2009-07-11
I have a 500GB SATA HDD used for storage. its ext3 file system. As of yesterday, out of the blue my system was starting to freeze up on me. When looking at the logs i saw the following errors when accessing that drive. -hdd error {DRDY err}-

i looked this up and saw this as a possible solution
e2fsck -f -c -v /dev/sda1

so i unmounted my drive and ran it. but i still am having problems. I tried it in a different computer and running it in windows with a ext2/3 mounter program, and nothing!

i tried acronis, clonezilla, something just to salvage my data, and again i have problems. Now the thing is, that i can still access te dive, and see my folders/data, it just spews out alot of errors?

anything anyone can think of so that i can back up my files?

thanks!!!

---

