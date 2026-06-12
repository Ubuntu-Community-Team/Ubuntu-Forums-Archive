---
title: "hda renamed hdb, grub calls it hda and chokes..."
date: 2006-07-13
forum: Hardware &amp; Laptops
---

### Post by Sean-Michael on 2006-07-13
So, after installing a new hd, a WD250gb, my primary drive, a WD40gb was renamed to hdb but every time I have updates my "/boot/grub/menu.lst" entries get changed back to "hda6" after I've manually edited them back to "hdb6" ](*,) 

I dont know what I need to do to get things back in the proper working order,:-k

Heres a look at my grub menu.lst
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		60

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
title		Microsoft Windows XP Home Edition
root		(hd0,0)
makeactive
chainloader	+1
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
# kopt=root=/dev/hda6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdb6 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdb6 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title		Ubuntu, kernel 2.6.15-23-386 (on /dev/hda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda3 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title		Ubuntu, kernel 2.6.15-23-386 (recovery mode) (on /dev/hda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda3 ro single 
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title		Ubuntu, kernel 2.6.12-10-386 (on /dev/hda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda3 ro quiet splash 
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title		Ubuntu, kernel 2.6.12-10-386 (recovery mode) (on /dev/hda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda3 ro single 
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title		Ubuntu, kernel 2.6.12-9-386 (on /dev/hda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro quiet splash 
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title		Ubuntu, kernel 2.6.12-9-386 (recovery mode) (on /dev/hda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro single 
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title		Ubuntu, memtest86+ (on /dev/hda3)
root		(hd0,2)
kernel		/boot/memtest86+.bin  
savedefault
boot


``` 

Thankyou in advance for helping me! :D

---

### Post by geco on 2006-07-13
You have to change this 
```

root		(hd0,5)

```
to this
```

root		(hd1,5)

```
or try with something as
```

sudo dpkg-reconfigure linux-image-your_kernel_version

```
If it doesn't work - but I can't see why - try to add your lines after the 
 ### END DEBIAN AUTOMAGIC KERNELS LIST
line
```

### END DEBIAN AUTOMAGIC KERNELS LIST
title		Ubuntu, your kernel
root		(hd1,5)
kernel		/boot/vmlinuz-your_kernel_version root=/dev/hdb6 ro quiet 
initrd		/boot/initrd.img-your_kernel_version
savedefault
boot

```
Anyway... do you have a separated boot partition? You have to check it.
It is if you have something like this:
```

user@localhost:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda9             3.4G  238M  3.0G   8% /
varrun                505M   64K  505M   1% /var/run
varlock               505M  4.0K  505M   1% /var/lock
udev                  505M  152K  505M   1% /dev
devshm                505M     0  505M   0% /dev/shm
lrm                   505M   18M  487M   4% /lib/modules/2.6.15-23-686/volatile
/dev/hda6              96M   14M   77M  15% /boot
/dev/hda4              21G  5.8G   14G  31% /home
/dev/hda8             9.9G  3.4G  6.1G  36% /usr
/dev/hda7             1.5G  823M  542M  61% /var
/dev/hda2              36G   30G  5.9G  84% /mnt/winc
user@localhost:~$

```
i.e. my boot partition is /dev/hda6 - (hd0,5) for GRUB - and my root partition is /dev/hda9 so my menu.lst is something like this:
```

title           Ubuntu, kernel 2.6.15-23-686
root            (hd0,5)
kernel          /vmlinuz-2.6.15-23-686 root=/dev/hda9 ro quiet
initrd          /initrd.img-2.6.15-23-686
savedefault
boot

```
Hope this can help you!

---

### Post by Sean-Michael on 2006-07-13
So I'm not sure where to edit "root (hd0,5)" into "root (hd1,5)", but when I run "sudo dpkg-reconfigure linux-image-2.6.15-26-386" my grub menu.lst entries got changed back again to the hda values,

Here's a look at my partitions,

```
sean-michael@nitro:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdb6             3.9G  2.8G  932M  76% /
varrun               1014M   76K 1014M   1% /var/run
varlock              1014M  4.0K 1014M   1% /var/lock
udev                 1014M  124K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   19M  996M   2% /lib/modules/2.6.15-26-386/volatile
/dev/hda1             233G   32G  201G  14% /media/hda1
/dev/hdb1              26G   21G  4.4G  83% /media/hdb1
/dev/hdb3             3.2G  2.7G  325M  90% /media/hdb3
/dev/hdb5             3.9G  137M  3.8G   4% /media/hdb5
/dev/hdc              261M  261M     0 100% /media/cdrom0

```

So, from what I know, /dev/hda1 is my mass storage drive, containing no boots,  /dev/hdb1 contains my windows system, and the rest is my linux system,  hdb5 is a partition that I use to swap files between linux and windows, grub sits on hdb3 and I boot hdb6 for linux,

Sorry, this is confusing to me, this is all new territory to me.

---

### Post by geco on 2006-07-13
> **Sean-Michael said:**
> So I'm not sure where to edit "root (hd0,5)" into "root (hd1,5)", but when I run "sudo dpkg-reconfigure linux-image-2.6.15-26-386" my grub menu.lst entries got changed back again to the hda values,

Here's a look at my partitions,

```
sean-michael@nitro:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdb6             3.9G  2.8G  932M  76% /
varrun               1014M   76K 1014M   1% /var/run
varlock              1014M  4.0K 1014M   1% /var/lock
udev                 1014M  124K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   19M  996M   2% /lib/modules/2.6.15-26-386/volatile
/dev/hda1             233G   32G  201G  14% /media/hda1
/dev/hdb1              26G   21G  4.4G  83% /media/hdb1
/dev/hdb3             3.2G  2.7G  325M  90% /media/hdb3
/dev/hdb5             3.9G  137M  3.8G   4% /media/hdb5
/dev/hdc              261M  261M     0 100% /media/cdrom0

```

So, from what I know, /dev/hda1 is my mass storage drive, containing no boots,  /dev/hdb1 contains my windows system, and the rest is my linux system,  hdb5 is a partition that I use to swap files between linux and windows, grub sits on hdb3 and I boot hdb6 for linux,

Sorry, this is confusing to me, this is all new territory to me.

So you are saying that > grub sits on hdb3  do you mean that your menu.lst file is on hdb3?
if so, it seems strange to me that you have no boot partition displayed by df command... :neutral: 
try this 
```

cat /etc/fstab

```
to check out *where* your partitions are mounted
e.g.
```

user@localhost:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda9       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       /boot           ext3    defaults        0       2
/dev/hda4       /home           ext3    defaults        0       2
/dev/hda8       /usr            ext3    defaults        0       2
/dev/hda7       /var            ext3    defaults        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hda2       /mnt/winc       vfat    rw,exec,uid=1000,gid=1000,auto  0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda        /media/sda      vfat,udf,iso9660 user,noauto     0       0
user@localhost:~$   

```
as you can see I have the /dev/hda6 partition mounted on /boot
that is, I have a boot partition (where my kernel lies) separated from others.

you told that:
```
sean-michael@nitro:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdb6             3.9G  2.8G  932M  76% /
varrun               1014M   76K 1014M   1% /var/run
varlock              1014M  4.0K 1014M   1% /var/lock
udev                 1014M  124K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   19M  996M   2% /lib/modules/2.6.15-26-386/volatile
/dev/hda1             233G   32G  201G  14% /media/hda1
/dev/hdb1              26G   21G  4.4G  83% /media/hdb1
/dev/hdb3             3.2G  2.7G  325M  90% /media/hdb3
/dev/hdb5             3.9G  137M  3.8G   4% /media/hdb5
/dev/hdc              261M  261M     0 100% /media/cdrom0

```
so i guess that you too have a separated boot partition in /dev/hdb3 but for any reason it is not mounted as /boot but as /media/hdb3
anyway fstab could answer to this question...

if it is so, you should edit your /etc/fstab
from, for example,
```

/dev/hdb3       /media/hdb3           ext3    defaults        0       0

```
to
```

/dev/hdb3       /boot           ext3    defaults        0       2

```

your menu.lst file should be similar to
```

title           Ubuntu, kernel 2.6.15-23-686
root            (hd1,2)
kernel          /vmlinuz-your_kernel_version root=/dev/hdb6 ro quiet
initrd          /initrd.img-your_kernel_version
savedefault
boot

```
anyway you can alway try to edit your menu.lst simply adding the lines above at the end... the worst you can do is edit a "blind" menu entry without damaging the system.

bye ;)

---

### Post by geco on 2006-07-14
> **Sean-Michael said:**
>  when I run "sudo dpkg-reconfigure linux-image-2.6.15-26-386" my grub menu.lst entries got changed back again to the hda values,

I forgot to tell you that ```
 sudo dpkg-reconfigure linux-image-2.6.15-26-386
``` reads the instruction directly from /boot/grub/menu.lst
```


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
# kopt=root=/dev/hda9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)


```
as you can see, the automagic kernel script will set always the "root device" (i.e. where your kernel lies) on (hd0,5) (in my case), so you have to edit your menu.lst file to change this option from your /dev/hda6 - that is hd0,5 - device to your /dev/hdb6 - hd1,5 - device.

You can also do
```

sudo update-grub

```
instead of
```

sudo dpkg-reconfigure linux-image-version

```

---

