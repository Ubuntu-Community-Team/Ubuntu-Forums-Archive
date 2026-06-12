---
title: "Alienware Area51 RAID 0"
date: 2006-11-15
forum: Hardware &amp; Laptops
---

### Post by SupaRice on 2006-11-15
Howdy!

This is my first post, although I've been lurking for a while.  I've been using Ubuntu on my existing laptop for a while, and I'm very excited about it as I'm a long time Debian user. :D 

I've just got my new Alienware Area51 laptop in, and I'm super excited about it.  Only I'm having a problem getting Ubuntu installed properly.  It has a VIA RAID controller, and two drives in a RAID 0 drive aray.  However, when I got to install Ubuntu it sees each drive indedpendant of the array.  I've got to say, I'm not exactly a n00b but I'm no expert either. :-| 

I've searched the forums a bit, but haven't found anything that looks like my problem.  Any ideas?

Thanks in advance for any help!

---

### Post by SupaRice on 2006-11-16
Well, did some more digging, and found [https://help.ubuntu.com/community/FakeRaidHowto]("https://help.ubuntu.com/community/FakeRaidHowto") in another thread.

I'm almost there!

I get a "Error 15: File not found" when I choose Ubuntu to boot.

I figure I've messed up my grub config somewhere, so I'm trying to mount the drives after booting from the live CD to alter the config.

Here is my grub config:
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

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
password --md5 $1BHNKOi1$nKcoqvcZUGHh6TJCLlEu4.
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
# kopt=root=/dev/mapper/via_ihgbjfbde6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=true

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
title Windows XP
rootnoverify (hd0,0)
chainloader +1

title           Ubuntu, kernel 2.6.15-27-686
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.15-27-686 root=/dev/mapper/via_ihgbjfbde6 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-686
boot

title           Ubuntu, kernel 2.6.15-27-686 (recovery mode)
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.15-27-686 root=/dev/mapper/via_ihgbjfbde6 ro single
initrd          /boot/initrd.img-2.6.15-27-686
boot

title           Ubuntu, memtest86+
root            (hd0,4)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

```

And this is my partition table:
```

Disk /dev/mapper/via_ihgbjfbde: 160.0 GB, 160052722688 bytes
255 heads, 63 sectors/track, 19458 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

                    Device Boot      Start         End      Blocks   Id  System
/dev/mapper/via_ihgbjfbde1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/mapper/via_ihgbjfbde2           12749       13053     2449912+  83  Linux
/dev/mapper/via_ihgbjfbde3           13054       19458    51448162+   5  Extended
/dev/mapper/via_ihgbjfbde5           13054       13115      497983+  83  Linux
/dev/mapper/via_ihgbjfbde6           13116       19458    50950116   83  Linux

Command (m for help):

```

And this is my /etc/fstab
```

root@ubuntu:/# cat /etc/fstab
#FileSystem                     MountPoint      Type       Options                      Dump/Pass
proc                            /proc           proc       defaults                     0 0
/dev/mapper/via_ihgbjfbde6      /               ext3       defaults,errors=remount-ro   0 1
/dev/mapper/via_ihgbjfbde5      /boot           ext3       defaults,errors=remount-ro   0 2
/dev/mapper/via_ihgbjfbde2      none            swap       sw                           0 0


```

So can anyone tell me what bone headed thing I've done wrong?  I'm really stuck here.

---

### Post by SupaRice on 2006-11-17
Typo in my menu.lst, works now!

WHOOOHOOO :D

---

