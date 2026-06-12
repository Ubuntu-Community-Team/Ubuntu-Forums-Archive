---
title: "Hardy, won't boot with extra HD installed"
date: 2008-05-02
forum: Hardware
---

### Post by garton on 2008-05-02
I've got an Ubuntu server with a system harddrive that boots just fine. However, when I plug in an extra harddrive it will no longer boot. This did not happen with Gutsy, which I was running up until yesterday. In gutsy everything worked fine.

I've taken a picture of the boot process when it grinds to a halt, here:

[[IMG]http://img297.imageshack.us/img297/1529/20080502me9.th.jpg[/IMG]](http://img297.imageshack.us/my.php?image=20080502me9.jpg)

The system harddrive is 120GB, the extra harddrive is 400GB. The mobo is rather old, circa 1999 I think.

---

### Post by garton on 2008-05-03
Really, no idea on this at all?

(Bump!)

---

### Post by starcannon on 2008-05-03
Are your hard drives set to cable select?

If so you likely need to set one specifically to master, and the other specifically to slave. My best guess is that they are in cable select mode, and that the new drive is grabbing master position, grub looks to it for an os that does not exist because its actually on the original 120gb drive.

GL

---

### Post by garton on 2008-05-03
> **starcannon said:**
> Are your hard drives set to cable select?

If so you likely need to set one specifically to master, and the other specifically to slave. My best guess is that they are in cable select mode, and that the new drive is grabbing master position, grub looks to it for an os that does not exist because its actually on the original 120gb drive.

GL

No, that can't be it, since the two harddrives are installed on two different IDE controllers. And this setup worked perfectly under Gutsy.

Besides, if the wrong HD took master position, wouldn't the error message be that the root partition didn't contain a valid system? 

This error makes the system freeze long before any mounting of file systems is attempted.

---

### Post by garton on 2008-05-03
Ouch! I've been lying! I didn't upgrade from Gutsy to Hardy on this machine, I upgraded from DAPPER to Hardy! Sorry.

---

### Post by pcmantinker on 2008-05-04
Make sure that you have grub configured correctly. It could be that your second hard drive is mounted as your first hard drive. Boot into your live cd and post what you have for /boot/grub/menu.lst on your primary drive.
Type:
```

sudo gedit pathtolinuxpartition/boot/grub/menu.lst #Replace pathtolinuxpartition with your physical drive location

```
Hopefully this works.

---

### Post by garton on 2008-05-06
Here you go. I haven't touched it from when I was running Dapper, so I doubt this is the source of the error.

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
# kopt=root=/dev/mapper/Ubuntu-root ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title		Ubuntu 8.04, kernel 2.6.24-16-386
root		(hd0,4)
kernel		/vmlinuz-2.6.24-16-386 root=/dev/mapper/Ubuntu-root ro
initrd		/initrd.img-2.6.24-16-386

title		Ubuntu 8.04, kernel 2.6.24-16-386 (recovery mode)
root		(hd0,4)
kernel		/vmlinuz-2.6.24-16-386 root=/dev/mapper/Ubuntu-root ro single
initrd		/initrd.img-2.6.24-16-386

title		Ubuntu 8.04, kernel 2.6.15-26-386
root		(hd0,4)
kernel		/vmlinuz-2.6.15-26-386 root=/dev/mapper/Ubuntu-root ro
initrd		/initrd.img-2.6.15-26-386

title		Ubuntu 8.04, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,4)
kernel		/vmlinuz-2.6.15-26-386 root=/dev/mapper/Ubuntu-root ro single
initrd		/initrd.img-2.6.15-26-386

title		Ubuntu 8.04, memtest86+
root		(hd0,4)
kernel		/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
frepe@berit:~$ 


```

---

### Post by garton on 2008-06-24
I'm really sorry, everyone who's spent time trying to solve this problem. I had the extra HD jumpered the wrong way. I had it set to "master with slave present" which didn't work. When I set it to "master", it worked again.

---

