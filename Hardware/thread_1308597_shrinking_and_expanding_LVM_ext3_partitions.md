---
title: "shrinking and expanding LVM ext3 partitions"
date: 2009-10-31
forum: Hardware
---

### Post by aresnick on 2009-10-31
Hi!  I'm trying to shrink my /home partition so that I can expand my usr, root, and var partitions (I'm running out of space while using apt-get, and in general, they're unreasonably small).  I've Googled for a while, and am still pretty confused about how to do this, and what's safe.  I was hoping someone could help me out?  Here's some potentially pertinent info:

```

aresnick@dror:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/dror-root
                      322M  250M   56M  82% /
tmpfs                 1.9G     0  1.9G   0% /lib/init/rw
varrun                1.9G  348K  1.9G   1% /var/run
varlock               1.9G     0  1.9G   0% /var/lock
udev                  1.9G  176K  1.9G   1% /dev
tmpfs                 1.9G   84K  1.9G   1% /dev/shm
lrm                   1.9G  2.5M  1.9G   1% /lib/modules/2.6.28-15-generic/volatile
/dev/sda5             228M   29M  188M  14% /boot
/dev/mapper/dror-home
                      212G  117G   85G  59% /home
/dev/mapper/dror-tmp  368M   11M  339M   3% /tmp
/dev/mapper/dror-usr  5.5G  5.4G     0 100% /usr
/dev/mapper/dror-var  2.8G  548M  2.1G  21% /var
/dev/sdb1             7.4G  2.7G  4.7G  37% /media/disk

```

and then,

```

aresnick@dror:~$ sudo !!
sudo lvdisplay
[sudo] password for aresnick: 
  --- Logical volume ---
  LV Name                /dev/dror/root
  VG Name                dror
  LV UUID                R1mw77-NjHG-RS64-Txzc-vebQ-bl65-pvwPVb
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                332.00 MB
  Current LE             83
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0
   
  --- Logical volume ---
  LV Name                /dev/dror/usr
  VG Name                dror
  LV UUID                21l7XK-bYa6-JCFT-0Ghn-5PXM-9Oa0-ewf4sG
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                5.59 GB
  Current LE             1430
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1
   
  --- Logical volume ---
  LV Name                /dev/dror/var
  VG Name                dror
  LV UUID                KHxLUw-j4Hr-BR6J-3vU4-ejkd-tUke-ElRKdl
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                2.79 GB
  Current LE             715
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:2
   
  --- Logical volume ---
  LV Name                /dev/dror/swap_1
  VG Name                dror
  LV UUID                Rs5CiP-sfkc-ih8c-AYZx-IaZp-8DYQ-lKkr9H
  LV Write Access        read/write
  LV Status              available
  # open                 2
  LV Size                8.38 GB
  Current LE             2144
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:3
   
  --- Logical volume ---
  LV Name                /dev/dror/tmp
  VG Name                dror
  LV UUID                sUcFU8-tCqT-Ujej-cKyE-JcKr-89EN-XI5xCA
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                380.00 MB
  Current LE             95
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:4
   
  --- Logical volume ---
  LV Name                /dev/dror/home
  VG Name                dror
  LV UUID                CuK2Jc-ZXb6-7k2U-JXNe-RIYq-UXeZ-9DLsdM
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                215.20 GB
  Current LE             55090
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:5

```

As I understand it, I need to use a rescue CD/OS to resize the physical volumes, then the logical volumes, and then do something to get the journaling to work out?

My questions:
+ Is this even possible without data loss?

+ What rescue OS?  (gparted doesn't support ext3)

+ What do I do then? =)

---

### Post by aresnick on 2009-11-03
bump?  Any pointers would be appreciated (or if I'd be better off just backing up and reinstalling--let me know that, too)...

---

### Post by jshank on 2010-01-19
I'm not sure if it differs in ext3 vs ext4 but I was able to move some free space around by using the following commands:
```

$sudo lvresize -L-50m /dev/vg/varlib
Rounding up size to full physical extent 48.00 MB
  WARNING: Reducing active logical volume to 9.95 GB
  THIS MAY DESTROY YOUR DATA (filesystem etc.)
Do you really want to reduce varlib? [y/n]: y
  Reducing logical volume varlib to 9.95 GB
  Logical volume varlib successfully resized
$ sudo e2fsck -f /dev/vg/varlib
e2fsck 1.41.9 (22-Aug-2009)
/dev/vg/varlib: recovering journal
The filesystem size (according to the superblock) is 2621440 blocks
The physical size of the device is 2609152 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort<y>? no

Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/vg/varlib: 6438/655360 files (0.3% non-contiguous), 194200/2621440 blocks
$ sudo resize2fs /dev/vg/varlib
resize2fs 1.41.9 (22-Aug-2009)
Resizing the filesystem on /dev/vg/varlib to 2609152 (4k) blocks.
The filesystem on /dev/vg/varlib is now 2609152 blocks long.

$ echo Phew!
Phew!
```

Note that you can only shrink an unmounted device. You have to boot to a LiveCD/DVD/USB if you want to shrink the ext3/4 filesystem on a device you can't unmount. 

Resize2fs will only grow mounted systems, shrinking is a no-no.

---

