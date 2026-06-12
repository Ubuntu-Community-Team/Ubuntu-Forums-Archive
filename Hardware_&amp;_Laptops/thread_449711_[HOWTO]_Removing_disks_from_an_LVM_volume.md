---
title: "[HOWTO] Removing disks from an LVM volume"
date: 2007-05-20
forum: Hardware &amp; Laptops
---

### Post by busfahrer on 2007-05-20
[SIZE="5"]**Removing disks from an LVM volume**[/SIZE]

I recently came across the problem of removing a disk from a LVM setup that is currently in use by a volume group, and had to discover that that's a non-trivial problem, so I decided to write this little HowTo.
[I]Disclaimer: I assume you are familiar with the usual LVM terms like VG, LV, PV, LE and PE. If that is not the case, read the LVM HowTo at:
[http://tldp.org/HOWTO/LVM-HOWTO/](http://tldp.org/HOWTO/LVM-HOWTO/) [/i].

I will explain how to achieve our goal via a documented example.

Our test box has 3 harddisks sda, sdb and sdc, each 2 GB in size. 1 GB of sda is used for the root filesystem, and 350 MB of sda is used as swap. The rest of sda, and all of sdb and sdc is used for
one logical volume, called lv_home, inside a volume group called vg_home.
```

**vmtyan:~# df -h**
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             942M  441M  454M  50% /
tmpfs                  78M     0   78M   0% /lib/init/rw
udev                   10M   68K   10M   1% /dev
tmpfs                  78M     0   78M   0% /dev/shm
/dev/mapper/vg_home-lv_home
                      4.7G  139M  4.3G   4% /mnt/home
**vmtyan:~# vgscan**
  Reading all physical volumes.  This may take a while...
  Found volume group "vg_home" using metadata type lvm2
**vmtyan:~# lvscan**
  ACTIVE            '/dev/vg_home/lv_home' [4.73 GB] inherit
**vmtyan:~# pvscan**
  PV /dev/sda3   VG vg_home   lvm2 [752.00 MB / 0    free]
  PV /dev/sdb1   VG vg_home   lvm2 [2.00 GB / 0    free]
  PV /dev/sdc1   VG vg_home   lvm2 [2.00 GB / 0    free]
  Total: 3 [4.73 GB] / in use: 3 [4.73 GB] / in no VG: 0 [0   ]

```

Now we decided that we have to remove sdb1 from the setup.
As you can see there is one single filesystem (FS) mounted inside the LV that spans all of it.
First we have to make sure that the fs has enough free space to be able to tolerate the removal of one 2 GB disk. This is already the case in our setup, as you can see from df, only 139MB are in use.

Next, we have to shrink the filesystem to make it smaller by the amount of the size of the disk we want to remove, i.e. 2 GB in this case. To find out the correct amount, use df (without parameters) and then calculate with that, and then specify the amount in KB, like you will see in the following example).
This is not possible on an online (i.e. mounted) fs, so first we will have to unmount the fs. If the fs in question is your root fs, you will have to boot from a CD that contains the LVM tools as well, or something else. Just make sure the fs is offline during shrinking if you value your data.
The resize2fs tool will probably complain about the fs not being checked, so we follow its advice and run e2fsck on it prior to shrinking it:

```

**vmtyan:~# umount /mnt/home**
**vmtyan:~# resize2fs -p /dev/vg_home/lv_home 2781120k**
resize2fs 1.40-WIP (14-Nov-2006)
Please run 'e2fsck -f /dev/vg_home/lv_home' first.
**vmtyan:~# e2fsck -f /dev/vg_home/lv_home**
e2fsck 1.40-WIP (14-Nov-2006)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/vg_home/lv_home: 13/620160 files (7.7% non-contiguous), 54954/1239040 blocks
**vmtyan:~# resize2fs -p /dev/vg_home/lv_home 2781120k**
resize2fs 1.40-WIP (14-Nov-2006)
Resizing the filesystem on /dev/vg_home/lv_home to 695280 (4k) blocks.
Begin pass 3 (max = 38)
Scanning inode table          XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
The filesystem on /dev/vg_home/lv_home is now 695280 blocks long.

```

Next, we have to find out how many PE's sdb1 comprises:
```

**vmtyan:/# pvdisplay**
  --- Physical volume ---
  PV Name               /dev/sda3
  VG Name               vg_home
  PV Size               752.00 MB / not usable 0
  Allocatable           yes (but full)
  PE Size (KByte)       4096
  Total PE              188
  Free PE               0
  Allocated PE          188
  PV UUID               6jtA4q-UzY5-Cv3M-j2U6-4ant-mkEp-9QBHJG

  --- Physical volume ---
  PV Name               /dev/sdb1
  VG Name               vg_home
  PV Size               2.00 GB / not usable 0
  Allocatable           yes (but full)
  PE Size (KByte)       4096
  Total PE              511
  Free PE               0
  Allocated PE          511
  PV UUID               6ijjwO-iEhc-LRyd-0rFe-qJf3-sk57-4Q2hrk

  --- Physical volume ---
  PV Name               /dev/sdc1
  VG Name               vg_home
  PV Size               2.00 GB / not usable 0
  Allocatable           yes (but full)
  PE Size (KByte)       4096
  Total PE              511
  Free PE               0
  Allocated PE          511
  PV UUID               AGtht2-LoQR-zmpL-hsHr-PEsb-AmG5-Fhj5Rx

```

As we can see, sdb1 consists of 511 PE's.
Next, we will use lvreduce to shrink the LV. Pay special attention to the parameter -511 here, the minus sign indicates that we wish to shrink the LV **by** that amount, if we left the minus sign out, the LV's size would be **set** to 511 PE's.
Alternatively you can use the parameter -L to indicate the size in KB, MB or GB.
```

**vmtyan:/# lvreduce -l -511 /dev/vg_home/lv_home**
  WARNING: Reducing active logical volume to 2.73 GB
  THIS MAY DESTROY YOUR DATA (filesystem etc.)
Do you really want to reduce lv_home? [y/n]: y
  Reducing logical volume lv_home to 2.73 GB
  Logical volume lv_home successfully resized

```

We can use pvscan to check the new state:
```

**vmtyan:/# pvscan**
  PV /dev/sda3   VG vg_home   lvm2 [[COLOR="Blue"]752.00 MB / 752.00 MB free[/COLOR]]
  PV /dev/sdb1   VG vg_home   lvm2 [2.00 GB / 0    free]
  PV /dev/sdc1   VG vg_home   lvm2 [[COLOR="Blue"]2.00 GB / 1.26 GB free[/COLOR]]
  Total: 3 [4.73 GB] / in use: 3 [4.73 GB] / in no VG: 0 [0   ]

```
But wait, the space didn't get freed on sdb1, but on sda3 and sdc1 instead.

This is where the pvmove tool comes into play. (If at this point your harddisk shows as 100% free, i.e. 2.00 GB / 2.00 GB free in our example, you can skip the pvmove step).
On some distributions, we first have to load the dm-mirror module in order to get access to the mirroring capabilities of the kernel's device mapper that are used by the pvmove tool. (for example this was necessary on my Feisty box).
However, pvmove can only move PE's onto a **contiguous** space of the same size. This means for us that if we want to free all of sdb1's 511 PE's we have to free up 511 contiguous PE's. This is why we first have to use pvmove on sdc1, and not sdb1.
The -v and -i 10 parameters indicate that we want pvmove to periodically (every 10 secs) want it to inform us about the progress.
```

**vmtyan:/# modprobe dm-mirror**
**vmtyan:/# pvmove -v -i 10 /dev/sdc1**
    Wiping cache of LVM-capable devices
    Finding volume group "vg_home"
    Archiving volume group "vg_home" metadata (seqno 3).
    Creating logical volume pvmove0
    Moving 188 extents of logical volume vg_home/lv_home
    Found volume group "vg_home"
    Updating volume group metadata
    Creating volume group backup "/etc/lvm/backup/vg_home" (seqno 4).
    Found volume group "vg_home"
    Found volume group "vg_home"
    Suspending vg_home-lv_home (254:0)
    Found volume group "vg_home"
    Creating vg_home-pvmove0
    Loading vg_home-pvmove0 table
    Resuming vg_home-pvmove0 (254:1)
    Found volume group "vg_home"
    Loading vg_home-pvmove0 table
    Resuming vg_home-pvmove0 (254:1)
    Loading vg_home-lv_home table
    Resuming vg_home-lv_home (254:0)
    Checking progress every 10 seconds
  /dev/sdc1: Moved: 4.8%
- snip -  
  /dev/sdc1: Moved: 98.4%
  /dev/sdc1: Moved: 100.0%
    Found volume group "vg_home"
    Found volume group "vg_home"
    Loading vg_home-lv_home table
    Suspending vg_home-lv_home (254:0)
    Suspending vg_home-pvmove0 (254:1)
    Found volume group "vg_home"
    Found volume group "vg_home"
    Found volume group "vg_home"
    Resuming vg_home-pvmove0 (254:1)
    Found volume group "vg_home"
    Resuming vg_home-lv_home (254:0)
    Found volume group "vg_home"
    Removing vg_home-pvmove0 (254:1)
    Found volume group "vg_home"
    Removing temporary pvmove LV
    Writing out final volume group after pvmove
    Creating volume group backup "/etc/lvm/backup/vg_home" (seqno 6).

```

Use pvdisplay to check:
```

**vmtyan:/# pvdisplay**
  --- Physical volume ---
  PV Name               /dev/sda3
  VG Name               vg_home
  PV Size               752.00 MB / not usable 0
  Allocatable           yes (but full)
  PE Size (KByte)       4096
  Total PE              188
  Free PE               0
  Allocated PE          188
  PV UUID               6jtA4q-UzY5-Cv3M-j2U6-4ant-mkEp-9QBHJG

  --- Physical volume ---
  PV Name               /dev/sdb1
  VG Name               vg_home
  PV Size               2.00 GB / not usable 0
  Allocatable           yes (but full)
  PE Size (KByte)       4096
  Total PE              511
  Free PE               0
  Allocated PE          511
  PV UUID               6ijjwO-iEhc-LRyd-0rFe-qJf3-sk57-4Q2hrk

  --- Physical volume ---
  PV Name               /dev/sdc1
  VG Name               vg_home
  PV Size               2.00 GB / not usable 0
  Allocatable           yes
  PE Size (KByte)       4096
  Total PE              511
  Free PE               511
  Allocated PE          0
  PV UUID               AGtht2-LoQR-zmpL-hsHr-PEsb-AmG5-Fhj5Rx

```
As you can see, now we have 511 free PE's on sdc1, and that's enough contiguous space to hold sdb1's 511 PE's.

So now we can use pvmove to free up sdb1:
```

**vmtyan:/# pvmove -v -i 10 /dev/sdb1**
    Wiping cache of LVM-capable devices
    Finding volume group "vg_home"
    Archiving volume group "vg_home" metadata (seqno 6).
    Creating logical volume pvmove0
    Moving 511 extents of logical volume vg_home/lv_home
    Found volume group "vg_home"
    Updating volume group metadata
    Creating volume group backup "/etc/lvm/backup/vg_home" (seqno 7).
    Found volume group "vg_home"
    Found volume group "vg_home"
    Suspending vg_home-lv_home (254:0)
    Found volume group "vg_home"
    Creating vg_home-pvmove0
    Loading vg_home-pvmove0 table
    Resuming vg_home-pvmove0 (254:1)
    Found volume group "vg_home"
    Loading vg_home-pvmove0 table
    Resuming vg_home-pvmove0 (254:1)
    Loading vg_home-lv_home table
    Resuming vg_home-lv_home (254:0)
    Checking progress every 10 seconds
  /dev/sdb1: Moved: 1.8%
- snip -
  /dev/sdb1: Moved: 97.1%
  /dev/sdb1: Moved: 100.0%
    Found volume group "vg_home"
    Found volume group "vg_home"
    Loading vg_home-lv_home table
    Suspending vg_home-lv_home (254:0)
    Suspending vg_home-pvmove0 (254:1)
    Found volume group "vg_home"
    Found volume group "vg_home"
    Found volume group "vg_home"
    Resuming vg_home-pvmove0 (254:1)
    Found volume group "vg_home"
    Resuming vg_home-lv_home (254:0)
    Found volume group "vg_home"
    Removing vg_home-pvmove0 (254:1)
    Found volume group "vg_home"
    Removing temporary pvmove LV
    Writing out final volume group after pvmove
    Creating volume group backup "/etc/lvm/backup/vg_home" (seqno 9).

```

Check with pvdisplay:
```

**vmtyan:/# pvdisplay**
  --- Physical volume ---
  PV Name               /dev/sda3
  VG Name               vg_home
  PV Size               752.00 MB / not usable 0
  Allocatable           yes (but full)
  PE Size (KByte)       4096
  Total PE              188
  Free PE               0
  Allocated PE          188
  PV UUID               6jtA4q-UzY5-Cv3M-j2U6-4ant-mkEp-9QBHJG

  --- Physical volume ---
  PV Name               /dev/sdb1
  VG Name               vg_home
  PV Size               2.00 GB / not usable 0
  Allocatable           yes
  PE Size (KByte)       4096
  [COLOR="Blue"]Total PE              511[/COLOR]
  [COLOR="Blue"]Free PE               511[/COLOR]
  Allocated PE          0
  PV UUID               6ijjwO-iEhc-LRyd-0rFe-qJf3-sk57-4Q2hrk

  --- Physical volume ---
  PV Name               /dev/sdc1
  VG Name               vg_home
  PV Size               2.00 GB / not usable 0
  Allocatable           yes (but full)
  PE Size (KByte)       4096
  Total PE              511
  Free PE               0
  Allocated PE          511
  PV UUID               AGtht2-LoQR-zmpL-hsHr-PEsb-AmG5-Fhj5Rx

```
As we can see, all of sdb1's PE's are free now.

So now we can remove sdb1 from the VG:
```

**vmtyan:/# vgreduce vg_home /dev/sdb1**
  Removed "/dev/sdb1" from volume group "vg_home"
**vmtyan:/# pvscan**
  PV /dev/sda3   VG vg_home   lvm2 [752.00 MB / 0    free]
  PV /dev/sdc1   VG vg_home   lvm2 [2.00 GB / 0    free]
  [COLOR="Blue"]PV /dev/sdb1                lvm2 [2.00 GB][/COLOR]
  Total: 3 [4.73 GB] / in use: 2 [2.73 GB] / in no VG: 1 [2.00 GB]

```
As we can see, sdb1 does not longer belong to any VG.

For a proper cleanup, we will also remove the LVM label from sdb1:
```

**vmtyan:/# pvremove /dev/sdb1**
  Labels on physical volume "/dev/sdb1" successfully wiped
**vmtyan:/# pvscan**
  PV /dev/sda3   VG vg_home   lvm2 [752.00 MB / 0    free]
  PV /dev/sdc1   VG vg_home   lvm2 [2.00 GB / 0    free]
  Total: 2 [2.73 GB] / in use: 2 [2.73 GB] / in no VG: 0 [0   ]

```

Now we can mount our fs again, and verify that the data still is using the correct blocks, i.e. is intact.
For that purpose I did a md5 hash on one of my files before, which I can now check:
```

**vmtyan:/# mount /mnt/home**
**vmtyan:/# df -h**
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             942M  441M  454M  50% /
tmpfs                  78M     0   78M   0% /lib/init/rw
udev                   10M   68K   10M   1% /dev
tmpfs                  78M     0   78M   0% /dev/shm
/dev/mapper/vg_home-lv_home
                      2.7G  137M  2.4G   6% /mnt/home
**vmtyan:/# cd /mnt/home**
**vmtyan:/mnt/home# md5sum -c blob.md5**
blob: OK

```

I hope this helps a bit. If you still run into problems, I sometimes hang out on the Freenode IRC Network under the same nickname as I use here.

Greetings, busfahrer

---

