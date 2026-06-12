---
title: "Ubuntu 8.04 Dual Booting Help"
date: 2009-02-27
forum: Installation &amp; Upgrades
---

### Post by gsgentry on 2009-02-27
I recently installed Ubuntu 8.04 on my Win XP Machine. After completing the installation and rebooting, I get a "Client Mac Addr:" Error and then a PXE-E53: No boot filename received error.

I designated Ubuntu to install to a separate drive which happens to be the exact same make, model and size as my Win XP drive (I had this setup in RAID back in the day). Both drives are SATA and my BIOS does not allow me to select one or the other to boot from, just Hard Drive in general.

I was requested by another member to run the Boot Info Script from my Live CD Desktop and paste the contents of the "Results.txt" here for review.

Ultimately I am hoping to receive a menu of sorts when turning on my PC that will allow me to choose to boot Win XP or Ubuntu.

Thanks for everyone's help on this.


```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.2
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

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sdb1 and 
                       looks at sector 54181951 on boot drive #1 for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders, total 72303840 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa86ceb42

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    69,288,344    69,288,282  83 Linux
/dev/sda2          69,288,345    72,292,499     3,004,155   5 Extended
/dev/sda5          69,288,408    72,292,499     3,004,092  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders, total 72303840 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xffffffff

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    72,276,434    72,276,372   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="22dee61f-f5bb-42c4-8f4b-cc542bf10bb0" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="d040d054-9058-4ef2-a154-b17c8ea06a11" 
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
timeout		10

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
# kopt=root=UUID=22dee61f-f5bb-42c4-8f4b-cc542bf10bb0 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=22dee61f-f5bb-42c4-8f4b-cc542bf10bb0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=22dee61f-f5bb-42c4-8f4b-cc542bf10bb0 ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=22dee61f-f5bb-42c4-8f4b-cc542bf10bb0 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=d040d054-9058-4ef2-a154-b17c8ea06a11 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  27.7GB: boot/grub/menu.lst
  27.7GB: boot/grub/stage2
  27.7GB: boot/initrd.img-2.6.24-23-generic
  27.6GB: boot/vmlinuz-2.6.24-23-generic
  27.7GB: initrd.img
  27.6GB: vmlinuz
```

---

### Post by caljohnsmith on 2009-02-27
It looks like part of the problem is you accidentally installed Grub to the boot sector of your sdb1 Windows partition. When you went through the Ubuntu installer, did you click the "Advanced" button near the end of the installation process and specify to have Grub installed to maybe "/dev/sdb1"? Or did you run some Grub commands since installing Ubuntu? To fix your Windows partition boot sector, how about booting your Windows Install CD, go to the "recovery console" and do:
```
fixboot
```
Most likely that will be all it takes to fix your Windows partition, but let me know if it returns any errors. Next, how about doing the following to install Grub to the MBR (Master Boot Record) of your Ubuntu sda drive:
```

sudo grub
grub> root (hd0,0)
grub> makeactive
grub> setup (hd0)
grub> quit
```
Then reboot, and let me know if you get a Grub menu on start up or not. We can work from there.

---

### Post by gsgentry on 2009-02-27
Yes to the Advanced Tab Windows question. :(

OK... I will get started on this now.

---

### Post by gsgentry on 2009-02-27
Both resolved my problem and now I have a dual booting machine with a menu!!!

Is it ok to plug my other 2 hard drives in now?

Thank you ever so much!!! :grin:

---

### Post by caljohnsmith on 2009-02-27
That's great news, glad to hear you can boot Windows and Ubuntu now. Cheers and enjoy your dual-boot setup. :)

---

