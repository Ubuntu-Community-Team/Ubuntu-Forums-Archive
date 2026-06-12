---
title: "How do I mount an existing partition as /home?"
date: 2008-11-05
forum: General Help
---

### Post by mjpatey on 2008-11-05
Hi, all!

Last time I installed Ubuntu (8.04), I created a separate partition with a mount point of /home.  Unfortunately, I just did a fresh install of 8.10 to my intended partition, leaving the previous /home partition untouched... but forgot to mount it as /home.

I've seen tutorials on how to move an existing /home folder to its own partition, but I want to do just the opposite.  I have a separate partition that has my previous /home contents, and I want to now mount it as /home.

In my fresh 8.10 install, when I run gparted, for some reason I don't have the option to edit the partition, or change its mount point.  I'm running gparted as root (of course, since you can only run it as root), so I don't think it's a permissions problem... or is it?

Any idea what may be preventing me from changing the mount point of this partition?

Thanks for any input you may have!

-Mark

---

### Post by bogdan.veringioiu on 2008-11-05
Hi.

You should probably modify your fstab, mounting as /home, the desired partition.

Is your old home partition mounted?

can you paste the content of the /etc/fstab file?

Thanks

Bogdan

---

### Post by ad_267 on 2008-11-05
Can you also post the output of "sudo fdisk -l" which will list your partitions.

---

### Post by l0wender on 2008-11-05
Just add a single line to the end of /etc/fstab like this one (use sudo or log in as root):

```
/dev/sdaX /home ext3 defaults 0 2
```

Where sdaX must be your home partition and ext3 is the filesystem type (Replace them if necessary)

Invoke "man fstab" and "man mount" in a shell window if you like to learn more about the other options you may specify in /etc/fstab (character encoding, access control etc.)

---

### Post by hyper_ch on 2008-11-05
you could also have a look at [http://www.psycocats.net](http://www.psycocats.net) --> there's a great howto on how to create a seperate /home and it also has in it what you need to alter in the fstab.

---

### Post by mjpatey on 2008-11-05
Thank you all for the answers.  Here 's my part...

Contents of /etc/fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=06c14dca-100c-4c5f-9c75-cb92b1d85d31 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=de8e5ebb-d549-45d9-a067-dba54b5e47a7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```Output of sudo fdisk -l:
```

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa29ca29c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14946   120053713+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7ad43fbd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4620    37110118+  83  Linux
/dev/sdb2            4621        9726    41013945    5  Extended
/dev/sdb5            9325        9726     3229033+  82  Linux swap / Solaris
/dev/sdb6            4621        9324    37784817   83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000618f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    b  W95 FAT32
```sdb2 is the one I'm interested in; it was my old /home partition.  Incidentally, I tried what l0wender suggested, but it caused trouble.  Upon reboot, I was taken out to a shell with an fsck error on sdb2.  I guess it was too soon to add that line?

-Mark

---

### Post by l0wender on 2008-11-10
Hi Mark,

The sdb2 is the wrong ID for the partition you're interested in:

Looking at your fdisk output one can see that the sdb2 is the container of the other sub-partitions. That's why it is called "Extended" - it is comprised of other partitions contained within. The sdb5 and sdb6 partitions are inside the Extended partition. Thank Billy Gates and Microsoft for such a wierd layout. You may also check the cylinder numbers: can you see them overlapping? That's how the Extended partition works. There can only be up to 4 Primary partitions on a standard PC disk. If you need more, that's where the Extended partitions come into play. The Extended partition is almost like a Primary one, except that it can host a few more partitions inside itself (sdb5 and sdb6 inside sdb2 in your case)

Most likely, sdb6 is your old /home partition since sdb5 is for swapping.
(I presume that sdb1 is your old / (root) partition of your old system)

Serge

---

### Post by l0wender on 2008-11-10
Hi Mark,

The sdb2 is the wrong ID for the partition you're interested in:

Looking at your fdisk output one can see that the sdb2 is the container of the other sub-partitions. That's why it is called "Extended" - it is comprised of other partitions contained within. The sdb5 and sdb6 partitions are inside the Extended partition. Thank Billy Gates and Microsoft for such a wierd layout. You may also check the cylinder numbers: can you see them overlapping? That's how the Extended partition works. There can only be up to 4 Primary partitions on a standard PC disk. If you need more, that's where the Extended partitions come into play. The Extended partition is almost like a Primary one, except that it can host a few more partitions inside itself (sdb5 and sdb6 inside sdb2 in your case)

Most likely, sdb6 is your old /home partition since sdb5 is for swapping.
(I presume that sdb1 is your old / (root) partition of your old system)

Serge

---

### Post by Thoht on 2008-11-13
Hi!

I installed Xubuntu by Wubi and then used LVPM to make it "the real deal" on my MSI Wind.

I want one swap partition, one / and one /home. However, things have gone a bit... weird.

```
Thoht@Wind:~$ cat /etc/fstab 
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc        defaults    0   0
# /dev/sda1
UUID=8a3d1cd2-3ca6-4162-abc6-375c4dd122b9      none            swap        sw          0   0
# /dev/sda2
UUID=bac212af-56c0-4ce4-9a60-951e201cf31c     /               ext3        defaults,errors=remount-ro    0   1
# /dev/sda3
UUID=828C58228C5812D1       /home       ext3         defaults      0   2

```

```
Thoht@Wind:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x38b83a1a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         510     4096543+  82  Linux swap / Solaris
/dev/sda2   *         511        1815    10482412+  83  Linux
/dev/sda3            1816       19457   141709365   83  Linux
```

```
Thoht@Wind:~$ blkid
/dev/sda1: LABEL="WINRE" UUID="3489-AC5F" TYPE="vfat" 
/dev/sda2: UUID="bac212af-56c0-4ce4-9a60-951e201cf31c" TYPE="ext3" 
/dev/sda3: UUID="2132b8a6-7d22-4290-84e8-39fc71fa0c15" SEC_TYPE="ext2" TYPE="ext3"
``` 

```
Thoht@Wind:~$ cat /boot/grub/menu.lst
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
timeout		4

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
# kopt=root=UUID=bac212af-56c0-4ce4-9a60-951e201cf31c  ro ROOTFLAGS=syncio

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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

title		Xubuntu 8.10
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sda2 ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic

### END DEBIAN AUTOMAGIC KERNELS LIST
```

What am I doing wrong here? This feels like a mess, and I don't understand the difference between blkid and fdisk. This configuration also yields an error at boot because the file systems can't be checked for errors.

Any ideas? Thank you in advance!

/T

---

### Post by Thoht on 2008-11-13
By the way, this is the error message I get in gparted:

```
org.freedesktop.hal.storage.mount-fixed auth_admin_keep_always <-- (action, result).
```

---

