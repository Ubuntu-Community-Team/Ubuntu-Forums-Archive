---
title: "Loading a CD during start-up?"
date: 2008-08-06
forum: General Help
---

### Post by lupinesoul on 2008-08-06
How do I do this?  Also, once I get Windows XP installed, is there a way to files from the Ubuntu memory over to Windows?

---

### Post by Taxman415a on 2008-08-06
You'll have to be more specific by what you mean by loading a cd during startup. What are you trying to do?

And yes, once you install XP you can install this driver [http://sourceforge.net/projects/ext2fsd](http://sourceforge.net/projects/ext2fsd) and it will allow you to access your Ubuntu filesystems when you are running XP. I assume files saved to hard disk is what you meant by Ubuntu memory, since memory usually refers to RAM and the contents of RAM are lost from all operating systems once you shutdown or reboot unless it is specifically saved.

---

### Post by pytheas22 on 2008-08-06
> And yes, once you install XP you can install this driver [http://sourceforge.net/projects/ext2fsd](http://sourceforge.net/projects/ext2fsd) and it will allow you to access your Ubuntu filesystems when you are running XP.

Yes, that's the way to access your Ubuntu files from within Windows.  Ubuntu Hardy by default can read your Windows files from within Ubuntu--just go to the Places menu and you can open up your C: drive, and read and write from it.

Also, if your first question is about how to boot your computer to a CD (to install Windows or Ubuntu), you need to press a button to bring up a boot menu when your computer first turns on.  Usually the button is F1, F2, F8 or the delete key.  The first or second screen that you see when your computer is turned on should say something like, "To select boot device, press button XXX."  Once you get the boot menu to come up, you can select to boot the CD drive instead of the hard drive.

Also keep in mind that if you press the pause/break key (on most keyboards this is located above the page-up key, over by delete and insert) while your computer is starting, it will pause the screen so that you have more time to read the instructions on getting a boot menu to come up.

---

### Post by lupinesoul on 2008-08-06
> **Taxman415a said:**
> You'll have to be more specific by what you mean by loading a cd during startup. What are you trying to do?

And yes, once you install XP you can install this driver [http://sourceforge.net/projects/ext2fsd](http://sourceforge.net/projects/ext2fsd) and it will allow you to access your Ubuntu filesystems when you are running XP. I assume files saved to hard disk is what you meant by Ubuntu memory, since memory usually refers to RAM and the contents of RAM are lost from all operating systems once you shutdown or reboot unless it is specifically saved.

You know how it says it should boot with Windows by itself (before it loads any other OS *cough*Ubuntu*cough*)?  Is there a way to that manually?  And ,yes, that's what I meant by memory.

Edit: Oh, and thanks for the link to the download.

---

### Post by lupinesoul on 2008-08-06
I see... Ask for some help on code and you get an immediate answer, but try to get some information to install another OS and the thread dies.  Nice. :mad:

---

### Post by Taxman415a on 2008-08-06
> **lupinesoul said:**
> You know how it says it should boot with Windows by itself (before it loads any other OS *cough*Ubuntu*cough*)?  Is there a way to that manually?  And ,yes, that's what I meant by memory.

No, not sure what you mean. How what says that? A way to do what manually? 

I'm guessing you want to boot from a Windows CD and to do that, follow the instructions pytheas22 gave. You can also set in your BIOS to boot from CD first by default. How to access your BIOS varies by manufacturer. Sometimes it's del, sometimes it's F something, but as he mentioned, how to do it usually flashes on your screen at the beginning of a boot sequence.

> Edit: Oh, and thanks for the link to the download.

No problem, glad to help.

> I see... Ask for some help on code and you get an immediate answer, but try to get some information to install another OS and the thread dies. Nice.
Well 30 minutes isn't exactly dead, and mostly I think it's just hard to figure out what you're trying to do. But if you try to explain it carefully, we can help.

---

### Post by mb_webguy on 2008-08-06
> I see... Ask for some help on code and you get an immediate answer, but try to get some information to install another OS and the thread dies. Nice.
Relax.  It's only been half an hour since your last post.  Remember that everyone here is a fellow user, and voluntarily offering our time to help others.  And we're spread around the world, so it might be 2:00am for the person(s) who can best answer your question.

As for how to set Ubuntu as the default OS, I'm assuming you're talking about a dual-boot setup with Ubuntu and Windows.  You need to edit the /boot/grub/menu.lst file.  Be VERY CAREFUL editing this file.  Open up the terminal and type "sudo gedit /boot/grub/menu.lst".  Look for the entry for Windows, which should look something like this:```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

Cut-and-paste that section to the bottom of the file, somewhere below the line "### END DEBIAN AUTOMAGIC KERNELS LIST".

(By the way, if the Windows entry is already at the end of the file, you can set the OS that boots by default by changing the "default" line near the top of the file.  The number corresponds to the item on the boot menu you want to boot by default, starting with 0.  So if Ubuntu is at the top of the list and you want to boot into Ubuntu, the line should say "default 0".)

---

### Post by lupinesoul on 2008-08-06
> **mb_webguy said:**
> Relax.  It's only been half an hour since your last post.  Remember that everyone here is a fellow user, and voluntarily offering our time to help others.  And we're spread around the world, so it might be 2:00am for the person(s) who can best answer your question.

As for how to set Ubuntu as the default OS, I'm assuming you're talking about a dual-boot setup with Ubuntu and Windows.  You need to edit the /boot/grub/menu.lst file.  Be VERY CAREFUL editing this file.  Open up the terminal and type "sudo gedit /boot/grub/menu.lst".  Look for the entry for Windows, which should look something like this:```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

Cut-and-paste that section to the bottom of the file, somewhere below the line "### END DEBIAN AUTOMAGIC KERNELS LIST".

(By the way, if the Windows entry is already at the end of the file, you can set the OS that boots by default by changing the "default" line near the top of the file.  The number corresponds to the item on the boot menu you want to boot by default, starting with 0.  So if Ubuntu is at the top of the list and you want to boot into Ubuntu, the line should say "default 0".)

Sorry, I've been impatient.  I have to be at a LAN party in about 2 hours and I can't find any other way to run the games (Wine is pretty much useless, can't even run XFire).

It's nowhere to be found in the file:
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
# kopt=root=UUID=a635444a-4909-440e-b59c-fc0541f553b8 ro

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a635444a-4909-440e-b59c-fc0541f553b8 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a635444a-4909-440e-b59c-fc0541f553b8 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by mb_webguy on 2008-08-06
Try typing "sudo update-grub" in the terminal, and see if it adds an entry for Windows.  If not, then you can try copying the Windows entry I posted earlier and modifying the root parameter.  Type "sudo fdisk -l" to get a listing of the partitions on your drives.  Look for an NTFS partition -- that will be your Windows partition.

GRUB partitions follow a slightly different scheme than fdisk.  GRUB starts counting with 0, where fdisk starts with 1.  GRUB identifies a hard drive by a number, where fdisk identifies it by a letter.  So if your Windows partition is listed by fdisk as "/dev/sda1", then the corresponding GRUB notation would be "(hd0,0)".  "/dev/sdb3" would become "(hd1,2)".  Got it?

So just copy the GRUB listing for Windows that I posted earlier and modify the "root" parameter accordingly.  Hopefully, when you reboot you'll be able to select and boot into Windows.

---

