---
title: "Why is grub being retarded?"
date: 2009-02-14
forum: Installation &amp; Upgrades
---

### Post by itlarson on 2009-02-14
I am trying to install kubuntu 8.10 on a computer with several drives containing multiple ext3 partitions-  several of which contain data.  I installed into an empty partition, leaving a suse install intact.  When I rebooted I got the suse grub, although it wouldn't start.  I tried reinstalling over the suse install, and got "grub error 15".  Every install I have done since gives the same result, no matter what partition I install into.  Here is my drive info:

sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes                               
Disk identifier: 0x000ba902

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    41335244    20667591   83  Linux
/dev/sda4        41335245   976768064   467716410   83  Linux

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   234436544   117218241   83  Linux

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2e543a6a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63    29302559    14651248+  83  Linux
/dev/sdc2        31471335   488392064   228460365    5  Extended
/dev/sdc3        29302560    31471334     1084387+  82  Linux swap / Solaris
/dev/sdc5        31471398   488392064   228460333+  83  Linux

Partition table entries are not in disk order

sdc is actualy the first boot disk in bios.  I installed in sdc1 most recently.
Can anyone help with this?

---

### Post by itlarson on 2009-02-14
Interestingly there's no /boot/grub directory.  Has this location changed?

---

### Post by caljohnsmith on 2009-02-14
In order to get a clearer picture of your setup, how about booting your Kubuntu Live CD, download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to the Live CD desktop, open a Konsole and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by itlarson on 2009-02-14
Here's the whole mess.  The last partition of sda and sdc are data.  sdd is just a flash drive I have plugged in.

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #3 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on boot drive #3 in 
    partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on boot drive #3 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000ba902

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    41,335,244    41,335,182  83 Linux
/dev/sda4          41,335,245   976,768,064   935,432,820  83 Linux


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcab10bee

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   234,436,544   234,436,482  83 Linux


Drive sdc: _____________________________________________________________________

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2e543a6a

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63    29,302,559    29,302,497  83 Linux
/dev/sdc2          31,471,335   488,392,064   456,920,730   5 Extended
/dev/sdc5          31,471,398   488,392,064   456,920,667  83 Linux
/dev/sdc3          29,302,560    31,471,334     2,168,775  82 Linux swap / Solaris


Drive sdd: _____________________________________________________________________

Disk /dev/sdd: 2021 MB, 2021654016 bytes
255 heads, 63 sectors/track, 245 cylinders, total 3948543 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x91f72d24

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63     3,948,542     3,948,480   6 FAT16

/dev/sdd1 ends after the last cylinder of /dev/sdd

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="f9952d15-cd14-440f-8338-59f334ebf8f8" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: UUID="d27d3114-5764-4584-99ec-a02eafa08e91" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="a5bab1d6-dc1e-4934-93bc-ad255b9a2fd3" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: UUID="0d86f0ab-270f-44e5-a07f-79a6e4f910e5" TYPE="ext3" 
/dev/sdc3: UUID="d808f197-f1d1-439e-91f8-68b4f881259c" TYPE="swap" 
/dev/sdc5: UUID="14e2cd2c-c5ec-4dc2-aefb-051bcdd9de1a" SEC_TYPE="ext2" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 
/dev/sdd1: SEC_TYPE="msdos" UUID="0000-3C8F" TYPE="vfat" 

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
/dev/sdc1 on /mnt type ext3 (rw)
/dev/sdd1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,uid=999,codepage=437,iocharset=utf8)

=========================== sdc1/boot/grub/menu.lst: ===========================

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=0d86f0ab-270f-44e5-a07f-79a6e4f910e5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=0d86f0ab-270f-44e5-a07f-79a6e4f910e5

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		0d86f0ab-270f-44e5-a07f-79a6e4f910e5
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0d86f0ab-270f-44e5-a07f-79a6e4f910e5 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		0d86f0ab-270f-44e5-a07f-79a6e4f910e5
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0d86f0ab-270f-44e5-a07f-79a6e4f910e5 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		0d86f0ab-270f-44e5-a07f-79a6e4f910e5
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=0d86f0ab-270f-44e5-a07f-79a6e4f910e5 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc5
UUID=14e2cd2c-c5ec-4dc2-aefb-051bcdd9de1a /home           ext3    relatime        0       2
# /dev/sda1
UUID=f9952d15-cd14-440f-8338-59f334ebf8f8 /home/.extra    ext3    relatime        0       2
# /dev/sda4
UUID=d27d3114-5764-4584-99ec-a02eafa08e91 /home/temp      ext3    relatime        0       2
# /dev/sdb1
UUID=a5bab1d6-dc1e-4934-93bc-ad255b9a2fd3 /home/temp/dvd1 ext3    relatime        0       2
# /dev/sdc3
UUID=d808f197-f1d1-439e-91f8-68b4f881259c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


   5.0GB: boot/grub/menu.lst
   4.9GB: boot/grub/stage2
   4.9GB: boot/initrd.img-2.6.27-7-generic
   5.0GB: boot/vmlinuz-2.6.27-7-generic
   4.9GB: initrd.img
   5.0GB: vmlinuz


```

---

### Post by caljohnsmith on 2009-02-14
OK, how about doing:
```
sudo grub
grub> root (hd2,0)
grub> setup (hd2)
grub> quit
```
Reboot, set your BIOS to boot the 250 GB Ubuntu drive first, and if all goes well you should get the Grub menu and be able to boot into Ubuntu. Just make sure your BIOS is set to boot the sdc drive, because three of your HDDs have Grub installed to their MBR; that means if you boot any drive other than the sdc drive, you will most likely get a Grub error like you have been. Let me know how that goes or if you run into problems.

---

