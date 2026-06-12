---
title: "fixing Wubiboot after reinstalling vista"
date: 2009-07-24
forum: Installation &amp; Upgrades
---

### Post by izint on 2009-07-24
Well I installed ubuntu after i had vista on my laptop, 
then i reformatted my windows partition and reinstalled it with vista
i was wondering how do i get back the loader to be able to boot into ubuntu as well?

i first thought i was suppose to use the other thread about fixing grub, but i dont think so now [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) since someone mentioned wubiboot, pg92

thx

---

### Post by lisati on 2009-07-24
Did you install Ubuntu "within" windows using Wubi, or did you install Ubunti in its own partition?
If you installed Ubuntu via wubi, then there's a strong chance it has gone.

---

### Post by izint on 2009-07-24
uhh I mounted the iso and installed onto another partition, with wubi.exe im guessing

---

### Post by lisati on 2009-07-24
Wubi.exe doesn't normally install Ubuntu into its own partition, it sets up a special folder in the Windows partition.

Do you have an Ubuntu CD available to start your computer with?

---

### Post by izint on 2009-07-24
yea I have a livedvd/usb to run ubuntu, 
I didnt know much when installing it, so i just set the drive to my 8gb partition, and windows in my main partition

---

### Post by lisati on 2009-07-24
ok, sounds promising. Since you have a LiveDVD available, there are options to see if Ubuntu is still sitting in your system somewhere. If it is still there, someone here might be able to guide you through getting it back without the hassle of a complete reinstallation. This might sound complicated, but the underlying idea is fairly straightforward.

If you are able to boot (start) your computer from the liveDVD or LiveUSB, you should be able to select the option "Try Ubuntu without any change to your computer". 

Once you have the Ubuntu Desktop showing, you will be able to get an idea of what's on your computer. There are a couple of ways of doing this - here goes with one of them.

From the Applications->Accessories menu, choose "Terminal". Could you please type in the following and report back with the output:
```
sudo fdisk -l
```
(That's a little "ell", not the number one)

Based on the output we'll be able to tell if there's a partition somewhere which has Ubuntu on it, and from there be able to come up with suggestions.


(Apologies for the delay answering, I was double-checking what to suggest on another machine)

---

### Post by izint on 2009-07-24
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6e236e23

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13502   108454783+   7  HPFS/NTFS
/dev/sda2           13503       14594     8764416    7  HPFS/NTFS

Disk /dev/sdb: 1021 MB, 1021125120 bytes
32 heads, 63 sectors/track, 989 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Disk identifier: 0xa87e3b4b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         989      996788+   6  FAT16

```

this is a boot script thing I ran, that someone frmo the other thread told me to do, just incase this was more useful

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/disks/boot/grub/menu.lst 
                       /ubuntu/winboot/menu.lst /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/disks/root.disk

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6e236e23

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   216,909,629   216,909,567   7 HPFS/NTFS
/dev/sda2         216,909,824   234,438,655    17,528,832   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1021 MB, 1021125120 bytes
32 heads, 63 sectors/track, 989 cylinders, total 1994385 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa87e3b4b

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *            247     1,993,823     1,993,577   6 FAT16


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="0EFE1F53FE1F3287" LABEL="Local Disk" TYPE="ntfs" 
/dev/sda2: UUID="AE80633680630465" TYPE="ntfs" 
/dev/sdb1: SEC_TYPE="msdos" UUID="B288-271C" TYPE="vfat" 

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
/dev/sdb1 on /cdrom type vfat (rw,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda2 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1 on /media/Local Disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2 on /mnt/root type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


==================== sda2/ubuntu/disks/boot/grub/menu.lst: ====================

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
# kopt=root=UUID=AE80633680630465 loop=/ubuntu/disks/root.disk ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=AE80633680630465 loop=/ubuntu/disks/root.disk ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=AE80633680630465 loop=/ubuntu/disks/root.disk ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
rootnoverify	(hd0,0)
savedefault
chainloader	+1


======================== sda2/ubuntu/winboot/menu.lst: ========================

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

================================== sda2Wubi: ==================================

Operating System: "Ubuntu 9.04"

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

=================== sda2: Location of files loaded by Grub: ===================


 116.8GB: ubuntu/disks/boot/grub/menu.lst
 115.5GB: ubuntu/disks/boot/initrd.img-2.6.28-11-generic
 116.7GB: ubuntu/disks/boot/vmlinuz-2.6.28-11-generic
```

---

### Post by lisati on 2009-07-24
Thank you. 
On the output from fdisk, I see no sign of Ubuntu. My initial thought is that you might have to reinstall.

 I'm not used to interpreting the output from the script, so would welcome comments from other forum users before I commit myself further.

---

### Post by izint on 2009-07-24
are we allowed to bump this up hehe?

---

### Post by lisati on 2009-07-26
> **izint said:**
> are we allowed to bump this up hehe?

Yes

---

### Post by izint on 2009-07-27
I have googled quite a bit but doesn't seem to find anyone with the same problem? im sure people have done what I did before O_o

---

### Post by izint on 2009-07-27
i found this link, but not sure if it works since no one has replied
does anyone know?
[http://ubuntuforums.org/showthread.php?t=1198406](http://ubuntuforums.org/showthread.php?t=1198406)

i actually tried that, but it failed :/

---

### Post by izint on 2009-08-17
anyone?

---

