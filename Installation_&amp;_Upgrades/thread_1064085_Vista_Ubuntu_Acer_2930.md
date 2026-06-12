---
title: "Vista Ubuntu Acer 2930"
date: 2009-02-08
forum: Installation &amp; Upgrades
---

### Post by retrodans on 2009-02-08
I have recently got a new laptop (Acer 2930).  It came with Vista, which I want to keep for various gaming reasons, as well as for quick setup by the work IT team that aren't Linus savvy.

Anyway, Vista works fine, so I install Ubuntu on a new partition, Ubuntu then works fine.  BUT when I log back into vista, it takes me to a vista recovery page, and if it recovers, I can no longer access vista.  So it seems I can only have one or the other.

I have mounted my c:, and the windows system is still there, as is the user account I was using, so it has not been removed.  Acer comes with a recovery partition, and I have a feeling grub is pointing to this rather than my real Vista account, although I don't know for sure.  anCan anyone help, as of course, I would like to have both, and currently whilst I sort this, I haven't set up either.

Thankyou for your help,
Dan

---

### Post by logos34 on 2009-02-08
post the output of

sudo fdisk -l

and

cat /boot/grub/menu.lst

that should tell us where grub is pointing

---

### Post by retrodans on 2009-02-08
sudo fdisk -l
[HTML]Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6a47d0d0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1306    10490413+  27  Unknown
/dev/sda2   *        1307       20110   151041024    7  HPFS/NTFS
/dev/sda3           20110       20502     3145796   82  Linux swap / Solaris
/dev/sda4           20503       38913   147886357+   5  Extended
/dev/sda5           20503       38913   147886326   83  Linux
[/HTML]

cat /boot/grub/menu.lst
[HTML]# menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=ae8ebe98-8b37-41b0-be08-72f803ec8894 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ae8ebe98-8b37-41b0-be08-72f803ec8894

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		ae8ebe98-8b37-41b0-be08-72f803ec8894
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=ae8ebe98-8b37-41b0-be08-72f803ec8894 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		ae8ebe98-8b37-41b0-be08-72f803ec8894
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=ae8ebe98-8b37-41b0-be08-72f803ec8894 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		ae8ebe98-8b37-41b0-be08-72f803ec8894
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ae8ebe98-8b37-41b0-be08-72f803ec8894 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		ae8ebe98-8b37-41b0-be08-72f803ec8894
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ae8ebe98-8b37-41b0-be08-72f803ec8894 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		ae8ebe98-8b37-41b0-be08-72f803ec8894
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1
[/HTML]

---

### Post by logos34 on 2009-02-08
well, you've got two vista entries.  Are they both appearing on the menu screen and can you choose the second? (the latter is the one you want, it points to 'hd0,1', which is sda2, the vista c: partition)

maybe rename them 'Windows Vista (Recovery)' and 'Windows Vista (on /dev/sda2)' to distinguish them

sudo gedit /boot/grub/menu.lst

---

### Post by retrodans on 2009-02-09
Awesome, thankyou for that, it solved my problem a dream.  How did you know the c: was hd0,1 though, just so I understand in the future.

Cheers,
Dan

---

### Post by ratmandall on 2009-02-09
> **retrodans said:**
> Awesome, thankyou for that, it solved my problem a dream.  How did you know the c: was hd0,1 though, just so I understand in the future.

Cheers,
Dan
The grub line 
```
root		(hd0,1)

```
Is pointing to the second partition on your hard-disk which is.
```

/dev/sda2   *        1307       20110   151041024    7  HPFS/NTFS
NOTE:grub counts from 0 on-wards

```
And windows file-systems in this day and age are usually "NTFS", so I'm assuming that's how 'logos34' figured it out.

---

### Post by retrodans on 2009-06-08
I have now got a similar problem on an XP machine at work.  I have installed Ubuntu, and got GRUB to display, but it isn't showing my XP boot.

I don't know what disk to put for XP, or whether all the other values are the same.  I can see that my NTFS drive is on sdb2, which is a seperate unpartitioned drive, but what do I put into grub to run this?

sudo fdisk -l
```

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18657   149862321   83  Linux
/dev/sda2           18658       19452     6385837+   5  Extended
/dev/sda5           18658       19452     6385806   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000081

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9725    78116031    7  HPFS/NTFS

```



grub
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
# hiddenmenu

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=UUID=99a61784-4670-4e0f-9c50-7df0e09acf01 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=99a61784-4670-4e0f-9c50-7df0e09acf01

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		99a61784-4670-4e0f-9c50-7df0e09acf01
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=99a61784-4670-4e0f-9c50-7df0e09acf01 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		99a61784-4670-4e0f-9c50-7df0e09acf01
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=99a61784-4670-4e0f-9c50-7df0e09acf01 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.27-7-generic
uuid		99a61784-4670-4e0f-9c50-7df0e09acf01
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=99a61784-4670-4e0f-9c50-7df0e09acf01 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-7-generic (recovery mode)
uuid		99a61784-4670-4e0f-9c50-7df0e09acf01
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=99a61784-4670-4e0f-9c50-7df0e09acf01 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 9.04, memtest86+
uuid		99a61784-4670-4e0f-9c50-7df0e09acf01
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

I tried adding the below, but if I try it, it just shows 'Starting Up ...' on screen and doesn't do anything.  I hope it hasn't messed up my XP install, as I really do need it for all my Adobe CS4 apps.
```

title		Windows XP
root		(hd1,0)
savedefault
makeactive
chainloader	+1

```

Thankyou for your help,
Dan

---

### Post by logos34 on 2009-06-08
Booting Windows on a separate disk requires some trickery---need to fool XP into thinking it's the boot disk, otherwise it refuses to start.  So add this to your entry:

> title Windows XP
root (hd1,0)
savedefault
makeactive
[COLOR="Red"]map (hd0) (hd1)
map (hd1) (hd0)[/COLOR]
chainloader +1

---

### Post by retrodans on 2009-06-08
I am now getting an error message when I try the XP login saying 

> NTLDR is missing
Press CTRL + ALT + DEL to restart

This is a windows error message, a bit concerned my XP install is fried, will continue to look, but if you know of any info on this, that would be great.

---

### Post by logos34 on 2009-06-08
relax, windows can't be fried

[http://tinyempire.com/notes/ntldrismissing.htm](http://tinyempire.com/notes/ntldrismissing.htm)

---

### Post by retrodans on 2009-06-08
Thankyou for your help, sadly I had to leave the office so wont be able to continue till wednesday, but I have managed to get into XP via safemode (with 2nd option) and copied the files.  I then went to reboot with 2nd, and got an error, I was trying again with the 1st when I had leave.

Thankyou again for your help, will keep you updated with whether it was all successful.

Cheers,
Dan

---

