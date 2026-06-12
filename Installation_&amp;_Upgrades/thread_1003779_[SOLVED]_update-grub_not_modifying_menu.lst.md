---
title: "[SOLVED] update-grub not modifying menu.lst"
date: 2008-12-06
forum: Installation &amp; Upgrades
---

### Post by sang137 on 2008-12-06
When I run sudo update-grub I have the following output:

```
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.27-9-generic
Found kernel: /boot/vmlinuz-2.6.27-7-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... Updating the default booting kernel
done

```

Which includes the latest kernel I have installed, 2.6.27-9, however when I look at the menu.lst file it is not there.

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
default         0

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=49380053-7cde-4262-80d4-468808609dd9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=49380053-7cde-4262-80d4-468808609dd9

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
# updatedefaultentry=true

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		49380053-7cde-4262-80d4-468808609dd9
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=49380053-7cde-4262-80d4-468808609dd9 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		49380053-7cde-4262-80d4-468808609dd9
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=49380053-7cde-4262-80d4-468808609dd9 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		49380053-7cde-4262-80d4-468808609dd9
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

I used to have startupmanager installed but I removed it in an attempt to solve this problem.  What am I doing wrong?

Thanks in advance.

---

### Post by caljohnsmith on 2008-12-06
How about posting the full session output of all the following commands:
```
sudo apt-get purge grub
sudo apt-get install grub
sudo update-grub
cat /boot/grub/menu.lst
```
That might be enough to fix the problem, but if not, we can work from there if you want.

---

### Post by sang137 on 2008-12-06
That did it.  Thanks, I guess I just screwed something up along the way.

Here is the output anyway.

```
jswhitaker@Serenity:~$ sudo apt-get purge grub
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  grub*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 938kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 113996 files and directories currently installed.)
Removing grub ...
Purging configuration files for grub ...
Processing triggers for man-db ...
jswhitaker@Serenity:~$ sudo apt-get install grub
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  grub-doc mdadm
The following NEW packages will be installed:
  grub
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/402kB of archives.
After this operation, 938kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package grub.
(Reading database ... 113944 files and directories currently installed.)
Unpacking grub (from .../grub_0.97-29ubuntu45_i386.deb) ...
Processing triggers for man-db ...
Setting up grub (0.97-29ubuntu45) ...

jswhitaker@Serenity:~$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.27-7-generic
Found kernel: /boot/memtest86+.bin
Found kernel: /boot/vmlinuz-2.6.27-9-generic
Found kernel: /boot/vmlinuz-2.6.27-7-generic
Found kernel: /boot/memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... Updating the default booting kernel
done

jswhitaker@Serenity:~$ cat /boot/grub/menu.lst
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
default         2

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=49380053-7cde-4262-80d4-468808609dd9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=49380053-7cde-4262-80d4-468808609dd9

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
# updatedefaultentry=true

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		49380053-7cde-4262-80d4-468808609dd9
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=49380053-7cde-4262-80d4-468808609dd9 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		49380053-7cde-4262-80d4-468808609dd9
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=49380053-7cde-4262-80d4-468808609dd9 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		49380053-7cde-4262-80d4-468808609dd9
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=49380053-7cde-4262-80d4-468808609dd9 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		49380053-7cde-4262-80d4-468808609dd9
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=49380053-7cde-4262-80d4-468808609dd9 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		49380053-7cde-4262-80d4-468808609dd9
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by caljohnsmith on 2008-12-06
Glad to hear that fixed it; I helped someone about a month ago who had the exact same problem as you, and that's how we ended up fixing his problem. I'm wondering if using startupmanager has anything to do with causing that glitch with the update-grub command, but I doubt it. Anyway, cheers and have fun with Ubuntu. :)

---

### Post by iconfat on 2009-02-06
I had the same problem where sudo update-grub wasnt updating my menu.lst.

caljohnsmith, your procedure fixed everything and got my kernel updated in menu.lst.

Thanks a lot!

---

### Post by afrodeity on 2011-05-01
Will this work for 11.04? Have similar problem with grub list not updating and wondering how to go about fixing it.

---

### Post by MXIIA on 2011-05-01
I'm having similar problems... 
I am using the liveCD of 11.04 to run update-grub in a chroot on my main hd (sda6) with the boot partition (sda7) mounted as boot. 

It says it works, however, on boot, it goes to grub>.

---

### Post by afrodeity on 2011-05-01
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/694040](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/694040)

---

