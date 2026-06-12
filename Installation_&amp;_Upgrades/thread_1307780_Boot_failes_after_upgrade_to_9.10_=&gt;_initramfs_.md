---
title: "Boot failes after upgrade to 9.10 =&gt; initramfs prompt"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by hrafninn on 2009-10-31
I just upgraded from 9.04 to 9.10.  Everything seemed to work well and I was able to login after the boot.  Then I started Opera and the system froze.  I had to turn off the computer (Dell Latitude) and restart it. After that I always get messages like (also in recovery mode):

Begin: Starting AppArmor profiles ...
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /dev on /root/dev failed: No such file or directory
...
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init=bootarg

Then I get the following prompt:

(initramfs)

What can I do?

---

### Post by slamelov on 2009-10-31
I have the same problem here. I upgraded from 9.04, after rebooting, appears that message and, of course, does not boot again.

Any help?

---

### Post by hrafninn on 2009-10-31
I did not make a backup of my data before I upgraded to 9.10 (not very wise!). 

On the other hand, I was able to recover:

1) I burned an Ubuntu 9.10 Live CD
2) I booted from the Live CD
3) In a Terminal, I typed
sudo fsck.ext3 -f /dev/sda4  (where sda4 is my Ubuntu partition). This fixed something.
4) I mounted my /dev/sda4:
sudo mkdir /mnt/ubuntu && sudo mount /dev/sda4 /mnt/ubuntu
5) Then I was able to get to the relevant data on /dev/sda4

---

### Post by slamelov on 2009-10-31
I suppose that the problem is that system does not start from hd ( I have 4 hd), but I don't know how to solve it. For any reason, upgrade changed boot disk.

---

### Post by hrafninn on 2009-10-31
I finally decided to do a clean install.

I log in, start Firefox and the system hangs! Neither Ctrl-Alt-Backspace nor Ctrl-Alt-F1 works.

What is wrong with this upgrade?

---

### Post by hrafninn on 2009-10-31
Didn't have another option but burning a 9.04 ISO and doing a clean install. Back up and running without any problems :-)

Guess I will not try upgrading to 9.10 again!

---

### Post by slamelov on 2009-11-01
Sure a clean install solve the problem, but I need to access the disk and I don't know how to do it. When I start from live, I don't know how to mount the HD

EDIT: Well, I can access to the HD with the 9.04 Live, but not with 9.10.

---

### Post by slamelov on 2009-11-01
I assume that nobody knows how to solve this...

Really, is not there any way to solve the problem without a clean install?

---

### Post by Tristan_F on 2009-11-01
> **slamelov said:**
> I suppose that the problem is that system does not start from hd ( I have 4 hd), but I don't know how to solve it. For any reason, upgrade changed boot disk.

I also got this problem. Unplugging 2 of the hardrive allowed me to boot into the system. I had afterwards to do "sudo dpkg --configure -a" because it seemed that upgrade was not finished.

I can now use the system but didn"t try to replugg my 3 other hard drives.

I have to say that using the Live CD of 9.10 to try to install the system when my 5 hardrives were plugged was not possible since the drive I wanted to install it on was not detected. It seems that 9.10 cannot find more than 2 hard drives with the live CD. for the system as I stated before I cannot say.

---

### Post by slamelov on 2009-11-01
> **Tristan_F said:**
> I also got this problem. Unplugging 2 of the hardrive allowed me to boot into the system. I had afterwards to do "sudo dpkg --configure -a" because it seemed that upgrade was not finished.

I can now use the system but didn"t try to replugg my 3 other hard drives.

I have to say that using the Live CD of 9.10 to try to install the system when my 5 hardrives were plugged was not possible since the drive I wanted to install it on was not detected. It seems that 9.10 cannot find more than 2 hard drives with the live CD. for the system as I stated before I cannot say.

I'll try it, but if I can't use 4 HD is not a solution... 
Thanks for the help, Ill tell you if solve the boot ptoblem.

---

### Post by slamelov on 2009-11-01
Before unplugging HD, I have checked the menu.lst 

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
# kopt=root=UUID=03ee0623-e91b-4b13-a285-ac700528fc99 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=03ee0623-e91b-4b13-a285-ac700528fc99

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

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		03ee0623-e91b-4b13-a285-ac700528fc99
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=03ee0623-e91b-4b13-a285-ac700528fc99 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		03ee0623-e91b-4b13-a285-ac700528fc99
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=03ee0623-e91b-4b13-a285-ac700528fc99 ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.28-16-generic
uuid		03ee0623-e91b-4b13-a285-ac700528fc99
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=03ee0623-e91b-4b13-a285-ac700528fc99 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
uuid		03ee0623-e91b-4b13-a285-ac700528fc99
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=03ee0623-e91b-4b13-a285-ac700528fc99 ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.10, memtest86+
uuid		03ee0623-e91b-4b13-a285-ac700528fc99
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 9.04, kernel 2.6.28-13-generic (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=a3c5ad4c-e754-4ed7-b626-aa5410b7b19e ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode) (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=a3c5ad4c-e754-4ed7-b626-aa5410b7b19e ro single 
initrd		/boot/initrd.img-2.6.28-13-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=a3c5ad4c-e754-4ed7-b626-aa5410b7b19e ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=a3c5ad4c-e754-4ed7-b626-aa5410b7b19e ro single 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 9.04, memtest86+ (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sde1.
title		Ubuntu 9.04, kernel 2.6.28-3-rt (on /dev/sde1)
root		(hd4,0)
kernel		/boot/vmlinuz-2.6.28-3-rt root=UUID=38fd650c-92a1-45d7-92a7-b04a07a9c907 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-3-rt
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sde1.
title		Ubuntu 9.04, kernel 2.6.28-3-rt (recovery mode) (on /dev/sde1)
root		(hd4,0)
kernel		/boot/vmlinuz-2.6.28-3-rt root=UUID=38fd650c-92a1-45d7-92a7-b04a07a9c907 ro single 
initrd		/boot/initrd.img-2.6.28-3-rt
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sde1.
title		Ubuntu 9.04, memtest86+ (on /dev/sde1)
root		(hd4,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

```

May be the problem has something to do with menu.lst , but not sure.

---

### Post by Tristan_F on 2009-11-01
Be sure to backup menu.lst before doing what I will siggest. According to your menu.lst, the root uuid for 9.10 and 9.04 doesn't seem to be the same. Maybe you can try to copy the uuid number of the 9.04 menu to the 9.10...i.e. replacing  root=UUID=03ee0623-e91b-4b13-a285-ac700528fc99 by root=UUID=a3c5ad4c-e754-4ed7-b626-aa5410b7b19e

---

### Post by slamelov on 2009-11-01
It says "Error 15 File Not Found"

---

### Post by slamelov on 2009-11-01
Unplugging HD's does not work.

I have done this:

```
root@ubuntu:/# sudo update-grub
sudo: unable to resolve host ubuntu
Searching for GRUB installation directory ... found: /boot/grub
findfs: imposible resolver «UUID=03ee0623-e91b-4b13-a285-ac700528fc99»
Cannot determine root device.  Assuming /dev/hda1
This error is probably caused by an invalid /etc/fstab
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.31-14-generic
Found kernel: /boot/vmlinuz-2.6.28-16-generic
Found kernel: /boot/memtest86+.bin
sed: advertencia: falló al obtener el contexto de seguridad de /tmp/fileZDhsgI: No hay datos disponiblessed: advertencia: falló al obtener el contexto de seguridad de /tmp/fileRg066e: No hay datos disponiblesUpdating /boot/grub/menu.lst ... done

```

And the FSTAB:

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=03ee0623-e91b-4b13-a285-ac700528fc99 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=68ce092d-7006-4df2-a22f-a13f33934811 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

I think that there is anything bad in those files, but I don't know what. I have read this link:

[https://answers.launchpad.net/ubuntu/+source/grub/+question/63005](https://answers.launchpad.net/ubuntu/+source/grub/+question/63005)

But I'm lost here:
> 
Browse to /media/root/boot/grub and look at menu.lst and make sure that references the correct sda# value.
Browse to /media/root/etc/ and look at fstab and see if the values are correct (you can also replace the uuid values with the sda# values in the comments),

How do I check references are correct?

---

### Post by slamelov on 2009-11-03
Is there anybody out there?

---

### Post by RevMike on 2009-11-03
I found a solution to this issue...

When prompted I hit ESC to get to the grub menu.  The default boot option was "**Ubuntu 9.10, kernel 2.6.31-14-generic-pae**".

On a whim, I booted the third option for me, which was "**Ubuntu 9.10, kernel 2.6.31-14-generic**".  That booted fine.  So, running under sudo I edited /boot/grub/menu.lst and made the non-pae kernel the default.  Now everything is running fine.

FYI, I am running Ubuntu under VM-Ware Fusion on a MacBook Pro with Snow Leopard.

---

### Post by slamelov on 2009-11-07
It does not work for me, but thanks anyway

---

### Post by slamelov on 2009-11-12
Any other suggestion?

---

### Post by pigphish on 2009-11-13
Had the same issue. FSCK fixed it. 

I believe the problem was that there were errors that wouldn't let the main partition mount to boot. 

I booted from a 9.10 cd and did an fsck from terminal:
```
sudo fsck /dev/sda3
```

obviously replace sda3 with your drive. Gparted may be helpful in deciding which is yours. Incidentally my grub and 9.10 partition are on sda3

Fsck found some issues which it corrected. Once the issues were gone the drive became mountable and bootable. You can check if its mountable through the places menu. Select the appropriate hard drive. Or manually mount it in the terminal. 

Hope this helps.

---

