---
title: "how to reuse hdd"
date: 2007-07-29
forum: Hardware &amp; Laptops
---

### Post by darkhut on 2007-07-29
I had a RAID0 setup with two sata drives. after running in all sorts of confusing outputs from programs like fstab and parted, I decided to ditch it. I started using the first drive only, that was /dev/sda. After a while, I noticed that fstab /dev/sdb was reporting "unable to seek on /dev/sdb". Now, I'm trying to actually install windowsXp on that drive alone, but I get "setup cannot use the drive" and I can only see a MBR partition of 980mb, when the drive is 80gb. From whithin live knoppix i get the same fdisk message: "unable to seek on /dev/sda" (it's sda because i moved it to sata1).

My question is how do I make this hdd usable again?

---

### Post by bwhaley on 2007-07-29
You should run filesystem check on the drive. Try

```
% sudo e2fsck /dev/sda 
```

That may report/fix some errors. If you don't have any important data on the drive, you can also recreate the partition table (with sudo fdisk /dev/sda).

---

### Post by darkhut on 2007-07-29
# e2fsck /dev/sda
e2fsck 1.40-WIP (14-Nov-2006)
e2fsck: Device or resource busy while trying to open /dev/sda
Filesystem mounted or opened exclusively by another program?


# fdisk /dev/sda

The number of cylinders for this disk is set to 10011.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Unable to seek on /dev/sda


see? it's beeing stuborn:)

---

### Post by bwhaley on 2007-07-29
Hmm, sounds like you could potentially have a bad drive. Can you run any BIOS-level diagnostics on it?

---

### Post by darkhut on 2007-07-29
hmm, it shouldnt be bad, I bought it a couple of months ago. and it really worked in raid0, I can tell the difference in performance. but anyway, I'll try and see if it is bad as u say.

---

### Post by darkhut on 2007-07-29
after using the shred utility:

# fdisk -l

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 1031 MB, 1031798272 bytes
32 heads, 62 sectors/track, 1015 cylinders
Units = cylinders of 1984 * 512 = 1015808 bytes

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/dm-0: 82.3 GB, 82348212224 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/dm-0 doesn't contain a valid partition table


hope it works this time:)

---

### Post by darkhut on 2007-07-29
I still have a small 783 mb partition(?) besides the big 78000mb chunk. Im gona see if i can erase it with dd.

---

### Post by darkhut on 2007-08-02
xp setup still sees the separate disk, but fdsik -l is normal after erasing with dd

---

