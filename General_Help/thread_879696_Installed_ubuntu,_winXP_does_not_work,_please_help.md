---
title: "Installed ubuntu, winXP does not work, please help with grub conf"
date: 2008-08-04
forum: General Help
---

### Post by Arrowx7 on 2008-08-04
Hello,
My windows partition was on sdb1.
I installed ubuntu on sdb7
Grub did not automatically add the windows XP partition to the boot list.  I changed menu.lst and added the windows XP entry.

Now when I boot and select windows XP, it just says "Starting up" and then hangs....

Here are my specs: (NOTE: sda hard drive is for storage only, it is currently empty with two partitions)
ANOTHER NOTE: sda is IDE and sdb is SATA

Thanks in advance for your help!

```

$ sudo fdisk -l

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9e3c171e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9722    78091933+   b  W95 FAT32
/dev/sda2            9723        9964     1943865    b  W95 FAT32

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc587c587

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       10326    82943563+   7  HPFS/NTFS
/dev/sdb2           10327       16708    51263415    5  Extended
/dev/sdb3           16709       38380   174080340    7  HPFS/NTFS
/dev/sdb4           38381       38913     4281322+   c  W95 FAT32 (LBA)
/dev/sdb5           13062       16708    29294527+   b  W95 FAT32
/dev/sdb6           12575       13060     3903763+  82  Linux swap / Solaris
/dev/sdb7           10327       12573    18048964+  83  Linux

Partition table entries are not in disk order

```


```

$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb7             17906416   2736800  14267168  17% /
varrun                 1037748        96   1037652   1% /var/run
varlock                1037748         0   1037748   0% /var/lock
udev                   1037748        76   1037672   1% /dev
devshm                 1037748        12   1037736   1% /dev/shm
lrm                    1037748     39760    997988   4% /lib/modules/2.6.24-19-generic/volatile
/dev/sda1             78082368        64  78082304   1% /mnt/fs7200
/dev/sda2              1940056         4   1940052   1% /mnt/reit620
/dev/sdb5             29280208        16  29280192   1% /mnt/sata7200b
gvfs-fuse-daemon      17906416   2736800  14267168  17% /home/apavel/.gvfs

```


```

$ tail -n1000 /boot/grub/menu.lst
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
# kopt=root=UUID=2b9da588-e622-4a59-9543-7943873c49f8 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,6)

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
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2b9da588-e622-4a59-9543-7943873c49f8 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2b9da588-e622-4a59-9543-7943873c49f8 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2b9da588-e622-4a59-9543-7943873c49f8 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2b9da588-e622-4a59-9543-7943873c49f8 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,6)
kernel		/boot/memtest86+.bin
quiet

title           Windows XP
root            (hd1,0)
makeactive
chainloader     +1

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by caljohnsmith on 2008-08-04
Windows XP does not like to be booted from anything other then the master drive :rolleyes:, so you have to trick it into thinking it is on the master HDD. Just change your Windows entry to:
```
title           Windows XP
root            (hd1,0)
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader     +1

```
Assuming there are no other issues, that should work.

---

### Post by Arrowx7 on 2008-08-04
thanks for your reply,
I did that, but now it says
Starting up...
 NTLDR is missing
Press Ctrl+Alt+Del to restart


Could it be that grub overwrote my windows partition?

---

### Post by caljohnsmith on 2008-08-04
Well, you definitely have other issues with Windows then that won't be solved with just that simple remapping technique. :) I think the following thread will help you solve your "NTLDR is missing" error:
[http://ubuntuforums.org/showthread.php?t=450329&page=4](http://ubuntuforums.org/showthread.php?t=450329&page=4)

---

### Post by Arrowx7 on 2008-08-04
good link, thank you

---

