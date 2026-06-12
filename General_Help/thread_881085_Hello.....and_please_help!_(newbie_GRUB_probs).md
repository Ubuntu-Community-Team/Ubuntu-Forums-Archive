---
title: "Hello.....and please help! (newbie GRUB probs)"
date: 2008-08-05
forum: General Help
---

### Post by seymour71 on 2008-08-05
Hello to you all, been checking out these forums for a couple of days (mostly on works time!) and it seems like a friendly place.

I've recently installed Ubuntu 8.04 onto my system, alongside XP and Vista.I have a total of 4 hard drives, 1 for each OS, and one for storage - music etc.

Now, after a couple of days of browsing these forums I have managed to change the default os in GRUB to Vista. But the wife would still prefer XP, thing is, I can't see XP as on option anywhere. I have used the excellent StartUp Manager prog, but that only finds Ubuntu & Vista. 

I can still access all files etc on the XP drive from within Ubuntu, so I know I've not installed over it.

Any ideas guys? And please be gentle with me, I am an idiot.

---

### Post by Qchan on 2008-08-05
> **seymour71 said:**
> Hello to you all, been checking out these forums for a couple of days (mostly on works time!) and it seems like a friendly place.

I've recently installed Ubuntu 8.04 onto my system, alongside XP and Vista.I have a total of 4 hard drives, 1 for each OS, and one for storage - music etc.

Now, after a couple of days of browsing these forums I have managed to change the default os in GRUB to Vista. But the wife would still prefer XP, thing is, I can't see XP as on option anywhere. I have used the excellent StartUp Manager prog, but that only finds Ubuntu & Vista. 

I can still access all files etc on the XP drive from within Ubuntu, so I know I've not installed over it.

Any ideas guys? And please be gentle with me, I am an idiot.

[b][color=darkred]
What does your /boot/grub/menu.lst look like?
You can open up gedit to view it. Just copy and paste it here so we can see.
[/b][/color]

---

### Post by seymour71 on 2008-08-05
Ok, i think this is it:

            grub-install(8), grub-floppy(8),
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
timeout		20

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
# kopt=root=UUID=49882365-89d5-4766-a826-a39f1826b68d ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd3,0)

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
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=49882365-89d5-4766-a826-a39f1826b68d ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=49882365-89d5-4766-a826-a39f1826b68d ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd3,0)
kernel		/boot/memtest86+.bin
quiet

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
makeactive
chainloader	+1

---

### Post by Qchan on 2008-08-05
[b][color=darkred]
In terminal, type
> 
sudo fdisk -l


Copy and paste what you see there.
[/b][/color]

---

### Post by seymour71 on 2008-08-05
woops, sorry, here it is:

Disk /dev/sda: 203.9 GB, 203928109056 bytes
16 heads, 63 sectors/track, 395136 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0xa7aa7e28

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      395133   199147000+   7  HPFS/NTFS

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7fc7646c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2        9964    80027797+   f  W95 Ext'd (LBA)
/dev/sdb5               2        9964    80027766    7  HPFS/NTFS

Disk /dev/sdc: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x36f936f8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        2327    18691596   83  Linux
/dev/sdc2            2328        2434      859477+   5  Extended
/dev/sdc5            2328        2434      859446   82  Linux swap / Solaris

Disk /dev/sdd: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc905c905

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       10010    80405293+   7  HPFS/NTFS
craig@craig-desktop:~$

---

### Post by seymour71 on 2008-08-05
Bit of an update, I've just found that if I select Vista from the GRUB menu, I then get the choice of XP or Vista.(like I did before installing Ubuntu)

This still seems a bit messy though, and in order for me to keep Ubuntu, I would prefer XP to be the default option.

---

### Post by Qchan on 2008-08-05
[b][color=darkred]
Ok, add the following on the bottom of your /boot/grub/menu.lst

> 

# This is Windows XP
# on /dev/sdd1
title Windows XP (loader)
root (hd4,0)
savedefault
makeactive
chainloader +1


Good luck!
[/b][/color]

---

### Post by seymour71 on 2008-08-05
Thanks for that, just tried it but i get something like this message:

Error 21: the selected disk does not exist.

---

### Post by fooman on 2008-08-05
sorry, my bad. :oops:

---

### Post by Qchan on 2008-08-05
> **seymour71 said:**
> Thanks for that, just tried it but i get something like this message:

Error 21: the selected disk does not exist.

[b][color=darkred]

Hmm... Try this then.
> 
# This is Windows XP
# on /dev/sdd1
title Windows XP (loader)
root (hd2,4)
savedefault
makeactive
chainloader +1 

[/b][/color]

---

### Post by seymour71 on 2008-08-06
Hello, just tried that and got:

Error 12: the selected disk does not exist.

Saw on another post that because Vista takes over the boot control, the only way of getting XP will be through the Vista loader....unless anyone knows any different?

---

### Post by caljohnsmith on 2008-08-06
Seymour71, from you fdisk output, your NTFS partitions are:
```
/dev/sda1
/dev/sdb5
/dev/sdd1

```
And since your Vista is sda1 (which we know since its grub entry is (hd0,0), then you should try either:
```
/dev/sdb5  --> [COLOR="Blue"](hd1,4)[/COLOR]
/dev/sdd1  --> [COLOR="Blue"](hd3,0)[/COLOR]
```
In other words, Grub's numbering starts with 0, not 1. So change the line for "root (hdX,Y)" that you have now to either of the entries above, and one should work.

---

### Post by seymour71 on 2008-08-07
Hi there, just tried that, and I now get:

Error 13: Invalid or unsupported executable format.

Just to make sure I've understood, here is the output from the GRUB boot menu thingy:

entry
# (normally the first entry defined).
timeout		20

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
# kopt=root=UUID=49882365-89d5-4766-a826-a39f1826b68d ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd3,0)

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
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=49882365-89d5-4766-a826-a39f1826b68d ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=49882365-89d5-4766-a826-a39f1826b68d ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd3,0)
kernel		/boot/memtest86+.bin
quiet

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
makeactive
chainloader	+1

# This is Windows XP
# on /dev/sdd1
title Windows XP (loader)
/dev/sdd1  --> (hd3,0)
savedefault
makeactive
chainloader +1

---

### Post by caljohnsmith on 2008-08-07
Seymour71, I should have been more clear, and also I didn't notice that you are not trying to boot Windows XP from the master HDD. Therefore, change your Windows XP entry to look like the following:
```
title Windows XP (loader)
root (hd3,0)
savedefault
makeactive
map        (hd0) (hd3)
map        (hd3) (hd0)
chainloader +1

```
And if that doesn't work, you can try the following:
```
title Windows XP (loader)
root (hd1,4)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

```
One of those should hopefully work just fine.

---

### Post by seymour71 on 2008-08-07
Thanks for your patience mate, but with the 1st one i still get error 13, and with the second I get:

Error 22: No such partition.

---

### Post by caljohnsmith on 2008-08-07
Ok, that most likely means that your /boot/grub/device.map does not agree with how your BIOS sees the order of your HDDs. Please post the output of that device.map file:
```
cat /boot/grub/device.map
```

---

### Post by seymour71 on 2008-08-07
Ok, here it is:

(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
(hd3)	/dev/sdd

---

### Post by caljohnsmith on 2008-08-07
Seymour71, OK what we need to do is use Grub's CLI to help figure out which HDD is which. Please do the following in terminal:
```
sudo grub
grub> geometry (hd0)
grub> geometry (hd1)
grub> geometry (hd2)
grub> geometry (hd3)
```
Please copy and paste the output of all those commands back here, and we should be able to figure out which HDD is which in Grub's World, based on your previous post of your fdisk output.

---

### Post by seymour71 on 2008-08-07
Man, I'm confused, good job you know what you're doing!:)

Here it is:

grub> geometry (hd0)
drive 0x80: C/H/S = 395136/16/63, The number of sectors = 398297088, /dev/sda
   Partition num: 0,  Filesystem type unknown, partition type 0x7

grub> geometry (hd1)
drive 0x81: C/H/S = 9964/255/63, The number of sectors = 160086528, /dev/sdb
   Partition num: 4,  Filesystem type unknown, partition type 0x7

grub> geometry (hd2)
drive 0x82: C/H/S = 2434/255/63, The number of sectors = 39102336, /dev/sdc
   Partition num: 0,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 4,  Filesystem type unknown, partition type 0x82

grub> geometry (hd3)
drive 0x83: C/H/S = 10011/255/63, The number of sectors = 160836480, /dev/sdd
   Partition num: 0,  Filesystem type unknown, partition type 0x7

---

### Post by caljohnsmith on 2008-08-07
Seymour71, I must be missing something here, because I went again more carefully through your menu.lst, fdisk, and geometry outputs, and something seems to be contradictory. Please clarify:

Are you able to boot into Ubuntu OK? Because your menu.lst you posted says it is (hd3,0), yet in your post #19 above, grub's geometry command claims hd3 is file system type unknown, only one partition, ~80 GB, so it is probably one of your NTFS drives. According to post #19, your hd2 is your Linux drive. 

Something isn't right here. Try doing:
```
sudo grub
grub> find /boot/grub/stage1

```
Copy/paste the results back here, and also check:
```
sudo fdisk -l
```
And make sure it is exactly like you posted in post #5, if not, post the new one back here.

Also according to fdisk your only bootable NTFS partition (other then Vista which is on /dev/sda) is /dev/sdd1. The only combinations we haven't tried yet involving booting a first partition is (hd2,0) and (hd1,0), so try adding *both* entries below Windows XP in the menu.lst:
```
title Windows XP (hd2,0)
root (hd2,0)
savedefault
makeactive
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1

```
Or:
```
title Windows XP (hd1,0)
root (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

```
Restart and hopefully one of those will work. But I'm still curious what the contradiction here seems to be, so be sure to post the output of the above commands too.

---

### Post by seymour71 on 2008-08-08
Ok, here we go:

from: grub> find /boot/grub/stage1 

I get:

(hd2,0)

from: sudo fdisk -l

I get:

Disk /dev/sda: 203.9 GB, 203928109056 bytes
16 heads, 63 sectors/track, 395136 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0xa7aa7e28

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      395133   199147000+   7  HPFS/NTFS

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7fc7646c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2        9964    80027797+   f  W95 Ext'd (LBA)
/dev/sdb5               2        9964    80027766    7  HPFS/NTFS

Disk /dev/sdc: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x36f936f8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        2327    18691596   83  Linux
/dev/sdc2            2328        2434      859477+   5  Extended
/dev/sdc5            2328        2434      859446   82  Linux swap / Solaris

Disk /dev/sdd: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc905c905

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       10010    80405293+   7  HPFS/NTFS
craig@craig-desktop:~$ 

I've just tried both of the options, with the first one I get:

Error 12: Invalid device requested

With the second I get this:

NTLDR is missing
Press Ctrl+Alt+Del to restart.

---

### Post by caljohnsmith on 2008-08-08
Seymour71, are you able to boot into Ubuntu OK? 

When you did that "find /boot/grub/stage1", it shows your grub files are on (hd2,0), and also from post #19, Grub's geometry command shows Ubuntu is on (hd2,0), and yet your menu.lst has (hd3,0) for Ubuntu. So are you able to boot Ubuntu from Grub? 

Because you got that NTLDR error when using (hd1,0) for your Win XP partition, that's an indication that we *finally* found your Win XP partition, but that NTLDR can mean problems with your boot files in Windows XP. If you want more info about NTLDR problems, see:

[http://ubuntuforums.org/showthread.php?t=450329&page=4](http://ubuntuforums.org/showthread.php?t=450329&page=4)
[http://tinyempire.com/notes/ntldrismissing.htm](http://tinyempire.com/notes/ntldrismissing.htm)

I can't be sure what exactly is your NTLDR problem, but here is what I would do: first back up the following three files that are in the root directory of Win XP:
```
boot.ini
ntldr
NTDETECT.COM
```
Replace those three files with the working ones that I've included as an attachment to this post. They are from my own working Win XP. After that, reboot, and select the Win XP entry in Grub that uses (hd1,0). Hopefully Win XP will finally boot.

---

### Post by seymour71 on 2008-08-10
Hi again.

I'm able to boot into Ubuntu fine from GRUB, and indeed into XP - as long as I go through Vista.
I might have mis-understood, but when I enter the code above into a terminal, I get command not found.

...(thinks quietly to himself)....

Unless I'm supposed to do it in XP?

Many thanks for your continued help with this, I'm loving my Ubuntu experience, and I just trying to find a way to keep the Mrs. happy, as she does need XP for MS Publisher.

---

### Post by caljohnsmith on 2008-08-10
OK, before we go any further, how about first posting the contents of your Windows XP's boot.ini file. Please do the following in a terminal:
```

sudo umount /dev/sdd1
sudo mount /dev/sdd1 /mnt
cat /mnt/boot.ini

```
Copy and paste the results back here.

---

### Post by seymour71 on 2008-08-11
Ok, this is what i get:

umount: /dev/sdd1: not mounted

---

### Post by caljohnsmith on 2008-08-11
> **seymour71 said:**
> Ok, this is what i get:

umount: /dev/sdd1: not mounted
Yes, that's OK, I only included that step as a precaution in case you all ready had that partition mounted somewhere else. But since you obviously don't, just do:
```
sudo mount /dev/sdd1 /mnt
ls -l /mnt
cat /mnt/boot.ini
```
And paste the full results back here.

---

### Post by seymour71 on 2008-08-11
Ok mate, here we go:

total 787386
-rwxrwxrwx 1 root root         0 2005-12-04 12:41 AUTOEXEC.BAT
drwxrwxrwx 1 root root      4096 2007-02-22 05:18 Boot
-rwxrwxrwx 1 root root       355 2007-02-22 05:18 Boot.BAK
-rwxrwxrwx 1 root root       355 2008-08-04 21:42 boot.ini
-rwxrwxrwx 1 root root    438840 2006-11-02 09:53 bootmgr
-rwxrwxrwx 1 root root      8192 2007-02-22 05:18 BOOTSECT.BAK
-rwxrwxrwx 1 root root      4683 2005-03-14 23:36 CLDMA.LOG
drwxrwxrwx 1 root root         0 2005-03-26 20:20 CloneDVDTemp
-rwxrwxrwx 1 root root         0 2005-01-20 20:16 CONFIG.SYS
drwxrwxrwx 1 root root      4096 2007-09-01 00:15 Documents and Settings
drwxrwxrwx 1 root root     16384 2008-04-19 20:33 Downloads
-rwxrwxrwx 1 root root      2176 2007-02-15 20:48 dvdlog.txt
drwxrwxrwx 1 root root         0 2008-05-26 20:55 games
-rwxrwxrwx 1 root root       900 2007-02-15 20:48 graph.txt
-rwxrwxrwx 2 root root       423 2007-09-18 23:01 InstallHelper.log
-rwxrwxrwx 1 root root         0 2005-01-20 20:16 IO.SYS
-rwxrwxrwx 1 root root         0 2005-01-20 20:16 MSDOS.SYS
drwxrwxrwx 1 root root         0 2007-02-11 14:12 MSOCache
drwxrwxrwx 1 root root         0 2005-01-20 22:07 My Music
-rwxrwxrwx 1 root root     47564 2004-08-04 03:38 NTDETECT.COM
-rwxrwxrwx 1 root root    250032 2004-08-04 03:59 ntldr
-rwxrwxrwx 1 root root 805306368 2008-08-11 20:59 pagefile.sys
drwxrwxrwx 1 root root     28672 2008-08-04 20:14 Program Files
drwxrwxrwx 1 root root         0 2007-02-21 21:37 $RECYCLE.BIN
drwxrwxrwx 1 root root         0 2005-01-20 21:27 RECYCLER
drwxrwxrwx 1 root root      4096 2006-02-12 15:27 System Volume Information
drwxrwxrwx 1 root root         0 2007-02-03 18:19 TempDVD
drwxrwxrwx 1 root root      4096 2007-06-21 22:34 TWUSB_TEMP
drwxrwxrwx 1 root root    143360 2008-07-09 20:19 WINDOWS

;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT
craig@craig-desktop:~$

---

### Post by caljohnsmith on 2008-08-11
Seymour71, your Windows XP's boot.ini file indicates it has been vandalized by your Vista installation like I suspected. :shock: Seriously though, since you are a bit new at alot of this, I think our safest bet at this point is for you to use this free program called [VistaBootPro]("http://www.vistabootpro.org/") to fix your Windows XP booting problems. That way we don't have to mess directly with your system boot files. Please do the following:
[LIST=1]
[*]Boot into Windows XP, go to the [VistaBootPro website]("http://www.vistabootpro.org/"), scroll to the bottom of the web page, and click on the button to download it (near the donate button). 
[*]Once you get it downloaded, install the VistaBootPro program (while you are in Windows XP, not Vista). 
[*]Run the program, and first thing is use the option it provides to backup all your boot files/configuration.
[*]Choose the option to remove the Vista bootloader from your Windows XP partition (not your Vista partition!), and then choose the option to install the Windows XP bootloader *to your Windows XP partition*.
[/LIST]
That should be all you need to do; let me know how it goes.

---

### Post by seymour71 on 2008-08-13
Hi there, and sorry for the delay in replying. this is the info i get using Vista Boot Pro:

There is currently 2 OS(s) installed on your system.
The current boot timeout is: 30

Default OS: Microsoft Windows Vista

Entry 1
----------------------------------------------------------------------------
Name:			Microsoft Windows Vista
BCD ID:			{default}
Boot Drive:		G:
Windows Drive:		G:
System Bootloader:	\Windows\system32\winload.exe
Windows Directory:	\Windows

Entry 2
----------------------------------------------------------------------------
Name:			Earlier Version of Windows
BCD ID:			{ntldr}
Boot Drive:		C:
System Bootloader:	\ntldr



Now, when I click on the 'Manage OS Entries' tab, I can see the two entries, but each has it's own drive - Am I safe to delete Vista's entry? There doesn't seem to be a BCD entry for Vista on Xp's drive.

---

### Post by caljohnsmith on 2008-08-13
Based on the info you shared with me from the VistaBootPro program, it appears your Win XP boot files might actually be OK, at least according to that program.

But as I've mentioned in my previous posts, some of the data you've shared seems to be contradictory, so I can't be sure of your setup. Given that and the fact that you a bit on the inexperienced side when troubleshooting computers, I'm not sure I feel comfortable asking you to go ahead and replace your Win XP boot files anymore; since you said you can boot into Win XP from the Win Vista boot menu, would that be simple enough for your wife or is that still too complicated of a solution?

It's totally up to you, Craig, whether you want to continue and try and get Win XP booting directly from Ubuntu, but there's a small chance we could render Win XP not bootable for a while, and then have to fix it again; I'm reasonably confident we could fix any problems you might encounter, but I'm just wondering, do you want to continue given this risk?

---

### Post by seymour71 on 2008-08-14
Many thanks for all your help & advice mate, but i think you're right - I'm REALLY out of my depth now! And I don't want to incur the wrath of the Mrs. by rendering XP unbootable.

Thanks very much for your help & patience - much appriciated.:)

---

