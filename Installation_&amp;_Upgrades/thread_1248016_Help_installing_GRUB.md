---
title: "Help installing GRUB"
date: 2009-08-23
forum: Installation &amp; Upgrades
---

### Post by jonny1 on 2009-08-23
Hi,

I appear to be having some problems installing GRUB. My current OS is Windows 7. When installing Ubuntu, I chose the location to install Grub to the same partition on which Windows 7 was installed (sdb2).

After the installation was complete, I did not see the GRUB boot loader screen that I was expecting. Instead, I got a Windows error message informing me that Windows could not boot because the device was inaccessible. Upon further examination, the drive containing Windows (sdb2) was somehow messed up, and could not be accessed in either Ubuntu (running from the LiveCD) or from command prompt (running from Win7 disc), though it was visible. A simple startup repair allowed me to boot into windows and fix the Windows partition.

To help illustrate my hard drive partitions, see below (sudo fdisk -l)

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          13      102400    7  HPFS/NTFS. **System Reserved (Win7**)
/dev/sdb2              14       54505   437706990    7  HPFS/NTFS **Win7 OS**
/dev/sdb3           60879      121601   487750656    7  HPFS/NTFS** Data (no OS)**
/dev/sdb4           54506       60878    51191122+   5  Extended **Logical partition which contains sdb5, sdb6 and sdb7**
/dev/sdb5           54506       56417    15358108+  83  Linux **Ubuntu OS folder (/)**
/dev/sdb6           60114       60878     6144831   82  Linux swap / Solaris **Swap partition**
/dev/sdb7           56418       60113    29688088+  83  Linux **(/home)**


So now I have Ubuntu installed, but not GRUB, with Win7 booting normally. I assume that GRUB has now been overwritten by Windows, since when I check GRUB in terminal by typing **find /boot/grub/stage1 **I get a "File not found" error. IIRC, before I did the Win7 startup repair, I would get hd(1,4).

My question is, how do I now install GRUB correctly, and more importantly, to which partition would I install it to? Was I initially correct in installing it to sdb2?

---

### Post by stlsaint on 2009-08-23
you need to re-install GRUB to mbr...try super grub disk!!

---

### Post by jonny1 on 2009-08-23
Ok, I followed the instructions here [http://webupd8.blogspot.com/2009/05/fix-restore-grub-boot-loader.html](http://webupd8.blogspot.com/2009/05/fix-restore-grub-boot-loader.html) and now GRUB is working! Now all I need to do is add Windows to the GRUB loader...

---

### Post by stlsaint on 2009-08-23
post your menu.lst here....

sudo gedit /boot/grub/menu.lst in terminal

---

### Post by jonny1 on 2009-08-23
Ok, here is my menu.lst file.

> 
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
# kopt=root=UUID=55fbbdd5-a04a-429e-a753-1ba44bc3e83c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=55fbbdd5-a04a-429e-a753-1ba44bc3e83c

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
uuid        55fbbdd5-a04a-429e-a753-1ba44bc3e83c
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=55fbbdd5-a04a-429e-a753-1ba44bc3e83c ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        55fbbdd5-a04a-429e-a753-1ba44bc3e83c
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=55fbbdd5-a04a-429e-a753-1ba44bc3e83c ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        55fbbdd5-a04a-429e-a753-1ba44bc3e83c
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Windows 7
rootnoverify    (hd1,2)
savedefault
map        (hd1) (hd0)
map        (hd0) (hd1)
chainloader    +1


I was trying to boot to Win7 using the last entry. My BIOS is set to boot from hd1(sdb) and not hd0(sda) if that helps, where Windows is the second partition (though you can probablt tell from my first post).

---

### Post by nhanquy on 2009-08-23
Get rid of :
map        (hd1) (hd0)
map        (hd0) (hd1)

---

### Post by jonny1 on 2009-08-23
So I deleted the 2 map lines.

When I have it set so
rootnoverify    (hd1,2)
then I get a message telling me that there is no such partition.

I then tried changing it to
rootnoverify    (hd0,2)
but that also gives me an error message that the "bootmgr is missing"

**EDIT: **Thanks everyone for your help. I found that the correct value to load Windows was
rootnoverify    (hd0,0)
through trial and error.

---

