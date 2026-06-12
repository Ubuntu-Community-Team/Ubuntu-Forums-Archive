---
title: "Xubuntu grub broken..."
date: 2009-05-08
forum: Installation &amp; Upgrades
---

### Post by Jhodas on 2009-05-08
Hi all.
I appreciate that this may not be a strictly Xubuntu related problem, nevertheless I hope the wealth of knowlege on these forums can help me out.

I've had xubuntu on my laptop happily for a while. I tried to install Gentoo alongside it, and somewhere along the line gentoo tried to hijack grub for itself. I can still get to my files from a live CD, so the partition table is fine. 

When I boot, I get a flash of "stage 1.5 loading" and then the system hangs with a blinking cursor.

I think I need to force grub to look at the xubuntu partition rather than the gentoo partition at boot time, but have no idea how to go about this. 

Any help would be great, but if this is too far off topic for these forums I apolgise.

Jho.

---

### Post by caljohnsmith on 2009-05-08
I think it would help to first get a clearer picture of your setup related to your booting problem, so how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

John

---

### Post by Jhodas on 2009-05-11
As requested. Hope this is right. Many thanks.

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:   This is .()
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab

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
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda3 and 
                       looks at sector 31227967 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on the same partition for 
                       /boot/grub/stage2.
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x13bc13bb

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    40,965,749    40,965,687  83 Linux
/dev/sda2         150,416,595   156,296,384     5,879,790   5 Extended
/dev/sda5         150,432,660   156,296,384     5,863,725  82 Linux swap / Solaris
/dev/sda3          40,965,750   150,416,594   109,450,845  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="b951807d-2e22-4472-b91e-3146f113ffcc" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: UUID="c1ed221f-13f2-4ca4-a999-4185d6f663a4" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="a5a52bcd-7322-46a1-b771-dd2129b97681" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)


========================== sda1/boot/grub/grub.conf: ==========================

default 0
timeout 30
splashimage=(hd0,0)/boot/grub/splash.xpm.gz
title=Gentoo Linux
root (hd0,0)
kernel /boot/kernel-genkernel-x86-2.6.24-gentoo-r5 root=/dev/ram0 init=/linuxrc ramdisk=8192 real_root=/dev/sda1 
initrd /boot/initramfs-genkernel-x86-2.6.24-gentoo-r5

=============================== sda1/etc/fstab: ===============================

/dev/sda1	 /	 ext3	 defaults		 0 1
none        /proc     proc    defaults          0 0
none        /dev/shm  tmpfs   defaults          0 0

=================== sda1: Location of files loaded by Grub: ===================


  16.0GB: boot/grub/grub.conf
  16.0GB: boot/grub/menu.lst
  16.0GB: boot/grub/stage2

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
# kopt=root=UUID=c1ed221f-13f2-4ca4-a999-4185d6f663a4 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=c1ed221f-13f2-4ca4-a999-4185d6f663a4 ro vga=0x0305 quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=c1ed221f-13f2-4ca4-a999-4185d6f663a4 ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.


splashimage=(hd0,0)/boot/grub/splash.xpm.gz
title=Gentoo Linux
root (hd0,0)
kernel /boot/kernel-genkernel-x86-2.6.24-gentoo-r5 root=/dev/ram0 init=/linuxrc ramdisk=8192 real_root=/dev/sda1 
initrd /boot/initramfs-genkernel-x86-2.6.24-gentoo-r5


=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=c1ed221f-13f2-4ca4-a999-4185d6f663a4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=a5a52bcd-7322-46a1-b771-dd2129b97681 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


  45.4GB: boot/grub/menu.lst
  45.5GB: boot/grub/stage2
  45.4GB: boot/initrd.img-2.6.24-19-generic
  45.4GB: boot/initrd.img-2.6.24-19-generic.bak
  45.4GB: boot/initrd.img-2.6.24-21-generic
  45.4GB: boot/initrd.img-2.6.24-21-generic.bak
  45.4GB: boot/initrd.img-2.6.24-22-generic
  45.4GB: boot/initrd.img-2.6.24-22-generic.bak
  45.4GB: boot/initrd.img-2.6.24-23-generic
  45.4GB: boot/initrd.img-2.6.24-23-generic.bak
  45.5GB: boot/vmlinuz-2.6.24-19-generic
  45.4GB: boot/vmlinuz-2.6.24-21-generic
  45.4GB: boot/vmlinuz-2.6.24-22-generic
  45.4GB: boot/vmlinuz-2.6.24-23-generic
  45.4GB: initrd.img
  45.4GB: initrd.img.old
  45.4GB: vmlinuz
  45.4GB: vmlinuz.old

```

---

### Post by Jhodas on 2009-05-11
Fixed.

I booted from a live cd and mounted the second partiton.

Had to mount /proc and /dev as well, then chrooted to said partition.

```

grub> root (hd0,2)
grub> setup (hd0)

```

sorted.
Not sure this is the best way to go about it, but thanks for your help. The only issues remaining are directly gentoo related. :P

---

