---
title: "External Hard Disk question"
date: 2009-03-04
forum: Hardware
---

### Post by floyd0 on 2009-03-04
Hi guys,
       I'm fairly new to linux, so please forgive me if I seem a bit clueless!
I'm having a nightmare with my external hard drive - (500GB Maxtor Basics) and I am running the Intrepid ibex 64-bit version of Ubuntu.

After finding out linux didn't want to give me write permissions to my hard drive (due to it previously being NTFS), I decided to wipe my external hard drive so that it's completely blank (in RAW format).

Firstly, I want to know if it is possible to format it in a way so that I can have write/read access from both ubuntu and windows OS's. FAT/FAT32? Or something else?

Furthermore, what software is available to do this?

Any advice would be much appreciated! Regards, Floyd0

---

### Post by anubhavrocks on 2009-03-04
Chk this out:
```
https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G
```

---

### Post by Therion on 2009-03-04
Okay so your external HDD is now unpartitioned and unformatted, correct?  You should be able to connect it to your lappy and, using gParted, format the drive using NTFS.  Yes, you could use FAT32 if you prefer, both are acceptable to Linux and Windows both.  

FAT32 is not a journaled file-system, so I would *suggest* NTFS, but that's just my opinion.  Your previous "ownership" problems with this drive, most likely, could have been easily resolved by changing the drive permissions, but it's a little late for that now.

Edit: The ntfs-3g package is fine, but to my knowledge it's just a GUI-front end for managing *existing* NTFS partitions, not creating them.  NTFS read/write support is native to Ubuntu since, I think, Gutsy Gibbon.  It's certainly present, natively, in Intrepid though.

---

### Post by floyd0 on 2009-03-04
Thanks for the quick replies. 
I've installed Gparted and attempted to reformat... However, it won't let me select a partition size or file system type (they're disabled) - It says the drive has -512.00 B! I'm also getting the error message "A partition cannot have a length of -1 sectors". It seems as if something horribly wrong has happened in the hardware... Any ideas/suggestions?
Cheers

---

### Post by Therion on 2009-03-04
Weird.  Time to pull out the big gun.  Download a Parted Magic LiveCD; it's only ~85MB (link below).  

Burn it to a bootable .iso CD and reboot via this new CD.  Using Parted', remove any and all existing partitions on the drive and reformat the entire drive with NTFS.  Remove the CD, reboot the PC normally and proceed to see if the external drive now mounts as it should under Ubuntu.

[http://wiki.partedmagic.com/index.php/Downloads](http://wiki.partedmagic.com/index.php/Downloads)

---

### Post by floyd0 on 2009-03-04
I tried the live cd but it didn't make any difference. One thing i've noticed though, is that when i run the fdisk -l command, the external hard drive doesn't have any data associated with it (/dev/sdb)

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3e173e16

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37332   299869258+  83  Linux
/dev/sda2           37333       38913    12699382+   5  Extended
/dev/sda5           37333       38913    12699351   82  Linux swap / Solaris

Disk /dev/sdb (Sun disk label): 255 heads, 63 sectors, 0 cylinders
Units = cylinders of 16065 * 512 bytes

   Device Flag    Start       End    Blocks   Id  System
floyd@floyd:~$ 


```

---

### Post by floyd0 on 2009-03-05
I've also tried recovering any old partitions using the testdisk program from cgsecurity, but that doesn't find or recover any information either! 
I'm running out of ideas, although i'm sure there must be a fix! It seems as though a lot of people have similar problems, where they're drive is apparently "unallocated", but they still can't create a new partition. :(

---

