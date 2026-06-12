---
title: "Error 15 When Attempting to Boot 9.04 (32 bit)"
date: 2009-06-27
forum: Installation &amp; Upgrades
---

### Post by Erik Anderson on 2009-06-27
Hello to all,

I'm trying to boot up Ubuntu 9.04 on an external Seagate Free Agent Desktop Drive.  I've tried using EasyBCD2.0 Beta 63 and have not had success.  My install always fails at the point near the end when it says 'Executing grub-install (hd0) failed.  Fatal Error' and eventually boots into the Live version of Ubuntu.

I saw some notes to run a script called boot_info_script.  So I'm attaching the output here in hopes someone can help me set up this machine so I can dual boot Vista (on hd0) and Ubuntu 9.04 in its own partition on hd1.

What I think I was installing was: 
/dev/sda = Vista64

on SCSI7 (0,0,0) (the external USB Free Agent Drive)
/dev/sdb2 = /
/dev/sdb5 = /boot
/dev/sdb6 = /usr
/dev/sdb7 = /tmp
/dev/sdb8 = /home
/dev/sdb9 = /usr/local
/dev/sdb10 = swap

And they're visible as Media in my File Browser

```

============================= Boot Info Summary: ==============================

 => HP/Gateway is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /NST/menu.lst /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /etc/fstab

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb9: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _________________________________________________
____

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1549f232

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 1,436,966,054 1,436,965,992   7 HPFS/NTFS
/dev/sda2       1,436,966,055 1,465,144,064    28,178,010   7 HPFS/NTFS


Drive: sdb ___________________ _________________________________________________
____

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9e6ec85e

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 2,637,423,358 2,637,423,296   7 HPFS/NTFS
/dev/sdb2       2,637,424,640 2,832,737,139   195,312,500  83 Linux
/dev/sdb3       2,832,741,450 2,930,272,064    97,530,615   5 Extended
/dev/sdb5       2,832,741,513 2,833,127,009       385,497  83 Linux
/dev/sdb6       2,833,127,073 2,873,128,859    40,001,787  83 Linux
/dev/sdb7       2,873,128,923 2,882,896,379     9,767,457  83 Linux
/dev/sdb8       2,882,896,443 2,898,897,119    16,000,677  83 Linux
/dev/sdb9       2,898,897,183 2,906,270,954     7,373,772  83 Linux
/dev/sdb10      2,906,271,018 2,930,272,064    24,001,047  82 Linux swap / Solar
is


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="9E8A155A8A15306F" LABEL="HP" TYPE="ntfs" 
/dev/sda2: UUID="949CA48C9CA46A86" LABEL="FACTORY_IMAGE" TYPE="ntfs" 
/dev/sdb1: UUID="B4C4B099C4B05EF4" LABEL="FreeAgent Drive" TYPE="ntfs" 
/dev/sdb2: UUID="5f6951aa-5179-440a-9aa0-1c1466d885c9" TYPE="ext3" 
/dev/sdb5: UUID="a104c616-ed09-4db1-82eb-5a67a74d5f46" TYPE="ext3" 
/dev/sdb6: UUID="e06be856-5a1f-48fb-a9b3-544ff3a3f88b" TYPE="ext3" 
/dev/sdb7: UUID="0ab31bad-6c16-4805-8afb-c6eb2b4a04ba" TYPE="ext3" 
/dev/sdb8: UUID="f4f739f0-2ece-4137-9535-ceab59f9171d" TYPE="ext3" 
/dev/sdb9: UUID="3f9f24af-82fb-496d-9a04-084d69d1c718" TYPE="ext3" 
/dev/sdb10: UUID="f0dcc513-d836-4712-9b30-d921ea8cbb58" TYPE="swap" 

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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev
)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nod
ev,user=ubuntu)
/dev/sdb1 on /media/FreeAgent Drive type fuseblk (rw,nosuid,nodev,allow_other,bl
ksize=4096)
/dev/sdb9 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sdb6 on /media/disk-1 type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sdb7 on /media/disk-2 type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sdb8 on /media/disk-3 type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sdb2 on /media/disk-4 type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sdb5 on /media/disk-5 type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sdb5 on /mnt/root type ext3 (rw)


============================== sda1/NST/menu.lst: ==============================

# NeoSmart NeoGrub Bootloader Configuration File
#
# This is the NeoGrub configuration file, and should be located at C:\NST\menu.l
st
# Please see the EasyBCD Documentation for information on how to create/modify e
ntries:
# http://neosmart.net/wiki/display/EBCD/

timeout 0
default 0

title /boot/grub/menu.lst
fallback 1
find --set-root --ignore-floppies /boot/grub/menu.lst
configfile /boot/grub/menu.lst

title /grub/menu.lst
fallback 2
find --set-root --ignore-floppies /grub/menu.lst
configfile /grub/menu.lst

title /boot/grub.conf
find --set-root --ignore-floppies /boot/grub.conf
configfile /boot/grub.conf

# All your boot are belong to NeoSmart!
=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb2 during installation
UUID=5f6951aa-5179-440a-9aa0-1c1466d885c9 /               ext3    relatime,error
s=remount-ro 0       1
# /boot was on /dev/sdb5 during installation
UUID=a104c616-ed09-4db1-82eb-5a67a74d5f46 /boot           ext3    relatime      
  0       2
# /home was on /dev/sdb8 during installation
UUID=f4f739f0-2ece-4137-9535-ceab59f9171d /home           ext3    relatime      
  0       2
# /tmp was on /dev/sdb7 during installation
UUID=0ab31bad-6c16-4805-8afb-c6eb2b4a04ba /tmp            ext3    relatime      
  0       2
# /usr was on /dev/sdb6 during installation
UUID=e06be856-5a1f-48fb-a9b3-544ff3a3f88b /usr            ext3    relatime      
  0       2
# /usr/local was on /dev/sdb9 during installation
UUID=3f9f24af-82fb-496d-9a04-084d69d1c718 /usr/local      ext3    relatime      
  0       2
# swap was on /dev/sdb10 during installation
UUID=f0dcc513-d836-4712-9b30-d921ea8cbb58 none            swap    sw            
  0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


1450.5GB: grub/stage2
1450.3GB: initrd.img-2.6.28-11-generic
1450.3GB: vmlinuz-2.6.28-11-generic
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd 
=============================== StdErr Messages: ===============================

sed: can't read /media/disk/etc/issue: No such file or directory

```dev sdc and sdd are partitions on another external hard drive (I think) which I messed up earlier but for now have turned off 

With fingers crossed for good luck,
Erik

---

