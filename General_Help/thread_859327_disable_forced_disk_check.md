---
title: "disable forced disk check"
date: 2008-07-14
forum: General Help
---

### Post by abazoskib on 2008-07-14
Every time I let the disk check at the splash screen run, it fails, and yet I know nothing is wrong with my hard drives. How can I disable the disk check altogether because it is really annoying?

---

### Post by Vivaldi Gloria on 2008-07-14
> **abazoskib said:**
> Every time I let the disk check at the splash screen run, it fails, and yet I know nothing is wrong with my hard drives. How can I disable the disk check altogether because it is really annoying?

Use

```
sudo tune2fs -c 9999 /dev/sda1
```

to check sda1 once in every 9999 boots. See 

```
man tune2fs
```

---

### Post by abazoskib on 2008-07-14
that command doesnt work it says: tune2fs 1.40.8 (13-Mar-2008)
tune2fs: Bad magic number in super-block while trying to open /dev/sda1
Couldn't find valid filesystem superblock.

---

### Post by abazoskib on 2008-07-14
why does the check fail in the first place? nothing is wrong with my disks

---

### Post by Vivaldi Gloria on 2008-07-14
> **abazoskib said:**
> that command doesnt work it says: tune2fs 1.40.8 (13-Mar-2008)
tune2fs: Bad magic number in super-block while trying to open /dev/sda1
Couldn't find valid filesystem superblock.

Sorry mate, this is beyond my knowlege. A google search for "filesystem superblock" comes back with a lot of results including

[http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html](http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html)

[http://linux.derkeiler.com/Mailing-Lists/Debian/2005-12/msg00231.html](http://linux.derkeiler.com/Mailing-Lists/Debian/2005-12/msg00231.html)

I suggest you read these and google around. Maybe open a new thread with the subject "Bad magic number in super-block" and post the result of that tune2fs command and also

```
sudo fdisk -l
```

I cannot be of further help.

---

### Post by mcduck on 2008-07-15
> **abazoskib said:**
> that command doesnt work it says: tune2fs 1.40.8 (13-Mar-2008)
tune2fs: Bad magic number in super-block while trying to open /dev/sda1
Couldn't find valid filesystem superblock.

That sounds like /dev/sda1 is not Ext2 or Ext3 artition. Tune2fs is only for those file systems.

Anyway, the boot-time fsck always failing could be a result of some srror in your /etc/fstab, causing fsck to try to check a partition it doesn't support. Are you perhaps dual-booting with Windows?

Could you please post the contents of your /etc/fstab here?

---

### Post by cdtech on 2008-07-15
I would like to see your fstab file and what drives you have mounted. Have you tried to manually run fsck.ext3 on your primary Ubuntu drive (sda1, if that's the correct drive)?

**P.S.**
The only thing I would use tune2fs for is to setup the mount count between devices so their not all checked at the same time. Personally I would not disable it.......

---

### Post by abazoskib on 2008-07-17
this is what my fstab file looks like:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=fcd3c9de-b0a8-4d91-922c-aa9b8e71a0d3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=9ae52073-41bd-44cf-a5c0-a4219f35e4c2 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

```




I do in fact dual boot Win XP and Ubuntu.

---

### Post by Flag on 2008-07-17
Change the last two digits in each line starting with /dev or UUID to 0 0, but the it will never check again.

rgds

---

### Post by abazoskib on 2008-07-18
> **cdtech said:**
> I would like to see your fstab file and what drives you have mounted. Have you tried to manually run fsck.ext3 on your primary Ubuntu drive (sda1, if that's the correct drive)?

**P.S.**
The only thing I would use tune2fs for is to setup the mount count between devices so their not all checked at the same time. Personally I would not disable it.......

so if i dont disable it, then what should i do?

---

### Post by cdtech on 2008-07-18
Been out of town....

You only have one partition checked, which is the correct setup in your fstab file.

Have you tried to manually run fsck.ext3 /dev/hda3 ?

Having a look at your /boot/grub/menu.lst could help as well, the kernel options to be specific.

Unless you already have this resolved........

---

### Post by abazoskib on 2008-07-18
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
default         5

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         30

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
#

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
# kopt=root=UUID=fcd3c9de-b0a8-4d91-922c-aa9b8e71a0d3 ro

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

title           Ubuntu 8.04 - Linux
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=fcd3c9de-b0a8-4d91-922c-aa9b8e71a0d3 ro quiet splash
initrd          /boot/initrd.img-2.6.24-19-generic
quiet

title           Ubuntu 8.04 - Linux (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=fcd3c9de-b0a8-4d91-922c-aa9b8e71a0d3 ro single
initrd          /boot/initrd.img-2.6.24-19-generic

title           Ubuntu 8.04, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Windows NT/2000/XP RECOVERY
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title           Microsoft Windows XP Home Edition
root            (hd0,1)
savedefault
makeactive
chainloader     +1

```

thats my menu.lst. and no i have not tried to do it manually. how would i do that?

---

### Post by cdtech on 2008-07-18
On a command line do:
sudo fsck.ext3 /dev/hda3

If in fact that is your root partition for your Ubuntu install.

You can see the partition using:
sudo fdisk -l

---

### Post by p_quarles on 2008-07-19
Disabling the fsck function altogether is really not so wise -- you say there is nothing wrong with your disk, but that's irrelevant: fsck is identifying a problem with your filesystem, which there almost certainly is. Fix that and this problem should resolve itself. 

So, what have you done so far in attempting to fix the filesystem? 

Moved to General Help, also.

---

### Post by abazoskib on 2008-07-19
dont i have to unmount the filesystem before i run fsck?

---

### Post by abazoskib on 2008-07-21
bump?

---

### Post by ferral-cat on 2008-10-31
Thank You very much Vivaldi Gloria,  I was wondering how to turn that pesky disk check off!

```
daka@daRk-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             287G   14G  259G   6% /
varrun                1.7G  104K  1.7G   1% /var/run
varlock               1.7G     0  1.7G   0% /var/lock
udev                  1.7G   72K  1.7G   1% /dev
devshm                1.7G     0  1.7G   0% /dev/shm
lrm                   1.7G   38M  1.6G   3% /lib/modules/2.6.24-19-generic/volatile
daka@daRk-desktop:~$ sudo tune2fs -c -9999 /dev/sdb1
[sudo] password for daka: 
tune2fs 1.40.8 (13-Mar-2008)
Setting maximal mount count to -9999
daka@daRk-desktop:~$ 

```

---

### Post by Yellow Pasque on 2008-10-31
> **ferral-cat said:**
> Thank You very much Vivaldi Gloria,  I was wondering how to turn that pesky disk check off!
So are you going to fsck your filesystems manually, or are you just going to pray to the storage gods that your data is safe?

---

### Post by jago25_98 on 2011-11-19
I've disabled using 

tune2fs -c 9999 /dev/sda3 and all other partitions I could

also changed 

0 1
to 
0 0
 
in /etc/fstab

and still it is disk checking at boot up even though I've done a fsck and all partitions have come back clean. 

I can't boot because of this; it just runs disk checking forever (left it for days). I have to use init=/bin/bash by editing the boot line. 

Clearly there's a bug somewhere. 

Coincidentally, once I've booted using init=/bin/bash how can I then get to a full system? #init 3 doesn't seem to take me to that runlevel.

---

