---
title: "Duel boot problems"
date: 2009-06-11
forum: Installation &amp; Upgrades
---

### Post by Zero++ on 2009-06-11
I am trying to install Ubuntu 9.04 along side windows XP Pro. I have 2 hard drives a 120 gig with xp pro and a 250 gig that i am trying to install Ubuntu on. When I install ubuntu the insall is successful but I get an error 18 from GRUB when it tries to boot. One time I unhooked the Windows drive and was able to make ubuntu work. I really need the system to duel boot so I played around a little more and now I keep getting the error 18 wether I am using 2 hard drives or 1. 

I have even tried using vcom system commander with no luck

Any advice would be appreciated.

---

### Post by merlinus on 2009-06-11
With both hdds plugged in, post results of:

```

sudo fdisk -l
cat /boot/grub/menu.lst

```

---

### Post by Zero++ on 2009-06-12
Here is the results:
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb3beb3be

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14946   120053713+   7  HPFS/NTFS

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009d28a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       29953   240597441   83  Linux
/dev/sdb2           29954       30515     4514265    f  W95 Ext'd (LBA)
/dev/sdb5           29954       30515     4514233+  82  Linux swap / Solaris

Disk /dev/sdc: 1053 MB, 1053032448 bytes
2 heads, 63 sectors/track, 16323 cylinders
Units = cylinders of 126 * 512 = 64512 bytes
Disk identifier: 0x0084f599

---

### Post by Zero++ on 2009-06-12
Here is my grub menu.lst file:


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
# kopt=root=UUID=54d07ac7-c87f-4698-ad7c-af3ce8503bd0 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=54d07ac7-c87f-4698-ad7c-af3ce8503bd0

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        54d07ac7-c87f-4698-ad7c-af3ce8503bd0
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=54d07ac7-c87f-4698-ad7c-af3ce8503bd0 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        54d07ac7-c87f-4698-ad7c-af3ce8503bd0
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=54d07ac7-c87f-4698-ad7c-af3ce8503bd0 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        54d07ac7-c87f-4698-ad7c-af3ce8503bd0
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by merlinus on 2009-06-12
Looks like the install did not recognize your windows hdd and partition.

Try adding this to the very end of menu.lst:

title Windows
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1

---

### Post by Zero++ on 2009-06-12
When I try to save the file i do not have permission. (probably because I am running Live CD) Is there anyway around this?

---

### Post by martiendejong on 2009-06-12
go to terminal and type:
sudo nano /dev/sdb1/boot/grub/menu.lst

You will get a text-based editor but you should be able to find your way with it.

Good luck,
Martien

---

### Post by merlinus on 2009-06-12
```

gksudo gedit /boot/grub/menu.lst

```will give you a much easier to use editor.

But if you are using the live cd, you will not be able to access that file.  Your ubuntu partition must be mounted in order to view the correct one.

---

### Post by Zero++ on 2009-06-12
I edited the menu.lst file and am still getting the same Grub Error 18. Here is a copy of the new fdisk reading and the new menu.lst

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb3beb3be

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14946   120053713+   7  HPFS/NTFS

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009d28a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30029   241207911   83  Linux
/dev/sdb2           30030       30515     3903795    5  Extended
/dev/sdb5           30030       30515     3903763+  82  Linux swap / Solaris

Disk /dev/sdc: 1053 MB, 1053032448 bytes
2 heads, 63 sectors/track, 16323 cylinders
Units = cylinders of 126 * 512 = 64512 bytes
Disk identifier: 0x0084f599

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       16324     1028336    b  W95 FAT32






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
timeout        10

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
# kopt=root=UUID=49004e40-b2cf-470e-bc77-298f07ef82f0 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=49004e40-b2cf-470e-bc77-298f07ef82f0

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        49004e40-b2cf-470e-bc77-298f07ef82f0
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=49004e40-b2cf-470e-bc77-298f07ef82f0 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        49004e40-b2cf-470e-bc77-298f07ef82f0
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=49004e40-b2cf-470e-bc77-298f07ef82f0 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        49004e40-b2cf-470e-bc77-298f07ef82f0
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1

---

### Post by Zero++ on 2009-06-12
I know this sounds very unlinux but is there any way to use a commercial bootloader or the Win XP bootloader?

---

### Post by merlinus on 2009-06-12
Your menu.lst seems correct, but grub may not be installed correctly.  This may help:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Zero++ on 2009-06-12
Figured it out thanks for all the help

I made a 1 gig boot partition on my hdd during install

Fired right up!

---

### Post by merlinus on 2009-06-12
Glad to hear it, and I will remember this for the future should I run into a similar problem.

Happy ubuntuing!

---

