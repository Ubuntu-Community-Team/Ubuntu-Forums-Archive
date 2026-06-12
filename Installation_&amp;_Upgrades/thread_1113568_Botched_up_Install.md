---
title: "Botched up Install"
date: 2009-04-01
forum: Installation &amp; Upgrades
---

### Post by jixtersnoop on 2009-04-01
Ok, so I completely newbed up my Ubuntu installation. I went with the default partition settings and completely wiped my Vista installation >.> I haven't done anything since installing ubuntu except get on Mozilla and post here, so to my knowledge all the data should be there. I have a recovery disc, but given what I already messed up I don't want to proceed until someone more knowledgeable in these things lets me know what I should do. Ideally, I want to recover my vista installation and all the files I had there. I am not worried about damaging anything on my ubuntu one since there is nothing there yet, and I can correctly reinstall it later.

---

### Post by upchucky on 2009-04-01
download this

[http://sourceforge.net/project/platformdownload.php?group_id=250055](http://sourceforge.net/project/platformdownload.php?group_id=250055) 

then open a terminal, applications-->accessories--->terminal

then do this

```
sudo bash ~/Desktop/boot_info_script*.sh

```

post the results here and we can see if windows is truly gone, it may be repairable.

---

### Post by jixtersnoop on 2009-04-01
Here it is

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/menu.lst /ubuntu/winboot/wubildr.mbr

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1549f232

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   605,393,459   605,393,397  83 Linux
/dev/sda2         605,393,460   625,137,344    19,743,885   5 Extended
/dev/sda5         605,393,523   625,137,344    19,743,822  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x363ca2d6

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   625,137,344   625,137,282   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="86edc6d6-5a2d-4484-bb73-16f1fa5cb50e" TYPE="ext3" 
/dev/sda5: UUID="cf803eb2-314a-4e8a-b392-6a9e44dfd1ba" TYPE="swap" 
/dev/sdb1: UUID="9E180E84180E5C21" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ct/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ct)


=========================== sda1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=86edc6d6-5a2d-4484-bb73-16f1fa5cb50e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=86edc6d6-5a2d-4484-bb73-16f1fa5cb50e

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		86edc6d6-5a2d-4484-bb73-16f1fa5cb50e
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=86edc6d6-5a2d-4484-bb73-16f1fa5cb50e ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		86edc6d6-5a2d-4484-bb73-16f1fa5cb50e
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=86edc6d6-5a2d-4484-bb73-16f1fa5cb50e ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		86edc6d6-5a2d-4484-bb73-16f1fa5cb50e
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=86edc6d6-5a2d-4484-bb73-16f1fa5cb50e ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		86edc6d6-5a2d-4484-bb73-16f1fa5cb50e
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=86edc6d6-5a2d-4484-bb73-16f1fa5cb50e ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		86edc6d6-5a2d-4484-bb73-16f1fa5cb50e
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=86edc6d6-5a2d-4484-bb73-16f1fa5cb50e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=cf803eb2-314a-4e8a-b392-6a9e44dfd1ba none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  10.8GB: boot/grub/menu.lst
  10.8GB: boot/grub/stage2
  10.7GB: boot/initrd.img-2.6.27-11-generic
  10.8GB: boot/initrd.img-2.6.27-7-generic
  10.8GB: boot/vmlinuz-2.6.27-11-generic
  10.8GB: boot/vmlinuz-2.6.27-7-generic
  10.7GB: initrd.img
  10.8GB: initrd.img.old
  10.8GB: vmlinuz
  10.8GB: vmlinuz.old

======================== sdb1/ubuntu/winboot/menu.lst: ========================

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
	find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
	configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
	fallback 2
	find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
	configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
	fallback 3
	find --set-root --ignore-floppies /menu.lst
	configfile /menu.lst

title find /boot/grub/menu.lst
	fallback 4
	find --set-root --ignore-floppies /boot/grub/menu.lst
	configfile /boot/grub/menu.lst

title find /grub/menu.lst
	fallback 5
	find --set-root --ignore-floppies /grub/menu.lst
	configfile /grub/menu.lst

title commandline
	commandline

title reboot
	reboot

title halt
	halt
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf

---

### Post by jixtersnoop on 2009-04-02
Right...so I don't know what any of that means? Can someone tell me where I stand?

---

### Post by upchucky on 2009-04-02
im sure windows is gone but this is confusing

sdb1: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows XP
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files/dirs: /ubuntu/winboot/menu.lst /ubuntu/winboot/wubildr.mbr

open the file manager Nautilus, and look at sdb1 to see if any windows files are there. im sure they are not. in case the windows is intact there are ways to get it to boot, we can entertain that later if true.

there are multiple listings of ubuntu, once we have verified whether windows is there or not you can create a new post about how to get rid of the multiple listings of ubuntu in the bootup selection screen, you will again have to post the results of the scan i had you do into your new post.

if windows is not there, you can not re-install windows without messing up the ubuntu install, microsoft hates linux and thinks it should not be on the drive. if you want both windows and ubuntu you have to install windows first then ubuntu, this time be careful about how the drive is set up to not overwrite windows partition.

---

### Post by pieisgood4589 on 2009-04-02
It seems as if Vista has just been formatted off the hard drive. I don't believe there's any way of recovering it inside Ubuntu.

However, I'm not sure what the Vista recovery disk does. If you can recover your data, and since you don't care about your Ubuntu install, do that, and then perhaps install Ubuntu OVER Vista so that you may dual boot.

---

