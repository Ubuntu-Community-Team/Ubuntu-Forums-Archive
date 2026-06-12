---
title: "hard drive boot order_UUID"
date: 2009-03-07
forum: Hardware
---

### Post by lazylew on 2009-03-07
I found this (locked) post that looks like it has the answer to my problem: [http://ubuntuforums.org/showthread.php?t=486599](http://ubuntuforums.org/showthread.php?t=486599)

The problem I'm facing is installing a 3rd hard drive; it changes the boot order so that Ubuntu doesn't pick the right disk to boot.
(Changing boot order in BIOS didn't solve it.)

So my questions are:
- how do I get such UUIDs?
- I suppose I need a UUID for both already installed disks, and can then (after changing the fstab-file) install the 3rd disk?

If you have an answer, keep it simple for me please; I'm still a novice and my friend who's helping out is an expert in Windows only.

I'm on Hardy Heron 8.04

---

### Post by sisco311 on 2009-03-07
open a terminal and post the output of:
```
cat /etc/fstab
```
```
cat /boot/grub/menu.lst
```
```
mount
```and
```
sudo blkid
```

---

### Post by lazylew on 2009-03-07
> **sisco311 said:**
> open a terminal and post the output of:
```
cat /etc/fstab
``````
cat /boot/grub/menu.lst
``````
mount
```and
```
sudo blkid
```

aha, I see there's some UUID there; a good start I guess :-)

ludo@ludo-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=18686b15-ac28-4b5c-b294-7a499d50d5af /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=d387594d-f3e8-4a41-8fd9-821e4a23867d none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda3 /home ext3 nodev,nosuid 0 2

===============================
ludo@ludo-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=18686b15-ac28-4b5c-b294-7a499d50d5af /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=d387594d-f3e8-4a41-8fd9-821e4a23867d none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda3 /home ext3 nodev,nosuid 0 2
ludo@ludo-desktop:~$ clear
ludo@ludo-desktop:~$ cat /boot/grub/menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

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
# kopt=root=UUID=18686b15-ac28-4b5c-b294-7a499d50d5af ro

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

title        Ubuntu 8.04.2, kernel 2.6.24-23-rt
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-23-rt root=UUID=18686b15-ac28-4b5c-b294-7a499d50d5af ro quiet splash
initrd        /boot/initrd.img-2.6.24-23-rt
quiet

title        Ubuntu 8.04.2, kernel 2.6.24-23-rt (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-23-rt root=UUID=18686b15-ac28-4b5c-b294-7a499d50d5af ro single
initrd        /boot/initrd.img-2.6.24-23-rt

title        Ubuntu 8.04.2, kernel 2.6.24-23-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=18686b15-ac28-4b5c-b294-7a499d50d5af ro quiet splash
initrd        /boot/initrd.img-2.6.24-23-generic
quiet

title        Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=18686b15-ac28-4b5c-b294-7a499d50d5af ro single
initrd        /boot/initrd.img-2.6.24-23-generic

title        Ubuntu 8.04.2, kernel 2.6.24-16-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=18686b15-ac28-4b5c-b294-7a499d50d5af ro quiet splash
initrd        /boot/initrd.img-2.6.24-16-generic
quiet

title        Ubuntu 8.04.2, kernel 2.6.24-16-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=18686b15-ac28-4b5c-b294-7a499d50d5af ro single
initrd        /boot/initrd.img-2.6.24-16-generic

title        Ubuntu 8.04.2, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
====================
ludo@ludo-desktop:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-23-rt/volatile type tmpfs (rw)
/dev/sda3 on /home type ext3 (rw,nosuid,nodev)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ludo/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ludo)
======================
ludo@ludo-desktop:~$ sudo blkid
[sudo] password for ludo: 
/dev/sda1: UUID="18686b15-ac28-4b5c-b294-7a499d50d5af" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sda5: TYPE="swap" UUID="d387594d-f3e8-4a41-8fd9-821e4a23867d" 
/dev/sdb1: UUID="955ea609-3a59-4d16-ad57-325f70ea2ef1" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb2: TYPE="swap" UUID="1a9fce61-a9a3-4e2f-9f2d-cb49bd091e97" 
/dev/sdb3: UUID="8781003e-b3c3-42b8-89f9-24b4c053b69e" TYPE="reiserfs" 
/dev/sda3: UUID="01e842a7-4b26-42bb-926c-5617a63b19eb" SEC_TYPE="ext2" TYPE="ext3"

---

### Post by sisco311 on 2009-03-07
the /home partition is not mounted by uuid.

edit the /etc/fstab file:
```
gksu gedit /etc/fstab
```
and change the last line to:
```
UUID=01e842a7-4b26-42bb-926c-5617a63b19eb /home ext3 nodev,nosuid 0 2
```

> The problem I'm facing is installing a 3rd hard drive; it changes the boot order so that Ubuntu doesn't pick the right disk to boot.
(Changing boot order in BIOS didn't solve it.)
 

So you can not boot or can't login?

---

### Post by lazylew on 2009-03-07
> **sisco311 said:**
> the /home partition is not mounted by uuid.
......
So you can not boot or can't login?
yes I can at present, because I have only the 2 already working drives installed.
It's when I attach the 3rd drive that the boot problem occurs.

Before I try your suggestion, this is what it would look like; correct?
(just want to be sure, because I don't see mention of /dev/sda3 in your added line)


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=18686b15-ac28-4b5c-b294-7a499d50d5af /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=d387594d-f3e8-4a41-8fd9-821e4a23867d none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
[COLOR=Red]/dev/sda3 /home ext3 nodev,nosuid 0 2[/COLOR] [COLOR=DarkOrchid]<-- delete this line?[/COLOR] add this one? -->
UUID=01e842a7-4b26-42bb-926c-5617a63b19eb /home ext3 nodev,nosuid 0 2

---

### Post by sisco311 on 2009-03-07
> **lazylew said:**
> 
Before I try your suggestion, this is what it would look like; correct?
(just want to be sure, because I don't see mention of /dev/sda3 in your added line)


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=18686b15-ac28-4b5c-b294-7a499d50d5af /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=d387594d-f3e8-4a41-8fd9-821e4a23867d none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
[COLOR=Red]/dev/sda3 /home ext3 nodev,nosuid 0 2[/COLOR] [COLOR=DarkOrchid]<-- delete this line?[/COLOR] add this one? -->
UUID=01e842a7-4b26-42bb-926c-5617a63b19eb /home ext3 nodev,nosuid 0 2

yes, that's correct.

or you can just comment out the old line with a #:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=18686b15-ac28-4b5c-b294-7a499d50d5af / ext3 relatime,errors=remount-ro 0 1
# /dev/sda5
UUID=d387594d-f3e8-4a41-8fd9-821e4a23867d none swap sw 0 0
/dev/scd1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/scd0 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
# /dev/sda3 /home ext3 nodev,nosuid 0 2 this line is a comment
UUID=01e842a7-4b26-42bb-926c-5617a63b19eb /home ext3 nodev,nosuid 0 2
```

---

### Post by lazylew on 2009-03-07
> **sisco311 said:**
> yes, that's correct.

ok that's done, thanks for your help.
I'll now reboot and see what happens; if all goes well I'll install the 3rd drive too and hope it works (so if you don't see another "thanks" within the hour I'll probably be in a mess ;-))

---

### Post by lazylew on 2009-03-07
> **lazylew said:**
> ... If you don't see another "thanks" within the hour i'll probably be in a mess ;-)
thanks!!
:-)

---

