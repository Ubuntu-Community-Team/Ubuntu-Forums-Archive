---
title: "Unable to boot into windows"
date: 2009-08-12
forum: Hardware
---

### Post by Audiomad on 2009-08-12
I just installed ubuntu 9.04 on my portable hard drive all is working ok but for one major problem I cant boot windows unless the portable drive is connected even going through the bios setup, once the drive is connected I can boot into windows I get 5 options to pick from, I get a grub error when its not plugged in "grub 1.5 error 17". I use the drive for work and bring it around with me realy need to get this back to the way it was I want to keep ubuntu but windows needs to be the main os.

Please help

---

### Post by AggravatedGestalt on 2009-08-12
I myself just installed WindowsXP and had to boot Ubuntu via live CD to reinstall the GRUB and MBR (master boot record). That all worked well enough, though now I cannot boot in WindowsXP. Can anyone help with this dual boot? 
PS: How does one start a new post or thread on these forums? I see no option for this.

---

### Post by ZaHACKieL on 2009-08-12
> **AggravatedGestalt said:**
> 
PS: How does one start a new post or thread on these forums? I see no option for this.

Just go to the forum category and you will see a New Thread button on the top part

---

### Post by Audiomad on 2009-08-12
help anyone?

---

### Post by AggravatedGestalt on 2009-08-12
I thought I should mention that fdisk -l shows the following for me:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0a2ded7c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12158    97659103+  83  Linux
/dev/sda2           12159       13131     7815622+   5  Extended
/dev/sda3           13132       30400   138713242+   7  HPFS/NTFS
/dev/sda5           12159       13131     7815591   82  Linux swap / Solaris

I have tried all sorts of things in menu.list, and most instructions use "hd0,0" or hd rather sda. I am quite confused about this. So far, I've restarted 20+ times cheking the results. The windows option shows, but I get an error when attempting to boot. Below is my menu.list configuration which I have mangled. After I reinstalled grub from live cd, there was no Windows entry, so the two at the bottom are some of my many attempts.

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
timeout        9

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
# kopt=root=UUID=0336c27d-039c-4867-b6d5-6be02ec39442 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=0336c27d-039c-4867-b6d5-6be02ec39442

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

title        Ubuntu 9.04, kernel 2.6.28-14-generic
uuid        0336c27d-039c-4867-b6d5-6be02ec39442
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=0336c27d-039c-4867-b6d5-6be02ec39442 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid        0336c27d-039c-4867-b6d5-6be02ec39442
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=0336c27d-039c-4867-b6d5-6be02ec39442 ro  single
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        0336c27d-039c-4867-b6d5-6be02ec39442
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=0336c27d-039c-4867-b6d5-6be02ec39442 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        0336c27d-039c-4867-b6d5-6be02ec39442
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=0336c27d-039c-4867-b6d5-6be02ec39442 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        0336c27d-039c-4867-b6d5-6be02ec39442
kernel        /boot/memtest86+.bin
quiet
 
title Windows XP
rootnoverify (sda,2)
makeactive
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST

title        Windows NT/2000/XP
rootnoverify        (hd0,0)
savedefault
makeactive
map        (sda2) (sda3)
map        (sd1) (sd0)
chainloader    boot

---

### Post by AggravatedGestalt on 2009-08-12
I have fixed mine and am able to choose my boot options after changing the following:

### END DEBIAN AUTOMAGIC KERNELS LIST

title Windows XP Professional
root (hd0,2)
savedefault
chainloader +1

Note: I deleted the reference to Windows just above the ###END DEBIAN AUTOMAGIC KERNELS LIST, thus leaving the above as the only Windows entry. 
I hope this helps someone else; it's been a wretched task for myself.

---

### Post by Audiomad on 2009-08-13
No one? why are people aloud to hijack threads on this site?

---

### Post by AggravatedGestalt on 2009-08-15
Please pardon my error. I was intending to both help and receive help. I find the Ubuntu forums a bit confusing and apologize.

---

### Post by mickwombat on 2009-10-09
Audiomad,

Are you still having this issue?  When you try to boot without the external drive, does it still give you some options & when you choose it fails?  Or is it just not booting at all.

Post the output of > sudo fdisk -l

Cheers

---

### Post by adrian15 on 2009-10-15
> **Audiomad said:**
> once the drive is connected I can boot into windows I get 5 options to pick from,

Please check: [http://www.supergrubdisk.org/w/index.php5?title=GrubOnRemovableExternalHardDisk](http://www.supergrubdisk.org/w/index.php5?title=GrubOnRemovableExternalHardDisk)

adrian15

---

