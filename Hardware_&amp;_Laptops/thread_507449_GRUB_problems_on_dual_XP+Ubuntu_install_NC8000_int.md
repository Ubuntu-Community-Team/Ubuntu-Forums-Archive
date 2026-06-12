---
title: "GRUB problems on dual XP+Ubuntu install NC8000 internal+multibay"
date: 2007-07-23
forum: Hardware &amp; Laptops
---

### Post by scotchfx on 2007-07-23
I have an HP NC8000 with Windows XP (all SPs) installed on the primary drive and Ubuntu Feisty installed on a removable multibay drive.

With the removable multibay drive inserted I can boot into GRUB and choose my operating system and eveything works fine however when I remove multibay drive (to make room for a 2nd battery) I can no longer boot into XP (GRUB Error 21).

Looking through the forums here I've got an idea of how I might remedy this (repair MBR using XP installation or SuperGRUB) but I'd like to know what the error is and how I might be able to get my dual XP/Ubuntu configuration working properly...

Any takers?

I've tried reconfiguring GRUB using the following procedure:

sudo grub
root (hd0,0)
setup (hd0)
quit

However I cannot execute setup (hd0)... I think the problem may be that I cannot see my Windows partition from Linux (or vice versa for that matter)... I am appending my /boot/grub/menu.lst for reference:


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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=UUID=e8d22829-eeca-4f6f-8160-d3dabdfc3889 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=e8d22829-eeca-4f6f-8160-d3dabdfc3889 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=e8d22829-eeca-4f6f-8160-d3dabdfc3889 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=e8d22829-eeca-4f6f-8160-d3dabdfc3889 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=e8d22829-eeca-4f6f-8160-d3dabdfc3889 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,0)
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



I'm a noob at Linux - I use Unix at work but that's my closest equivalent. That being said, I'm impressed with Ubuntu thus far but need to have access to my XP installation standalone... I can configure my BIOS to prompt me as to which drive I wish to boot into but atm GRUB doesn't allow me to boot my internal drive standalone...

Any takers?

---

### Post by scotchfx on 2007-07-23
I've just figured out how to list out my partitions (go newbie!)...

Disk /dev/sda: 100.0 GB, 100030242816 bytes
240 heads, 63 sectors/track, 12921 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12921    97682728+   7  HPFS/NTFS

Disk /dev/sdb: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        6992    56163208+  83  Linux
/dev/sdb2            6993        7296     2441880    5  Extended
/dev/sdb5            6993        7296     2441848+  82  Linux swap / Solaris

... it would seem that sda1 is my XP installation and sdb1 is Linux...

given this info can anyone clue me in to how to fix GRUB so that I can boot into XP (sda1) w/o my multibay drive installed... ie how to get GRUB installed entirely on the sda1 drive?

---

### Post by logos34 on 2007-07-23
> ... it would seem that sda1 is my XP installation and sdb1 is Linux...

given this info can anyone clue me in to how to fix GRUB so that I can boot into XP (sda1) w/o my multibay drive installed... ie how to get GRUB installed entirely on the sda1 drive?

Short of inserting a separate /boot partition on sda, there isn't.  Grub needs to access the boot files, which usually are located on / (root) partition (in your case, drive sdb).  I mean, you COULD put Grub on a floppy or CD and boot to that first, which would then allow you to choose either OS, but most people don't care for that approach.

Here are your alternatives, as I see it:

(1) Restore the windows bootloader to the MBR of sda, then reinstall grub on the linux drive sdb.  When the multibay drive is disconnected windows boots up by default, and when you connect up the multibay drive all you have to do is go in to the BIOS and set the linux drive first in the BIOS hard disk boot order. In which case you would write Grub to the mbr of sdb, which is (hd1), NOT (hd0):

> [B]sudo grub
root (hd[COLOR="Red"]1[/COLOR],0)
setup (hd[COLOR="Red"]1[/COLOR])
qui[/B]t

After grub is installed on the mbr of sdb, you will have to then edit menu.lst and device.map because the minute you change the boot order in the bios the designation of sdb will change from (hd1) to (hd0).  So change all linux entries to '(hd0,0)' and windows to '(hd1,0)'.  Reverse the entries in /boot/grub/device.map as well:

> (hd0) /dev/sdb
(hd1) /dev/sda

EDIT: and [read this]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk") on mapping your windows entry so that it will boot from grub.

OR (perhaps a better way):
(2) Use windows bootloader to boot linux.

Basically all you have to do is add a menu.lst to your windows C: base directory and put an entry in your boot.ini pointing to it. Then when you boot windows you get a screen where you choose the winxp or linux entry, and the latter pulls up the menu.lst which points to your kernels over in /boot on sdb.

You need just need two things: a menu.lst and something called grldr. 

You can find both in the **[COLOR="Blue"]Grub4dos[/COLOR]** package (available at sourceforge or [here]("http://sarovar.org/projects/grub4dos/")).

Download the latest zip file (0.4.3pre1)

Extract the file [COLOR="Blue"]grldr[/COLOR] to C: (same place as boot.ini).

Create a folder in C: called **boot**.  Create a folder inside boot named **grub**.

Then extract [COLOR="Blue"]menu.lst[/COLOR] to **C:\boot\grub**.

Copy and paste your Feisty kernel entries from /boot/grub/menu.lst to the top of that new menu.lst (you might have to adjust the entry format).

Open **boot.ini** file (type 'C:\boot.ini' in the address bar -- it's hidden) and add this line:

**[COLOR="Blue"]c:\grldr="Ubuntu"[/COLOR] **

That's it.  Works on my setup.  (I modified it from [this howto]("https://help.ubuntu.com/community/Installation/FromWindows"))

---

### Post by scotchfx on 2007-07-23
A few questions: 

For the second option (adding a menu.lst and editing the boot.ini file in XP) I shouldn't just copy over the menu.lst file from my Ubuntu installation, but rather I should use the menu.lst file from the Grub4dos package?

If I do not have the multibay installed will the XP bootloader still detect this - or will I be able to boot into a device that is not installed?

If I updated my Ubuntu installation (for instance, when I boot into GRUB I have the option of 2 different kernels)... Will I need to manually update the menu.lst file whenever Ubuntu has a kernel (or anything that affects the boot configuration) update?

Thanks!

---

### Post by logos34 on 2007-07-23
> For the second option (adding a menu.lst and editing the boot.ini file in XP) I shouldn't just copy over the menu.lst file from my Ubuntu installation, but rather I should use the menu.lst file from the Grub4dos package?

If I do not have the multibay installed will the XP bootloader still detect this - or will I be able to boot into a device that is not installed?

If I updated my Ubuntu installation (for instance, when I boot into GRUB I have the option of 2 different kernels)... Will I need to manually update the menu.lst file whenever Ubuntu has a kernel (or anything that affects the boot configuration) update?

I guess you could just copy over the entire ubuntu menu (I've only ever used the grub4dos version), but yes you will have to manually edit the  copy on the windows drive after kernel updates.  

Windows bootloader won't won't detect if the drive is connected or not.  The boot.ini will appear as usual and choosing linux will bring up the menu.lst, but it will return an error when you select the kernel, that's all.

---

### Post by scotchfx on 2007-07-24
I think I am going to give the first option you suggested in your initial reply on this thread (i.e. "Restore the windows bootloader to the MBR of sda, then reinstall grub on the linux drive sdb") a shot... this is partly based on the assumption that by installing GRUB completely on my removable linux drive (and restoring the MBR on my XP drive), if I ever choose to make Ubuntu my "primary" installation (by switching out my linux hard disk from my removable multibay drive with the fixed internal disk in my laptop that currently contains XP), I will be able to do so relatively seemlessly...

In essence, the first option ensures that both XP and Linux can boot standalone, additionally Linux updates will automatically be reflected in the menu.lst file...

Am I correct in my assumptions?

*My thanks to you logos34...* I'm relatively new to this forum but if there is any way I can give someone a "kudos" for helping a newbie out just let me know...

---

