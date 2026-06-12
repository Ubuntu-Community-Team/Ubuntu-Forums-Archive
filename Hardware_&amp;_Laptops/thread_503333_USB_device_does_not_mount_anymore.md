---
title: "USB device does not mount anymore"
date: 2007-07-17
forum: Hardware &amp; Laptops
---

### Post by foxy123 on 2007-07-17
I've got a problem unmounting my SE k750i mobile phone and after that it stopped mounting at all. I can mount it on Windows though not straight away: I have to plug it in, swtch off and then switch on.

In Ubuntu I've got the following:
```
~$ dmesg | tail
[ 2173.675000] sdb : sense not available. 
[ 2173.676000] sdb: Write Protect is off
[ 2173.676000] sdb: Mode Sense: 00 00 00 00
[ 2173.676000] sdb: assuming drive cache: write through
[ 2173.676000] sdb : READ CAPACITY failed.
[ 2173.676000] sdb : status=0, message=00, host=1, driver=00 
[ 2173.676000] sdb : sense not available. 
[ 2173.677000] sdb: Write Protect is off
[ 2173.677000] sdb: Mode Sense: 00 00 00 00
[ 2173.677000] sdb: assuming drive cache: write through

```

```
~$ fsck.vfat /dev/sdb
fsck.vfat /dev/sdb
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Got 0 bytes instead of 512 at 0

```

And if I try to boot with he phone plugged in, I've got:

```
Buffer I/O error on device sdb, logical block 0
```

It looks that the device became corrupted, but I've got no idea how to repair it.

---

### Post by Ulysses361 on 2007-07-19
Hi,

I just had a similar problem today mounting my ipod in Ubuntu. Apparently, my ipod's filesystem was slightly corrupted. Here's how I solved my issue. It might help you out:

ulysses@desktop:/dev/disk/by-uuid$ sudo fsck.vfat /dev/dm-2
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Reclaimed 4 unused clusters (16384 bytes).
Free cluster summary wrong (292630 vs. really 292634)
1) Correct
2) Don't correct
? 1
Leaving file system unchanged.
/dev/dm-2: 560 files, 176346/468980 clusters

ulysses@desktop:/dev/disk/by-uuid$ sudo fsck.vfat --help
fsck.vfat: invalid option -- -
usage: fsck.vfat [-aAflrtvVwy] [-d path -d ...] [-u path -u ...]
               device
  -a       automatically repair the file system
  -A       toggle Atari file system format
  -d path  drop that file
  -f       salvage unused chains to files
  -l       list path names
  -n       no-op, check non-interactively without changing
  -r       interactively repair the file system
  -t       test for bad clusters
  -u path  try to undelete that (non-directory) file
  -v       verbose mode
  -V       perform a verification pass
  -w       write changes to disk immediately
  -y       same as -a, for compat with other *fsck
ulysses@desktop:/dev/disk/by-uuid$ sudo fsck.vfat -a /dev/dm-2
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Reclaimed 4 unused clusters (16384 bytes) in 4 chains.
Performing changes.
/dev/dm-2: 564 files, 176350/468980 clusters
ulysses@desktop:/dev/disk/by-uuid$ sudo fsck.vfat -a /dev/dm-2
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/dm-2: 564 files, 176350/468980 clusters

/dev/dm-2: 564 files, 176350/468980 clusters
ulysses@desktop:/dev/disk/by-uuid$ sudo dosfsck /dev/dm-2
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/dm-2: 564 files, 176350/468980 clusters

ulysses@desktop:/dev/disk/by-uuid$ sudo mount /dev/dm-2 /media/ipod/
ulysses@desktop:/dev/disk/by-uuid$ mount

...
/dev/dm-2 on /media/ipod type vfat (rw)

Also run the command "sudo fdisk -l" to check if fdisk can find your usb drive. Also try plugging in the USB cable from your phone into different USB ports on your pc.

If this does not help, then try a scandisk/chkdisk of the usb drive in Windows and then retry in Linux.

Regards,

Ulysses

---

