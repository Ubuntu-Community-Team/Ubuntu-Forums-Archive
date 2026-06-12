---
title: "Boot Loader Problem after upgrading to 9.04 and messing with Grub"
date: 2009-06-10
forum: Installation &amp; Upgrades
---

### Post by iamthebest235 on 2009-06-10
Ok so I am in deep trouble with my laptop.  Let me try and explain the situation as well as the problem as clearly as possible.

This is what I had: Windows 7 and Ubuntu 8.10 both on my 60GB harddrive.  Ubuntu had like 35 gigs or so and the rest was Win 7.  I used to get the Grub Bootloader menu (pressing escape while booting) to select what OS I wanted to boot into.  Hadn't booted in Ubuntu for a long time because there were some problems with it (due to a skin/theme file I had downloaded that went bad and didn't feel like fixing it).

So I was content with Win7 Beta.  Then I saw Ubuntu Studio 9.04 and thought that I should give it a try.  Downloaded the iso (but turned out to be the alternate CD) was not an easy install like a LiveCD.

I went crazy with the partitioning of the hd then:- Used the Ubuntu 8.04 LiveCD and started Gparted.  In there I had couple partitions (ext3, ntfs, swap and one other I don't remember).  So I erased the ext3 and the 'one other' completely and resized the Win7 to give it more space (35GBs) and had unallocated space of 25 GBs.  I renamed the unallocated to be a ext3 so that I can install Ubuntu Studio 9.04 on it.  And then started with the installation of Ubuntu Studio 9.04.

After the installation:- The Grub bootloader now does not show the Win7 OS, so now I can't boot into my main OS.  It is there I know because when I boot into the Ubuntu Studio I can access the 35 GBs of the Win7 drive from >Places.

1) How do I get the Win7 back on the GRUB so that I can boot into it?

Also, (2) since its been a long time since I've messed with Ubuntu I don't know how to get my Wireless running on it.  Any help would be great.  (3) when installing via the alternate iso dvd, at the end it asked me what softwares to install (2d/3d photo editing, music etc) and I didn't read the bottom instructions line properly and figures If i just press enter on all 3 groups I would get all of them (I want all) but stupid of me, pressing enter on the first option (2d/3d softwares) obviously skipped the rest and the installation was done.  How do I get those other packages???

Thanks for your help, I really appreciate it

---

### Post by presence1960 on 2009-06-10
run this in terminal ```
sudo fdisk -l
``` then post the output here.

also run in terminal > gksu gedit /boot/grub/menu.lst and post that output here also. BTW those are lowercase Ls in those commands

Can't help with wireless as I don't use it.

---

### Post by iamthebest235 on 2009-06-10
sudo fdisk -l
---------------------
Disk /dev/sda: 58.5 GB, 58506416640 bytes
255 heads, 63 sectors/track, 71113 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

  Device Boot          Start     End     Blocks      Id      System
/dev/sda1 *              1       2993   24041241     83    Linux
/dev/sda3              2994     6817    30716280     7  HPFS/NTFS  
/dev/sda4             6818      7113    2377620     5      Extended
/dev/sda5           6818        7113  2377688+      82    Linux swap
---------------------------------------------------------------------------------


gksu gedit /boot/grub/menu.lst 
-----------------------------------
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
# kopt=root=UUID=2f2cc951-2edf-482a-8861-09fe52900784 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=2f2cc951-2edf-482a-8861-09fe52900784

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

title		Ubuntu 9.04, kernel 2.6.28-3-rt
uuid		2f2cc951-2edf-482a-8861-09fe52900784
kernel		/boot/vmlinuz-2.6.28-3-rt root=UUID=2f2cc951-2edf-482a-8861-09fe52900784 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-3-rt
quiet

title		Ubuntu 9.04, kernel 2.6.28-3-rt (recovery mode)
uuid		2f2cc951-2edf-482a-8861-09fe52900784
kernel		/boot/vmlinuz-2.6.28-3-rt root=UUID=2f2cc951-2edf-482a-8861-09fe52900784 ro  single
initrd		/boot/initrd.img-2.6.28-3-rt

title		Ubuntu 9.04, memtest86+
uuid		2f2cc951-2edf-482a-8861-09fe52900784
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by merlinus on 2009-06-10
You might try adding this to the end of menu.lst:

 title		Windows 7
root		(hd0,2)
makeactive
chainloader	+1

Also, try removing the boot flag from sda1 and adding it to sda3.

---

### Post by iamthebest235 on 2009-06-10
will try that....

but how do i the boot flag?????

---

### Post by iamthebest235 on 2009-06-10
Ok so I added that last bit in the menu.lst and tried to boot into win7 but when I selected win 7 from the grub menu it said that BOOTMGR does not exist press ctrl alt del to restart or something along those lines. Then I put in the live cd of ubuntu 8.04 that I had and started gparted. In there I made sure that the boot flag is checked on the sda3 and not on sda1 (which is how it was from the beginning)

---

### Post by merlinus on 2009-06-10
gparted on the ubuntu live cd will do it.  You can set the boot flag from it by right-clicking in the Flags column of the partition and selecting Manage Flags.

---

### Post by iamthebest235 on 2009-06-10
Did that doesn't help

---

### Post by iamthebest235 on 2009-06-10
I really need to boot into win7 as there is some things I have to do in that os.  Please someone help

---

### Post by merlinus on 2009-06-10
This small change may help:

title		Windows 7
rootnoverify		(hd0,2)
makeactive
chainloader	+1

Otherwise, from the results of fdisk -l, it would appear that something is amiss, because there is no sda2:

sudo fdisk -l
---------------------
Disk /dev/sda: 58.5 GB, 58506416640 bytes
255 heads, 63 sectors/track, 71113 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

  Device Boot          Start     End     Blocks      Id      System
/dev/sda1 *              1       2993   24041241     83    Linux
/dev/sda3              2994     6817    30716280     7  HPFS/NTFS  
/dev/sda4             6818      7113    2377620     5      Extended
/dev/sda5           6818        7113  2377688+      82    Linux swap

When you run gparted, what is it showing as to partitions?  Also, you might post a screenshot.

If nothing works, you should be able to boot from your windows disk, select recovery, and fixmbr. That should at least let you boot directly into windows, and you can reinstall grub if you want to run linux as well.

---

### Post by iamthebest235 on 2009-06-10
I can't really post a screenshot since I'm accessing the Internet via my iPod only. But this is what the gpartition displays:
Sda1 22.93 gb ext3 (no flags)
Sda3 29.29 gb ntfs (boot flag)
Sda4 2.27 gb extended
- sda5 2.27 gb Linux swap

---

### Post by merlinus on 2009-06-10
Again, interestingly enough, sda2 is missing.

Did you try changing the lines in menu.lst to:

title		Windows 7
rootnoverify		(hd0,2)
makeactive
chainloader	+1

---

### Post by iamthebest235 on 2009-06-10
When I insert the win7 disk I select the repair ur computer option. It detects that there is a problem with start up and asks me to repair n install. Don't c a option for fixmbr. And after restarting it doesn't work

---

### Post by iamthebest235 on 2009-06-10
Good news guys it's working. All I did was booted with the win7 cd selected repair install and opted for the startup repair. It automatically fixed the prob and now I can start win from grub without any problems. 
Thanks for all your help.

Also, how do I get the wireless working on my ubuntu studio os. And I don't have all the programs that come with the os.

---

### Post by merlinus on 2009-06-10
Glad it is working.  I guess win7 uses something different from xp's fixmbr to do the same thing.

Don't know about the wireless, but you can find lots of apps via Applications/Add/Remove and synaptic.

---

