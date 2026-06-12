---
title: "mouting encrypted external USB hard drive"
date: 2014-09-09
forum: Hardware
---

### Post by bradhaack on 2014-09-09
xubuntu 14.04

I set up this encrypted external USB hard drive quite a while ago under ubuntu, switched to kde for a while (it worked there), now back to xubuntu.  Now I can't get it mounted.  It was mounted, but I was getting an error that said something like it was a read only device.  I checked all the permissions and they were rw.   In the process of debugging that I broke it further.  I'm not sure that I did anything other than unmount it, but now I can't even mount it.

Mounting from file manager give this:
```
Error mounting /dev/dm-2 at /media/brad/Maxtor-1: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/dm-2" "/media/brad/Maxtor-1"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/mapper/luks-2af249c9-2d65-47ac-8349-69e790353b5e,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
At the tail of the dmesg output is this:
```
[ 3909.306808] end_request: critical target error, dev sdb, sector 0
[ 3909.306830] JBD2: recovery failed
[ 3909.306836] EXT4-fs (dm-2): error loading journal
```

sudo mount /dev/sdb1 /media/Maxtor/ 
mount: unknown filesystem type 'crypto_LUKS'

The relevant output from fdisk -l:
```
Disk /dev/sdb: 100.3 GB, 100256292864 bytes
255 heads, 63 sectors/track, 12188 cylinders, total 195813072 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x78ab3edc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   195784154    97892046   83  Linux

Disk /dev/mapper/luks-2af249c9-2d65-47ac-8349-69e790353b5e: 100.2 GB, 100240926720 bytes
255 heads, 63 sectors/track, 12186 cylinders, total 195783060 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000
```

I also tried this
```
cryptsetup luksOpen /dev/sdb1 test
Enter passphrase for /dev/sdb1: 
Cannot use device /dev/sdb1 which is in use (already mapped or mounted)
```.
Hmmm, already mapped or mounted?

---

### Post by bradhaack on 2014-09-09
OK, I think I'm back to where I was before I munged it up, but it is still showing as a read only file system.
```
sudo mkdir /media/test
sudo cryptsetup luksOpen /dev/sdb1 test
```
this prompted for passwd & succeeded
But I still couldn't mount it:
```
sudo mount /dev/mapper/test /media/Maxtor-1/
dmesg | tail
[ 4752.344261] end_request: critical target error, dev sdb, sector 0
[ 4752.344306] JBD2: recovery failed
[ 4752.344313] EXT4-fs (dm-2): error loading journal
```
So...
```
sudo fsck -r /dev/mapper/test
fsck from util-linux 2.20.1
e2fsck 1.42.9 (4-Feb-2014)
Maxtor-1: recovering journal
Maxtor-1 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Maxtor-1: 183305/6119424 files (1.0% non-contiguous), 18605008/24472882 blocks
```
Now I can mount it
```
sudo mount /dev/mapper/test /media/Maxtor-1/
```
But it's read only
```
touch /media/Maxtor-1/Backup/junk
touch: cannot touch ‘/media/Maxtor-1/Backup/junk’: Read-only file system
```
```
dmesg | tail
[ 5157.728963] end_request: critical target error, dev sdb, sector 0
[ 5221.781554] end_request: critical target error, dev sdb, sector 0
[ 5221.784402] end_request: critical target error, dev sdb, sector 0
[ 5221.785633] end_request: critical target error, dev sdb, sector 0
[ 5496.623425] EXT4-fs (dm-2): mounted filesystem with ordered data mode. Opts: (null)
[ 5501.842413] end_request: critical target error, dev sdb, sector 0
[ 5501.843660] end_request: critical target error, dev sdb, sector 96732263
[ 5501.843671] Aborting journal on device dm-2-8.
[ 5649.778569] EXT4-fs error (device dm-2): ext4_journal_check_start:56: Detected aborted journal
[ 5649.778578] EXT4-fs (dm-2): Remounting filesystem read-only

```
I ran fsck again and got the same output.  Mounted it again, this time using sudo I was able to touch junk once, but only once, & now I'm getting the read only file system error again.  
Tried fsck again and is indicated that it fixed an error this time.
```
sudo fsck -r /dev/mapper/test
fsck from util-linux 2.20.1
e2fsck 1.42.9 (4-Feb-2014)
Maxtor-1: recovering journal
Maxtor-1 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Free inodes count wrong (5936119, counted=5936118).
Fix<y>? yes

Maxtor-1: ***** FILE SYSTEM WAS MODIFIED *****
Maxtor-1: 183306/6119424 files (1.0% non-contiguous), 18605008/24472882 blocks
```
But still showing read only.

Is this drive failed or is there something wacked about going from fedora to ubuntu?

---

