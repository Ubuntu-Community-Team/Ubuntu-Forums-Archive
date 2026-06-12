---
title: "Grub a upon restart nd Vista"
date: 2009-04-04
forum: Installation &amp; Upgrades
---

### Post by themagicmanfromtrent on 2009-04-04
I just installed Ubuntu on a computer with Vista Home Premium, and upon restart, I get the following in grub:

Ubuntu
Ubuntu Recovery
memtest
Vista
Vista

The second Vista takes me to the recovery manager for vista, in order to restore my laptop to it's original factory settings.

The first vista doesn't work. Upon selection, it just says "Starting Up..." and doesn't do anything.

Here's my fdisk -l:
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x86764515

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       33346   267851713+   7  HPFS/NTFS
/dev/sda2           37208       38913    13703445    7  HPFS/NTFS
/dev/sda3           33347       37207    31013482+   5  Extended
/dev/sda5           33347       37042    29688088+  83  Linux
/dev/sda6           37043       37207     1325331   82  Linux swap / Solaris

Partition table entries are not in disk order

```

---

### Post by namaku0 on 2009-04-04
First, please post your /boot/grub/menu.lst too.

---

### Post by themagicmanfromtrent on 2009-04-04
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
timeout		15

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
# kopt=root=UUID=59d328d5-8d88-4cfc-8f4f-673a2d3951fc ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=59d328d5-8d88-4cfc-8f4f-673a2d3951fc

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		59d328d5-8d88-4cfc-8f4f-673a2d3951fc
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=59d328d5-8d88-4cfc-8f4f-673a2d3951fc ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		59d328d5-8d88-4cfc-8f4f-673a2d3951fc
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=59d328d5-8d88-4cfc-8f4f-673a2d3951fc ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		59d328d5-8d88-4cfc-8f4f-673a2d3951fc
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader) (Recovery)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

---

### Post by meierfra. on 2009-04-04
The "starting up" error often means that the boot sector of the Visa partition is corrupted.  Did you resize the Vista partition before or during the Ubuntu installation? If yes, how?
Could you also post the output of

```
sudo fdisk -lu
```


Anyway, testdisk might be able to fix your problem: 

Download the [testdisk-6.10.linux26.tar.bz2 package](http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2) to your desktop, and then do:

```


cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static /dev/sda

```


Choose "proceed" on the first screen, then
"intel"
"advanced",
Select the Windows partition (although it should be selected already) and choose
"boot"
"RebuildBS"
"Write"  

then press "q" a few times to quit  testdisk, reboot and see whether you can boot into Vista.
 (If it does not give you an option to "write", it means that the original and rebuild boot sector are identical, and  testdisk RebuildBS won't be able to solve your problem)

---

### Post by themagicmanfromtrent on 2009-04-04
Actually, I wish I could do that, but I justed did mbrfix and bootfix through the recovery disk, and now i get the message

> A Disk Error Occured
Press Ctrl+Atl+Del to restart

---

### Post by themagicmanfromtrent on 2009-04-04
Also, when I went into the recovery disk, it displayed the vista partition as 0MB

I just booted the liveCD, and I can see all my vista files in the HD...

What now?

---

### Post by meierfra. on 2009-04-04
> but I justed did mbrfix and bootfix
Oh well. 

Boot from the Ubuntu LiveCD. Open a terminal, (Application->Accessories->Terminal)

and  reinstall grub via

```
sudo grub
root (hd0,4)
setup (hd0)
quit
```

Then follow the directions from my previous post.

Reboot and you should have the Grub menu back and should be able to boot into Ubuntu and maybe Vista.

---

### Post by themagicmanfromtrent on 2009-04-04
Okay, GRUB is back up and running!

Vista still doesn't work though.

> Did you resize the Vista partition before or during the Ubuntu installation? If yes, how?

Yup. Well I started by installing ubuntu as usual, and it auto-created a pratition for me. Half way through the installation, a friend picked up the laptop pretty fast and the HD head got interrupted and cut off the install.

I tried to re-install over that partition, but the wizard wouldn't let me so I just made another one intending to get rid of the old one after I installed. The install completed successfully, and the owner played around with ubuntu for a bit, and slowly began to love it. (muahahaha) He then asked me to cut the redundant partition in half, giving 10GB to vista and 10GB to ubuntu. In order to do this, I had to start by turning swapoff for the extended partition, and deleting the old one, then i had to move the unallocated space up one past the linux swap and next to the ubuntu partition. After doing that, I was able to increase the size of the ubuntu partition.

I did the same thing for the other unallocated space, I resized the whole extended partition bit and made it smaller, moving the unallocated space out of that bit and into the same "tree" if you like, as the ntfs partition.

But that didn't work. So I just deleted everything again, and made the ntfs partition 100%. I then re-installed ubuntu.

It now looks like this:
[img]http://img12.imageshack.us/img12/1850/gpartedm.png[/img]

These are the contents of fdisk -lu:

```

 Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x86764515

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   535703489   267851713+   7  HPFS/NTFS
/dev/sda2       597730455   625137344    13703445    7  HPFS/NTFS
/dev/sda3       535703490   597730454    31013482+   5  Extended
/dev/sda5       535703553   595079729    29688088+  83  Linux
/dev/sda6       595079793   597730454     1325331   82  Linux swap / Solaris

Partition table entries are not in disk order

```

---

### Post by meierfra. on 2009-04-04
> Vista still doesn't work though

Did "testdisk" gave you an option to write a new bootsector?

Are you still getting the "starting up" error ? Or a different error message?

---

### Post by themagicmanfromtrent on 2009-04-04
Still getting the "Starting up..." error.

These are the partitions testdisk listed:

[img]http://img228.imageshack.us/img228/6059/testdisk.png[/img]

It gave me the option to write, and I did. I'm rebooting now to see if it worked.

Cross your fingers!

---

### Post by themagicmanfromtrent on 2009-04-04
If I knew any small amount of programming (and I was an evil person), I would spend the next 3 years figuring out how to penetrate the ubuntuforums.org server and enable the "thank" feature, then precede to thank you 1000 times for 1 post.

Thank you.

---

### Post by meierfra. on 2009-04-04
> If I knew any small amount of programming (and I was an evil person), I would spend the next 3 years figuring out how to penetrate the ubuntuforums.org server and enable the "thank" feature, then precede to thank you 1000 times for 1 post.

Well, you could first spend 3 years learning how to program (which should automatically turn you into an evil person) and then continue with your above plan:lolflag:


> Thank you.
Your are welcome.

---

