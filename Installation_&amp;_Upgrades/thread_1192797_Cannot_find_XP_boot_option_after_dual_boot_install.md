---
title: "Cannot find XP boot option after dual boot install"
date: 2009-06-20
forum: Installation &amp; Upgrades
---

### Post by newbee75 on 2009-06-20
I am new to linux and hoping someone can help. I just installed ubuntu 9.04. 

1) Prior to install , my desktop had 1 hard disk with 2 windows ntfs partitions : 
C: -> Had windows XP home edition (16 GB)
D:-> had Windows XP professsional (60 GB)

2) I installed ubuntu through a min CD version that had textual interface. I recall that it found both partitions 1 primary (16 GB) and  1 logical (60 GB). I don't' know much about partitioning, but i guessed 16  GB pri was C: and 60 Gb logical was D: partitions

3) I requested the ubuntu installer to earse 16GB partition and use it as the primary for the ubuntu install, hoping that my Xp professional partition (60 GB) would  be intact.

4) Installation completed, but I did not find XP listed as one of the options in grub boot menu.  The "Gparted" tool shows the following : 

/dev/sda1 : EXT3   with "/" mountpoint. used +un-used space ~16 GB 
/dev/sda2 : Extended,  size = ~60 GB 
  - /dev/sda6 : Linux -swap , 690.23 MB 
  - /dev/sda5 : NTFS, size =  59.59 GB 

5) So it looks like /dev/sda5 is  my  XP professional partition ?  After reading more about partitions, I edited the " /boot/grub/menu.lst" file to include : 

title Windows  XP
root (hd0,4)  <=== Assuming /dev/sda5 == Grub (hd0, 4) 
makeactive
chainloader +1

6) rebooting the system showed "Windows  XP" as  the  boot option,  but selecting it  said " Invalid Device"  or something. 

Questions :
1) How do  i get the XP professional partition to show up and boot ? 
2) Can I access it from Linux to make sure if it is at least intact ? 

Thanks a lot for your help!!

---

### Post by merlinus on 2009-06-20
I seriously doubt that you can run windows in a logical partition, which is what you have done.

But post results of these anyway:

```

sudo fdisk -l
cat /boot/grub/menu.lst

```

---

### Post by newbee75 on 2009-06-20
Thanks Merlinus here it is : 
$ sudo fdisk -l
[sudo] password for kota: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5763a57f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1862    14956483+  83  Linux
/dev/sda2            1863        9729    63191677+   f  W95 Ext'd (LBA)
/dev/sda5            1951        9729    62484786    7  HPFS/NTFS
/dev/sda6            1863        1950      706797   82  Linux swap / Solaris

$ cat /boot/grub/menu.lst

Partition table entries are not in disk order
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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

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

title Windows  XP
root (hd0,4)
makeactive
chainloader +1

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
# kopt=root=UUID=fdcafe03-5069-48c6-87a9-c22f2a58b5b3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=fdcafe03-5069-48c6-87a9-c22f2a58b5b3

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
# defoptions=quiet splash quiet

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

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        fdcafe03-5069-48c6-87a9-c22f2a58b5b3
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=fdcafe03-5069-48c6-87a9-c22f2a58b5b3 ro quiet splash quiet 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        fdcafe03-5069-48c6-87a9-c22f2a58b5b3
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=fdcafe03-5069-48c6-87a9-c22f2a58b5b3 ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, memtest86+
uuid        fdcafe03-5069-48c6-87a9-c22f2a58b5b3
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by merlinus on 2009-06-20
Methinks the problem is that windows will not run from a logical partition.  When partitioning for ubuntu, somehow an extended partition got created that now includes xp.

You can try supergrub to boot xp.  If that does not work, you should be able to manually mount your xp partition in ubuntu and copy your data.

---

### Post by newbee75 on 2009-06-20
Thanks a lot Merlin! I was able to at least mount the XP partition & browsee files. Will give supergrub a try.

---

