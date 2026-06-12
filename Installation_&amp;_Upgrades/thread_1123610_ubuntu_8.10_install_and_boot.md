---
title: "ubuntu 8.10 install and boot"
date: 2009-04-12
forum: Installation &amp; Upgrades
---

### Post by Mike_Alt on 2009-04-12
Hi,

I am a newbie to Linux and have been experiencing problems installing it on my system for several weeks.

My system;
Pentium 4, 1.8ghz with 750 meg ram and 5 disks;
500 gig SATA formatted NTFS [sda]
20 gig IDE primary master formatted NTFS with win2k (C:)  [sdb]
10 gig IDE primary slave for linux  [sdc]
CD/ DVD reader/burner IDE secondary master
80 gig IDE secondary slave partitioned 30 gig fat32 and 50 gig NTFS  [sdd]
500 gig USB2 drive formatted NTFS  [sde]

I have tried several times to install Ubuntu Linux without success - trying direct install as well as starting a live 
session then installing.

After installing, I go into the BIOS and set the 10 gig disk as the boot device - allowing GRUB to be the boot manager. 

All I get is a message "press any key to reboot".

I start another live session and find I don't have the rights to edit 'menu.lst' or copy a file into the Linux 
partition. From what I have read, there seems to be a problem with menu.lst. I tried to logout and login using the 
username and password used when doing the install - no help.

///////////////////menu.lst/////                                    

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
# kopt=root=UUID=d88fe3b4-c9ad-4ff9-b4f2-790ba71ab731 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d88fe3b4-c9ad-4ff9-b4f2-790ba71ab731

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
uuid		d88fe3b4-c9ad-4ff9-b4f2-790ba71ab731
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d88fe3b4-c9ad-4ff9-b4f2-790ba71ab731 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		d88fe3b4-c9ad-4ff9-b4f2-790ba71ab731
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d88fe3b4-c9ad-4ff9-b4f2-790ba71ab731 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		d88fe3b4-c9ad-4ff9-b4f2-790ba71ab731
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		win2k - win2k
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

//////////////////////////////////////////////////////////////

This file seems to be missing the line "root...." for each of the Linux entries.

From another book, I found a technique to use the Windows boot loader to boot to Linux. I added the line 
c:\bootsect.lnx="Linux" to 'boot.ini' and copied the 'stage1' file to C:\, renaming it to 'bootsect.lnx'. When I boot and select linux all I get is GRUB on the screen - the only way out is to turn off power or the reset button on the case.

This DVD came with the book "A Practical Guide to Ubuntu Linux - Second Edition", written by Mark G. Sobell and published by Prentice Hall. Prentice states clearly they are not responsible for the contents of the DVD. 

I realize Linux is improved and maintained by volunteers and appreciate the effort. However, I would suggest that a release meant for newcomers to Linux should be tested to ensure the basics work especially when the release is distributed in a book.

Prior to buying this book/DVD, I tried several times to download other distributions of Linux but ran into problems - trying to get a 4 gig file on a DSL connection is very time consuming and error prone. Even tried downloading CD images about 400 meg each needing several CD's - nogo.

If someone thinks this should be reported as a bug let me know and I would be willing to take the time to post it.

Thanks in advance for your help.

---

### Post by dandnsmith on 2009-04-12
I think you'll find that the *uuid* line, immediately after the title line in an entry serves the same effect as the root line.

For the bootsect, I think you got the wrong info somehow. The technique does work (the PC I'm using, does so successfully). The fact that you got the GRUB> prompt shows that GRB gets started - but it hadn't been provided with the info about what disk and where to look for the rest of the process - that gets planted when you do an install of grub.

Process should be:
install grub (somewhere it won't mess you up), working with the planned HDD setup.
grab the grub code from the first block of wherever you installed it (using the dd command, and put result somewhere you can get it later)
copy the saved block to C:\
use it in the Windows boot menu (as you did)

---

### Post by vinceshaw on 2009-04-12
Boot from a slave IDE HD is tricky and, and it is virtually impossible for Windows, bios does not treat it equally as primary HD: the ID is 128 vs 129
Why don't you use your primary HD? You can, at least, free as small as 100 MB to put your /boot partition there and other partitions to the slave HD, then the life is much easier for your installation.

Good luck

vince

---

### Post by Mike_Alt on 2009-04-28
I finally got it installed and booting up.

I was trying to use the graphical installer and it didn't ask/allow installation of Grub.

On one of my attempts, I tried to use the recovery mode to fix the install and found myself doing a complete install using the text based installer. At the end I was asked what to do with Grub with a suggestion as to where to put it. THAT WORKED!! The MBR of the primary master (c:) is modified.

Its too bad the graphical installer doesn't ask what to do with Grub.

Mike

---

