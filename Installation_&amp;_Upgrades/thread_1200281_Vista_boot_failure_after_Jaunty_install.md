---
title: "Vista boot failure after Jaunty install"
date: 2009-06-29
forum: Installation &amp; Upgrades
---

### Post by scott20 on 2009-06-29
I'm getting a "disk boot failure, insert system disk" when I try to boot my primary which is Vista 64 bit ultimate.  This happened when I installed Ubuntu 9.04 64-bit on a separate Hdd.  When I boot the Ubuntu partition the grub menu doesn't even appear so I can't select Vista from there.  Note: I did not resize the Vista partition. (I didn't do anything to it)

---

### Post by merlinus on 2009-06-29
Post results of:

```
sudo fdisk -l
cat /boot/grub/menu.lst
```

---

### Post by scott20 on 2009-06-29
Ok here:

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x124f3850

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      121602   976759808    7  HPFS/NTFS

Disk /dev/sdb: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4c114c10

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4795    38515806   83  Linux
/dev/sdb2            4796        5005     1686825    5  Extended
/dev/sdb5            4796        5005     1686793+  82  Linux swap / Solaris

---

### Post by merlinus on 2009-06-29
What about

cat /boot/grub/menu.lst

---

### Post by scott20 on 2009-06-29
Oh I missed that one:

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
# kopt=root=UUID=5f5f12da-41b0-45ac-a924-a173ea28cd1c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5f5f12da-41b0-45ac-a924-a173ea28cd1c

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
uuid		5f5f12da-41b0-45ac-a924-a173ea28cd1c
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=5f5f12da-41b0-45ac-a924-a173ea28cd1c ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		5f5f12da-41b0-45ac-a924-a173ea28cd1c
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=5f5f12da-41b0-45ac-a924-a173ea28cd1c ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		5f5f12da-41b0-45ac-a924-a173ea28cd1c
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by merlinus on 2009-06-29
Change the timeout line to 10.  It is now 3.

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

Place a hashmark (#) in front of hiddenmenu.  That's why you never even see it.

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

Add the following to the very end of menu.lst:

title Windows
rootnoverify (hd0,0)
makeactive
chainloader +1

Then restart.

---

### Post by scott20 on 2009-06-29
hmmm...I'm not really understanding exactly how to change those values on that menu.  Do I need to open a system file?

---

### Post by presence1960 on 2009-06-29
> **scott20 said:**
> hmmm...I'm not really understanding exactly how to change those values on that menu.  Do I need to open a system file?

open a terminal and run ```
gksu gedit /boot/grub/menu.lst
```and try merlin's suggestions.

if the windows entry doesn't boot after adding it try this :

> title         Windows
rootnoverify  (hd0,0)
map           (hd0) (hd1)
map           (hd1) (hd0)
makeactive
chainloader   +1

you may need the map lines because windows is on a different drive than linux drive which you are booting from.

---

### Post by philcamlin on 2009-06-29
> **presence1960 said:**
> open a terminal and run ```
gksu gedit /boot/grub/menu.lst
```and try merlin's suggestions.

once you change those you should be able to boot from it 
:popcorn:

---

### Post by presence1960 on 2009-06-29
change this:
```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu
```
 To:
```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu
```

---

### Post by scott20 on 2009-06-29
Ok the Grub list is displayed properly but Windows still wont boot.  When I select it from grub it displays "Starting up..." then nothing happens.

---

### Post by merlinus on 2009-06-29
If you unplug the second hdd, the one with ubuntu, from your computer, can you boot into vista?  If not, then something may be corrupted.

Another way instead of unplugging it is to remove it temporarily from your bios listing.

A third way is to use supergrub to boot vista.

[http://supergrubdisk.org]("http://supergrubdisk.org/")

And finally, you can use your vista install cd to fixmbr (or fixboot) by selecting repair (or restore) from the menu.  Then it will be easy to reinstall grub so you can boot both.

[URL="http://supergrubdisk.org"]
[/URL]

---

### Post by presence1960 on 2009-06-29
> **scott20 said:**
> Ok the Grub list is displayed properly but Windows still wont boot.  When I select it from grub is displays "Starting up..." then nothing happens.

Try 2 things. First did you add the map lines to your windows entry in menu.lst? If not do that and try to boot windows again. 

If that fails check the order of your hard disks in BIOS for boot order. If your Linux disk is set to boot before the windows disk change the windows entry to this:

```
title         Windows
rootnoverify  (hd1,0)
map           (hd0) (hd1)
map           (hd1) (hd0)
makeactive
chainloader   +1 

```

---

### Post by scott20 on 2009-06-30
Well nothing I've tried has worked yet. Looks like I'll have to either repair using vista install cd or *gulp* reinstall windows.  (That Super Grub Disk looked promising but...didn't work.)  Thanks for the help.

---

### Post by Saint_ on 2009-06-30
Paste the results of: ```
**root (hd0,0)** 
**setup (hd0)** 
```

---

