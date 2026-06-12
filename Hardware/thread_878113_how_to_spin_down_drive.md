---
title: "how to spin down drive?"
date: 2008-08-02
forum: Hardware
---

### Post by fredfelter on 2008-08-02
Since I'm a Linux beginner maybe this should be in that forum?

I am using a Thinkpad T22 with Ubuntu installed on a HD that runs in the CD bay but as a second drive. I have Win 2K on the primary HD and I move between the 2 through the BIOS startup. It works great so far. My idea is to spin down the Win. drive while I'm using Ubuntu as it has an irritating habit of whinning as it seems to spin up and down (why?).

Here is what my fdisk and mount commands return:

fred@fred-laptop:~$ mount
/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/fred/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=fred)

fred@fred-laptop:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
240 heads, 63 sectors/track, 5168 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x669b0829

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4848    36650848+   c  W95 FAT32 (LBA)
/dev/sda2            4849        5168     2419200   1c  Hidden W95 FAT32 (LBA)

Disk /dev/sdb: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa048b3fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3492    28049458+  83  Linux
/dev/sdb2            3493        3648     1253070    5  Extended
/dev/sdb5            3493        3648     1253038+  82  Linux swap / Solaris
fred@fred-laptop:~$ 

It looks like my Windows drive is "sda" and the Linux one "sdb". My questions are:
   1) Is it feasible to spin down the Windows drive while using Linux and not mess up it's use when I boot to Windows? If so, how?
   2) Why doesn't the Win. drive show up in "mount"
   3) In Places > Computer there is an IBM_Preload which must be that Win. drive but R click > Mount or Unmount seemingly do nothing. Why not?

Thanks a lot in advance.

---

### Post by ajgreeny on 2008-08-02
> 1) Is it feasible to spin down the Windows drive while using Linux and not mess up it's use when I boot to Windows? If so, how?I'm not sure, but if the disk is not mounted it may not spin all the time.  So if your windows drive is mounted at bootup, stop that happening by editing your /etc/fstab file by commenting out the windows line with # at the beginning.  It looks as if it is not mounted judging by the "mount" command output, so that may not be a correct answer of mine, and if that's the case, I don't think I can help.

>     2) Why doesn't the Win. drive show up in "mount"Because it is not mounted.  Only mounted partitions show in this command.

> 3) In Places > Computer there is an IBM_Preload which must be that Win. drive but R click > Mount or Unmount seemingly do nothing. Why not?I suspect that is the sda2 partition, ie the hidden one, but why your sda1 partition does not show in Places I don't know. (Or does it show?)  Right clicking usually mounts drives easily if you choose to, so perhaps the fact that it is a hidden partition is the reason for it not mounting or at least not showing (perhaps you have not got nautilus set to show hidden folders and files).

Just to be certain, let's see the output of ```
cat /etc/fstab
```to see if there are any clues there.

---

### Post by fredfelter on 2008-08-02
Thanks for the reply ajgreeny.
Here is that result:


fred@fred-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=39a12d12-a65d-4e82-923c-c113823675a2 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=1a58b061-a596-4298-8609-a33e4c6f348e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
fred@fred-laptop:~$ 

I'm not sure what this is telling me but hopefully you can decipher it.

---

### Post by ajgreeny on 2008-08-03
Well that is a bit confusing as your fstab file which mounts the partitions at boot shows that your ubuntu partitions are at sda1 and the swap at sda5, and there are no windows partitions mounted at boot as I suspected.  However your fdisk -l command shows that the windows partitions are at sda1 and sda2, so how we've arrived there I can't quite sort out.

Can you boot into both windows and ubuntu at the moment without problem?  Just to sort out what is happening can you post the output of ```
cat /boot/grub/menu.lst
```to see what the grub menu says and try to figure out which disk really is which.

---

### Post by fredfelter on 2008-08-03
Thanks again for your help ajgreeny. I'm having no problem booting into either drive/OS. As I mentioned I do it by entering Bios>Startup>changing between drives.

Here is the result of "cat /boot/grub/...

fred@fred-laptop:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=39a12d12-a65d-4e82-923c-c113823675a2 ro

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=39a12d12-a65d-4e82-923c-c113823675a2 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=39a12d12-a65d-4e82-923c-c113823675a2 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=39a12d12-a65d-4e82-923c-c113823675a2 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=39a12d12-a65d-4e82-923c-c113823675a2 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
fred@fred-laptop:~$

---

### Post by ajgreeny on 2008-08-04
It was only seeing your menu.lst that I remembered that you boot according to the changed BIOS boot device.  Not the most practical, I suggest, but it works as I know from experience.  However, as your windows drive is not mounted at boot time I don't think my idea of it not spinning if not mounted is correct.  I wonder if there is any way you can set it to not be detected in BIOS when you chose to boot into ubuntu, though that may then mean that you can't even mount it as the BIOS does not even realise that it exists.

---

