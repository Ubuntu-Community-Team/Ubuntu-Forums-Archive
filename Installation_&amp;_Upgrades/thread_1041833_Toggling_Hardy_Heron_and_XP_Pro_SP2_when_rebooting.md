---
title: "Toggling Hardy Heron and XP Pro SP2 when rebooting remotely"
date: 2009-01-17
forum: Installation &amp; Upgrades
---

### Post by maporojo on 2009-01-17
Situation:
- I am not a computer expert and I am trying to learn.
- I own a home computer partitioned to have Hardy Heron and XP Pro SP2
- I work with a Mac OS 10 and XP Pro away from home and I don't have administrative rights on either machine.
- When I leave my home computer with Ubuntu running, I can use ssh to access the terminal. When I leave it with XP running, I can use Remote Desktop Connection to access it.
- Whenever I reboot from home I have to make a choice on which OS I want to boot otherwise it boots the one set as default in menu.lst

Requirement:
- I would like my home computer to toggle between Hardy Heron and XP Pro SP2 when I boot remotely. In other words, if I left XP running and I restart the machine using Remote Desktop Connection I want it to boot Ubuntu. On the other hand, if I left the machine running Ubuntu and I reboot it remotely using ssh, then I want it to boot XP.

Question:
- What is grub?
- Can the menu.lst file (which I think grub reads) contain a script that toggles the default OS between XP and Ubuntu anytime the computer is rebooted? (I am thinking of some script that swaps values.)

PS - Below is a copy of the menu.lst file contents:

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
default		4

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
# kopt=root=UUID=e8a6b04d-5c48-466c-b03f-a37e042f261e ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

title		Ubuntu 8.04.1, kernel 2.6.24-23-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=e8a6b04d-5c48-466c-b03f-a37e042f261e ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=e8a6b04d-5c48-466c-b03f-a37e042f261e ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,4)
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

---

### Post by kranny on 2009-01-17
First create a backup for your menu.lst
```
sudo cp menu.lst menu.lst_backup
```
Now create a menu1.lst file which has the default option of windows..
```
sudo cp menu.lst menu1.lst
sudo gedit menu.lst
```

and change the default value to 4
When you boot into ubuntu via ssh Just be sure that the menu.lst file is menu1.lst
And efore rebooting into windows change it to menu.lst

Just to automate the task Setup a cron job for the same...If you want help regarding that,let me know

---

### Post by maporojo on 2009-01-27
Sorry for the delay in responding. I will need help with that (i.e. setting up the cron job(s) if that's necessary).

I know I can always manually edit the menu.lst file while in ubuntu in order to make whichever OS I want to be the default one. What I was curious about is whether it is possible to write a script that edits the menu.lst file by replacing either "default 4" with "default 0" or "default 0" with "default 4" and then saving the file before grub reads it. That way, I never have to access the menu.lst file or create multiple copies of it.

---

### Post by uidb4056 on 2009-01-27
You can install startupmanagar it is in the repositories, you can find it in Synaptic Package Manager under Administration menu. You can change with it the default boot option among another features.

---

