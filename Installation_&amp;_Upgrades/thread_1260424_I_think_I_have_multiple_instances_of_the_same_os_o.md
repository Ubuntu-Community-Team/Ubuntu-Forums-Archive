---
title: "I think I have multiple instances of the same os on my machine"
date: 2009-09-07
forum: Installation &amp; Upgrades
---

### Post by cc.chapman on 2009-09-07
My (IBM ThinkPad R61i) laptop came pre-installed with SUSE Linux which I later decided I did not like (ran too slow, poor interface).  This past January I switched to Ubuntu (Intrepid Ibex).  I was very happy with it and when Janty Jackalope became available, I decided to upgrade.  I think somehow in installing new os, the old ones did not get fully deleted.

This is what my pre-startup screen looks like:

Ubuntu 9.04, kernel 2.6.28- 15 generic
Ubuntu 9.04, kernel 2.6.28- 15 generic (recovery mode)
Ubuntu 9.04, kernel 2.6.28- 14 generic
Ubuntu 9.04, kernel 2.6.28- 14 generic (recovery mode)
Ubuntu 9.04, kernel 2.6.28- 13 generic
Ubuntu 9.04, kernel 2.6.28- 13 generic (recovery mode)
Ubuntu 9.04, kernel 2.6.28- 11 generic
Ubuntu 9.04, kernel 2.6.28- 11 generic (recovery mode)
Ubuntu 9.04, memtest 86+
Other operating systems:
SUSE Linux Enterprise Desktop 10 - 2.6.16.54-0.2.5 (on /dev/sda2)
Failsafe SUSE Linux Enterprise Desktop 10 - 2.6.16.54-0.2.5 (on /dev/sda2)
Linux (on /dev/sda2)
Failsafe Linux (on /dev/sda2)


Is there anything I can do to shorten this list, it seems like I have too many os options taking up valuable space?

---

### Post by Whiffle on 2009-09-07
Could you post the output of "sudo fdisk -l"

---

### Post by cc.chapman on 2009-09-07
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ef029

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            1247        1483     1903702+  82  Linux swap / Solaris
/dev/sda2   *           1        1246    10008463+  83  Linux
/dev/sda3            1484        1696     1710922+  83  Linux
/dev/sda4            1697        9729    64525072+   5  Extended
/dev/sda5            1697        9396    61850218+  83  Linux
/dev/sda6            9397        9729     2674791   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by drs305 on 2009-09-07
Since you don't have repetitive kernels, it is more likely you have just updated and haven't modified your menu.lst or removed older kernels you no longer need. As newer kernels are released, old kernels continue to display on the menu until you make a change.

Here is a link that explains it and gives guidance on what you can do to change the menu:
[HOWTO: Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by Whiffle on 2009-09-07
Looks to me like you might have more than one linux install on there.  Could you post up your /boot/grub/menu.lst file ?

---

### Post by cc.chapman on 2009-09-07
I'm not sure if this is what you wanted (/boot/grub/menu.lst file):

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
# kopt=root=UUID=859ea41a-fb12-4bd0-8888-41857772d152 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=859ea41a-fb12-4bd0-8888-41857772d152

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
# howmany=2

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
# updatedefaultentry=true

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		859ea41a-fb12-4bd0-8888-41857772d152
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=859ea41a-fb12-4bd0-8888-41857772d152 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		859ea41a-fb12-4bd0-8888-41857772d152
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=859ea41a-fb12-4bd0-8888-41857772d152 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		859ea41a-fb12-4bd0-8888-41857772d152
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=859ea41a-fb12-4bd0-8888-41857772d152 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		859ea41a-fb12-4bd0-8888-41857772d152
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=859ea41a-fb12-4bd0-8888-41857772d152 ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, memtest86+
uuid		859ea41a-fb12-4bd0-8888-41857772d152
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		SUSE Linux Enterprise Desktop 10 - 2.6.16.54-0.2.5 (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.16.54-0.2.5-smp root=/dev/sda2 vga=0x314 resume=/dev/sda1 splash=silent showopts 
initrd		/boot/initrd-2.6.16.54-0.2.5-smp
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Failsafe -- SUSE Linux Enterprise Desktop 10 - 2.6.16.54-0.2.5 (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.16.54-0.2.5-smp root=/dev/sda2 vga=normal showopts ide=nodma apm=off acpi=off noresume nosmp noapic maxcpus=0 edd=off 
initrd		/boot/initrd-2.6.16.54-0.2.5-smp
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Linux (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz root=/dev/sda2 vga=0x314 resume=/dev/sda1 splash=silent showopts 
initrd		/boot/initrd-2.6.16.54-0.2.5-smp
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Failsafe (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz root=/dev/sda2 vga=normal showopts ide=nodma apm=off acpi=off noresume nosmp noapic maxcpus=0 edd=off 3 
initrd		/boot/initrd-2.6.16.54-0.2.5-smp
savedefault
boot

---

### Post by Hobgoblin on 2009-09-07
> **cc.chapman said:**
> 
This is what my pre-startup screen looks like:

Ubuntu 9.04, kernel 2.6.28- 15 generic
Ubuntu 9.04, kernel 2.6.28- 15 generic (recovery mode)
Ubuntu 9.04, kernel 2.6.28- 14 generic
Ubuntu 9.04, kernel 2.6.28- 14 generic (recovery mode)
Ubuntu 9.04, kernel 2.6.28- 13 generic
Ubuntu 9.04, kernel 2.6.28- 13 generic (recovery mode)
Ubuntu 9.04, kernel 2.6.28- 11 generic
Ubuntu 9.04, kernel 2.6.28- 11 generic (recovery mode)
Ubuntu 9.04, memtest 86+
Other operating systems:
SUSE Linux Enterprise Desktop 10 - 2.6.16.54-0.2.5 (on /dev/sda2)
Failsafe SUSE Linux Enterprise Desktop 10 - 2.6.16.54-0.2.5 (on /dev/sda2)
Linux (on /dev/sda2)
Failsafe Linux (on /dev/sda2)


Is there anything I can do to shorten this list, it seems like I have too many os options taking up valuable space?

The Ubuntu 9.04 options are older kernels which have been updated, not complete installations.

You can trim that list down by editing menu.lst or by installing startup manager and selecting the number of kernels to be shown.

As for the SUSE entries, it looks like you installed alongside the previous installation, not over the top of it.

---

### Post by raymondh on 2009-09-07
If you want to be lazy (like me, today :) ), download and install startupmanager (search for it in synaptic).  It is GUI and writes to the menu.lst.  In SUM, you can set defaults, no. of kernels to show, etc.

---

### Post by drs305 on 2009-09-07
Ubuntu Entries:

The first post you made said your menu showed 4 kernels, their associated recovery modes, and a memtest86+ entry. The menu.lst you posted only includes 2 of those kernels, plus memtest86+. Did you just not post the complete menu.lst?

In any case, you probably only need 2 kernels, so it would be safe to remove the menu items for -13 and -11 (it they exist). You can remove the with synaptic, which would automatically remove them and their recovery modes from the menu.lst. In synaptic, look for "vmlinuz-2.6.28-13-generic: and "vmlinuz-2.6.28-11-generic". You can also remove the associated header packages. An easy way to find the related packages is to type "2.6.28-11-generic" in the search window.

If you don't want to remove the kernels from your machine but want to remove them from the menu, use Startup-Manager (see my first post).

As for the Suse entries, it appears you have a SUSE install and recovery mode on sda2. I can't positively say all four entries refer to the same installation but it appears so to me. The all refer to the same kernel on the same partition. It seems unlikely you would have two separate installs on the same partition, which means the last two entries are repetitive and can probably be safely removed from your menu. To be safe, you could just put a # symbol at the start of each line of the last two sections. They will disappear from your menu but will still be there if you decide you need them. 

Someone familiar with SUSE can elaborate on the entries and whether it is possible to have two installs on the same partition (unlikely) but in any case it would be safe to "comment out" the last two to immediately reduce the size of your menu.lst.

---

