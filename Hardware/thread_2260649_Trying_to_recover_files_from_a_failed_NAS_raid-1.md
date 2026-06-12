---
title: "Trying to recover files from a failed NAS raid-1"
date: 2015-01-13
forum: Hardware
---

### Post by northern-link on 2015-01-13
I'm trying to recover files from a failed D-Link DNS-321. 

When I try to mount the drive I get the message: "mount: unknown filesystem type 'linux_raid_member' "

I tried following the directions listed:
[https://blog.sleeplessbeastie.eu/2012/05/08/how-to-mount-software-raid1-member-using-mdadm/](https://blog.sleeplessbeastie.eu/2012/05/08/how-to-mount-software-raid1-member-using-mdadm/)

After trying to mount the virtual device I get the output:
> wrong fs type, bad option, bad superblock on /dev/md9,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

dmesg reads:
> [606972.984421] md: md9 stopped.
[606972.984426] md: unbind<sde2>
[606973.000042] md: export_rdev(sde2)
[612331.088563] md: md9 stopped.
[612331.089194] md: bind<sde2>
[612331.091307] md/raid1:md9: active with 1 out of 2 mirrors
[612331.091350] md9: detected capacity change from 0 to 498221580288
[612331.092184]  md9: unknown partition table
[612466.617616] EXT4-fs (md9): mounting ext3 file system using the ext4 subsystem
[612466.617751] EXT4-fs (md9): bad geometry: block count 121636147 exceeds size of device (121636128 blocks)


I ran: file -s /dev/sde2 to confirm the drive type:
> /dev/sde2: Linux rev 1.0 ext3 filesystem data, UUID=111f568a-b08b-440a-9c43-2ac04367be93 (errors) (large files)


I tried mount -t with ext2, ext3, and ext4, each time the error was substantially the same:
> [612466.617616] EXT4-fs (md9): mounting ext3 file system using the ext4 subsystem
[612466.617751] EXT4-fs (md9): bad geometry: block count 121636147 exceeds size of device (121636128 blocks)
[613912.204594] EXT4-fs (md9): mounting ext3 file system using the ext4 subsystem
[613912.204738] EXT4-fs (md9): bad geometry: block count 121636147 exceeds size of device (121636128 blocks)
[614226.946017] EXT4-fs (md9): mounting ext3 file system using the ext4 subsystem
[614226.946167] EXT4-fs (md9): bad geometry: block count 121636147 exceeds size of device (121636128 blocks)
[614237.273397] EXT4-fs (md9): mounting ext2 file system using the ext4 subsystem
[614237.273517] EXT4-fs (md9): bad geometry: block count 121636147 exceeds size of device (121636128 blocks)
[614245.369678] EXT4-fs (md9): mounting ext2 file system using the ext4 subsystem
[614245.369805] EXT4-fs (md9): bad geometry: block count 121636147 exceeds size of device (121636128 blocks)

mdadm --examine yields:
             > Magic : a92b4efc
           Version : 0.90.00
              UUID : c580b924:23b04722:f0025da7:73d84b8d
  Creation Time : Tue Feb 15 01:24:27 2011
        Raid Level : raid1
  Used Dev Size : 486544512 (464.01 GiB 498.22 GB)
        Array Size : 486544512 (464.01 GiB 498.22 GB)
     Raid Devices : 2
    Total Devices : 1
 Preferred Minor : 0


     Update Time : Tue May  7 14:56:47 2013
                State : clean
   Active Devices : 1
Working Devices : 1
   Failed Devices : 1
   Spare Devices : 0
         Checksum : b23b7a0c - correct
              Events : 1077998




      Number   Major   Minor   RaidDevice State
this     0       8        2        0      active sync   /dev/sda2


   0     0       8        2        0      active sync   /dev/sda2
   1     1       0        0        1      faulty removed

I tried the slightly different instructions at:
[http://serverfault.com/questions/383362/mount-unknown-filesystem-type-linux-raid-member](http://serverfault.com/questions/383362/mount-unknown-filesystem-type-linux-raid-member)
and get the same issues on the terminal side. The main difference is that then a Raid Array shows up in Disks although under 'state' is says: "Array is Degraded - 1 disk is missing"

I get it seems like my block count is off, but how do I go about fixing that? Or is something else going on here?

Thanks for any help.

---

### Post by northern-link on 2015-02-02
Anybody?

---

