---
title: "Error2 grub 1.5 in a upgrade"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by xosinho10 on 2009-05-07
Hi. 

I upgrade my system from 8.10 to 9.04, and the first time all were right. Then someone crashes and I have to turn off my laptop. 

Then, when the computer reboots, it gets me that error.

I try do that meierfra. wrotes in this post: [http://ubuntuforums.org/showthread.php?t=1135662](http://ubuntuforums.org/showthread.php?t=1135662) 

For the first solution I get an error, and try the second. 

This is my RESULTS.txt 

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xda762e97

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    62,910,539    62,910,477   7 HPFS/NTFS
/dev/sda2          62,910,540   122,913,314    60,002,775  83 Linux
/dev/sda3         122,913,315   123,411,329       498,015  82 Linux swap / Solaris
/dev/sda4         123,411,330   488,392,064   364,980,735   f W95 Ext d (LBA)
/dev/sda5         123,411,393   333,123,839   209,712,447   7 HPFS/NTFS
/dev/sda6         333,123,903   488,392,064   155,268,162   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="BA80E5D080E59365" TYPE="ntfs" 
/dev/sda2: UUID="cea056a9-ccb5-4c7e-a371-6d1f3e5739a2" TYPE="ext3" 
/dev/sda3: TYPE="swap" UUID="6972035c-eb88-4cd6-bee4-3dea8d0c6d89" 
/dev/sda5: UUID="9CCCC097CCC06D58" LABEL="AlmacM-in" TYPE="ntfs" 
/dev/sda6: UUID="6808D24908D215C2" LABEL="Garbage" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /mnt type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=================== sda1: Location of files loaded by Grub: ===================


   3.5GB: boot/grub/stage2
=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

Thanks for the help, and sorry about my poor english.

---

