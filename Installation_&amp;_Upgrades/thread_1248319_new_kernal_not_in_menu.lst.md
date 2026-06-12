---
title: "new kernal not in menu.lst"
date: 2009-08-24
forum: Installation &amp; Upgrades
---

### Post by SteveNorman on 2009-08-24
I have 2 hard drives, on with winxp and fedora, the second with Ubuntu 9.04

I let fedora own grub since it updates kernals with allarming frequency. I usually update ubuntu, then mount my fedora hd and copy the new ubuntu menu.lst entry into the fedora menu.lst

since kernal 29-11 I have not had a new kernal show up in my ubuntu menu.lst, so I cant copy anything to fedora's grub. Especially now that ubuntu grub has that huge location id instead of the good ol hda1 type thing.

Things I have tried:
- running update-grub from fedora
- running update-grub from ubuntu

thats really all I know to do.

---

### Post by lisati on 2009-08-24
It should show up if there's a new kernel available on your system after you've run update manager. Do you still have a section in your menu.lst titled 'Automatic kernels list'?

---

### Post by SteveNorman on 2009-08-24
here is the whole dam thing:

from ubuntu
```

~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=8c93c548-9e53-4637-b557-a84661c54aa2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=8c93c548-9e53-4637-b557-a84661c54aa2

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
uuid		8c93c548-9e53-4637-b557-a84661c54aa2
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=8c93c548-9e53-4637-b557-a84661c54aa2 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		8c93c548-9e53-4637-b557-a84661c54aa2
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=8c93c548-9e53-4637-b557-a84661c54aa2 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		8c93c548-9e53-4637-b557-a84661c54aa2
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=bcff3fcd-a60d-4931-ab38-00802d3ada03 ro quiet splash vga=775 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=bcff3fcd-a60d-4931-ab38-00802d3ada03 ro single 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 8.10, kernel 2.6.24-21-generic (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=bcff3fcd-a60d-4931-ab38-00802d3ada03 ro quiet splash vga=775 
initrd		/boot/initrd.img-2.6.24-21-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 8.10, kernel 2.6.24-21-generic (recovery mode) (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=bcff3fcd-a60d-4931-ab38-00802d3ada03 ro single 
initrd		/boot/initrd.img-2.6.24-21-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 8.10, memtest86+ (on /dev/sda2)
root		(hd0,1)
kernel		/boot/memtest86+.bin  
savedefault
boot

```

---

### Post by Monkey.feets on 2009-08-24
I had a similar problem a few days ago and fixed it by backing up then deleting menu.lst and running update-grub to create a new menu.lst, new kernel showed up after....not sure how that will effect other options in your list though, I had to manually add windows option to new menu.lst and remove older kernels

---

### Post by SteveNorman on 2009-08-24
yeah I thought about that as well, I might try that tomorrow, copy my home and usr directory over to fedora then delete menu.lst.

Thanks!

---

### Post by SteveNorman on 2009-08-24
deleted old menu.lst, rebooted, did update grub, all it saw was 11 again. here is the output of update-grub

```
~$ sudo !!
sudo update-grub
[sudo] password for steve: 
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... 

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) y
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

```

the new menu.lst I just generated:

```
## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		8c93c548-9e53-4637-b557-a84661c54aa2
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=8c93c548-9e53-4637-b557-a84661c54aa2 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		8c93c548-9e53-4637-b557-a84661c54aa2
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=8c93c548-9e53-4637-b557-a84661c54aa2 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		8c93c548-9e53-4637-b557-a84661c54aa2
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

something aint right

---

### Post by ShawnKemp on 2009-08-24
I have the same issue, although mine was a new install at 2.6.28-14.  I ran apt-get dist-upgrade a few days ago, and that installed 2.6.28-15.  I noticed today after a reboot that I'm still running 2.6.28-14, so I ran grub-update and it found 2.6.28-15, but didn't modify menu.lst to include it.

I'm not sure whether this is controlled by the "updatedefaultentry" variable in menu.lst, so I tried setting that to true, but it didn't change the outcome.

```
root@server_name:/# uname -r
2.6.28-14-server
root@server_name:/# update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.28-15-server
Found kernel: /vmlinuz-2.6.28-14-server
Found kernel: /vmlinuz-2.6.28-11-server
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

root@server_name:/# grep 15 /boot/grub/menu.lst
root@server_name:/# grep 14 /boot/grub/menu.lst
title           Ubuntu 9.04, kernel 2.6.28-14-server
kernel          /vmlinuz-2.6.28-14-server root=/dev/mapper/server_name-root ro quiet splash
initrd          /initrd.img-2.6.28-14-server
title           Ubuntu 9.04, kernel 2.6.28-14-server (recovery mode)
kernel          /vmlinuz-2.6.28-14-server root=/dev/mapper/server_name-root ro  single
initrd          /initrd.img-2.6.28-14-server
root@server_name:/# cat /boot/grub/menu.lst
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
# kopt=root=/dev/mapper/server_name-root ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5#######-####-####-####-###########b

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

title           Ubuntu 9.04, kernel 2.6.28-14-server
uuid            5#######-####-####-####-###########b
kernel          /vmlinuz-2.6.28-14-server root=/dev/mapper/server_name-root ro quiet splash
initrd          /initrd.img-2.6.28-14-server
quiet

title           Ubuntu 9.04, kernel 2.6.28-14-server (recovery mode)
uuid            5#######-####-####-####-###########b
kernel          /vmlinuz-2.6.28-14-server root=/dev/mapper/server_name-root ro  single
initrd          /initrd.img-2.6.28-14-server

title           Ubuntu 9.04, kernel 2.6.28-11-server
uuid            5#######-####-####-####-###########b
kernel          /vmlinuz-2.6.28-11-server root=/dev/mapper/server_name-root ro quiet splash
initrd          /initrd.img-2.6.28-11-server
quiet

title           Ubuntu 9.04, kernel 2.6.28-11-server (recovery mode)
uuid            5#######-####-####-####-###########b
kernel          /vmlinuz-2.6.28-11-server root=/dev/mapper/server_name-root ro  single
initrd          /initrd.img-2.6.28-11-server

title           Ubuntu 9.04, memtest86+
uuid            5#######-####-####-####-###########b
kernel          /memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
root@server_name:/#
```

---

### Post by ronparent on 2009-08-24
I ran into the same problem because I had inadvertently selected not to update grub during the update. I manually edited menu.lst as admin to add the new kernel (afer verifying that the new kernel was present in /boot).

---

### Post by ShawnKemp on 2009-08-24
I just tried Monkey.feets' suggestion, and it worked, although it messed up the groot setting because I changed my boot drive to a RAID 1 after the device.map was created.   I manually updated groot and it seems to be working now.

---

### Post by SteveNorman on 2009-08-24
how do you get the info for a manual update these days? I dont get the uuid thing. Also update-grub is not even seeing the kernals

---

### Post by SteveNorman on 2009-08-25
I think the problem is with my repos, gonna start a more relevant thread. Thanks all

---

