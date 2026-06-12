---
title: "how to uninstall xubunu (dual boot installed from liveCD)"
date: 2009-09-10
forum: Installation &amp; Upgrades
---

### Post by rhythmiccycle on 2009-09-10
I installed xubuntu on my laptop, and i like regular ubuntu better. Because of 2 things that are important to me, 2 monitors and tor. I had these working fine on ubuntu, but I can get them to work on xubuntu. and no one is responding to my post.

my pc is a dual boot (with xp) xubuntu is installed on a 6gb partition. I know how to delete partitions, but i'm afraid that if i just delete the xubuntu partition the boot option will still be there. 

Will just deleting the partition, make it so xp will just start up (as if linux was never there)?

i don't know much about GRUB, do i need to change anything in the boot settings after i delete the partition?

i don't feeling like reinstalling xp, so i want to verify before i do anything.

---

### Post by earthpigg on 2009-09-10
clarification, please:

do you want to completely remove all traces of Linux?

or

replace xubuntu with ubuntu?

---

### Post by rhythmiccycle on 2009-09-11
replace xubuntu with ubuntu

i decided to take the risk and just put in the ubuntu liveCD. 

because I found out that Super Grub Disk can fix things if i have a problem (i ended up not needing to use it)

then i went to advance partitioning, and reformatted the partition that had xbuntu on it. and set the mount point to "/" (ex3 format)
and i left the swap partition the same.

i then when on and installed ubuntu as normal.

it seems to be working.

but in the initial boot (GRUB i think) 

i still see xbuntu there (actually i see ubuntu there twice, but i know the second one is xubuntu)

how to I get the xbuntu to get out of the initial boot option?

---

### Post by running_rabbit07 on 2009-09-11
Are you seeing two different kernels to select from or two completely separate Ubuntus?

---

### Post by rhythmiccycle on 2009-09-11
yes ubuntu and recovery both twice

---

### Post by running_rabbit07 on 2009-09-11
Are they the same kernel or both different.

---

### Post by rhythmiccycle on 2009-09-14
it says:
> 
Ubuntu 9.04. kernel 2.6.28-15-generic
Ubuntu 9.04. kernel 2.6.28-15-generic (recovery mode)
Ubuntu 9.04. kernel 2.6.28-15-generic
Ubuntu 9.04. kernel 2.6.28-15-generic (recovery mode)
Ubuntu 9.04. memtest86+
Other operating systems:
Dell Utility Partition
Microsoft Windows XP Home Edition


i've only booted in the top and bottom os's
never tried out booting in any of the others

---

### Post by earthpigg on 2009-09-14
> **rhythmiccycle said:**
> it says:


i've only booted in the top and bottom os's
never tried out booting in any of the others

odd that they are the same kernel (...28-15-generic).

try the middle one, let us know what it is.

also, please post the output of:

```
df -Th
```

and

```
cat /boot/grub/menu.lst
```

please show the output in ```
code tags like this
``` and not > quote tags.

---

### Post by rhythmiccycle on 2009-09-15
```

mrm@mrm-laptop:~$ df -Th
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda5     ext3    6.1G  3.5G  2.3G  61% /
tmpfs        tmpfs    498M     0  498M   0% /lib/init/rw
varrun       tmpfs    498M  148K  498M   1% /var/run
varlock      tmpfs    498M     0  498M   0% /var/lock
udev         tmpfs    498M  152K  498M   1% /dev
tmpfs        tmpfs    498M  200K  498M   1% /dev/shm
lrm          tmpfs    498M  2.2M  496M   1% /lib/modules/2.6.28-15-generic/volatile
/dev/sda2  fuseblk     31G   25G  5.9G  81% /media/disk
mrm@mrm-laptop:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=97e42711-44bd-40b7-aee9-4584ac23c4c1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=97e42711-44bd-40b7-aee9-4584ac23c4c1

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
uuid		97e42711-44bd-40b7-aee9-4584ac23c4c1
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=97e42711-44bd-40b7-aee9-4584ac23c4c1 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		97e42711-44bd-40b7-aee9-4584ac23c4c1
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=97e42711-44bd-40b7-aee9-4584ac23c4c1 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		97e42711-44bd-40b7-aee9-4584ac23c4c1
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=97e42711-44bd-40b7-aee9-4584ac23c4c1 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		97e42711-44bd-40b7-aee9-4584ac23c4c1
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=97e42711-44bd-40b7-aee9-4584ac23c4c1 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		97e42711-44bd-40b7-aee9-4584ac23c4c1
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Dell Utility Partition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Home Edition
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1


```


can i just go into /boot/grub/menu.lst with gedit, and delete the middle boot options?

---

### Post by earthpigg on 2009-09-16
> **rhythmiccycle said:**
> 
can i just go into /boot/grub/menu.lst with gedit, and delete the middle boot options?

you can if you want.

but those are different kernel versions, and are sort of supposed to be there.... so if a new kernel comes out and suddenly something stops working? no prob, use the older kernel. make sense?

if you want a graphical way of playing with that file, install startup manager.

---

