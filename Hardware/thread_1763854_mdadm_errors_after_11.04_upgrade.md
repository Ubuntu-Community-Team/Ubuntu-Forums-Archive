---
title: "mdadm errors after 11.04 upgrade"
date: 2011-05-20
forum: Hardware
---

### Post by PapaGoose on 2011-05-20
Hi all,

I have a media server that was running Ubuntu 10.10. It has 2 mdadm RAID devices, /dev/md0 (a 5 disk RAID-5 array) and /dev/md1 (a 2 disk RAID-0 array). This morning I upgraded to 11.04, and after rebooting /dev/md1 no longer works. The problem I'm having is very strange. The reason I can't assemble /dev/md1 is because the devices (/dev/sdg and /dev/sdh) are both busy...and the reason they are busy is because they are already part of an array! For some reason mdadm is creating /dev/md127 on boot, so the devices can't be added to the proper /dev/md1. 

Here is my /proc/mdstat

```

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : inactive md127p1[0](S)
      390708736 blocks
       
md127 : active (auto-read-only) raid1 sdh[1] sdg[0]
      390711296 blocks [2/2] [UU]
      
md0 : active raid5 sda1[4] sdb1[1] sdc1[3] sdd1[2] sde1[0]
      3907039744 blocks level 5, 64k chunk, algorithm 2 [5/5] [UUUUU]
      
unused devices: <none>

```

The output from mdadm --examine --scan is
```

ARRAY /dev/md0 UUID=aae1df8f:3e9ee100:47a9d36a:62411c8f
ARRAY /dev/md127 UUID=126b9468:2f301b90:36d5fed0:1a3e403e
ARRAY /dev/md1 UUID=7483240d:af0df3c9:47a9d36a:62411c8f
```
which I find strange because I've never seen /dev/md127 before. I can't stop the device
```

user@host:~$ sudo mdadm --stop /dev/md127
mdadm: failed to stop array /dev/md127: Device or resource busy
Perhaps a running process, mounted filesystem or active volume group?
```
I can see a partition on it with fdisk -l

```
Disk /dev/md127: 400.1 GB, 400088367104 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x32c24a1d

      Device Boot      Start         End      Blocks   Id  System
/dev/md127p1               1       48641   390708801   fd  Linux RAID autodetect

```

But I can't mount it (which I suppose is unsurprising since it is meant to be a RAID-0 array but /dev/md127 seems to be RAID-1)
```
user@host:~$ sudo mount /dev/md127p1 /test
mount: unknown filesystem type 'linux_raid_member'
```

Any ideas? I've also made sure dmraid is removed, and I added nodmraid to the kernel switches in /boot/grub/menu.lst. I just can't understand why the RAID0 device is having all this difficulty, while the RAID5 device worked fine straight away

---

### Post by Daxe on 2011-05-22
Similar issue here.

I was using a 6-disk raid5 array. The first time I rebooted after the  upgrade the raid array worked fine, but after that strange stuff  happened:
- cat /proc/mdstat reported only an inactive raid5 array named/dev/md127
- the old dev /dev/md/myraid has disappeared from the directory structure
- 1 of the 6 identical drives now reports a different size (2000397852160 bytes instead of 2000398934016)

I tried this:
- tried to stop the md127 array, but the system says it doesn't exist.
- the graphical disk utility reported the array and it could be stopped there.
- after that I could mdadm -A /dev/md/myraid, but one of the drives wasn't available (that's also the drive reporting the odd size)
  mdadm: failed to add /dev/sdg to /dev/md/myraid: Invalid argument 

How can I fix my array?

---

### Post by Abaddon on 2011-05-22
I'm not sure if my thread is a symptom of the same problem:

[Thread here.]("http://ubuntuforums.org/showthread.php?t=1761447")


```
$cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
unused devices: <none>

```


```
$ sudo mdadm --examine --scan
ARRAY metadata=imsm UUID=1e9bb89e:5ca91129:31f561c1:365cfae6
ARRAY /dev/md/RAID container=1e9bb89e:5ca91129:31f561c1:365cfae6 member=0 UUID=a8eadc8d:5db9da57:cc5ce116:b5c536a4

```


```
/dev/mapper$ ls
control  cryptswap1  isw_bgeiebgiac_RAID
$:/dev/mapper$ sudo mdadm --stop /dev/mapper/isw_bgeiebgiac_RAID 
mdadm: /dev/mapper/isw_bgeiebgiac_RAID does not appear to be an md device

```

Rather strangely, my RAID continues to work no worries in Windows 7.  I'm planning on reformatting one of the partitions so I can use it as a windows/ubuntu shared drive, but the other partition has got all my games installed; so I don't want to have to reformat it again :(

---

### Post by lolmaus on 2011-07-26
Ran into this issue. Tried everything with no luck. :(

So... Have you guys resolved it?

---

### Post by elcocoonline on 2011-09-23
Had the same problem. Managed to fix it in this thread: [http://ubuntuforums.org/showthread.php?t=1764861](http://ubuntuforums.org/showthread.php?t=1764861)

---

