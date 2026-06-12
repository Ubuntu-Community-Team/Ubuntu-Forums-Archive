---
title: "fdisk problems"
date: 2009-06-16
forum: Installation &amp; Upgrades
---

### Post by koiril on 2009-06-16
I've been been trying with no avail to setup a RAID 5 array using mdadm. I'm semi new to the whole linux scene by the way. Here's how the story goes:

I downloaded Ubuntu Server edition and installed it on my PC with no problems but before doing that I first setup my ASUS P5Q Pro motherboard's raid in RAID 5. Once everything was installed I booted up Linux and ran the usual upgrades/updates. Once all that was done I installed mdadm; fdisk'ed 3 1TB drives (sda,sdb,sdc) to each have 1 partition of type 'fd'; then used the following command to create my array:
 
     ```
sudo mdadm -Cvf /dev/md0 -l5 -n3 -c64 /dev/sd{a,b,c}1 
```Beautiful! Everything worked perfectly.

So, now that I have the array up and running I make sure to edit /etc/mdadm/mdadm.conf so that it knows I have an array using this:
 
     ```
sudo mdadm --detail --scan --verbose > /etc/mdadm/mdadm.conf 
```That works fine as well.

Next I run mkfs.ntfs on /dev/md0 and put a new entry in 'fstab':
 
    ```
 /dev/md0      /storage     ntfs    defaults    0 0 
```After that I run 'mount -a' to mount it.

Now everything is mounted and working wonderfully but just to be sure I decided to reboot (and I'm glad I did). When the PC comes back online the drive is no longer mounted. Not only that /proc/mdstat has nothing in it. As well as /proc/partitions says I don't have any partitions on the drives I fdisk'ed yet fdisk -l says I do. Now I'll try to give you as much information as possible to hopefully solve my problem of my array not auto loading on boot.

 ```

     koiril@Sloth:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 9.04
Release:        9.04
Codename:       jaunty
koiril@Sloth:~$ 
     Code:
     koiril@Sloth:~$ sudo mdadm -A /dev/md0 /dev/sd{a,b,c}1
mdadm: cannot open device /dev/sda1: No such file or directory
mdadm: /dev/sda1 has no superblock - assembly aborted
koiril@Sloth:~$ 
     Code:
     koiril@Sloth:~$ cat /proc/partitions
major minor  #blocks  name

   8        0  976762584 sda
   8       16  976762584 sdb
   8       32  976762584 sdc
   8       48  312571224 sdd
   8       49  306608526 sdd1
   8       50          1 sdd2
   8       53    5960083 sdd5
koiril@Sloth:~$ 
```   ```
  koiril@Sloth:~$ sudo fdisk -l
[sudo] password for koiril:

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb308ff24

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x087acc0e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc7b9a7a7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x33e133e1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       38171   306608526   83  Linux
/dev/sdd2           38172       38913     5960115    5  Extended
/dev/sdd5           38172       38913     5960083+  82  Linux swap / Solaris
koiril@Sloth:~$ 
``` ```
    koiril@Sloth:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
unused devices: <none>
koiril@Sloth:~$
```

---

### Post by koiril on 2009-06-17
Just incase anyone is having the same problems, I fixed this by disabling the motherboard's RAID abilities and just using mdadm.

---

