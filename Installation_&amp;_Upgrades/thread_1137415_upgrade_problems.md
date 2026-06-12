---
title: "upgrade problems"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by foo-monger on 2009-04-25
Hi,

I hope someone can help me with this problem. I am really new to Linux.
I had 8.10 working really well on my laptop and upgraded through update manager. At first it said I could only do a partial upgrade then it down loaded over 800 updates. When I rebooted I get the option to boot either with Windows or 8.10 but then it 'hangs' and says that something is missing.
I tried to resolve the problem with the Alternate Boot CD but it was too complicated for me to understand.

I have done what someone suggested on another thread and got this result.


============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcc6d2272

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   168,007,769   168,005,722   7 HPFS/NTFS
/dev/sda2         168,007,770   234,436,544    66,428,775   5 Extended
/dev/sda5         168,007,833   231,609,104    63,601,272  83 Linux
/dev/sda6         231,609,168   234,436,544     2,827,377  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="F610C94F10C9178F" TYPE="ntfs" 
/dev/sda5: UUID="3c61aadf-6077-4dd3-8f80-a16daab8fde5" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="f998a919-b5d0-47c3-9a69-d71f177c3358" 

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
/dev/sda1 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


=================== sda1: Location of files loaded by Grub: ===================


  14.2GB: boot/grub/stage2

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
# kopt=root=UUID=3c61aadf-6077-4dd3-8f80-a16daab8fde5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3c61aadf-6077-4dd3-8f80-a16daab8fde5

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

title		Ubuntu 8.10, kernel 2.6.27-14-generic
uuid		3c61aadf-6077-4dd3-8f80-a16daab8fde5
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=3c61aadf-6077-4dd3-8f80-a16daab8fde5 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
uuid		3c61aadf-6077-4dd3-8f80-a16daab8fde5
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=3c61aadf-6077-4dd3-8f80-a16daab8fde5 ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 8.10, memtest86+
uuid		3c61aadf-6077-4dd3-8f80-a16daab8fde5
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=3c61aadf-6077-4dd3-8f80-a16daab8fde5 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=f998a919-b5d0-47c3-9a69-d71f177c3358 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  86.3GB: boot/grub/menu.lst
  86.2GB: boot/grub/stage2
  86.3GB: boot/initrd.img-2.6.27-14-generic
  86.3GB: boot/vmlinuz-2.6.27-14-generic
  86.3GB: initrd.img
  86.3GB: vmlinuz[CODE]


I hope this makes sense to someone because I had lots of stuff in Ubuntu that I dont want to loose.

Thanks in anticipation.

---

### Post by meierfra. on 2009-04-26
It seems the Ubuntu 9.04 kernel did not get installed. So I suggest to login into  Ubuntu 9.04  from the Ubuntu LiveCD and  update your system.

Boot from the LiveCD and open a terminal.Then


```
sudo mount /dev/sda5 /mnt
cd /mnt
sudo cp {/,}etc/resolv.conf
sudo mount --bind {/,}proc
sudo mount --bind {/,}sys
sudo mount --bind {/,}dev
sudo chroot /mnt

```
and at the new prompt


```
apt-get update
apt-get upgrade

```

Post the whole content of the terminal.

Reboot and see whether you can boot into Ubuntu.

---

