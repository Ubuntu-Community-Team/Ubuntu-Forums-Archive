---
title: "Upgrade to Heron problems"
date: 2009-02-11
forum: Installation &amp; Upgrades
---

### Post by tommalley on 2009-02-11
Hi Upgraded to Heron,

Seemed to be no problem but now I only have 280 mb of space on my working drive.

Tried different versions of gparted live to increase disk space, either hangs at a flashing cursor on the top left or goes into grub menu.

Tried booting from the ubuntu live cd but it is not showing the hard drive.

What information would you need to help me?
thanks all

---

### Post by zwygart on 2009-02-11
What is your problem? Can you boot your system? If you can't see the drive from live CD, did you checked what says gnome partition editor from de LiveCD?
How big are your partitions?

To give us the answer to these questions, the best would be that you run the script of [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/) . Post the output. All infos we need should be there.

---

### Post by tommalley on 2009-02-11
My Problem:
Things like youtube are stalling and im presuming they just dont have enough temp memory as they worked fine before. The graphics card hasnt installed properly. Restricted device manager is not there and i dont think its going to work properly with only 280mb of working hard drive to resource from.



I can boot the system but only if i choose the second kernel at the grub start up.

Used partition editor from live cd and it says no devices found, but on booting as per normal there are two partitions set up

/dev/hda1/ ext3 4.88 gigs, mountpoint /, 284 mb unused
/dev/hda2/ ext 3 33.15 gigs, mountpoint /home , 16.09 gigs unused
/dev/hda3/ ext 3 linux swap 258.16 mb

tried
chmod +x boot_info_script02.sh
./boot_info_script02.sh
to get the script to work but says no such file or directory. Im new to this systembut can generally work it out so thanks for your patience.

---

### Post by zwygart on 2009-02-11
First, it is ./boot_info_script024.sh and not ./boot_info_script02.sh
Second, i think you should decrease your home. 6G is a very minimum for Ubuntu with some applications. Better 10G. If you don't have enough space you may try xubuntu, wich works with xfce instead of Gnome. 

If the script don't works, post the output of fdisk -lu, blkid and df. Also the content of /etc/fstab and /boot/grub/menu.lst.

---

### Post by tommalley on 2009-02-12
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/hda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

hda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

hda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

hda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive hda: _____________________________________________________________________

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x381a426b

Partition  Boot         Start           End          Size  Id System

/dev/hda1                  63    16,048,934    16,048,872  83 Linux
/dev/hda2          16,048,935    78,734,564    62,685,630  83 Linux
/dev/hda3          78,734,565    80,292,869     1,558,305  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/hda1: UUID="cd6dec05-d6b1-4500-a97a-4155555b1815" TYPE="ext3" 
/dev/hda2: UUID="df2de6ca-8537-482e-83a2-4af268a44038" TYPE="ext3" 
/dev/hda3: TYPE="swap" UUID="a3870850-6314-41d2-b86d-bd661af14cd5" 

=============================== "mount" output: ===============================

/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-17-generic/volatile type tmpfs (rw)
/dev/hda2 on /home type ext3 (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

=========================== hda1/boot/grub/menu.lst: ===========================

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=UUID=cd6dec05-d6b1-4500-a97a-4155555b1815 ro

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
# defoptions=splash

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=cd6dec05-d6b1-4500-a97a-4155555b1815 ro splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=cd6dec05-d6b1-4500-a97a-4155555b1815 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.20-17-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-17-generic root=UUID=cd6dec05-d6b1-4500-a97a-4155555b1815 ro splash
initrd		/boot/initrd.img-2.6.20-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.20-17-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-17-generic root=UUID=cd6dec05-d6b1-4500-a97a-4155555b1815 ro single
initrd		/boot/initrd.img-2.6.20-17-generic

title		Ubuntu 8.04, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=cd6dec05-d6b1-4500-a97a-4155555b1815 ro splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=cd6dec05-d6b1-4500-a97a-4155555b1815 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 8.04, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=cd6dec05-d6b1-4500-a97a-4155555b1815 ro splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet

title		Ubuntu 8.04, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=cd6dec05-d6b1-4500-a97a-4155555b1815 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== hda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=cd6dec05-d6b1-4500-a97a-4155555b1815 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda2
UUID=df2de6ca-8537-482e-83a2-4af268a44038 /home           ext3    defaults        0       2
# /dev/hda3
UUID=93675e5a-89fa-4c37-9ac9-83b8ad94cf5f none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

=================== hda1: Location of files loaded by Grub: ===================


   4.3GB: boot/grub/menu.lst
   3.1GB: boot/grub/stage2
   2.8GB: boot/initrd.img-2.6.20-15-generic
   2.8GB: boot/initrd.img-2.6.20-15-generic.bak
   2.8GB: boot/initrd.img-2.6.20-16-generic
   2.8GB: boot/initrd.img-2.6.20-16-generic.bak
   2.9GB: boot/initrd.img-2.6.20-17-generic
   2.9GB: boot/initrd.img-2.6.20-17-generic.bak
   4.9GB: boot/initrd.img-2.6.24-16-generic
   4.8GB: boot/initrd.img-2.6.24-16-generic.bak
   2.8GB: boot/vmlinuz-2.6.20-15-generic
   2.8GB: boot/vmlinuz-2.6.20-16-generic
   2.9GB: boot/vmlinuz-2.6.20-17-generic
   2.8GB: boot/vmlinuz-2.6.24-16-generic
   4.9GB: initrd.img
   2.8GB: vmlinuz

=======Devices which don't seem to have a corresponding hard drive==============

 hdd .

---

### Post by tommalley on 2009-02-12
For anyone that has a similar problem the only live cd that worked for me and allowed me to use gparted was

[http://www.sysresccd.org/](http://www.sysresccd.org/)

so have now managed to adjust my partitions and have more space, but still hanging on the first kernel. Boots into the ini prompt.

---

### Post by zwygart on 2009-02-12
This is beginning out of my knowledge. I can give you some hints. May be it is because the new convention of drive calling is sdaX instead of hdaX. But it should not have an incidence because they are called by there UUID. 
Changing the names from the UUID's to /dev/sdaX will cause that you cannot boot in the old ones. 

Note : To have it easier to choose at boot up, put a # before the line hiddenmenu in your grub. You may also increase the number of timeout 3 to a bigger one. To do so : "sudo gedit /boot/grub/menu.lst".

Hopping that someone else would be able to explain more.

---

