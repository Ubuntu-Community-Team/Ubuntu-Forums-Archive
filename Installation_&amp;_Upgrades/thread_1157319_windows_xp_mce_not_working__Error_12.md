---
title: "windows xp mce not working  Error 12"
date: 2009-05-12
forum: Installation &amp; Upgrades
---

### Post by elsogan on 2009-05-12
first post ever for me ....
hi all, getting tired of windows problems i've tried ubuntu and looks good...
but ...
 
after many attemps to install ubuntu i got it right (i guess) and it's working.
now can't start in xp and got this ERROR 12 when selecting option windows xp in starting menu.
 
so after some reading here i did cat degit and sudo fdisk (see below)
 
1- this is a toshiba qosmio g15-av501r with 2 hard drives running a working xp mce on 1st hard drive (/dev/sda2) and then installed ubuntu on 2nd hard drive.
2- i can see all windows data in hd0 when booting from cd drive but partition editor doesnt show it in ubuntu.
 
any help please ?
 
thank you.
_______________________
fdisk 
 
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x261afd17
Device Boot Start End Blocks Id System
/dev/sda1 1 1 8001 7 HPFS/NTFS
/dev/sda2 * 2 7285 58508730 7 HPFS/NTFS
Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x298c4074
Device Boot Start End Blocks Id System
/dev/sdb1 * 1 284 2281198+ 83 Linux
/dev/sdb2 7739 30401 182040547+ 5 Extended
/dev/sdb3 285 7686 59456565 7 HPFS/NTFS
/dev/sdb4 7687 7738 417690 83 Linux
/dev/sdb5 30026 30401 3020188+ 82 Linux swap / Solaris
/dev/sdb6 7739 29648 175992012 83 Linux
/dev/sdb7 29649 30025 3028221 82 Linux swap / Solaris
Partition table entries are not in disk order
 
__________________________________
 
cat: degit: No such file or directory
# menu.lst - See: grub(8), info grub, update-grub(8)
# grub-install(8), grub-floppy(8),
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default 0
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu
# Pretty colours
#color cyan/blue white/blue
## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret
#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=788f6427-22c4-4f08-a82a-e5ed8d2b212d ro
## default grub root device
## e.g. groot=(hd0,0)
# groot=788f6427-22c4-4f08-a82a-e5ed8d2b212d
## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true
## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash
## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false
## Xen hypervisor options to use with the default Xen boot option
# xenhopt=
## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0
## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all
## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true
## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false
## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false
## ## End Default Options ##
title Ubuntu 8.10, kernel 2.6.27-11-generic
uuid 788f6427-22c4-4f08-a82a-e5ed8d2b212d
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=788f6427-22c4-4f08-a82a-e5ed8d2b212d ro quiet splash 
initrd /boot/initrd.img-2.6.27-11-generic
quiet
title Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid 788f6427-22c4-4f08-a82a-e5ed8d2b212d
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=788f6427-22c4-4f08-a82a-e5ed8d2b212d ro single
initrd /boot/initrd.img-2.6.27-11-generic
title Ubuntu 8.10, kernel 2.6.27-7-generic
uuid 788f6427-22c4-4f08-a82a-e5ed8d2b212d
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=788f6427-22c4-4f08-a82a-e5ed8d2b212d ro quiet splash 
initrd /boot/initrd.img-2.6.27-7-generic
quiet
title Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid 788f6427-22c4-4f08-a82a-e5ed8d2b212d
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=788f6427-22c4-4f08-a82a-e5ed8d2b212d ro single
initrd /boot/initrd.img-2.6.27-7-generic
title Ubuntu 8.10, memtest86+
uuid 788f6427-22c4-4f08-a82a-e5ed8d2b212d
kernel /boot/memtest86+.bin
quiet
### END DEBIAN AUTOMAGIC KERNELS LIST
# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root
 
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title Windows XP Media Center Edition
root (hd0,1)
savedefault
makeactive
chainloader +1
 
# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sdb1)
root (hd1,0)
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=f4d7bba6-b695-4839-9a6b-a4317be3035b ro quiet splash 
initrd /boot/initrd.img-2.6.27-7-generic
savedefault
boot
 
# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sdb1)
root (hd1,0)
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=f4d7bba6-b695-4839-9a6b-a4317be3035b ro single 
initrd /boot/initrd.img-2.6.27-7-generic
savedefault
boot
 
# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title Ubuntu 8.10, memtest86+ (on /dev/sdb1)
root (hd1,0)
kernel /boot/memtest86+.bin 
savedefault
boot
 
__________________________________

---

### Post by Pumalite on 2009-05-17
You are trying to boot Windows from a logical partition. That's a no-no.
[http://users.bigpond.net.au/hermanzone/p15.htm#12_](http://users.bigpond.net.au/hermanzone/p15.htm#12_)

---

