---
title: "GRUB 2 hard drives 3OS's...how the heck?"
date: 2008-07-18
forum: General Help
---

### Post by Nimaran on 2008-07-18
Okay, I had a hard drive it was partitioned with Windows and Ubuntu. I recently installed a second hard drive totally dedicated to Ubuntu. How do I set up GRUB to be able to load all three OS's on the two different hard drives?

That was brief, but I hope it is enough for some help. Thanks in advance!!

---

### Post by logos34 on 2008-07-18
Add a [configfile]("http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile") boot entry to the existing grub pointing to the root partition of ubuntu on the second drive.


So let's say root is the first partition of the second disk:

>   title        Ubuntu (on /dev/sdb1)
configfile   (hd1,0)/boot/grub/menu.lst

---

### Post by Nimaran on 2008-07-18
Okay, forgive me, this is a little bit of untreaded ground for me. Could you make it a little more step by step. Although I think I know where you're headed. Thanks!

---

### Post by Nimaran on 2008-07-18
Darn it!! I just realized I can no longer get to my Windows Partition, it dosen't mount from the live cd or my ubuntu setup. What should I do? I don't think it could have been deleted!!!??? That is where all my critical data is stored! Please help! Grub wouldn't load it, is it just a grub problem or am I in deep trouble??? Please help! Thank you!!!

---

### Post by logos34 on 2008-07-18
What happened?

run this in a terminal:

sudo fdisk -l

post it

---

### Post by Nimaran on 2008-07-18
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8057    64717821    7  HPFS/NTFS
/dev/sda2            8058        9444    11141077+  83  Linux
/dev/sda3            9445        9726     2265165    5  Extended
/dev/sda5            9445        9726     2265133+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19175   154023156   83  Linux
/dev/sdb2           19176       19457     2265165    5  Extended
/dev/sdb5           19176       19457     2265133+  82  Linux swap / Solaris

---

### Post by logos34 on 2008-07-18
windows is still there...

Try mounting it manually:

sudo mount /dev/sda1

(this will read the /etc/fstab line)

Open up your menu.lst as root:

gksudo gedit /boot/grub/menu.lst

add this to bottom:
> 
			 				  title        Ubuntu (on /dev/sdb1)
configfile   (hd1,0)/boot/grub/menu.lst

oh, and post the windows entry.

---

### Post by Nimaran on 2008-07-18
get this error:

gksudo gedit /boot/grub/menu.lst


and the menu.list is blank ??

---

### Post by Nimaran on 2008-07-18
sorry, tired, get this error:

mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab

---

### Post by logos34 on 2008-07-18
oh, if you're on the live cd, then:

sudo mkdir /media/sda2

sudo mount -t ext3 /dev/sda2 /media/sda2

sudo gedit /media/sda2/boot/grub/menu.lst

For windows try:

sudo mkdir /media/windows

sudo mount -t ntfs-3g -o force /dev/sda1 /media/windows

or

sudo mount -t ntfs -o force /dev/sda1 /media/windows

---

### Post by Nimaran on 2008-07-18
get this for windows:


ubuntu@ubuntu:~$ sudo mkdir /media/windows
ubuntu@ubuntu:~$ sudo mount -t ntfs-3g -o force /dev/sda1 /media/windows
Unexpected clusters per mft record (-1).
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo mount -t ntfs -o force /dev/sda1 /media/windows
Unexpected clusters per mft record (-1).
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$

---

### Post by logos34 on 2008-07-18
IS this XP?

If so, run error-checking on it by booting the XP install cd:

>Recovery Console>[B]chkdsk /r 
[/B]> [B]

Unexpected clusters per mft record (-1).[/B]
Failed to mount '/dev/sda1': Invalid argument
** The device '/dev/sda1' doesn't have a valid NTFS.**

---

### Post by Nimaran on 2008-07-18
Do that from the XP install disc?

---

### Post by logos34 on 2008-07-18
yep.

---

### Post by Nimaran on 2008-07-18
What should I do from there? I will have to dig out that disc, I'm not sure I even have it still. It will have to wait till morning. :)

Anything else to try?

---

### Post by logos34 on 2008-07-18
Linux doesn't have any ntfs filesystem checking tools (ntfsfix just flags it as dirty, which is then supposed to trigger chkdsk to run on next boot.  But you can't boot windows you say).  If you could only get to the Microsoft splash screen you might be able to hit F8 or whatever to enter Safe Mode and do chkdsk from there.  But it doesn't sound like your even getting that far.  

If you can't even mount it, not much you can do otherwise

---

### Post by logos34 on 2008-07-18
What about booting ubuntu on the other disk, did you try?

---

### Post by logos34 on 2008-07-19
Just for the heck of it try it inside ubuntu install, (without force option):

sudo mount -t ntfs-3g /dev/sda1 /media/mountpoint

(replace 'mountpoint' with the actual one listed in /etc/fstab)

---

### Post by Nimaran on 2008-07-19
using chkdsk /r gives me an error of something like this volume is damaged, etc..etc.. but how could that have happend, I didn't do anything with that hardrive except installing brub could that have broken it? What should I do?

---

### Post by Nimaran on 2008-07-19
No, I couldn't boot the other Ubuntu I installed on my second hard drive I got an grub error 21 "whatever it is doesn't exist" (you get the idea)

---

### Post by Nimaran on 2008-07-19
Here is the menu.lst from the only working OS right now. The Ubuntu installed on my primary hard drive. The priority is to recover Windows.

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
# kopt=root=UUID=829a07fc-922c-42fa-b2f9-ac7b04c30fd5 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=829a07fc-922c-42fa-b2f9-ac7b04c30fd5 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=829a07fc-922c-42fa-b2f9-ac7b04c30fd5 ro single
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
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title Ubuntu (on /dev/sdb1)
configfile (hd1,0)/boot/grub/menu.lst 


I really do appreciate all this help. Thank you so much for your time! :)

---

### Post by Nimaran on 2008-07-19
Now, if it is not possible for me to recover and get booted back into Windows is there some way at least I can recover my data. There really are only a few key things I need.

---

### Post by logos34 on 2008-07-19
> **Nimaran said:**
> Now, if it is not possible for me to recover and get booted back into Windows is there some way at least I can recover my data. There really are only a few key things I need.

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

It's hard to say what could have happened.  But if it says 'damaged', then it may have bad blocks that cannot be repaired.  Recover your files and then wipe it with a low-level format,  Reinstall.  Maybe that will fix it.

re ubuntu on second disk: can you at least mount the partition?  You could try reinstalling Grub and writing it to the root partition:

---

### Post by Nimaran on 2008-07-19
That is so weird, it was working fine the other day, and the Ubuntu on a different partition is what I am using now....

That PhotoRec, is it pretty intuitive?

Yes, I can mount the Ubuntu on the other hard drive. Could you explain or point to the best way to reinstall GRUB correctly...thanks.

---

### Post by logos34 on 2008-07-19
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

>  Yes, I can mount the Ubuntu on the other hard drive. 

That's good to hear.  If we can just get grub to find the drive.

[http://users.bigpond.net.au/hermanzone/p15.htm#21](http://users.bigpond.net.au/hermanzone/p15.htm#21)

Check /boot/grub--make sure stage2 and all the usual suspects are there, including menu.lst.

sudo grub-install --root-directory=/media/someplace /dev/sdb1

(replace '/media/someplace' with wherever you mounted sdb1)

The try adding a chainloader entry below the configile one:

> title ubuntu (on /dev/sdb1)
root (hd1,0)
chainloader +1

---

