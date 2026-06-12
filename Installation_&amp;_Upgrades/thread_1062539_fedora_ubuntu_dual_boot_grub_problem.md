---
title: "fedora ubuntu dual boot grub problem"
date: 2009-02-07
forum: Installation &amp; Upgrades
---

### Post by AutoC on 2009-02-07
HI,

I had ubuntu preinstalled on my system.I then installed fedora on another partition.I added a grub entry in /boot/grub/grub.conf for ubuntu by copying everything from menu.lst.It doesnt work.I've already looked at all possible posts relating to this.None have helped.Any help is appreciated

I did a find /sbin/init on the grub. It finds only (hd0,4).It hasnt located ubuntu
I mounted my ubuntu partition
here is my /boot/grub/menu.lst

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
timeout		3

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
# kopt=root=UUID=21af83fa-3999-4955-8590-ad156da80f6f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=21af83fa-3999-4955-8590-ad156da80f6f

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		21af83fa-3999-4955-8590-ad156da80f6f
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=21af83fa-3999-4955-8590-ad156da80f6f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		21af83fa-3999-4955-8590-ad156da80f6f
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=21af83fa-3999-4955-8590-ad156da80f6f ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		21af83fa-3999-4955-8590-ad156da80f6f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=21af83fa-3999-4955-8590-ad156da80f6f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		21af83fa-3999-4955-8590-ad156da80f6f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=21af83fa-3999-4955-8590-ad156da80f6f ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		21af83fa-3999-4955-8590-ad156da80f6f
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

here is my /boot/grub/grub.conf
```

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd0,4)
#          kernel /boot/vmlinuz-version ro root=/dev/sda5
#          initrd /boot/initrd-version.img
#boot=/dev/sda
default=0
timeout=5
splashimage=(hd0,0)/boot/grub/splash.xpm.gz
hiddenmenu
title Fedora Core (2.6.18-1.2798.fc6)
	root (hd0,4)
	kernel /boot/vmlinuz-2.6.18-1.2798.fc6 ro root=LABEL=/ rhgb quiet
	initrd /boot/initrd-2.6.18-1.2798.fc6.img

title           Ubuntu 8.10, kernel 2.6.27-9-generic
root           (hd0,0)
kernel          /boot/vmlinuz-2.6.27-9-generic root=UUID=21af83fa-3999-4955-8590-ad156da80f6f ro quiet splash
initrd          /boot/initrd.img-2.6.27-9-generic

```

#fdisk -l
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7295    58597056   83  Linux
/dev/sda2            7296        7544     2000092+  83  Linux
/dev/sda3            7545       12407    39062047+  83  Linux
/dev/sda4           12408       19457    56629125    5  Extended
/dev/sda5           12408       19164    54275571   83  Linux
/dev/sda6           19165       19419     2048256   82  Linux swap / Solaris

```

Thanks for any help

---

### Post by zvacet on 2009-02-07
[Reinstall grub]("http://ubuntuforums.org/showthread.php?t=224351&highlight=grub") and when you done it 

```
gksudo gedit /boot/grub/menu.lst
```

and below of this line

### END DEBIAN AUTOMAGIC KERNELS LIST

add 

title          Fedora
rootnoverify (hd0,4)
makeactive
chainloader +1

save and close file and you should be fine.

---

### Post by caljohnsmith on 2009-02-07
In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your desktop, and then do the following as **root user**, but replace <username> with your username:
```
bash /home/[COLOR="Blue"]<username>[/COLOR]/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post. That will help clarify your setup and hopefully what the solution to your problem might be.

---

