---
title: "Another post about GRUB and Vista"
date: 2009-06-28
forum: Installation &amp; Upgrades
---

### Post by MathMonkeyMan on 2009-06-28
Hello everyone,[INDENT]I've done some careful searching but still am perplexed by this issue. I began with a Vista system. I installed Ubuntu. A year passed. Then, Vista went fubar. I reinstalled Vista. It works.

The problem is, of course, that Vista overwrote my boot setup. I no longer have the selection that allows me to boot Ubuntu 8.04 (which is my primary, albeit smaller, system).

I am (now) running Ubuntu live from a USB stick. None of the proposed solutions have worked: GRUB keeps giving me Error 22. Gparted does not recognize either of the partitions on my internal hard drive. I cannot mount either file system, and things seem a bit confused altogether. Here is the information anyone needs:

[/INDENT]```

grub> find /boot/grub/stage1
 (hd0,0)

grub> root (hd0,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,0)/boot/grub/stage2
/boot/grub/menu.lst"... failed

Error 22: No such partition

grub> 

``````

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
mount: /dev/sdb1 already mounted or sdb1 busy

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x18b39c9d

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    61,368,299    61,368,237  83 Linux
/dev/sda2     ?    61,368,300   234,438,526   173,070,227   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8086 MB, 8086618112 bytes
255 heads, 63 sectors/track, 983 cylinders, total 15794176 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x04dd5721

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    15,794,175    15,794,113   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/sdb1: LABEL="BOOT_STICK" UUID="244C-69C1" TYPE="vfat" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1


Unknown BootLoader  on sda2



=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory

``````

ubuntu@ubuntu:~/Desktop$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x18b39c9d

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3820    30684118+  83  Linux
/dev/sda2   ?        3821       14594    86535113+   7  HPFS/NTFS

Disk /dev/sdb: 8086 MB, 8086618112 bytes
255 heads, 63 sectors/track, 983 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04dd5721

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         984     7897056+   b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(982, 254, 63) logical=(983, 36, 13)
ubuntu@ubuntu:~/Desktop$ 

```I appreciate any input that could help me solve this irritating problem.

---

### Post by MathMonkeyMan on 2009-06-29
Well, I managed to circumvent the issue by modifying Vista's boot loader to have an option for Ubuntu's grub. Then all I had to do was set Ubuntu's grub timeout to zero, and all is well.
I imagine this might be problematic in the future, but it works legitimately. So consider this issue solved.

---

