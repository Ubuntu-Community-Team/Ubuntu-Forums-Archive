---
title: "Seemingly Serious Complications With Upgrade to UbuntuStudio 14.04"
date: 2014-09-28
forum: Hardware
---

### Post by newsox2 on 2014-09-28
Hello thanks for your help. Had 13.04 Raring Ringtail running smooth on my system and loved it, but when I attempted to upgrade to 14.04 Trusty Tahr it left my system unable to install any OS.. Hope someone can help me thanks so much in advance..
 i have an error report ... 

 Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 31Jan2013]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of 
    /dev/mapper/isw_cheebaabbd_Lenovo_Raid.

isw_cheebaabbd_Lenovo_Raid1: ___________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

isw_cheebaabbd_Lenovo_Raid2: ___________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

isw_cheebaabbd_Lenovo_Raid5: ___________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: isw_cheebaabbd_Lenovo_Raid _____________________________________________________________________

Disk /dev/mapper/isw_cheebaabbd_Lenovo_Raid: 1000.2 GB, 1000210694144 bytes
255 heads, 63 sectors/track, 121602 cylinders, total 1953536512 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/isw_cheebaabbd_Lenovo_Raid1                512 1,928,460,799 1,928,460,288  83 Linux
/dev/mapper/isw_cheebaabbd_Lenovo_Raid2      1,928,461,310 1,953,536,511    25,075,202   5 Extended
/dev/mapper/isw_cheebaabbd_Lenovo_Raid5      1,928,461,312 1,953,536,511    25,075,200  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda                                                isw_raid_member 
/dev/sdb                                                isw_raid_member 
/dev/sr0                                                iso9660    Boot-Repair-Disk 64bit

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
isw_cheebaabbd_Lenovo_Raid
isw_cheebaabbd_Lenovo_Raid1
isw_cheebaabbd_Lenovo_Raid2
isw_cheebaabbd_Lenovo_Raid5

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on isw_cheebaabbd_Lenovo_Raid2

00000000  75 62 75 6e 74 75 31 0a  32 30 31 34 2d 30 37 2d  |ubuntu1.2014-07-|
00000010  32 32 20 32 32 3a 35 31  3a 32 37 20 73 74 61 74  |22 22:51:27 stat|
00000020  75 73 20 69 6e 73 74 61  6c 6c 65 64 20 6c 69 62  |us installed lib|
00000030  65 78 70 61 74 31 3a 61  6d 64 36 34 20 32 2e 31  |expat1:amd64 2.1|
00000040  2e 30 2d 34 75 62 75 6e  74 75 31 0a 32 30 31 34  |.0-4ubuntu1.2014|
00000050  2d 30 37 2d 32 32 20 32  32 3a 35 31 3a 32 37 20  |-07-22 22:51:27 |
00000060  63 6f 6e 66 69 67 75 72  65 20 6c 69 62 6c 6f 63  |configure libloc|
00000070  6b 66 69 6c 65 2d 62 69  6e 3a 61 6d 64 36 34 20  |kfile-bin:amd64 |
00000080  31 2e 30 39 2d 36 75 62  75 6e 74 75 31 20 3c 6e  |1.09-6ubuntu1 <n|
00000090  6f 6e 65 3e 0a 32 30 31  34 2d 30 37 2d 32 32 20  |one>.2014-07-22 |
000000a0  32 32 3a 35 31 3a 32 37  20 73 74 61 74 75 73 20  |22:51:27 status |
000000b0  75 6e 70 61 63 6b 65 64  20 6c 69 62 6c 6f 63 6b  |unpacked liblock|
000000c0  66 69 6c 65 2d 62 69 6e  3a 61 6d 64 36 34 20 31  |file-bin:amd64 1|
000000d0  2e 30 39 2d 36 75 62 75  6e 74 75 31 0a 32 30 31  |.09-6ubuntu1.201|
000000e0  34 2d 30 37 2d 32 32 20  32 32 3a 35 31 3a 32 37  |4-07-22 22:51:27|
000000f0  20 73 74 61 74 75 73 20  68 61 6c 66 2d 63 6f 6e  | status half-con|
00000100  66 69 67 75 72 65 64 20  6c 69 62 6c 6f 63 6b 66  |figured liblockf|
00000110  69 6c 65 2d 62 69 6e 3a  61 6d 64 36 34 20 31 2e  |ile-bin:amd64 1.|
00000120  30 39 2d 36 75 62 75 6e  74 75 31 0a 32 30 31 34  |09-6ubuntu1.2014|
00000130  2d 30 37 2d 32 32 20 32  32 3a 35 31 3a 32 37 20  |-07-22 22:51:27 |
00000140  73 74 61 74 75 73 20 69  6e 73 74 61 6c 6c 65 64  |status installed|
00000150  20 6c 69 62 6c 6f 63 6b  66 69 6c 65 2d 62 69 6e  | liblockfile-bin|
00000160  3a 61 6d 64 36 34 20 31  2e 30 39 2d 36 75 62 75  |:amd64 1.09-6ubu|
00000170  6e 74 75 31 0a 32 30 31  34 2d 30 37 2d 32 32 20  |ntu1.2014-07-22 |
00000180  32 32 3a 35 31 3a 32 37  20 63 6f 6e 66 69 67 75  |22:51:27 configu|
00000190  72 65 20 6c 69 62 6e 65  77 74 30 2e 35 32 3a 61  |re libnewt0.52:a|
000001a0  6d 64 36 34 20 30 2e 35  32 2e 31 35 2d 32 75 62  |md64 0.52.15-2ub|
000001b0  75 6e 74 75 35 20 3c 6e  6f 6e 65 3e 0a 32 00 fe  |untu5 <none>.2..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 9e 7e 01 00 00  |............~...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd 

=============================== StdErr Messages: ===============================

ERROR: ddf1: seeking device "/dev/dm-2" to 18446744073709421056
ERROR: hpt37x: seeking device "/dev/dm-2" to 4608
ERROR: hpt45x: seeking device "/dev/dm-2" to 18446744073709547008
ERROR: isw: seeking device "/dev/dm-2" to 18446744073708469760
ERROR: sil: seeking device "/dev/dm-2" to 18446744073709289984
ERROR: ddf1: seeking device "/dev/dm-2" to 18446744073709421056
ERROR: hpt37x: seeking device "/dev/dm-2" to 4608
ERROR: hpt45x: seeking device "/dev/dm-2" to 18446744073709547008
ERROR: isw: seeking device "/dev/dm-2" to 18446744073708469760
ERROR: sil: seeking device "/dev/dm-2" to 18446744073709289984
ERROR: ddf1: seeking device "/dev/dm-2" to 18446744073709421056
ERROR: hpt37x: seeking device "/dev/dm-2" to 4608
ERROR: hpt45x: seeking device "/dev/dm-2" to 18446744073709547008
ERROR: isw: seeking device "/dev/dm-2" to 18446744073708469760
ERROR: sil: seeking device "/dev/dm-2" to 18446744073709289984
File descriptor 8 (/proc/3008/mounts) leaked on lvscan invocation. Parent PID 8303: bash
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-repair 2014-09-27__03h38 ===================
boot-repair version : 3.198~ppa16~raring
boot-sav version : 3.198~ppa16~raring
glade2script version : 3.2.2~ppa45~raring
boot-sav-extra version : 3.198~ppa16~raring

BLKID BEFORE RAID ACTIVATION:
/dev/loop0: TYPE="squashfs"
/dev/sr0: LABEL="Boot-Repair-Disk 64bit" TYPE="iso9660"
/dev/sda: TYPE="isw_raid_member"
/dev/sdb: TYPE="isw_raid_member"
ERROR: ddf1: seeking device "/dev/dm-2" to 18446744073709421056
ERROR: hpt37x: seeking device "/dev/dm-2" to 4608
ERROR: hpt45x: seeking device "/dev/dm-2" to 18446744073709547008
ERROR: isw: seeking device "/dev/dm-2" to 18446744073708469760
ERROR: sil: seeking device "/dev/dm-2" to 18446744073709289984
dmraid -si -c:
dmraid -ay:
ERROR: ddf1: seeking device "/dev/dm-2" to 18446744073709421056
ERROR: hpt37x: seeking device "/dev/dm-2" to 4608
ERROR: hpt45x: seeking device "/dev/dm-2" to 18446744073709547008
ERROR: isw: seeking device "/dev/dm-2" to 18446744073708469760
ERROR: sil: seeking device "/dev/dm-2" to 18446744073709289984
RAID set "isw_cheebaabbd_Lenovo_Raid" already active
RAID set "isw_cheebaabbd_Lenovo_Raid1" already active
RAID set "isw_cheebaabbd_Lenovo_Raid5" already active
ERROR: ddf1: seeking device "/dev/dm-2" to 18446744073709421056
ERROR: hpt37x: seeking device "/dev/dm-2" to 4608
ERROR: hpt45x: seeking device "/dev/dm-2" to 18446744073709547008
ERROR: isw: seeking device "/dev/dm-2" to 18446744073708469760
ERROR: sil: seeking device "/dev/dm-2" to 18446744073709289984
dmraid -sa -c: isw_cheebaabbd_Lenovo_Raid
ERROR: ddf1: seeking device "/dev/dm-2" to 18446744073709421056
ERROR: hpt37x: seeking device "/dev/dm-2" to 4608
ERROR: hpt45x: seeking device "/dev/dm-2" to 18446744073709547008
ERROR: isw: seeking device "/dev/dm-2" to 18446744073708469760
ERROR: sil: seeking device "/dev/dm-2" to 18446744073709289984
File descriptor 8 (/proc/3008/mounts) leaked on lvs invocation. Parent PID 4578: /bin/sh
No volume groups found
boot-repair is executed in live-session (Boot-Repair-Disk 64bit 24avr2013, raring, Ubuntu, x86_64)
ls: cannot access /home/usr/.config: No such file or directory
CPU op-mode(s):        32-bit, 64-bit
file=/cdrom/preseed/lubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --
Disk /dev/sda doesn't contain a valid partition table
fdisk: unable to seek on /dev/sdb: Invalid argument

=================== os-prober:


=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sr0: LABEL="Boot-Repair-Disk 64bit" TYPE="iso9660"
/dev/sda: TYPE="isw_raid_member"
/dev/sdb: TYPE="isw_raid_member"


sfdisk: ERROR: sector 0 does not have an msdos signature
/dev/sda: unrecognized partition table type
No partitions found
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
lseek: Invalid argument

sfdisk: seek error on /dev/sdb - cannot seek to 1928461310
Disk /dev/sda doesn't contain a valid partition table
Disk /dev/sda doesn't contain a valid partition table
=================== UEFI/Legacy mode:
This live-session is not in EFI-mode.
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    no-os,    2048 sectors * 512 bytes
sdb    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    no-os,    2048 sectors * 512 bytes


=================== parted -l:


                                                                          
Error: /dev/sda: unrecognised disk label


                                                                          
Error: Can't have a partition outside the disk!


                                                                          
Error: /dev/mapper/isw_cheebaabbd_Lenovo_Raid1: unrecognised disk label


                                                                          
Error: /dev/mapper/isw_cheebaabbd_Lenovo_Raid5: unrecognised disk label


                                                                          
Error: Can't have a partition outside the disk!

Model: Linux device-mapper (striped) (dm)
Disk /dev/mapper/isw_cheebaabbd_Lenovo_Raid: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start  End     Size    Type      File system  Flags
1      262kB  987GB   987GB   primary
2      987GB  1000GB  12.8GB  extended
5      987GB  1000GB  12.8GB  logical



                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: /dev/sr0: unrecognised disk label

=================== parted -lm:


                                                                          
Error: /dev/sda: unrecognised disk label


                                                                          
Error: Can't have a partition outside the disk!


                                                                          
Error: /dev/mapper/isw_cheebaabbd_Lenovo_Raid1: unrecognised disk label


                                                                          
Error: /dev/mapper/isw_cheebaabbd_Lenovo_Raid5: unrecognised disk label


                                                                          
Error: Can't have a partition outside the disk!

BYT;
/dev/mapper/isw_cheebaabbd_Lenovo_Raid:1000GB:dm:512:4096:msdos:Linux device-mapper (striped);
1:262kB:987GB:987GB:::;
2:987GB:1000GB:12.8GB:::;
5:987GB:1000GB:12.8GB:::;


                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: /dev/sr0: unrecognised disk label


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
gvfsd-fuse on /run/user/lubuntu/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=lubuntu)


=================== ls:
/sys/block/dm-0 (filtered):  alignment_offset bdi capability dev discard_alignment dm ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/dm-1 (filtered):  alignment_offset bdi capability dev discard_alignment dm ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/dm-2 (filtered):  alignment_offset bdi capability dev discard_alignment dm ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/dm-3 (filtered):  alignment_offset bdi capability dev discard_alignment dm ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdc (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdd (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  alarm ashmem autofs binder block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency disk dm-0 dm-1 dm-2 dm-3 dri dvd dvdrw ecryptfs fb0 fd full fuse hidraw0 hidraw1 hidraw2 hpet input kmsg kvm log mapper mcelog mei mem net network_latency network_throughput null oldmem port ppp psaux ptmx pts random rfkill rtc rtc0 sda sdb sdc sdd sg0 sg1 sg2 sg3 sg4 shm snapshot snd sr0 stderr stdin stdout uinput urandom vga_arbiter vhost-net zero
ls /dev/mapper:  control isw_cheebaabbd_Lenovo_Raid isw_cheebaabbd_Lenovo_Raid1 isw_cheebaabbd_Lenovo_Raid2 isw_cheebaabbd_Lenovo_Raid5
Disk /dev/sda doesn't contain a valid partition table
fdisk: unable to seek on /dev/sdb: Invalid argument

=================== df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  5.9G   21M  5.9G   1% /
udev           devtmpfs   5.9G   12K  5.9G   1% /dev
tmpfs          tmpfs      1.2G  828K  1.2G   1% /run
/dev/sr0       iso9660    508M  508M     0 100% /cdrom
/dev/loop0     squashfs   435M  435M     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs      5.9G  8.0K  5.9G   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs      5.9G     0  5.9G   0% /run/shm
none           tmpfs      100M   12K  100M   1% /run/user

=================== fdisk -l:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


Error: no partitions
Partition outside the disk detected.

=================== Default settings
Recommended-Repair
This setting would reinstall the  of .
Additional repair would be performed:  repair-filesystems

=================== Settings chosen by the user
Boot-Info
This setting will not act on the MBR.



No change has been performed on your computer.

---

### Post by newsox2 on 2014-10-05
hello i am still stuck on this issue any ideas or feedback would be greatly appreciated! thanks

---

### Post by Vladlenin5000 on 2014-10-05
Hi, welcome.

Unfortunately the feedback isn't good news: Your current version is EoL since a long time ago and you're not getting security updates either. 13.04 is unsupported even for updates.
Please install a currently supported version like 14.04 of UbuntuStudio. You can also boot from a live DVD/USB, start the installation process and select upgrade when offered. Either way, from scratch or force-attempting the upgrade with live media, make sure you have a **backup**. You may need to reinstall some programs; the upgrade should keep all your files and settings but it should always be considered a risk procedure, so... [B]First of all, backup!

[/B]PS - Good luck. By the way, did I already mentioned you need a **backup**? Here's a reminder anyway: **BACKUP**

---

### Post by grahammechanical on 2014-10-05
I do not read very long posts. I do read Boot Repair reports that are linked to by a pastbin URL because the report opens in another browser window and I can switch back and forward between the forum post and the Boot Repair report. This is why I did not respond to your post when you first posted it. Just so you know. For next time.

I also tend to look mostly at the top and bottom of Boot Repair reports as I am baffled by most of what is printed there. In the case of your machine the report says that Grub was not installed into the MBR. The report also said that you did not accept the recommended repair being offered by Boot Repair. So nothing was changed.

Boot Repair cannot repair without our agreement. There you go.

Regards.

---

