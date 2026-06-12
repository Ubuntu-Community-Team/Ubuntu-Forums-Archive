---
title: "nVidia RAID 0 with dmraid"
date: 2008-05-03
forum: Hardware
---

### Post by murrayju on 2008-05-03
I am having a problem getting dmraid to properly detect my nvidia RAID 0 partition.  I have two 320GB sata drives that currently have a windows ntfs partition on it, from which I need to access some data.  Here is what I have tried:

$ sudo dmraid -s
*** Active Set
name   : nvidia_fdfaeieg
size   : 1250284800
stride : 128
type   : stripe
status : ok
subsets: 0
devs   : 2
spares : 0

$ sudo dmraid -r
/dev/sdb: nvidia, "nvidia_fdfaeieg", stripe, ok, 625142446 sectors, data@ 0
/dev/sda: nvidia, "nvidia_fdfaeieg", stripe, ok, 625142446 sectors, data@ 0

$ sudo dmraid -ay
ERROR: dos: partition address past end of RAID device

$ ls -lah /dev/mapper
total 0
drwxr-xr-x  2 root root      80 2008-05-03 17:51 .
drwxr-xr-x 13 root root     15K 2008-05-03 17:51 ..
crw-rw----  1 root root  10, 63 2008-05-03 17:14 control
brw-rw----  1 root disk 254,  0 2008-05-03 17:51 nvidia_fdfaeieg

So the array gets activated (with an ERROR), and mapped, but the partitions do not. If I open gParted, nvidia_fdfaeieg shows up as the correct size and everything, but there are no partitions (all unallocated).  I am positive that the partition is there because I can still boot into windows from this array and see all of the data.  I am out of ideas.  Any help is greatly appreciated!

---

### Post by murrayju on 2008-05-03
Here is some more info gathered from fdisk:

$ sudo fdisk /dev/mapper/nvidia_fdfaeieg 

The number of cylinders for this disk is set to 77826.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/mapper/nvidia_fdfaeieg: 640.1 GB, 640145817600 bytes
255 heads, 63 sectors/track, 77826 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa0babe71

                      Device Boot      Start         End      Blocks   Id  System
/dev/mapper/nvidia_fdfaeieg1   *           1       77827   625144353+   7  HPFS/NTFS

Command (m for help): v
Total allocated sectors 1250288708 greater than the maximum 1250284800

so I tried:
$ sudo mount /dev/mapper/nvidia_fdfaeieg1 /media/windows
mount: special device /dev/mapper/nvidia_fdfaeieg1 does not exist

damn...

---

### Post by couillard45682 on 2008-11-12
Please someone, i a have the same problem. In gparted i can see the array and the right size with the fs type, but nothing else like the used space etc. I can't mount que device /dev/mapper/nvidia/dehebdee. i get this error message : 
**fuse: mount failed: Périphérique ou ressource occupé** (yeah i'm french)
I get the right message when i'm doing : 'dmraid -r'
[B]/dev/sdb: "via" and "nvidia" formats discovered (using nvidia)!
/dev/sdb: nvidia, "nvidia_dehebdee", stripe, ok, 156249998 sectors, data@ 0
/dev/sda: nvidia, "nvidia_dehebdee", stripe, ok, 156249998 sectors, data@ 0[/B]
Thanks for the help ):P

---

