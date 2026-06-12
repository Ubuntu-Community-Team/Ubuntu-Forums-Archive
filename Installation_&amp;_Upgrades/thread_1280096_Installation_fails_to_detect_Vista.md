---
title: "Installation fails to detect Vista"
date: 2009-10-01
forum: Installation &amp; Upgrades
---

### Post by johnjwaring on 2009-10-01
Hi, I'm trying to install Ubuntu 9.04 on my Dell XPS computer that already has Vista 64 bit (Home). I want to keep both OSs - the computer has a 2TB disk so there is plenty of room. I have shrunk the partition that has the Vista OS on it, and I have run the installation using a downloaded iso image on CD.

The problem is at the 'Prepare Disk space' stage, unfortunately I get the message "This computer has no operating systems on it" - I expected it to find Vista. I have seen a similar posting on this forum and the advice from one posting was to continue with the manual install. Is this recommended?

I've run the fdisk -l (below) and just as in the install the disk appears to be recognised as two separate disks /dev/sda 1000.2 GB and /dev/sdb 1000.2 GB. The partition (in Vista) containig the Vista OS is around 1.5 TB and the free disk space is 0.5 TB.

Any suggestions?

Thanks, 

John.

```

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No known boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Windows Vista
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x08000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 3,231,249,839 3,231,249,777   7 HPFS/NTFS

/dev/sda1 ends after the last sector of /dev/sda

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdb

00000000  b8 70 00 00 00 00 00 00  d2 70 00 00 00 00 00 00  |.p.......p......|
00000010  da 70 00 00 00 00 00 00  f6 70 00 00 00 00 00 00  |.p.......p......|
00000020  06 71 00 00 00 00 00 00  10 71 00 00 00 00 00 00  |.q.......q......|
00000030  24 71 00 00 00 00 00 00  3c 71 00 00 00 00 00 00  |$q......<q......|
00000040  00 00 00 00 00 00 00 00  46 71 00 00 00 00 00 00  |........Fq......|
00000050  5e 71 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |^q..............|
00000060  01 0f 06 00 0f 64 07 00  0f 34 06 00 0f 32 0b 70  |.....d...4...2.p|
00000070  01 04 01 00 04 42 00 00  01 14 08 00 14 64 08 00  |.....B.......d..|
00000080  14 54 07 00 14 34 06 00  14 32 10 70 01 14 08 00  |.T...4...2.p....|
00000090  14 64 0a 00 14 54 09 00  14 34 08 00 14 52 10 70  |.d...T...4...R.p|
000000a0  01 0f 06 00 0f 64 0f 00  0f 34 0e 00 0f b2 0b 70  |.....d...4.....p|
000000b0  01 1c 0c 00 1c 64 0d 00  1c 54 0c 00 1c 34 0a 00  |.....d...T...4..|
000000c0  1c 32 18 f0 16 e0 14 d0  12 c0 10 70 01 0a 04 00  |.2.........p....|
000000d0  0a 34 06 00 0a 32 06 70  01 0a 04 00 0a 34 08 00  |.4...2.p.....4..|
000000e0  0a 52 06 70 01 1a 0a 00  1a 34 11 00 1a 72 16 f0  |.R.p.....4...r..|
000000f0  14 e0 12 d0 10 c0 0e 70  0d 60 0c 50 01 1c 0c 00  |.......p.`.P....|
00000100  1c 64 10 00 1c 54 0f 00  1c 34 0e 00 1c 72 18 f0  |.d...T...4...r..|
00000110  16 e0 14 d0 12 c0 10 70  01 00 00 00 00 00 00 00  |.......p........|
00000120  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000130  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

---

### Post by lemming465 on 2009-10-03
You almost certainly have the [fakeraid]("https://help.ubuntu.com/community/FakeRaidHowto") problem.

---

### Post by johnjwaring on 2009-10-04
Thank you for your help. 
 
I've looked at the help page linked above. I will follow the instructions. and report back on this forum on what happens.

---

