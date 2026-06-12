---
title: "Grub BIG Problem"
date: 2009-03-14
forum: Installation &amp; Upgrades
---

### Post by G@B0 on 2009-03-14
Well this is my problem. I have Chakra(Arch) + Vista + Kubuntu. 
Previously I had the grub that Chakra installed at first, but then I installed Kubuntu so it write another grub. 

It was nice until by mistake I selected an entry from the grub that activated the Vista restore... I didn't make any change, I just cancel and went back to the grub, but it throw me an error 22. I went to the live cd and restore the grub as always but, it restore the chakra grub and not the latest grub, so I can't acces Kubuntu.

The thing is that the partition where Kubuntu is located is on a extended and it show like an unallocated file.
Here is my fdisk -l:
```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc3f39db3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1003     8054784   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *        1004       13828   103016812+   7  HPFS/NTFS
/dev/sda3           13829       19104    42379470   83  Linux
/dev/sda4           19105       24321    41905552+   5  Extended
/dev/sda5           24102       24321     1767118+  82  Linux swap / Solaris

```

I tried to mount but it doesn't. I just want to mount that partition so I can see kernel version, etc, to add it to the arch grub so I can access Kubuntu. Or install a new grub, but it seems impossible. 

Please help, I dont want to delete the Kubuntu partition after all the problems I had trying to update to KDE 4.2.1. If no one can help me today, then I'll reinstall Kubuntu.

Thx

---

### Post by unutbu on 2009-03-14
Perhaps follow these instructions to run boot_info_script.sh:
[http://ubuntuforums.org/showpost.php?p=6725571&postcount=3](http://ubuntuforums.org/showpost.php?p=6725571&postcount=3)

This will give us more information about your boot setup, and maybe where the problem lies.

---

### Post by G@B0 on 2009-03-14
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  [H[2J Arch Linux () ()
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc3f39db3

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    16,111,615    16,109,568  27 Hidden HPFS/NTFS
/dev/sda2    *     16,113,195   222,146,819   206,033,625   7 HPFS/NTFS
/dev/sda3         222,146,820   306,905,759    84,758,940  83 Linux
/dev/sda4         306,905,760   390,716,864    83,811,105   5 Extended
/dev/sda5         387,182,628   390,716,864     3,534,237  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="B008817A08814078" LABEL="Recovery" TYPE="ntfs" 
/dev/sda2: UUID="6618A14D18A11D55" LABEL="VISTA" TYPE="ntfs" 
/dev/sda3: UUID="ed4a957b-b273-4785-8699-0099bdace73a" TYPE="ext3" 
/dev/sda5: UUID="b875c348-d1eb-4121-89b2-2363c8c76c3b" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
/dev/sda3 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)


=========================== sda3/boot/grub/menu.lst: ===========================

# Config file for GRUB - The GNU GRand Unified Bootloader
# /boot/grub/menu.lst

# DEVICE NAME CONVERSIONS 
#
#  Linux           Grub
# -------------------------
#  /dev/fd0        (fd0)
#  /dev/sda        (hd0)
#  /dev/sdb2       (hd1,1)
#  /dev/sda3       (hd0,2)
#

#  FRAMEBUFFER RESOLUTION SETTINGS
#     +-------------------------------------------------+
#          | 640x480    800x600    1024x768   1280x1024
#      ----+--------------------------------------------
#      256 | 0x301=769  0x303=771  0x305=773   0x307=775
#      32K | 0x310=784  0x313=787  0x316=790   0x319=793
#      64K | 0x311=785  0x314=788  0x317=791   0x31A=794
#      16M | 0x312=786  0x315=789  0x318=792   0x31B=795
#     +-------------------------------------------------+
#  for more details and different resolutions see
#  http://wiki.archlinux.org/index.php/GRUB#Framebuffer_Resolution 

# general configuration:
timeout   5
default   0
color light-blue/black light-cyan/blue

# boot sections follow
# each is implicitly numbered from 0 in the order of appearance below
#
#
#-*


# (1) Windows
 
# (0) Arch Linux
title Arch Linux
root (hd0,2)
kernel /boot/vmlinuz26 root=/dev/disk/by-uuid/ed4a957b-b273-4785-8699-0099bdace73a ro
initrd /boot/kernel26.img
 
# (1) Arch Linux Fallback
title Arch Linux Fallback
root (hd0,2)
kernel /boot/vmlinuz26 root=/dev/disk/by-uuid/ed4a957b-b273-4785-8699-0099bdace73a ro
initrd /boot/kernel26-fallback.img

title  Ubuntu Grub Menu 1
root (hd0,0)
chainloader +1

title  Ubuntu Grub Menu2
root (hd0,1)
chainloader +1

title  Ubuntu Grub Menu3
root (hd0,2)
chainloader +1

title  Ubuntu Grub Menu4
root (hd0,3)
chainloader +1

title  Ubuntu Grub Menu5
root (hd0,4)
chainloader +1
=============================== sda3/etc/fstab: ===============================

# 
# /etc/fstab: static file system information
#
# <file system>        <dir>         <type>    <options>          <dump> <pass>
none                   /dev/pts      devpts    defaults            0      0
none                   /dev/shm      tmpfs     defaults            0      0


UUID=ed4a957b-b273-4785-8699-0099bdace73a / ext3 defaults 0 0
 

=================== sda3: Location of files loaded by Grub: ===================


 130.8GB: boot/grub/menu.lst
 130.8GB: boot/grub/stage2
 130.8GB: boot/vmlinuz26

```

---

### Post by unutbu on 2009-03-14
Note this in the RESULTS.txt file:

```
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    **Boot files/dirs:   /BOOTMGR /boot/bcd**
```

Particularly worrisome is the last line which says /BOOTMGR and /boot/bcd directories were found. This means that the Vista restore program not only changed the partition type, it also placed an ntfs filesystem in the partition and wrote at least two directories to this filesystem. 

Recovering your old Linux filesystem on sda1 may or may not be possible at this point. I am not sure. However, if you'd like to try, then I think the thing to do is to use testdisk.

See 
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Save_the_partition_table_or_search_for_more_partitions.3F](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Save_the_partition_table_or_search_for_more_partitions.3F)
for an example of how testdisk is used.

Then boot from the LiveCD, open a terminal and type

```
sudo apt-get install testdisk
sudo testdisk
```


Choose "No Log", select the hard drive, "Proceed", "Intel", "Analyse". Do the "Quick Search" and the "Deeper Search". This could take a while. You can use the up/down arrows to select the various partitions. Press "p" to see a directory listing. See if you can get a listing of your Linux filesystem on sda1. If you can, then follow the menu options to set that version of sda1 as a primary partition. Write the new partition table to disk. 

If you can find a Linux filesystem on sda1 but can not read any files in it, then you may need to go to the Advanced menu to find older superblocks. Follow these instructions to find the superblocks and then run fsck to try to repair the filesystem: 
[http://www.cgsecurity.org/wiki/Advanced_Find_EXT2_EXT3_Backup_SuperBlock](http://www.cgsecurity.org/wiki/Advanced_Find_EXT2_EXT3_Backup_SuperBlock)

If you are uncertain what to do, post the output of the screen that has the deeper search results.

Also, some might tell you the very first thing you should do is clone your entire sda1 partition using a tool like Partimage (see [http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page), [http://ubuntuforums.org/showthread.php?t=287522](http://ubuntuforums.org/showthread.php?t=287522)). Then do all your recovery work on the cloned copy of sda1. Indeed, this may increase your chances of success, since you can try many recovery techniques and never worsen your situation. However, since you mentioned you are willing to reinstall Kubuntu, I'm suggesting the testdisk option straight away.

---

### Post by G@B0 on 2009-03-14
Thanks unutbu. It seems that I will lose so much time doing this that reinstalling Kubuntu.

I'll reinstall Kubuntu. I appreciate your help and if it happens again, I'll use it.
unutbu

---

### Post by unutbu on 2009-03-14
Fair enough. I agree it is rather a lengthy process with no guarantee of success. Good luck and happy (K)ubunting.

---

