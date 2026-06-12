---
title: "Mounting a NTFS partition"
date: 2008-03-19
forum: Hardware &amp; Laptops
---

### Post by Living2007 on 2008-03-19
I have 4 Partitions:
NTFS, SWAP, EXT3, NTFS (in that order)

The last NTFS was created after Ubuntu was installed. I want to mount this drive at startup but it fails to do so. I looked at Hardware Information and the difference between the two NTFS in that it doesn't have a fstab alocation, this is what is preventing it to happen.

What do I do next?

P.S.: I have tried putting in the drive information into fstab, but it doesn't work, why is it still failing?

---

### Post by penguinpi.com on 2008-03-19
try

```
sudo apt-get install ntfs-3g ntfs-config
```

---

### Post by dark_phantom on 2008-03-19
Post what you have done so far.  You need to find out what partition it is.  It should be something like /dev/sda7 or similar.  Try mounting it like this.  

/dev/<partition> /media/<moun point> ntfs-3g defaults,locale=en-US.utf8 0 0

---

### Post by Living2007 on 2008-03-19
The two NTFS partitions are the same but the forth was partition was created after I installed ubuntu.

How do i check if it has he ntfs-3g version

---

### Post by Living2007 on 2008-03-19
I bought my computer with XP installed under NTFS
2 years later: Shrunk XP and created linux-swap anf ext3
1 week later: Shrunk ext3 and created a 2nd NTFS partition
Ubuntu didn't pick this partition up. Missing fstab string in "Hardware information". This is part off the problem

---

### Post by Living2007 on 2008-03-27
Hello, I erganrly need this problem **FIXED!**

Note the spesifications are in the previous post

---

