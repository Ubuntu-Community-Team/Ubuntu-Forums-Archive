---
title: "30GB Missing from external HDD"
date: 2008-04-07
forum: Hardware &amp; Laptops
---

### Post by AutoGyro on 2008-04-07
I'm trying to format my 500GB external HDD (eSATA/USB) so I can use it as an easy stoarge repository.  Unfortunately, instead of getting the 465GB I'd expect, I get 435GB free space and a 7GB "lost+found" folder marked unreadable.  I formatted using gparted as ext3 and ext2 having the same result both times.  Any suggestions?

---

### Post by njparton on 2008-04-07
The file tables for different filesystems take up a varying amout of space at the start of the drive.
 
If you google for this I imagine there's some info out there to guide you on how much to expect to lose.
 
I take it the 465GB estimate was based on an NTFS or FAT format in windows?

---

### Post by AutoGyro on 2008-04-07
Actually, the 465GiB (I misread it this morning) is based on GParted's reading after being formatted to ext2.  7.38GiB is apparently used for the system table and the "lost+found" folder, leaving 458.38GiB unused.  Checking the disk information in Nautilus, it shows 435.1GB free space.  Now, doing the math, 458.38GiB equals about 447GB--another 12GB unaccounted for!

What I want to do here is potentially recover those 12GB (if they are, in fact, missing--I come from a Windows world where GB=10^6 and GiB doesn't exist, so my math may be off) and be rid of the "unreadable" lost+found directory now residing on my drive!  I know what information [fragments] is in the lost+found directory, and I don't need it.

Currently, the drive is formatted in ext2 format (with the exact same numbers), and I'm running e2fsck to see what develops.

---

### Post by AutoGyro on 2008-04-10
Found out that ext2/3 file systems set aside a certain percentage in addition to the file tables, etc, that njparton had mentioned for the purpose of journaling in the case of filling the available physical space on the drive.  This feature is handy for the root directory, but not so much for a storage drive like I'm setting up.

Anyway, ran across the tune2fs application by chance, and was able to find the exact solution I was looking for:

```
sudo tune2fs -m 0
```Sets the reserve to 0.

```
sudo rmdir (hard drive location)/lost+found/
```Kills the unreadable lost+found folder.

I knew if I dug a little more, I'd eventually find the answer.  :KS

---

