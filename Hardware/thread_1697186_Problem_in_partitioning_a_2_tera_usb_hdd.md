---
title: "Problem in partitioning a 2 tera usb hdd"
date: 2011-02-28
forum: Hardware
---

### Post by mer0090 on 2011-02-28
Hi,

I have just bought a 2 tera Segate Sata external hard drive usb connected. 

I am not able to partition the disk, here is the error log of GPart:

GParted 0.6.2

Libparted 2.3
Format /dev/sdd1 as ntfs *00:00:39 * *( ERROR )
** * ***
calibrate /dev/sdd1 *00:00:00 * *( SUCCESS )
** * ***
path: /dev/sdd1
start: 63
end: 3907024064
size: 3907024002 (1.82 TiB)
set partition type on /dev/sdd1 *00:00:01 * *( SUCCESS )
** * ***
new partition type: ntfs
create new ntfs file system *00:00:38 * *( ERROR )
** * ***
mkntfs -Q -v -L "" /dev/sdd1
** * ***
Cluster size has been automatically set to 4096 bytes.
Creating NTFS volume structures.
Creating root directory (mft record 5)
Creating $MFT (mft record 0)
Creating $MFTMirr (mft record 1)
Creating $LogFile (mft record 2)
Creating $AttrDef (mft record 4)
Creating $Bitmap (mft record 6)
Error writing to /dev/sdd1: Input/output error.
Error writing non-resident attribute value.
Couldn't create $Bitmap: Input/output error

---

### Post by gradinaruvasile on 2011-02-28
Try formatting it as ext3 or 4.

---

### Post by mer0090 on 2011-02-28
I have just tried formatting in ext3 I got this error log from Gparted:

GParted 0.6.2

Libparted 2.3
Format /dev/sdd1 as ext3  00:06:14    ( ERROR )
     	
calibrate /dev/sdd1  00:00:00    ( SUCCESS )
     	
path: /dev/sdd1
start: 63
end: 3907024064
size: 3907024002 (1.82 TiB)
set partition type on /dev/sdd1  00:00:00    ( SUCCESS )
     	
new partition type: ext3
create new ext3 file system  00:06:14    ( ERROR )
     	
mkfs.ext3 -L "" /dev/sdd1
     	
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
122101760 inodes, 488378000 blocks
24418900 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
14905 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks:
32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968,
102400000, 214990848

Writing inode tables: done
mke2fs 1.41.12 (17-May-2010)
ext2fs_mkdir: Attempt to read block from filesystem resulted in short read while creating root dir

---

