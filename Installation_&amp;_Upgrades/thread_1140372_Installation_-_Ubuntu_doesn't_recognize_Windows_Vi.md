---
title: "Installation - Ubuntu doesn't recognize Windows Vista presence"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by lefontiy on 2009-04-27
Hello everybody,

I'm new to Linux and I seek your help getting this problem resolved:
while trying to install Ubuntu 9.04 I'm asked to choose the partitioning method for the installation.
The problem is that Ubuntu installer **doesn't recognize Windows Vista presence** and I get only one option to use the entire drive for Ubuntu installation (installes says: _no operating found on this computer_, while I have Windows Vista installed on drive C:!)
I dont want to loose my Vista yet and make a dual booting mode...
I have drive C: with Vista, D: with stuff and in addition I've prepared 20GB of unallocated free space on my HDD for Ubuntu installation.
Maybe something wrong with the MBR? How do i make the installer "see" my currently installed operating system?

Thank you in advance,

[[COLOR=Green]update[/COLOR]]
after browsing a few related threads here is an output of
fdisk -lu
```
ubuntu@ubuntu:~$ sudo fdisk -lu
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x95f3457a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    12257279     6127616   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2        12257595    55279664    21511035    5  Extended
/dev/sda3        55281664   128952319    36835328    7  HPFS/NTFS
/dev/sda4       128953755   234436544    52741395    7  HPFS/NTFS
```sfdisk -d
```
ubuntu@ubuntu:~$ sudo sfdisk -d

sfdisk: ERROR: sector 12257595 does not have an msdos signature
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=     2048, size= 12255232, Id=27, bootable
/dev/sda2 : start= 12257595, size= 43022070, Id= 5
/dev/sda3 : start= 55281664, size= 73670656, Id= 7
/dev/sda4 : start=128953755, size=105482790, Id= 7
```

---

### Post by lefontiy on 2009-04-27
RESULTS.TXT:
```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x95f3457a

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    12,257,279    12,255,232  27 Hidden HPFS/NTFS
/dev/sda2          12,257,595    55,279,664    43,022,070   5 Extended
Invalid MBR Signature found
Empty Partition
/dev/sda3          55,281,664   128,952,319    73,670,656   7 HPFS/NTFS
/dev/sda4         128,953,755   234,436,544   105,482,790   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="52B876FEB876DFC1" LABEL="ServiceV002" TYPE="ntfs" 
/dev/sda3: UUID="8C501484501476E4" LABEL="Vista" TYPE="ntfs" 
/dev/sda4: UUID="01C7EA471A68C580" LABEL="Data" TYPE="ntfs" 

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
```

---

### Post by lefontiy on 2009-04-28
I'm getting frustrated trying to fix that... Does anybody have any suggestion?
Thanks

---

### Post by jncs12 on 2009-04-28
Hi,

Try the following:


[LIST=1]
[*]Startup your computer with Windows Vista CD/DVD;
[*]Choose your language;
[*]Select the option "**Repair Computer**";
[*]Select the option "**Command Prompt**";
[*]run: **bootrec.exe /FixMbr** ;
[*]"**exit**";
[*]"**Restart**".
[/LIST]
Any  feedback would be appreciate.

---

### Post by meierfra. on 2009-04-28
```
in addition I've prepared 20GB of unallocated free space on my HDD for Ubuntu installation.
```

Something went wrong when you prepared the unallocated space. The unallocated space sits inside an extended partition. But the partition table of that extended partition is messed up.  How did you create the unallocated space?  I suggested to delete the extended partition with whatever tool you used for partitioning.  If that does not work, try this from a terminal in the Ubuntu LiveCD


```
sudo fdisk /dev/sda
d
2
w
```

That should  erase your extended partition.

---

### Post by lefontiy on 2009-04-29
jncs12,
no success with that..

meierfra.,
after deleting that partition and recreating it again (i'm using Paragon partition manager) the installer successfully identified all OS on my laptop and now i'm enjoying my new Ubuntu!!!!
**THANK YOU!**

---

### Post by meierfra. on 2009-04-29
> now i'm enjoying my new Ubuntu!!!!

Great.

> now i'm enjoying my new Ubuntu!!!!

You are welcome.

---

