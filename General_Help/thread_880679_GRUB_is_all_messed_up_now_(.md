---
title: "GRUB is all messed up now :("
date: 2008-08-05
forum: General Help
---

### Post by jrharvey on 2008-08-05
Ok so i recently posted this thread [http://ubuntuforums.org/showthread.php?t=878412](http://ubuntuforums.org/showthread.php?t=878412)
Since then i have reinstalled windows XP and got it working. Obviously windows wrote over the MBR so I pop in my super grub disk and go through the steps to repair it. Soooo, i reboot and grub pops up (YAY) but when i choose to boot Ubuntu I get an error that its an unknown file system and i must reboot. Ok so then I reboot and try to start windows from my grub menu and it tells me the same thing. I went back into the Ubuntu live CD just to make sure all my files were still there and they are. Im assuming grub is messed up because the partition labels changed and now hda0,2 (is hda0,4 and all that jazz. Honestly im not even sure the ubuntu and windows partition labels even changed but they may have. What can i do here? I really dont want to have to reinstall ubuntu all over again.

---

### Post by hal8000 on 2008-08-05
Ideally you need to mount the / filesystem and post the contents of /boot/grub/menu.lst but as you dont know which is your root filesystem we'll have to ask your computer.
So boot with the live hardy CD then post the contents of:


fdisk -l

---

### Post by jrharvey on 2008-08-05
> **hal8000 said:**
> Ideally you need to mount the / filesystem and post the contents of /boot/grub/menu.lst but as you dont know which is your root filesystem we'll have to ask your computer.
So boot with the live hardy CD then post the contents of:


fdisk -l

Hmmm I really wish i could, im at work right now. Do you think you know a possible solution and i could ask you later? Sorry, i know i should have waited but im anxious to know if anyone thinks they can help me fix this.

---

### Post by caljohnsmith on 2008-08-05
Based on your description, I don't think you need to anxious at this point since it sounds like fixing your problem will be simple. :) To help us troubleshoot your problem, do like hal8000 said and post the output of the following from the Live CD:
```
sudo fdisk -l
```

---

### Post by jrharvey on 2008-08-05
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002bd71

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3824    30716248+   7  HPFS/NTFS
/dev/sda2   *        7649       11472    30716280   83  Linux
/dev/sda3           11473       30401   152047192+   5  Extended
/dev/sda4            3825        7648    30716280    7  HPFS/NTFS
/dev/sda5           11473       12492     8193118+  82  Linux swap / Solaris
/dev/sda6           12493       30401   143854011    7  HPFS/NTFS

Partition table entries are not in disk order
``` This is what i get.

---

### Post by caljohnsmith on 2008-08-05
So /dev/sda2 looks like your Ubuntu partition, so in Grub's World, since numbering begins with zero, that would be (hd0,1). Try changing the entries in your /boot/grub/menu.lst for Ubuntu to use (hd0,1). If you are unsure how to do that, just do the following:

Since you can't boot into Ubuntu right now, you'll need to boot a Live CD, and then mount your Ubuntu partition:
```
sudo mount /dev/sda2 /mnt

```
Then open up the menu.lst:
```
gksudo gedit /mnt/boot/grub/menu.lst &
```
Find the Ubuntu entries, they should look similar to:
```
title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		[COLOR="Red"](hd0,1)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=77677cb5-6e56-4936-a373-80c15de06bca ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
```
And change the "root (hdX,Y)" lines for Ubuntu to be (hd0,1) like above. After you are done, copy and paste the contents of your menu.lst and post it to this thread so we can see it. Save the file, reboot, and hope that Ubuntu boots. :) If not, we can help you troubleshoot further since you will have posted your menu.lst.

---

### Post by jrharvey on 2008-08-05
I went ahead and changed the Windows partition to hda0,0

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
# kopt=root=UUID=d09fe951-be84-461e-b91f-344fd50d9227 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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
# defoptions=quiet splash vga=773

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
# howmany=1

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d09fe951-be84-461e-b91f-344fd50d9227 ro quiet splash vga=773
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d09fe951-be84-461e-b91f-344fd50d9227 ro single
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
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by jrharvey on 2008-08-05
IT WORKED!!!! I would give you a hug if i could. Well what do i do if i want to remove an OS again? is there an easier way to do it? There should be a utility or something that searches the drive and automatically configures grub kinda the way it does when you freshly install ubuntu on dual boot. I mean, it wasnt that hard but its definately not something i could have figred out on my own.

---

### Post by caljohnsmith on 2008-08-05
Well, it really depends on which OS you want to remove. If you remove Windows, no problem, because Grub will be intact. If you remove Ubuntu though, Grub will still be in the MBR, but it won't have all the configuration files it needs from the /boot/grub directory in Ubuntu. Since I play with different distros alot, I created a small 50 MB partition on my HDD that is dedicated solely to Grub's config files. That way Grub is entirely independent of any particular distro I have on my HDD. 

Anyway, glad you're up-and-running again. :)

---

### Post by jrharvey on 2008-08-05
I think i got in trouble when i not only deleted the OS but completely removed the partition. It changed the order and therefore grub got really confused i guess.

---

### Post by caljohnsmith on 2008-08-05
Yes, if you change your partitioning, Grub will be quite confused. :) I think you have all the tools now though to fix anything like changing your partitioning yourself; its just a matter of figuring out which partition corresponds to which OS (using "sudo fdisk -l" usually), and then putting in the correct (hdX,Y) entries into menu.lst. All you have to do is remember in Grub's Neurotic World, everything begins with zero and not 1. Thus:
```

sda1 --> (hd0,0)
sda2 --> (hd0,1)
sda3 --> (hd0,2)
sdb1 --> (hd1,0)
sdb2 --> (hd1,1)
...etc
```
And lastly, if your menu.lst uses UUIDs in the kernel lines for Linux entries, you will probably have to change those. You can find the correct UUID for a partition by using:
```
sudo blkid -c /dev/null
```
Anyway, that's probably all you would need to know to fix Grub after messing with your partitioning. :)

---

