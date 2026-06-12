---
title: "XP disappeared, unable to MOUNT"
date: 2009-09-07
forum: Installation &amp; Upgrades
---

### Post by gpushkar on 2009-09-07
I initially had windows XP installed on one partition and had a few other partitions on the same HDD. I installed UBUNTU on one of the partitions, but now Windows XP is gone. 

While GRUB shows, XP, upon selecting it it loops back to the menu. 

I m unable to mount the partition in UBUNTU also. ::

pushkar@pushkar-laptop:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4fa8a60b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4403    35359169+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            4403        5810    11302025    7  HPFS/NTFS
/dev/sda3            5811       13890    64902600    f  W95 Ext'd (LBA)
/dev/sda4           13891       14593     5646847+   7  HPFS/NTFS
/dev/sda5            6952        9502    20480000    7  HPFS/NTFS
/dev/sda6            9502       13890    35249152    7  HPFS/NTFS
/dev/sda7            5811        6896     8723232   83  Linux
/dev/sda8            6897        6951      441756   82  Linux swap / Solaris

pushkar@pushkar-laptop:~$ sudo mount /dev/sda1 /media/WinXP -t ntfs-3g
Unexpected clusters per mft record (-1).
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

How can I get the dual booting functionality back>??

---

### Post by presence1960 on 2009-09-08
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by gpushkar on 2009-09-08
Thanks presence1960. Here s the results: ( looks like i screwed up the grub install didnt i? )


```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda1 and 
                       looks at sector 104216752 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #7 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4fa8a60b

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    70,718,401    70,718,339   7 HPFS/NTFS
/dev/sda2          70,719,488    93,323,537    22,604,050   7 HPFS/NTFS
/dev/sda3          93,337,650   223,142,849   129,805,200   f W95 Ext d (LBA)
/dev/sda5         111,681,536   152,641,535    40,960,000   7 HPFS/NTFS
/dev/sda6         152,643,584   223,141,887    70,498,304   7 HPFS/NTFS
/dev/sda7          93,337,776   110,784,239    17,446,464  83 Linux
/dev/sda8         110,784,303   111,667,814       883,512  82 Linux swap / Solaris
/dev/sda4         223,142,850   234,436,544    11,293,695   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda2: UUID="B80CE4490CE403EA" TYPE="ntfs" 
/dev/sda4: UUID="2C88743C8874071C" LABEL="PRESARIO_RP" TYPE="ntfs" 
/dev/sda5: UUID="4236F0CD36F0C349" LABEL="songs" TYPE="ntfs" 
/dev/sda6: UUID="B254BE6A54BE3149" LABEL="stuff" TYPE="ntfs" 
/dev/sda7: UUID="03dc481b-3ddd-4804-bca4-660b12e6aa10" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda8: TYPE="swap" UUID="ffc3dbc9-9258-4cbe-b0cc-bf555cf33c2d" 
/dev/ramzswap0: TYPE="swap" 

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


=========================== sda7/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=03dc481b-3ddd-4804-bca4-660b12e6aa10 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=03dc481b-3ddd-4804-bca4-660b12e6aa10

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        03dc481b-3ddd-4804-bca4-660b12e6aa10
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=03dc481b-3ddd-4804-bca4-660b12e6aa10 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        03dc481b-3ddd-4804-bca4-660b12e6aa10
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=03dc481b-3ddd-4804-bca4-660b12e6aa10 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        03dc481b-3ddd-4804-bca4-660b12e6aa10
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows NT/2000/XP (loader)
root    (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title        Windows Vista (loader)
rootnoverify    (hd0,3)
savedefault
chainloader    +1


=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda7 :
UUID=03dc481b-3ddd-4804-bca4-660b12e6aa10 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda8 :
UUID=ffc3dbc9-9258-4cbe-b0cc-bf555cf33c2d none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

=================== sda7: Location of files loaded by Grub: ===================


  53.3GB: boot/grub/menu.lst
  53.3GB: boot/grub/stage2
  53.3GB: boot/initrd.img-2.6.28-11-generic
  53.3GB: boot/vmlinuz-2.6.28-11-generic
  53.3GB: initrd.img
  53.3GB: vmlinuz
```

---

### Post by presence1960 on 2009-09-08
What partition was your windows installation on, sda1 or sda4? i think sda1 is windows XP and sda4 is your Vista Recovery partition. let me know please.

Also your sda5 & sda6 partitions appear to overlap since they both begin in the same sector. (edit: they are ok disregard!)

We can restore GRUB to MBR and be able to boot Ubuntu, but we want to get your windows straightened out first. it looks like you installed GRUB to the first sector of XP's partition (sda1)

---

### Post by gpushkar on 2009-09-08
> **presence1960 said:**
> What partition was your windows installation on, sda1 or sda4? i think sda1 is windows XP and sda4 is your Vista Recovery partition. let me know please.

Also your sda5 & sda6 partitions appear to overlap since they both begin in the same sector. (edit: they are ok disregard!)

We can restore GRUB to MBR and be able to boot Ubuntu, but we want to get your windows straightened out first. it looks like you installed GRUB to the first sector of XP's partition (sda1)

Windows was installed on sda1 and sda4 is the vista recovery partition that came with the laptop.

---

### Post by presence1960 on 2009-09-08
> **gpushkar said:**
> Windows was installed on sda1 and sda4 is the vista recovery partition that came with the laptop.

Ok, let's take a shot at fixing XP first, then we can restore GRUB. Keep in mind you may have to wind up reinstalling XP to sda1, but that would not affect your data on sda5 & sda6.

You want to boot your XP install disk and do [this]("http://ubuntuforums.org/showthread.php?t=1014708"). Follow the instructions for XP please. When completed reboot and hopefully you boot right into XP

---

### Post by gpushkar on 2009-09-08
Thanks presence1960! Appreciate it. I ll  try and restore WinXP and get back to you

---

### Post by gpushkar on 2009-09-08
before that i ll ve to find the win xp cd!:(

---

### Post by presence1960 on 2009-09-08
> **gpushkar said:**
> before that i ll ve to find the win xp cd!:(

yes that will help!

---

### Post by gpushkar on 2009-09-10
I got my windows XP cd but it doesnt have the "recovery "option in it. So i tried to do a fresh install in sda1 but it aborted because it couldnt find some files on the disk (i suspect the disk has gone BAD. 

Now i cant boot from HDD as nothing exists in the MBR ( ntdlr not found )  and when i do the following in grub i get an error :

```
grub> find /boot/grub/stage1
 (hd0,5)

grub> root (hd0,5)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,5)/boot/grub/stage2
/boot/grub/menu.lst"... failed

Error 12: Invalid device requested

```


```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda4 starts 
                       at sector 2048. But according to the info from fdisk, 
                       sda4 starts at sector 111681536.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4fa8a60b

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    70,718,401    70,718,339   7 HPFS/NTFS
/dev/sda2          70,719,488    93,323,537    22,604,050   7 HPFS/NTFS
/dev/sda3          93,337,650   223,142,849   129,805,200   f W95 Ext d (LBA)
/dev/sda5          93,337,776   110,784,239    17,446,464  83 Linux
/dev/sda6         110,784,303   111,667,814       883,512  82 Linux swap / Solaris
/dev/sda7         152,643,584   223,141,887    70,498,304   7 HPFS/NTFS
/dev/sda4         111,681,536   152,641,535    40,960,000   7 HPFS/NTFS

/dev/sda3 overlaps with /dev/sda4

blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="B044EC7B44EC45A6" TYPE="ntfs" 
/dev/sda2: UUID="B80CE4490CE403EA" TYPE="ntfs" 
/dev/sda4: UUID="4236F0CD36F0C349" LABEL="songs" TYPE="ntfs" 
/dev/sda5: UUID="03dc481b-3ddd-4804-bca4-660b12e6aa10" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="ffc3dbc9-9258-4cbe-b0cc-bf555cf33c2d" 
/dev/sda7: UUID="B254BE6A54BE3149" LABEL="stuff" TYPE="ntfs" 
/dev/ramzswap0: TYPE="swap" 

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


=========================== sda5/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=03dc481b-3ddd-4804-bca4-660b12e6aa10 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=03dc481b-3ddd-4804-bca4-660b12e6aa10

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        03dc481b-3ddd-4804-bca4-660b12e6aa10
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=03dc481b-3ddd-4804-bca4-660b12e6aa10 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        03dc481b-3ddd-4804-bca4-660b12e6aa10
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=03dc481b-3ddd-4804-bca4-660b12e6aa10 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        03dc481b-3ddd-4804-bca4-660b12e6aa10
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows NT/2000/XP (loader)
root    (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title        Windows Vista (loader)
rootnoverify    (hd0,3)
savedefault
chainloader    +1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda7 :
UUID=03dc481b-3ddd-4804-bca4-660b12e6aa10 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda8 :
UUID=ffc3dbc9-9258-4cbe-b0cc-bf555cf33c2d none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

=================== sda5: Location of files loaded by Grub: ===================


  53.3GB: boot/grub/menu.lst
  53.3GB: boot/grub/stage2
  53.3GB: boot/initrd.img-2.6.28-11-generic
  53.3GB: boot/vmlinuz-2.6.28-11-generic
  53.3GB: initrd.img
  53.3GB: vmlinuz

```

---

### Post by presence1960 on 2009-09-10
```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,4)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,4)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

Do the above exactly. Your Ubuntu is on sda5 which is (hd0,4). Numbering for devices and partitions starts at 0. thus sda1 = (hd0,0), sda2 = (hd0,1),
sda3 = (hd0,2), sda4 = (hd0,3), sda5 = (hd0,4). sdb1 = (hd1,0), sdb2 = (hd1,1), etc.

I can't help you with windows if you do not have a working XP install disk.

---

### Post by rpaskudniak on 2009-09-11
gpushkar,

I had a similar debacle last year.  I spent a month uselessly kicking myself for not having a complete backup in place before trying this. ](*,).

The grub live CD helped my get back something but XP still took 23 minutes of doing I-don't-know-what before presenting the login screen.

In the end, I bit the bullet and actually spent money to buy Acronis Disk Director.  I was able to boot their disk and repair my partition table.  Please don't all pelt me with overripe fruits for suggesting this. [-o<

I will not be upset if someone were to direct me to a free, downloadable partition editor that will provide this service. (I know Partition Doctor didn't quite do it for me.)  At the time, I just needed my PC back.

Good luck!

---

### Post by gpushkar on 2009-09-11
its been one ](*,) of a experience. now it throws up the error : 

```
grub> root (hd0,4)

grub> setup (hd0)

Error 17: Cannot mount selected partition

grub> root (hd0,5)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,5)/boot/grub/stage2
/boot/grub/menu.lst"... failed

Error 12: Invalid device requested

```

---

### Post by presence1960 on 2009-09-11
> **gpushkar said:**
> its been one ](*,) of a experience. now it throws up the error : 

```
grub> root (hd0,4)

grub> setup (hd0)

Error 17: Cannot mount selected partition

grub> root (hd0,5)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,5)/boot/grub/stage2
/boot/grub/menu.lst"... failed

Error 12: Invalid device requested

```

I don't understand why root (hd0,4) and set up (hd0) do not work. According to your lastest boot info script your Ubuntu is on sda5. I see you changed your partition table because on the prior boot info script ubuntu was on sda7.

I don't know what you did to change your partition table or why XP's info is different but something isn't right. You went from:
> ============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    [COLOR="Red"]Boot sector info:  Grub0.97 is installed in the boot sector of sda1 and 
                       looks at sector 104216752 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #7 for 
                       /boot/grub/menu.lst.[/COLOR]
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

[COLOR="Red"]sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab[/COLOR]

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD
to:
> ============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    [COLOR="Red"]Operating System:  
    Boot files/dirs:[/COLOR]   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

[COLOR="Red"]sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab[/COLOR]

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda4 starts 
                       at sector 2048. But according to the info from fdisk, 
                       sda4 starts at sector 111681536.
    Operating System:  
    Boot files/dirs:   





At this point since you don't have a Windows install disk and your Ubuntu will not boot you might as well wipe the disk and reinstall Ubuntu.

---

### Post by gpushkar on 2009-09-11
I have no idea how that happened!! 

I think its now back to Ubuntu single boot. I hope atleast thats possible now!

---

