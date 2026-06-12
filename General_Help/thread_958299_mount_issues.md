---
title: "mount issues"
date: 2008-10-25
forum: General Help
---

### Post by CasaSuprNova on 2008-10-25
hi,

installed ubuntu last night and still cant find a way to access my old files (hoping to leave xp this weekend).

sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe6d9e6d9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10942    87891583+  83  Linux
/dev/sda2           12749       60801   385985722+   b  W95 FAT32
/dev/sda3           10943       12748    14506695    5  Extended
/dev/sda5           10943       12748    14506663+  82  Linux swap / Solaris

Partition table entries are not in disk order
--

all my music and photos are in that fat32 partition (didnt touch it during installation). i have backup of that disc to an Iomaga firewire disc also, but my knowledge of linux at this point isnt any good.

--

sudo mount -t vfat /dev/sda2 /home/thomas/musikk/
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

--
someone on another forum suggested this for some reason (ye, im that noob):
sudo fsck /dev/sda2

fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sda2

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

---

and another one suggested that perhaps root was the owner of /dev/sda2, so i changed it:

before: 
ls -al sda2
brw-rw---- 1 root disk 8, 2 2008-10-25 11:50 sda2

sudo chown thomas sda2

after:
ls -al sda2
brw-rw---- 1 thomas disk 8, 2 2008-10-25 11:50 sda2

--

so, what i want to do is to be able to access my firewiredisc and my fat32-partition, and i would appretiate any help.

thanks-

---EDIT---

this is what testdisk says:

Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * Linux                    0   1  1 10941 254 63  175783167
check_FAT: Bad number of sectors per cluster
Invalid FAT boot sector
 2 P FAT32                12748   0  1 60800 254 63  771971445
 2 P FAT32                12748   0  1 60800 254 63  771971445
 3 E extended             10942   0  1 12747 254 63   29013390
 5 L Linux Swap           10942   1  1 12747 254 63   29013327

---

EDIT: Solved

"mount -t ntfs-3g /dev/sdb1 /some/path -o force" did the trick with the external firewire disk.

reformatted fat32 partition as linuxpartition, no problems. copying worls fine.

---

