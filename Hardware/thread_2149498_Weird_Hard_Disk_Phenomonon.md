---
title: "Weird Hard Disk Phenomonon"
date: 2013-05-29
forum: Hardware
---

### Post by rookcifer on 2013-05-29
I have a 1TB hard disk used as a backup/storage drive.  I had all 1TB formatted to NTFS so I could access the files (music and vids, etc) on my Windows partition.  While ago I decided to check the SMART data and discovered that the "reallocated sector count" is sitting at 2510 bad sectors.  There is also a "current pending sector count" of 1 (implying one sector cannot be allocated).

So, I decided to do a format the entire drive to ext4 so I could backup some Linux stuff (don't really care about the stuff the drive has on it now).  Anyway, I opened Gparted, deleted the NTFS partition and formatted the whole drive with one ext4 partition.  Now, here's the weird thing.  Whenever I mount the partition using "mount" the first directory i see is a directory that was on my NTFS partition!  This directory has 20-30 gaming videos that I put on it back when it had the NTFS partition.  Somehow they survived a format to ext4.  

Now my assumption is that since I am getting sector errors, that the drive has some internal failsafe mechanism and moved my data to a separate partition created by the drive somehow.  Problem is this partition is not visible to either fdisk or gparted.  Before I did any formatting of the disk, I looked at fdisk -l and saw a partition called "DiskSecure."  I Googled it and indeed it seems this "DiskSecure" partition is some sort of mechanism the drive manufacturer built-in to move data to if a hardware error is encountered.  But, now, after the format to ext4, the Windows files still exist (and can be viewed) but the "DiskSecure" partition is no longer visible to Gparted or Fdisk.

So, whats up with this?  Any ideas?  I would prefer to ust wipe the entire disk and start over at this point (assuming the disk isn't beyond repair, which it probably is).

---

### Post by ahallubuntu on 2013-05-29
~

---

### Post by CatKiller on 2013-05-29
I concur that a drive that is even remotely suspect is not worth bothering with. FWIW, though, most hard drive manufacturers have a downloadable utility that will do a low-level format.

---

### Post by mörgæs on 2013-05-29
Depends on the purpose. If the drive is not for valuable data there's nothing wrong with using it.

I would erase the drive with Killdisk booted from a USB stick. After that you can create a partition of (say) the first 20 GB, hoping to isolate the errors there. This partition is of course not used. 

After that you create root, home and swap partitions as usual.

**badblocks** is good for checking if a particular partitions has bad sectors, for example with ```
sudo badblocks -svw <partition>
```

---

### Post by CatKiller on 2013-05-29
> **mörgæs said:**
> Depends on the purpose. If the drive is not for valuable data there's nothing wrong with using it.

If the data's not valuable, there's not much point storing it either :)

---

### Post by mörgæs on 2013-05-29
Still there are many uses for a semi-dead drive. Testing 13.10, distrohopping and other kinds of experimenting, just to name a few.

---

