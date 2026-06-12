---
title: "Change boot order Fail"
date: 2008-10-29
forum: General Help
---

### Post by brandoncolorado on 2008-10-29
Hello,

I followed the instructions here:
[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/ch10s05.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/ch10s05.html)

to change my boot order.  I also changed the wait time from '10' to '5'.

I did this with the sudo access, and saved the document.  I restarted but the changes were not effective.  What else could I do?

---

### Post by Coreigh on 2008-10-29
I am not sure exactly what you are trying to make happen. Are you trying to make Windows be the default or a different kernel?

Just to clarify from the directions you referenced the 'X' should be a number that corresponds with the section in your config (menu.1st usually) that you want to be default. the first section starts at 0 (not 1).

If this doesn't get you going then could you please post the config file and indicate which one you want to be the default?

---

### Post by brandoncolorado on 2008-10-29
Sorry, I should have been more clear.  My computer boots to Windows XP as the default (because I installed using WUBI (sp?).  I would like to set the default time lower (5) and I would like Ubuntu to be the default.  The current default is '0' and I changed it to '1'.

My config file::
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
# kopt=root=UUID=4933D046769D42A1 loop=/ubuntu/disks/root.disk ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)/ubuntu/disks

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
root		(hd0,0)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4933D046769D42A1 loop=/ubuntu/disks/root.disk ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,0)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4933D046769D42A1 loop=/ubuntu/disks/root.disk ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,0)/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
chainloader	+1

---

### Post by Coreigh on 2008-10-29
It may be a Wubi issue. I am not familiar with Wubi I hope someone can answer this, but my question is when using a Wubi install is it even possible to make Ubuntu the default OS?

To change the timeout time find the line "timeout 10" and change the 10 to a number of seconds you want. 5 for 5 seconds, 30 for 30 seconds, etc.

I hope this helps you out.

---

### Post by caljohnsmith on 2008-10-29
If you are using a Wubi install, then on start up you should first see the Windows XP boot loader screen with two options, one for Win XP and the other for Ubuntu; if you choose Ubuntu, then it should take you to the Grub menu. Is this what yours is like? So are you trying to make Ubuntu the default OS to boot from the Win XP boot screen? If that's the case, you'll have to modify the Win XP boot.ini file slightly. Let me know if that's what you want to do, and I can give more specific instructions.

---

### Post by brandoncolorado on 2008-10-29
Cal,

I do have the two options.  Windows Vista and Ubuntu.  Ubuntu is second.  However, when I click ubuntu it automatically starts loading Ubuntu (not verbose mode, but I still see the scrolling lines of text).  I would like Ubuntu to be the default.  This seems like a minor thing, but I have to restart many times because I miss the option screen.

---

### Post by caljohnsmith on 2008-10-30
OK, I'm not following you, because you mentioned in post #3 that you have Windows XP; so do you have both XP and Vista? If you want to modify Vista's boot loader screen, including specifying the default OS, a good program for that is [EasyBCD]("http://neosmart.net/dl.php?id=1"). Is that maybe what you are looking for?

---

### Post by brandoncolorado on 2008-10-30
> **caljohnsmith said:**
> OK, I'm not following you, because you mentioned in post #3 that you have Windows XP; so do you have both XP and Vista? If you want to modify Vista's boot loader screen, including specifying the default OS, a good program for that is [EasyBCD]("http://neosmart.net/dl.php?id=1"). Is that maybe what you are looking for?

Sorry, the XP in the OP was an error.  I run Vista.  I'll try that program, thank you very much.  I assumed the boot loader was GRUB.

---

### Post by Drakkor on 2009-04-17
Guess better late than never, semi-found answer on another thread.
This is for wubi-installed Ubuntu.
To change boot order,go to Control Panel in Windows,hit System-Advenced System Settings>Statup and Recovery>Settings,you should get a configuration
screen like so, good luck ! :D

---

### Post by bendib on 2009-04-19
1. migrate your documents from the wubi-fied ubuntu to an external storage device
2. Boot from the cd and install alongside windows on a partition
3. ubuntu is now the default.

Keep in mind this is not as difficult as it seems to sound. If you can make your system boot from a cd, you can do this very easily. It's mostly just click next next next next next.
 I don't believe that I have to say to copy your documents back to the new installation. By doing this you also gain the advantage of being able to read all the partitions on your computer, including the one you used to have to boot from.

---

### Post by bendib on 2009-04-19
Well when you use wubi ntldr is still your default boot loader, it just makes a little file with grub on it and forces the system to boot from that little file.

---

### Post by KPDXHAM on 2009-04-27
> **Drakkor said:**
> Guess better late than never, semi-found answer on another thread.
This is for wubi-installed Ubuntu.
To change boot order,go to Control Panel in Windows,hit System-Advenced System Settings>Statup and Recovery>Settings,you should get a configuration
screen like so, good luck ! :D

THANKS!
Almost too simple.:lolflag:    Linux Newbi

---

