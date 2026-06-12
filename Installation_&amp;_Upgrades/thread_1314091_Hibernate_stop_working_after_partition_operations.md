---
title: "Hibernate stop working after partition operations"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by muito_fofinho on 2009-11-04
Hi guy's

After making some changes on my disk partitions (see [post]("http://ubuntuforums.org/showthread.php?t=1297864")), I **lost the Hibernate function** :(

I've tried to follow several threads in here like:
- [http://ubuntuforums.org/showthread.php?t=287962]("http://ubuntuforums.org/showthread.php?t=287962")


All seams correct:
- 'fstab' and 'resume' files have the same swap uuid;
- swap partition is correctly active after restart;

But when I do try to start ubuntu after hibernating, it simply starts ubuntu normally

Any ideas?
This happen just after moving the partition...

---

### Post by miklcct on 2009-11-04
Please post your "/boot/grub/menu.lst" (GRUB legacy) or "/boot/grub/grub.cfg" (GRUB 2), "/etc/fstab" and your output of "ls -l /dev/disk/by-uuid/" to help me diagnose the problem.

---

### Post by muito_fofinho on 2009-11-04
> **miklcct said:**
> Please post your "/boot/grub/menu.lst" (GRUB legacy) or "/boot/grub/grub.cfg" (GRUB 2), "/etc/fstab" and your output of "ls -l /dev/disk/by-uuid/" to help me diagnose the problem.

Here it goes:

**/boot/grub/menu.lst**
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
# kopt=root=UUID=ff947cce-b047-4a0d-bac3-90eb3d53761b ro

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

title		Ubuntu 8.10 (Intrepid), kernel 2.6.27-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=ff947cce-b047-4a0d-bac3-90eb3d53761b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=ff947cce-b047-4a0d-bac3-90eb3d53761b ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

#title		Ubuntu 8.10, kernel 2.6.27-11-generic
#root		(hd0,1)
#kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=ff947cce-b047-4a0d-bac3-90eb3d53761b ro quiet splash 
#initrd		/boot/initrd.img-2.6.27-11-generic
#quiet

#title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
#root		(hd0,1)
#kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=ff947cce-b047-4a0d-bac3-90eb3d53761b ro  single
#initrd		/boot/initrd.img-2.6.27-11-generic

#title		Ubuntu 8.10, kernel 2.6.27-9-generic
#root		(hd0,1)
#kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=ff947cce-b047-4a0d-bac3-90eb3d53761b ro quiet splash 
#initrd		/boot/initrd.img-2.6.27-9-generic
#quiet

#title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
#root		(hd0,1)
#kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=ff947cce-b047-4a0d-bac3-90eb3d53761b ro  single
#initrd		/boot/initrd.img-2.6.27-9-generic

#title		Ubuntu 8.10, kernel 2.6.24-22-generic
#root		(hd0,1)
#kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=ff947cce-b047-4a0d-bac3-90eb3d53761b ro quiet splash 
#initrd		/boot/initrd.img-2.6.24-22-generic
#quiet

#title		Ubuntu 8.10, kernel 2.6.24-22-generic (recovery mode)
#root		(hd0,1)
#kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=ff947cce-b047-4a0d-bac3-90eb3d53761b ro  single
#initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		HP Recovery Partition Disc
root		(hd0,3)
savedefault
makeactive
chainloader	+1

```

**/etc/fstab**
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=ff947cce-b047-4a0d-bac3-90eb3d53761b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=b756e4f7-be5a-4772-8825-937790938d48 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```


**ls -l /dev/disk/by-uuid/**
```
total 0
lrwxrwxrwx 1 root root 10 2009-11-04 10:42 6EA8E4BFA8E486C5 -> ../../sda4
lrwxrwxrwx 1 root root 10 2009-11-04 10:42 BECAE19CCAE15167 -> ../../sda1
lrwxrwxrwx 1 root root 10 2009-11-04 10:42 f405ff6a-7946-4ad3-b804-35a1cb62df19 -> ../../sda3
lrwxrwxrwx 1 root root 10 2009-11-04 10:42 ff947cce-b047-4a0d-bac3-90eb3d53761b -> ../../sda2
```

---

### Post by muito_fofinho on 2009-11-04
PROBLEM SOLVED! :D

miklcct you gave me the clue...

Following the thread a mentioned on the original post allowed to save my session indeed to swap partition.

the problem was on resume. It was not being done. And the mistake was in my menu.lst file.

all I needed to do was add: resume=uuid=<YOUR-SWAP-PARTITION-ID>
something like this:
```
/boot/vmlinuz-2.6.27-14-generic root=UUID=ff947cce-b047-4a0d-bac3-90eb3d53761b ro quiet splash **resume=UUID=f405ff6a-7946-4ad3-b804-35a1cb62df19**
```

Thank you very much!
Hope this helps people who had the same problem I had.

):P

---

### Post by MarlonNelson on 2010-01-24
my original reply made no sense after I read the prior comments more closely.
:D

had the same problem, caused by the resume file (/etc/initramfs-tools/conf.d/resume) referencing the old UUID

fixing that and running update-initramfs fixed my problem

i didn't need to add the resume UUID to my grub menu

here's a nice link: [https://help.ubuntu.com/community/UsingUUID#Resuming from Hibernation]("https://help.ubuntu.com/community/UsingUUID#Resuming from Hibernation")

---

