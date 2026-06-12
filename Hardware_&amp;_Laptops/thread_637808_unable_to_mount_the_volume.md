---
title: "unable to mount the volume"
date: 2007-12-11
forum: Hardware &amp; Laptops
---

### Post by Gouz on 2007-12-11
Greetings everyone.

i have been trying to mount an external HD which I formated myself couple of weeks ago and it was working perfectly.
I make 3 partitions in the same HDD and today when I need something from the HDD two of the three partitions doesn't mount.

I get the errror:unable to mount the volume 'S}nnlowmr'  (as you see the name is all messed up. 

 when I hit details the msg is the following:

mount:wrong fs type,bad option,bad superblock on /dev/sdb1, missing codepage or helper program, of other error.

do you have any idea?

oh and yes the format type is ext 2

---

### Post by linuxonbute on 2007-12-11
I would look at the manual pages for e2fsck.
open a terminal and type 

 man e2fsck 

In part it says 
```

 -b superblock
              Instead  of using the normal superblock, use an alternative superblock 

specified by superblock.  This option is normally used when the primary  superblock has 

been corrupted.  The location of the backup superblock is dependent on the  filesystem’s
  

blocksize.   For  filesystems with  1k  blocksizes, a backup superblock can be found at 

block 8193; for filesystems with 2k blocksizes, at block 16384; and for 4k block&#8208;sizes, 

at block 32768.

              Additional backup superblocks can be determined by using the mke2fs program 

using the -n option to print out  where  the  superblocks  were created.    

The  -b  option  to mke2fs, which specifies blocksize of the filesystem must be specified 

in order for the superblock locations
              that are printed out to be accurate.


```

so something like

```


sudo e2fsck -b 8193 /dev/sdb1 


```

might fix it depending on the block size you have on the drive.


I think this sort of corruption can occur if the drive has just been turned off without it being unmounted first.

---

### Post by Gouz on 2007-12-11
That is what I get as an out put

```
~$ sudo e2fsck -b 8193 /dev/sdb1
e2fsck 1.40.2 (12-Jul-2007)
e2fsck: Bad magic number in super-block while trying to open /dev/sdb1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

hmm I always unmount the dev..

Edit... oopss...
just run the fdisk and I got that the volumes are on NTFS (Id:86)

Do you know anyway that I can recover the data?

---

### Post by taurus on 2007-12-11
What happens if you mount it with ntfs-3g driver?

```
sudo apt-get update
sudo apt-get install ntfs-3g
sudo mkdir /media/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
df -h
```

---

### Post by Gouz on 2007-12-11
the output is 


```
:~$ sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
```

---

### Post by taurus on 2007-12-11
Can you post 

```
sudo fdisk -l
```

---

### Post by Gouz on 2007-12-11
```


Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb9ac557a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       10100    81128218+  86  NTFS volume set
/dev/sdb2           10101       20200    81128250   86  NTFS volume set
/dev/sdb3           20201       30401    81939532+  86  NTFS volume set

```[/CODE]

---

