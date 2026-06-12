---
title: "Error 15: File not found"
date: 2008-08-27
forum: General Help
---

### Post by xjgnsdof on 2008-08-27
I hot swapped a SATA hard drive to my computer and eventually restarted. I then got the following message:

> Error 16: Inconsistent filessystem structure
Press any key to continue

So, I booted from a LiveCD, ran fsck, answered "yes" to all of the questions, and rebooted.

Now, I get the following error message when I try to boot into Ubuntu:

> Error 15: File not found

There is no physical damage to the hard drive, as I backed up my files after this happened. What do I do now? Should I run fsck on my other partitions?

---

### Post by Taxman415a on 2008-08-27
Hmm, you didn't provide much info or say when that happened, but I'm guessing it was very early and it was a Grub error 15. Basically you need to reconfigure or reinstall Grub.
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)
Should get you there

---

### Post by xjgnsdof on 2008-08-27
Still get that error message. What now?

---

### Post by Taxman415a on 2008-08-27
With the information you have provided, it's hard to say, so I suppose the grub manual is the next step. [http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

The other possibility is that when you hot swapped the drive an important boot file got corrupted. Again, it's hard to say. You could try reinstalling or restoring your /boot directory from known good backups.

---

### Post by xjgnsdof on 2008-08-28
What other information would be helpful? I really don't want to reinstall Ubuntu and the programs I had.

---

### Post by Taxman415a on 2008-08-28
Honestly I can't even tell exactly what you did. When you say "I hot swapped a SATA hard drive to my computer and eventually restarted." What do you mean exactly, break down the steps you did. One thing to check is boot from a livecd and mount your root partition and do an ls in the /boot directory and post that here. Also post the contents of /boot/grub/menu.lst

---

### Post by xjgnsdof on 2008-08-29
My menu.lst reads as follows:

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
timeout		2

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## Splash image!
splashimage (hd0,1)/boot/grub/images/72774-hit.xpm.gz

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
# kopt=root=UUID=e0c7225e-ec0b-4b64-a5f1-1ed37b371b1d ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=e0c7225e-ec0b-4b64-a5f1-1ed37b371b1d ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=e0c7225e-ec0b-4b64-a5f1-1ed37b371b1d ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=e0c7225e-ec0b-4b64-a5f1-1ed37b371b1d ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=e0c7225e-ec0b-4b64-a5f1-1ed37b371b1d ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
makeactive
chainloader	+1
```

When I boot into 2.6.24-21-generic (even in recovery mode), I get the Error 15 message.

When I boot into 2.6.24-19-generic, the resolution is messed up, Firefox can't remember my plugin information (i.e. Forecastfox doesn't know my zip code), and I have a red icon in my taskbar that gives the following message:

```
Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Could not open file /var/lib/dpkg/status - open (2 No such file or directory), E:The package lists or status file could not be parsed or opened.'
```

---

### Post by Zimmer on 2008-08-29
Not sure if this will help, but I get an error 15 message if I try to boot if I have accidentally left my USB data drive plugged in and switched on. I have the BIOS set to look for a USB drive as first boot device, so it cannot find a boot sector on the USB data drive.. switch off drive, reset and it moves along to the internal drive.
So, if you have something USB plugged in that is just storage..and BIOS boot order set for USB before HDD then you will get an error 15.

---

### Post by xjgnsdof on 2008-08-29
My motherboard can't boot to USB drives, so that doesn't apply to my situation. I do know that it involves a SATA hard drive that I no longer have plugged in, though.

Also, I managed to fix the package manager error above by navigating to /var/lib/dpkg and changing my "status-old" file to "status." Package manager is running as we speak, but it returned the following error:

E: Internal Error, Could not perform immediate configuration (2) on libc6

---

### Post by phidia on 2008-08-29
From a live cd (seems like the easiest way) enter fdisk -l (you may need to use sudo or su depending on which live cd you're using). 
Post the output of that here.

I think what has happened is that you've changed the drive order. You could also go into bios and change the boot order there, but that may or may not work depending what your drive order actually is. 

Whenever you make a change like this your fstab will no longer be in sync with the actual drive position.

Also post your /etc/fstab file please.

---

### Post by xjgnsdof on 2008-08-29
Some outputs that might help

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfd55fd55

Device   Boot     Start     End    Blocks    Id  System
/dev/sda1  *        1        7483  60107166   7  HPFS/NTFS
/dev/sda2           7484     8456  7815622+   83  Linux
/dev/sda3           8457     19457 88365532+  83  Linux
```

```
ubuntu@ubuntu:/boot$ ls
abi-2.6.2416-generic      memtest86+.bin
config-2.6.24-16-generic  System.map-2.6.24-16-generic
initrd.img-2.6.24-16-generic.bak  vmlinuz-2.6.24-16-generic
```

---

### Post by tangibleorange on 2008-08-29
hmm yes i think the problem is that you're trying to boot into a kernel that you don't have. change -19 in your previous fstab to -16 and then try booting.

---

### Post by xjgnsdof on 2008-08-29
This sounds like it could really screw me up if I get it wrong. I've never done this, so can you walk me through it?

---

### Post by tangibleorange on 2008-08-29
> **elgilicious said:**
> This sounds like it could really screw me up if I get it wrong. I've never done this, so can you walk me through it?

yeah sure. first back up your current fstab file so you can restore it if anything goes wrong:

```
sudo cp /boot/grub/menu.lst /boot/grub/backup_menu.lst
```
now open it for editing:
```
gksu gedit /boot/grub/menu.lst
```
now replace the contents of this file with this: (don't be alarmed about the reduced size, i've simply removed all the pointless coments)
```

default		0
timeout		2

## Splash image!
splashimage (hd0,1)/boot/grub/images/72774-hit.xpm.gz

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=e0c7225e-ec0b-4b64-a5f1-1ed37b371b1d ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=e0c7225e-ec0b-4b64-a5f1-1ed37b371b1d ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

title		Microsoft Windows XP Home Edition
root		(hd0,0)
makeactive
chainloader	+1
```

and you should be good to go with that. paste it over the old contents of the file, save and then reboot. then try booting into the the first option, and see what happens! the worst that happens is that you get the same error.

---

### Post by xjgnsdof on 2008-08-29
I got the same error message. Any other ideas?

---

### Post by tangibleorange on 2008-08-29
> **elgilicious said:**
> I got the same error message. Any other ideas?

ok try this:

```
sudo cp /boot/initrd.img-2.6.24-16-generic.bak /boot/initrd.img-2.6.24-16-generic
```

then reboot.

---

### Post by xjgnsdof on 2008-08-29
I can't boot into Ubuntu anymore. I only have the option to boot using -16, and I get Error Message 15.

---

### Post by tangibleorange on 2008-08-29
> **elgilicious said:**
> I can't boot into Ubuntu anymore. I only have the option to boot using -16, and I get Error Message 15.

ah ok sorry i meant from a live cd, if that's possible. you will need to mount your ext3 ubuntu partition (probably done automatically), then change directory to the ubuntu root partition from the terminal (probably something like /media/10GB\ Volume), and then run the command.

---

### Post by xjgnsdof on 2008-08-29
On the Live CD, I mounted the root partition, but I didn't know how to change to that directory. Nevertheless, I ran the command, but I still couldn't boot into my partition.

---

### Post by tangibleorange on 2008-08-29
ok try it like this:

mount the root partition from a live cd, and then press Alt+F2 and type:

```
gksu nautilus
```

then navigate to the /boot directory of the root directory (not of the live CD - be careful it can get quite confusing), and find the file called initrd.img-2.6.24-16-generic.bak. right click copy, and the right click paste. this should make a copy of the file. then rename the new file so it looks EXACTLY like this:
```
initrd.img-2.6.24-16-generic
```

now reboot.

---

### Post by xjgnsdof on 2008-08-29
Same error message. I feel like we're onto the problem, but can't find the exact solution.

---

### Post by xjgnsdof on 2008-08-29
If nobody knows what to do, then I have no choice but to reinstall the OS and keep my home partition.

---

### Post by tangibleorange on 2008-08-30
> **elgilicious said:**
> If nobody knows what to do, then I have no choice but to reinstall the OS and keep my home partition.

sorry mate but i think i'm out of ideas. that's the great thing about a home partition though :lolflag:!

---

### Post by xjgnsdof on 2008-08-30
I reinstalled the OS. Thanks for the advice.

---

