---
title: "Windows not booting from Grub menu"
date: 2009-05-15
forum: Installation &amp; Upgrades
---

### Post by samk115 on 2009-05-15
Hey guys! im just new to Ubuntu but i love it so far!

1 small issue,
I play a fair few games and have kept windows installed to do this, however when i chhose it from the boot menu it wont do this. it says NTLDR is missing.

i have been into the Grub menu file and tried changing the location of the harddrives/partitions that it searches for the windows files, but am having no luck.

Windows is installed on a seperate 40gb harddrive that is conneced via IDE. Windows was installed before Ubuntu

Ubuntu is installed on a second 640gb harddrive.It is installed on a 40gb partition i have made on that harddrive in the EXT4 filesystem, the rest of the harddrive is NTFS and is where i store all my games and music for windows (music gets used on ubuntu aswell i suppose). when it boots it says its booting from HD(0,5) which i assume means harddrive 0, partition 5. the default entry for windows xp in the menu list is:

 # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
chainloader    +1

I assume that this means it is searching for windows on the same HD that ubuntu is installed on. I have tried changing to HD 1,2,3 etc (i only have 3 Hds, 40gb internal,640gb internal in 2 partitions and a 500gb external) and i have also tried changing what partition it is looking in in each of those HD's

Could the fact that one HD (windows) is IDE and the other (Ubuntu/media) is sata be causing the issue?

The thing is, i can get windows to work by going into the bios and changing the first boot source to the windows harddrive, thereby bypassing the grub boot loader, so because of this i am assuming that there are no files missing from my windows install and instead think that it is some sort of conflict between the harddrive ID's or that the grub boot loader is looking in the wrong place.

I dont know too much about computers(im learning though, i love the Hands on terminal aspect of ubuntu), so i thought id post up here and see if anyone can help me figure it out.

Apart from that, im pretty much a Ubuntu convert! so much more fun for everyday tasks, i just wish it supported all my games and my graphics card (i have an ATI radeon x1950xt and apparently there isnt any support for it on 9.04 because of driver issues or somewhat, if anyone can tell me how to get this running it would be appreciated aswell!!)

Thanks everyone!!!
Sam

---

### Post by bruno9779 on 2009-05-15
Hey!!

what is it with such a generic title!!???!!!

if you do not resume the problem i am not getting through the trouble of reading such a large post, and I guess many others won't either

---

### Post by samk115 on 2009-05-15
Is there any way to change this now? or should i make another post?

---

### Post by Sef on 2009-05-15
> Is there any way to change this now? or should i make another post?


Changed.

> 1 small issue,
I play a fair few games and have kept windows installed to do this, however when i chhose it from the boot menu it wont do this. it says NTLDR is missing.


Let's check your partitions first:  Applications > Accessories > Terminal

the copy and paste this command:

```
sudo fdisk -l
```  then copy and paste the results here.

---

### Post by samk115 on 2009-05-15
heres the output of that command:

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x19977efb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4864    39070048+   7  HPFS/NTFS

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9a0a4a4f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       72584   583030948+   7  HPFS/NTFS
/dev/sdb2           72585       77825    42098332+   5  Extended
/dev/sdb5           72585       72957     2996091   82  Linux swap / Solaris
/dev/sdb6           72958       77825    39102178+  83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    7  HPFS/NTFS

---

### Post by samk115 on 2009-05-15
I thought this might also help:

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x19977efb

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    78,140,159    78,140,097   7 HPFS/NTFS


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9a0a4a4f

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63 1,166,061,959 1,166,061,897   7 HPFS/NTFS
/dev/sdb2       1,166,061,960 1,250,258,624    84,196,665   5 Extended
/dev/sdb5       1,166,062,023 1,172,054,204     5,992,182  82 Linux swap / Solaris
/dev/sdb6       1,172,054,268 1,250,258,624    78,204,357  83 Linux


Drive sdc: _____________________________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x44fdfe06

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   976,768,064   976,768,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="4C5CB8255CB80BA8" TYPE="ntfs" 
/dev/sdb1: UUID="1468725368723418" LABEL="Media" TYPE="ntfs" 
/dev/sdb5: TYPE="swap" UUID="75d0b13b-2c37-4fec-bd92-381d6bb66857" 
/dev/sdb6: UUID="5a607cef-fc43-466e-96a4-2337cbd7f228" TYPE="ext4" 
/dev/sdc1: UUID="0048C94A48C93EE2" LABEL="Greddy HD" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sdb6 on / type ext4 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/sam/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=sam)
/dev/sdc1 on /media/Greddy HD type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 

=========================== sdb6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=5a607cef-fc43-466e-96a4-2337cbd7f228 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5a607cef-fc43-466e-96a4-2337cbd7f228

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
uuid        5a607cef-fc43-466e-96a4-2337cbd7f228
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=5a607cef-fc43-466e-96a4-2337cbd7f228 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        5a607cef-fc43-466e-96a4-2337cbd7f228
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=5a607cef-fc43-466e-96a4-2337cbd7f228 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        5a607cef-fc43-466e-96a4-2337cbd7f228
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
chainloader    +1


=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb6 during installation
UUID=5a607cef-fc43-466e-96a4-2337cbd7f228 /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=75d0b13b-2c37-4fec-bd92-381d6bb66857 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb6: Location of files loaded by Grub: ===================


 603.3GB: boot/grub/menu.lst
 601.8GB: boot/grub/stage2
 603.7GB: boot/initrd.img-2.6.28-11-generic
 601.9GB: boot/vmlinuz-2.6.28-11-generic
 603.7GB: initrd.img
 601.9GB: vmlinuz

---

### Post by samk115 on 2009-05-15
Can anyone help? id really like to get this sorted out

---

