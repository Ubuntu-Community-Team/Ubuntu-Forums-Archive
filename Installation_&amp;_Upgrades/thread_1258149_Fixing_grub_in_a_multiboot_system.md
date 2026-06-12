---
title: "Fixing grub in a multiboot system"
date: 2009-09-04
forum: Installation &amp; Upgrades
---

### Post by mcgeek on 2009-09-04
I have set-up a multi-boot system. Ubuntu 9.04 32-bit and 9.04 64-bit.

My HD layout is:

sda1 Ubuntu 9.04 32-bit
sda2 Extended partition
sda5 swap (in sda2)
sda3 Ubuntu 9.04 64-bit

I installed the 32 bit system first and then the 64-bit. They share the swap.

Everything runs fine but I'm not loading my updated kernels in the 32-bit enviroment. That is they are not showing up in grub to choose.

I know enough about computers to be dangerous. Soooooo.....

My guess is MBR is pointing to sda3 for loading grub?

When I run Update Manager and install kernel updates in the 32-bit environment Grub isn't being updated?

Any fixes I make to grub will need to be in the 64-bit environment?

If anyone can answer these questions I'm sure I will have more when I get down to editing menu.lst and whatever else will have to be done to see the newer kernels.

Thanks

---

### Post by presence1960 on 2009-09-04
That is because you are booting from the 64 bit Ubuntu GRUB which is installed on MBR of sda. When a distro updates it's kernels it only auto updates it's own menu.lst. So what you want to do is chainload the 32 bit from the 64 bit menu.lst. I can probably spit out now what you need to do. But i want to be sure so do this please:

Let's get a better look at your setup. Boot into Ubuntu 64 bit. Come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by mcgeek on 2009-09-06
Sorry for the delay. I didn't get back on the computer till this morning. Thanks for the help presence.

I wanted to try to edit the file myself so I can learn as much as possible. I will include results.txt, menu.lst (current), and menu.lst (edited) for comparison for review so as not to brick the whole thing....:D

Results.txt

```
Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x665a4d7d

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   488,392,064   488,392,002  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xde190163

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   234,436,544   234,436,482   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="53db8729-77a9-4550-91f4-a4e04bc1026c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: UUID="dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de" TYPE="ext3" 
/dev/sda5: UUID="9d9b4605-04ad-40ff-81b4-8b74a3de68f6" TYPE="swap" 
/dev/sdb1: UUID="3c8dee7c-3fef-4941-8c5e-28bf46ea0cce" TYPE="ext3" 
/dev/sdc1: UUID="20F834CEF834A3C6" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda3 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/xxxxx/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=xxxxx)
/dev/sdb1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)


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
# kopt=root=UUID=53db8729-77a9-4550-91f4-a4e04bc1026c ro xforcevesa

## default grub root device
## e.g. groot=(hd0,0)
# groot=53db8729-77a9-4550-91f4-a4e04bc1026c

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

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		53db8729-77a9-4550-91f4-a4e04bc1026c
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=53db8729-77a9-4550-91f4-a4e04bc1026c ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		53db8729-77a9-4550-91f4-a4e04bc1026c
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=53db8729-77a9-4550-91f4-a4e04bc1026c ro xforcevesa  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		53db8729-77a9-4550-91f4-a4e04bc1026c
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=53db8729-77a9-4550-91f4-a4e04bc1026c ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		53db8729-77a9-4550-91f4-a4e04bc1026c
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=53db8729-77a9-4550-91f4-a4e04bc1026c ro xforcevesa  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		53db8729-77a9-4550-91f4-a4e04bc1026c
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=53db8729-77a9-4550-91f4-a4e04bc1026c ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		53db8729-77a9-4550-91f4-a4e04bc1026c
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=53db8729-77a9-4550-91f4-a4e04bc1026c ro xforcevesa  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		53db8729-77a9-4550-91f4-a4e04bc1026c
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=53db8729-77a9-4550-91f4-a4e04bc1026c ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		53db8729-77a9-4550-91f4-a4e04bc1026c
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=53db8729-77a9-4550-91f4-a4e04bc1026c ro xforcevesa  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		53db8729-77a9-4550-91f4-a4e04bc1026c
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows 2000 Professional
rootnoverify	(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=53db8729-77a9-4550-91f4-a4e04bc1026c /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=9d9b4605-04ad-40ff-81b4-8b74a3de68f6 none            swap    sw              0       0
/dev/sdb1       /home/xxxxx/Mediadisk ext3 defaults 0 2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  99.5GB: boot/grub/menu.lst
  99.5GB: boot/grub/stage2
  99.5GB: boot/initrd.img-2.6.28-11-generic
  99.4GB: boot/initrd.img-2.6.28-13-generic
  99.5GB: boot/initrd.img-2.6.28-14-generic
  99.5GB: boot/initrd.img-2.6.28-15-generic
  99.4GB: boot/vmlinuz-2.6.28-11-generic
  99.5GB: boot/vmlinuz-2.6.28-13-generic
  99.5GB: boot/vmlinuz-2.6.28-14-generic
  99.5GB: boot/vmlinuz-2.6.28-15-generic
  99.5GB: initrd.img
  99.5GB: initrd.img.old
  99.5GB: vmlinuz
  99.5GB: vmlinuz.old

=========================== sda3/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de ro xforcevesa

## default grub root device
## e.g. groot=(hd0,0)
# groot=dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de

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

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de ro xforcevesa  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de ro xforcevesa  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de ro xforcevesa  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de ro xforcevesa  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-13-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=53db8729-77a9-4550-91f4-a4e04bc1026c ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=53db8729-77a9-4550-91f4-a4e04bc1026c ro xforcevesa single 
initrd		/boot/initrd.img-2.6.28-13-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=53db8729-77a9-4550-91f4-a4e04bc1026c ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=53db8729-77a9-4550-91f4-a4e04bc1026c ro xforcevesa single 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows 2000 Professional
rootnoverify	(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1


=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=9d9b4605-04ad-40ff-81b4-8b74a3de68f6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


 225.7GB: boot/grub/menu.lst
 225.7GB: boot/grub/stage2
 225.7GB: boot/initrd.img-2.6.28-11-generic
 225.6GB: boot/initrd.img-2.6.28-13-generic
 225.7GB: boot/initrd.img-2.6.28-14-generic
 225.7GB: boot/initrd.img-2.6.28-15-generic
 225.7GB: boot/vmlinuz-2.6.28-11-generic
 225.6GB: boot/vmlinuz-2.6.28-13-generic
 225.7GB: boot/vmlinuz-2.6.28-14-generic
 225.7GB: boot/vmlinuz-2.6.28-15-generic
 225.7GB: initrd.img
 225.7GB: initrd.img.old
 225.7GB: vmlinuz
 225.7GB: vmlinuz.old

================================ sdc1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINNT

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows 2000 Professional" /fastdetect

```

menu.lst (current)

```
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
# kopt=root=UUID=dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de ro xforcevesa

## default grub root device
## e.g. groot=(hd0,0)
# groot=dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de

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

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de ro xforcevesa  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de ro xforcevesa  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de ro xforcevesa  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de ro xforcevesa  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-13-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=53db8729-77a9-4550-91f4-a4e04bc1026c ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=53db8729-77a9-4550-91f4-a4e04bc1026c ro xforcevesa single 
initrd		/boot/initrd.img-2.6.28-13-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=53db8729-77a9-4550-91f4-a4e04bc1026c ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=53db8729-77a9-4550-91f4-a4e04bc1026c ro xforcevesa single 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows 2000 Professional
rootnoverify	(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

```

menu.lst (edited)

```
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
# kopt=root=UUID=dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de ro xforcevesa

## default grub root device
## e.g. groot=(hd0,0)
# groot=dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de

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

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de ro xforcevesa  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de ro xforcevesa  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de ro xforcevesa  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de ro xforcevesa  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-15-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=53db8729-77a9-4550-91f4-a4e04bc1026c ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=53db8729-77a9-4550-91f4-a4e04bc1026c ro xforcevesa single 
initrd		/boot/initrd.img-2.6.28-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-14-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=53db8729-77a9-4550-91f4-a4e04bc1026c ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=53db8729-77a9-4550-91f4-a4e04bc1026c ro xforcevesa single 
initrd		/boot/initrd.img-2.6.28-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-13-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=53db8729-77a9-4550-91f4-a4e04bc1026c ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=53db8729-77a9-4550-91f4-a4e04bc1026c ro xforcevesa single 
initrd		/boot/initrd.img-2.6.28-13-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=53db8729-77a9-4550-91f4-a4e04bc1026c ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=53db8729-77a9-4550-91f4-a4e04bc1026c ro xforcevesa single 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows 2000 Professional
rootnoverify	(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

```

Thanks for the help.

---

### Post by presence1960 on 2009-09-06
you are missing info from the script output (Boot Info Summary). Also paste it all in at once and highlight the text and click #.

see mine:```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc
 

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda6 and 
                       looks at sector 154167094 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #6 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sdc2 and 
                       looks at sector 281353491 on boot drive #3 for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sdc. Stage2 looks on partition #2 for 
                       /boot/grub/grub.conf.
    Operating System:   This is .()
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x85858585

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    37,752,749    37,752,687  83 Linux
/dev/sda2    *     37,752,832   142,608,383   104,855,552   7 HPFS/NTFS
/dev/sda3         142,609,005   174,064,274    31,455,270   5 Extended
/dev/sda5         142,609,068   150,994,934     8,385,867  82 Linux swap / Solaris
/dev/sda6         150,994,998   174,064,274    23,069,277  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000d562f

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   775,955,564   775,955,502  83 Linux
/dev/sdb3         775,955,565   976,768,064   200,812,500   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa7a57e45

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   274,823,954   274,823,892  83 Linux
/dev/sdc2         274,823,955   312,576,704    37,752,750  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="958bcb08-eb90-435a-a1b5-ddc12d0727f4" TYPE="ext4" 
/dev/sda2: UUID="1CBC7381BC73546C" LABEL="Vista" TYPE="ntfs" 
/dev/sda5: UUID="8eb314bd-7539-4208-b41f-87789f3f8af0" TYPE="swap" 
/dev/sda6: LABEL="CrunchBang" UUID="f5b8942a-f816-4f31-9248-8797e95707b7" TYPE="ext4" 
/dev/sdb1: LABEL="Linux_backup" UUID="0444d78c-85f0-4dfc-bae3-2ce54fb2c90c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb3: UUID="5B78B25B722FDD66" LABEL="Windows_backup" TYPE="ntfs" 
/dev/sdc1: LABEL="data" UUID="19165e00-e9f1-45b5-8054-18949d24c325" TYPE="ext3" 
/dev/sdc2: LABEL="Sabayon_4.1" UUID="bcbfcac3-dc98-4fe2-83eb-31e555e2c6bb" TYPE="ext4" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext4 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/raz/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=raz)
/dev/sdc1 on /media/data type ext3 (rw,nosuid,nodev,uhelper=hal)


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
timeout		4

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
# kopt=root=UUID=958bcb08-eb90-435a-a1b5-ddc12d0727f4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=958bcb08-eb90-435a-a1b5-ddc12d0727f4

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

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		958bcb08-eb90-435a-a1b5-ddc12d0727f4
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=958bcb08-eb90-435a-a1b5-ddc12d0727f4 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		958bcb08-eb90-435a-a1b5-ddc12d0727f4
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=958bcb08-eb90-435a-a1b5-ddc12d0727f4 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		958bcb08-eb90-435a-a1b5-ddc12d0727f4
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=958bcb08-eb90-435a-a1b5-ddc12d0727f4 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		958bcb08-eb90-435a-a1b5-ddc12d0727f4
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=958bcb08-eb90-435a-a1b5-ddc12d0727f4 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

#title		Ubuntu 9.04, kernel 2.6.28-11-generic
#uuid		958bcb08-eb90-435a-a1b5-ddc12d0727f4
#kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=958bcb08-eb90-435a-a1b5-ddc12d0727f4 ro quiet splash 
#initrd		/boot/initrd.img-2.6.28-11-generic
#quiet

#title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
#uuid		958bcb08-eb90-435a-a1b5-ddc12d0727f4
#kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=958bcb08-eb90-435a-a1b5-ddc12d0727f4 ro  single
#initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		958bcb08-eb90-435a-a1b5-ddc12d0727f4
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc2.
title           Sabayon 4.1
rootnoverify    (hd2,1)
chainloader     +1

title           CrunchBang Linux
rootnoverify    (hd0,5)
chainloader     +1

title           Windows Vista OEM
root            (hd0,1)
chainloader     +1

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=958bcb08-eb90-435a-a1b5-ddc12d0727f4 /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=8eb314bd-7539-4208-b41f-87789f3f8af0 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


   3.5GB: boot/grub/menu.lst
   1.8GB: boot/grub/stage2
   6.5GB: boot/initrd.img-2.6.28-11-generic
  19.3GB: boot/initrd.img-2.6.28-13-generic
   7.1GB: boot/initrd.img-2.6.28-15-generic
   6.5GB: boot/vmlinuz-2.6.28-11-generic
  15.1GB: boot/vmlinuz-2.6.28-13-generic
  12.9GB: boot/vmlinuz-2.6.28-15-generic
   7.1GB: initrd.img
  19.3GB: initrd.img.old
  12.9GB: vmlinuz
  15.1GB: vmlinuz.old

=========================== sda6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=f5b8942a-f816-4f31-9248-8797e95707b7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f5b8942a-f816-4f31-9248-8797e95707b7

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

title		CrunchBang, kernel 2.6.28-13-generic
uuid		f5b8942a-f816-4f31-9248-8797e95707b7
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=f5b8942a-f816-4f31-9248-8797e95707b7 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		CrunchBang, kernel 2.6.28-13-generic (recovery mode)
uuid		f5b8942a-f816-4f31-9248-8797e95707b7
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=f5b8942a-f816-4f31-9248-8797e95707b7 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		CrunchBang, memtest86+
uuid		f5b8942a-f816-4f31-9248-8797e95707b7
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-15-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=958bcb08-eb90-435a-a1b5-ddc12d0727f4 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=958bcb08-eb90-435a-a1b5-ddc12d0727f4 ro single 
initrd		/boot/initrd.img-2.6.28-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-13-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=958bcb08-eb90-435a-a1b5-ddc12d0727f4 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=958bcb08-eb90-435a-a1b5-ddc12d0727f4 ro single 
initrd		/boot/initrd.img-2.6.28-13-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista (loader)
rootnoverify	(hd0,1)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc2.
title		Sabayon Linux x86-64 (genkernel-x86_64-2.6.29-sabayon) (on /dev/sdc2)
root		(hd2,1)
kernel		/boot/kernel-genkernel-x86_64-2.6.29-sabayon root=/dev/ram0 ramdisk=8192 real_root=UUID=bcbfcac3-dc98-4fe2-83eb-31e555e2c6bb dolvm init=/linuxrc splash=silent,theme:sabayon vga=791 CONSOLE=/dev/tty1 quiet resume=swap:/dev/mapper/nvidia_fdcbjhba6 
initrd		/boot/initramfs-genkernel-x86_64-2.6.29-sabayon
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc2.
title		Sabayon Linux x86-64 (genkernel-x86_64-2.6.29-sabayon) (safe mode) (on /dev/sdc2)
root		(hd2,1)
kernel		/boot/kernel-genkernel-x86_64-2.6.29-sabayon root=/dev/ram0 ramdisk=8192 real_root=UUID=bcbfcac3-dc98-4fe2-83eb-31e555e2c6bb dolvm init=/linuxrc CONSOLE=/dev/tty1 resume=swap:/dev/mapper/nvidia_fdcbjhba6 nox acpi=off ide=nodma vga=normal 
initrd		/boot/initramfs-genkernel-x86_64-2.6.29-sabayon
savedefault
boot


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=f5b8942a-f816-4f31-9248-8797e95707b7 /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=8eb314bd-7539-4208-b41f-87789f3f8af0 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


  81.6GB: boot/grub/menu.lst
  78.9GB: boot/grub/stage2
  77.9GB: boot/initrd.img-2.6.28-13-generic
  81.6GB: boot/vmlinuz-2.6.28-13-generic
  77.9GB: initrd.img
  81.6GB: vmlinuz

========================== sdc2/boot/grub/grub.conf: ==========================

# grub.conf generated by the Sabayon Linux Installer
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd2,1)
#          kernel /boot/kernel-genkernel real_root=UUID=bcbfcac3-dc98-4fe2-83eb-31e555e2c6bb
#          initrd /boot/initramfs-genkernel
#boot=sdc2
default=0
timeout=5
splashimage=(hd2,1)/boot/grub/splash.xpm.gz

title Sabayon Linux x86-64 (genkernel-x86_64-2.6.29-sabayon)
	root (hd2,1)
	kernel /boot/kernel-genkernel-x86_64-2.6.29-sabayon  root=/dev/ram0 ramdisk=8192 real_root=UUID=bcbfcac3-dc98-4fe2-83eb-31e555e2c6bb dolvm init=/linuxrc splash=silent,theme:sabayon vga=791 CONSOLE=/dev/tty1 quiet resume=swap:/dev/mapper/nvidia_fdcbjhba6
	initrd /boot/initramfs-genkernel-x86_64-2.6.29-sabayon
	savedefault

title Sabayon Linux x86-64 (genkernel-x86_64-2.6.29-sabayon) (safe mode)
	root (hd2,1)
	kernel /boot/kernel-genkernel-x86_64-2.6.29-sabayon root=/dev/ram0 ramdisk=8192 real_root=UUID=bcbfcac3-dc98-4fe2-83eb-31e555e2c6bb dolvm init=/linuxrc CONSOLE=/dev/tty1 resume=swap:/dev/mapper/nvidia_fdcbjhba6 nox acpi=off ide=nodma vga=normal
	initrd /boot/initramfs-genkernel-x86_64-2.6.29-sabayon
	savedefault

title Other Operating System - Microsoft Windows
	rootnoverify (hd0,0)
	chainloader +1
	savedefault

### Other detected distributions
title		Linux Mint x64, kernel 2.6.24-16-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sdb7 ro splash all_generic_ide floppy=off irqpoll
initrd		/boot/initrd.img-2.6.24-16-generic

title		Linux Mint x64, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sdb7 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Linux Mint x64, kernel memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		4056b016-d185-439d-b630-29449b4f5912
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=4056b016-d185-439d-b630-29449b4f5912 ro quiet splash
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		4056b016-d185-439d-b630-29449b4f5912
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=4056b016-d185-439d-b630-29449b4f5912 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		4056b016-d185-439d-b630-29449b4f5912
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=4056b016-d185-439d-b630-29449b4f5912 ro quiet splash
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		4056b016-d185-439d-b630-29449b4f5912
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=4056b016-d185-439d-b630-29449b4f5912 ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, memtest86+
uuid		4056b016-d185-439d-b630-29449b4f5912
kernel		/boot/memtest86+.bin
quiet


=============================== sdc2/etc/fstab: ===============================

UUID=bcbfcac3-dc98-4fe2-83eb-31e555e2c6bb /                       ext4    user_xattr,noatime 1 1
/dev/shm                /dev/shm                tmpfs   defaults        0 0
/dev/mapper/nvidia_fdcbjhba6 swap                    swap    defaults        0 0

=================== sdc2: Location of files loaded by Grub: ===================


 153.9GB: boot/grub/grub.conf
 153.9GB: boot/grub/menu.lst
 144.0GB: boot/grub/stage2
=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg 
```

---

### Post by mcgeek on 2009-09-06
Though I was at the top of the file when I was selecting text. Here you go.

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x69205244

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   382,812,884   382,812,822  83 Linux
/dev/sda2         382,812,885   390,620,474     7,807,590   5 Extended
/dev/sda5         382,812,948   390,620,474     7,807,527  82 Linux swap / Solaris
/dev/sda3         390,620,475   488,392,064    97,771,590  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x665a4d7d

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   488,392,064   488,392,002  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xde190163

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   234,436,544   234,436,482   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="53db8729-77a9-4550-91f4-a4e04bc1026c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: UUID="dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de" TYPE="ext3" 
/dev/sda5: UUID="9d9b4605-04ad-40ff-81b4-8b74a3de68f6" TYPE="swap" 
/dev/sdb1: UUID="3c8dee7c-3fef-4941-8c5e-28bf46ea0cce" TYPE="ext3" 
/dev/sdc1: UUID="20F834CEF834A3C6" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda3 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/xxxxx/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=xxxxx)
/dev/sdb1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)


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
# kopt=root=UUID=53db8729-77a9-4550-91f4-a4e04bc1026c ro xforcevesa

## default grub root device
## e.g. groot=(hd0,0)
# groot=53db8729-77a9-4550-91f4-a4e04bc1026c

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

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		53db8729-77a9-4550-91f4-a4e04bc1026c
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=53db8729-77a9-4550-91f4-a4e04bc1026c ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		53db8729-77a9-4550-91f4-a4e04bc1026c
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=53db8729-77a9-4550-91f4-a4e04bc1026c ro xforcevesa  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		53db8729-77a9-4550-91f4-a4e04bc1026c
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=53db8729-77a9-4550-91f4-a4e04bc1026c ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		53db8729-77a9-4550-91f4-a4e04bc1026c
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=53db8729-77a9-4550-91f4-a4e04bc1026c ro xforcevesa  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		53db8729-77a9-4550-91f4-a4e04bc1026c
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=53db8729-77a9-4550-91f4-a4e04bc1026c ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		53db8729-77a9-4550-91f4-a4e04bc1026c
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=53db8729-77a9-4550-91f4-a4e04bc1026c ro xforcevesa  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		53db8729-77a9-4550-91f4-a4e04bc1026c
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=53db8729-77a9-4550-91f4-a4e04bc1026c ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		53db8729-77a9-4550-91f4-a4e04bc1026c
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=53db8729-77a9-4550-91f4-a4e04bc1026c ro xforcevesa  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		53db8729-77a9-4550-91f4-a4e04bc1026c
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows 2000 Professional
rootnoverify	(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=53db8729-77a9-4550-91f4-a4e04bc1026c /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=9d9b4605-04ad-40ff-81b4-8b74a3de68f6 none            swap    sw              0       0
/dev/sdb1       /home/xxxxx/Mediadisk ext3 defaults 0 2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  99.5GB: boot/grub/menu.lst
  99.5GB: boot/grub/stage2
  99.5GB: boot/initrd.img-2.6.28-11-generic
  99.4GB: boot/initrd.img-2.6.28-13-generic
  99.5GB: boot/initrd.img-2.6.28-14-generic
  99.5GB: boot/initrd.img-2.6.28-15-generic
  99.4GB: boot/vmlinuz-2.6.28-11-generic
  99.5GB: boot/vmlinuz-2.6.28-13-generic
  99.5GB: boot/vmlinuz-2.6.28-14-generic
  99.5GB: boot/vmlinuz-2.6.28-15-generic
  99.5GB: initrd.img
  99.5GB: initrd.img.old
  99.5GB: vmlinuz
  99.5GB: vmlinuz.old

=========================== sda3/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de ro xforcevesa

## default grub root device
## e.g. groot=(hd0,0)
# groot=dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de

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

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de ro xforcevesa  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de ro xforcevesa  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de ro xforcevesa  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de ro xforcevesa  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-13-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=53db8729-77a9-4550-91f4-a4e04bc1026c ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=53db8729-77a9-4550-91f4-a4e04bc1026c ro xforcevesa single 
initrd		/boot/initrd.img-2.6.28-13-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=53db8729-77a9-4550-91f4-a4e04bc1026c ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=53db8729-77a9-4550-91f4-a4e04bc1026c ro xforcevesa single 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows 2000 Professional
rootnoverify	(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1


=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=dd7dea42-eed7-48b6-8f6a-ee3dd0a2b7de /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=9d9b4605-04ad-40ff-81b4-8b74a3de68f6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


 225.7GB: boot/grub/menu.lst
 225.7GB: boot/grub/stage2
 225.7GB: boot/initrd.img-2.6.28-11-generic
 225.6GB: boot/initrd.img-2.6.28-13-generic
 225.7GB: boot/initrd.img-2.6.28-14-generic
 225.7GB: boot/initrd.img-2.6.28-15-generic
 225.7GB: boot/vmlinuz-2.6.28-11-generic
 225.6GB: boot/vmlinuz-2.6.28-13-generic
 225.7GB: boot/vmlinuz-2.6.28-14-generic
 225.7GB: boot/vmlinuz-2.6.28-15-generic
 225.7GB: initrd.img
 225.7GB: initrd.img.old
 225.7GB: vmlinuz
 225.7GB: vmlinuz.old

================================ sdc1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINNT

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows 2000 Professional" /fastdetect

```

---

### Post by presence1960 on 2009-09-06
Boot into Ubuntu 64 bit and open a terminal and run this command ```
gksu gedit /boot/grub/menu.lst
``` That is a lowercase L in .lst

scroll down and remove these entries:
```

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-13-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=53db8729-77a9-4550-91f4-a4e04bc1026c ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=53db8729-77a9-4550-91f4-a4e04bc1026c ro xforcevesa single 
initrd		/boot/initrd.img-2.6.28-13-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=53db8729-77a9-4550-91f4-a4e04bc1026c ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=53db8729-77a9-4550-91f4-a4e04bc1026c ro xforcevesa single 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot
```

Replace it with this:
```

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04 32 bit (on /dev/sda1)
root		(hd0,0)
chainloader     +1
```
 Now when you boot and you choose the 32 bit Ubuntu the GRUB from that version will come up and that will contain any new kernel upgrades. When 32 bit Ubuntu upgrades it's kernel the new kernel is written only to it's own menu.lst

This way is simpler and you can use that chainload entry even if you install another OS to that sda1 partition. just make sure you choose to install GRUB to sda1 not sda. Then all you will need to do is change the title in the entry to whatever OS you are using. When using multiple Distros chainloading off the GRUB in MBR is the simplest way to do. No editing of menu.lst for upgraded kernels.

---

### Post by mcgeek on 2009-09-06
Worked great!

Thanks

---

### Post by presence1960 on 2009-09-06
> **mcgeek said:**
> Worked great!

Thanks

Glad you got it! Enjoy Ubuntu.

---

