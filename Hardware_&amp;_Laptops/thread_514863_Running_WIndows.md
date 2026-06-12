---
title: "Running WIndows"
date: 2007-08-01
forum: Hardware &amp; Laptops
---

### Post by Knowmee on 2007-08-01
I've installed Linux on the main partition of my hard drive, and have windows installed on a smaller partition, the layout of my hard drive is:

[IMG]http://img260.imageshack.us/img260/2463/harddrivesv6.jpg[/IMG]

The 63gb being Ubuntu and the  10.53gb with 4.87 in use being windows. (I'm not exactly sure what the "extended" thing is.)

Now, when i turn my computer on it runs Ubuntu automatically, so I cannot use windows, this is my main problem, but as well as this, if i put a cd in (I.E. the windows install cd, or a live ubuntu cd) it doesn't boot from it but instead just runs ubuntu, where before i installed Ubuntu, it did.


Thanks in advanced :)

---

### Post by wjp.reg on 2007-08-01
> **Knowmee said:**
> I've installed Linux on the main partition of my hard drive, and have windows installed on a smaller partition, the layout of my hard drive is:

[IMG]http://img260.imageshack.us/img260/2463/harddrivesv6.jpg[/IMG]

The 63gb being Ubuntu and the  10.53gb with 4.87 in use being windows. (I'm not exactly sure what the "extended" thing is.)

Now, when i turn my computer on it runs Ubuntu automatically, so I cannot use windows, this is my main problem, but as well as this, if i put a cd in (I.E. the windows install cd, or a live ubuntu cd) it doesn't boot from it but instead just runs ubuntu, where before i installed Ubuntu, it did.


Thanks in advanced :)

I think your best bet is to wipe the drive clean and repartition only the space for windows and then install it.  Once you are certain it will boot, move on to installing ubuntu.

Ubuntu will recognize the free space you left for it to use and will partition it accordingly.  GRUB will then be installed with entries for windows and ubuntu and will boot properly.

Good luck!

---

### Post by dreadlord_chris on 2007-08-01
For you computer to boot from a CD your BIOS needs to be set for it. Booting between Windows & Ubuntu is handled by GRUB. Post the contents of **/boot/grub/menu.lst** and we'll see what we can do to fix you up...

---

### Post by 505 on 2007-08-01
To dual boot you must have grub (which you most likely will have). However, since Ubuntu starts, there is only one entry, so you need to add windows to it.
Go to /boot/grub and open menu.lst in sudo mode (e.g. sudo gedit menu.lst). At the end you find all entries. See if Windows is already there, other wise add:
```

title		Microsoft Windows XP Professional
root		(hd0,1) ## first hard disk, second partition
savedefault
makeactive
chainloader	+1

```
If Windows is you don't need to add it. Then check to see if there is a timeout. Search 'timeout' and make sure it is not 0.

If Ubuntu starts, and not a boot CD when inserted, you need to check the BIOS settings. Boot order is somewhere in your BIOS.

---

### Post by Knowmee on 2007-08-01
Edit: Didn't see the above post before i made this one.
Edit2: Where within the file does the code go?

I really don't want to through all the work of re-partitioning and installing, I spent a hell of along time yesterday setting up what I've already done, if there is any other way please let me know :)

Menu.lst :

> # menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=6aa98b20-3055-4a1d-bcb5-3959a8d6cce8 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=6aa98b20-3055-4a1d-bcb5-3959a8d6cce8 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=6aa98b20-3055-4a1d-bcb5-3959a8d6cce8 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=6aa98b20-3055-4a1d-bcb5-3959a8d6cce8 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=6aa98b20-3055-4a1d-bcb5-3959a8d6cce8 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by Knowmee on 2007-08-01
Checked for Windows, it's not there.
I'm not sure where to add the code 505 showed me.
How do i open menu.lst in sudo mode?

---

### Post by rohan000 on 2007-08-01
> How do i open menu.lst in sudo mode?
Go to the terminal (applications->Accessories->terminal) and type
sudo gedit /boot/grub/menu.lst

You can put the code 505 gave you anywhere among the list of Ubuntu boot options after "## ## End Default Options ##".
Which position you put it in will change where it appears on the GRUB menu. So if you put it before Ubuntu it will be first in the list, if you put it after it will be after.

---

### Post by Knowmee on 2007-08-01
> **rohan000 said:**
> Go to the terminal (applications->Accessories->terminal) and type
sudo gedit /boot/grub/menu.lst

You can put the code 505 gave you anywhere among the list of Ubuntu boot options after "## ## End Default Options ##".
Which position you put it in will change where it appears on the GRUB menu. So if you put it before Ubuntu it will be first in the list, if you put it after it will be after.

Ok thank you, I added the code and selected to boot windows, It said unable to load (or something similar) does this mean there is an error with Windows?

---

### Post by wjp.reg on 2007-08-01
> **505 said:**
> To dual boot you must have grub (which you most likely will have). However, since Ubuntu starts, there is only one entry, so you need to add windows to it.
Go to /boot/grub and open menu.lst in sudo mode (e.g. sudo gedit menu.lst). At the end you find all entries. See if Windows is already there, other wise add:
```

title		Microsoft Windows XP Professional
root		(hd0,1) ## first hard disk, second partition
savedefault
makeactive
chainloader	+1

```
If Windows is you don't need to add it. Then check to see if there is a timeout. Search 'timeout' and make sure it is not 0.

If Ubuntu starts, and not a boot CD when inserted, you need to check the BIOS settings. Boot order is somewhere in your BIOS.

for your setup you would replace ´ (hd0,1) with (hd0,4) as you have windows installed on the fifth partition.

I still don think it will work ;-)

---

### Post by Knowmee on 2007-08-01
> **wjp.reg said:**
> for your setup you would replace ´ (hdo,1) with (hd0,4) as you have windows installed on the fifth partition.

Using:
> title		Microsoft Windows XP Professional
root		(hd0,4) ## first hard disk, second partition
savedefault
makeactive
chainloader	+1

I got the error "Invalid Device Requested". Is there anything else i can try?

---

### Post by wjp.reg on 2007-08-01
> **Knowmee said:**
> Using:


I got the error "Invalid Device Requested". Is there anything else i can try?

Yes, what I said earlier ;-)

I believe Windows likes to be on the first partition.

anyone else have an opinion on that?

---

### Post by wjp.reg on 2007-08-01
Here´s another thread about a person in similar circumstances and he has been offered yet another solution.

[http://ubuntuforums.org/showthread.php?t=497139]("http://ubuntuforums.org/showthread.php?t=497139")

---

