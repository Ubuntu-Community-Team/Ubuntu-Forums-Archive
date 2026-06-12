---
title: "Unable to reformat a drive currently formatted as EFI GPT"
date: 2009-04-05
forum: Hardware
---

### Post by mastakebob on 2009-04-05
I have a drive that I am unable to reformat to EXT3.  The drive is a relatively new (~1 year) 500GB Western Digital 3.5'' EIDE drive.  The drive was originally used in my freeNAS box, so it was formatted with UFS.  However, I now want to use it in my Kubuntu box so I'm trying to reformat it to EXT3.  Thats where my problem is:  It won't reformat.  I've tried gparted and 'wipe'ing the partition clean (wipe /dev/sdg1).  Every time I list my drives with 'sudo fdisk -l', I get that the drive is formatted with "EFI GPT" and a warning saying that "GPT (GUID Partition Table) detected on '/dev/sdg'!  The until fdisk doesn't support GPT".  

Output of fdisk -l:

<...my other disks info...>

WARNING: GPT (GUID Partition Table) detected on '/dev/sdg'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdg: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1       60802   488386583+  ee  EFI GPT

When I try to reformat it in freeNAS, I get some error that about bad I/O (can't remember specifics right now).

---

### Post by taurus on 2009-04-05
Post a screenshot of gparted displaying that drive, /dev/sdg.

---

### Post by mastakebob on 2009-04-05
Gparted screenshot:
[http://img519.imageshack.us/img519/711/gpartedufsdisk.png](http://img519.imageshack.us/img519/711/gpartedufsdisk.png)

---

### Post by mastakebob on 2009-04-05
Some more information:  I bought the disk, formatted using freeNAS to UFS, used it in freeNAS for a bit and then moved it over to my ubuntu box to be used locally.  I reformatted it to ext3 with gparted, and didn't notice that fdisk still had it listed as EFI GPT.  I was able to use it for a bit in my linux box but noticed that some files (movie files) would play fine, but were unable to be copied off of the disk.  It was really weird.  When I would play the files in a media player, they played fine the whole way through, but when I tried to copy them to another drive (either different folder on the same drive or different physical drive entirely), they would get to some point in the copy (different for each file, but always at the same place for each individual file) and just stop copying, and then give me a message about not being able to read from the disk.

---

### Post by mastakebob on 2009-04-08
Bump.
Anyone have any experience with UFS formatted drives not behaving?

---

### Post by curly_nostrill on 2009-04-22
> **mastakebob said:**
> Bump.
Anyone have any experience with UFS formatted drives not behaving?
YES!  I use FreeNAS alot and recently ran into this same problem, i.e. GPT warning in fdisk and I couldn't figure out how to erase the GPT record.

Check my post over here... [HTML]http://ubuntuforums.org/showthread.php?t=1072033[/HTML]

My experience should be on page 2.

---

### Post by cariboo on 2009-04-23
Did you try parted like the error messages said?

---

### Post by curly_nostrill on 2009-04-24
YES! I did try parted and gparted in X and even the gparted live cd and dd if=/dev/zero of=/dev/hdx (with which I became impatient after running for a day and CTL c'd it).  What finally definitively fixed the problem was wiping the (backup?) sector at the *end* of the drive, i.e. what I assume to be 5088 sectors... whatever that means.  

**PLEASE correct me if I'm wrong... **but all the warnings have gone away.

In my post which I glommed from some other post the first command wipes some bit at the beginning of the drive.  I did bork grub on one of the drives I de-GPT'd but reinstalled grub with only slight trouble (since I have a separate /boot and barely know what I'm doing).

Hint: If you have a separate /boot and have to reinstall grub and you use a copy of your original /etc/fstab, be sure to edit the ```
#groot (hdX,X)
``` line in fstab to make the oddness persistent across grub-update 's

---

### Post by mastakebob on 2009-04-26
Wow, it worked!  It doesn't show up as GPT anymore!  Excellent!  Thanks for the excellent advise curly!

For the record:

Problem:  
Harddrive that was previously formatted with UFS refused to be reformated into EXT3.  fdisk gave error about GPT not being supported.  GParted wasn't able to reformat it satisfactorily (GParted returned 'success', but fdisk still saw it as GPT).  

Solution:  
Have to wipe both hidden GPT partitions.  One is located at beginning of disk (within the first 60 sectors), the other is located in the last 5088 sectors of the disk.  This requires determining which physical sectors these hidden partitions are located on (don't worry, its easy, just one subtraction)

DISCLAIMER:  Do at your own risk.  this worked for me, it might not work for you.  

Steps as follows.

step 1:  
Determine where the hidden partitions are located by the following
```
sudo fdisk -lu
```

this results in:  
```
WARNING: GPT (GUID Partition Table) detected on '/dev/sdg'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdg: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1   976773167   488386583+  ee  EFI GPT

```

(your results will have different values due to differing physical disks).  

Step 2:
Erase the GPT partitions
First partition is always in the first 60 sectors (this is just how it works)
so enter:
```
sudo dd if=/dev/zero of=/dev/sdg seek=1 count=60
```
to erase the first partition.  Specifically, this writes all zeros over the first 60 sectors of the drive (i think).  

Second partition is located in the last 5088 sectors.  As you can see above, on my disk, the last sector is sector#976773167, so you have to erase from sector#976768080 to 976773167.  I got 976768080 from subtracting 5088 from 976773167.

```
sudo dd if=/dev/zero of=/dev/sdg seek=976768080 count=5088
```

Step 3:
sudo fdisk -l
should result in the GPT warning being gone.  

```
Disk /dev/sdg: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1   976773167   488386583+  ee  EFI GPT

```

Hope this helps

---

