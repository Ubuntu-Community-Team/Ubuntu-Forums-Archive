---
title: "A little help fixing boot (grub) entries?"
date: 2009-06-06
forum: Installation &amp; Upgrades
---

### Post by Aped on 2009-06-06
Reinstalled ubuntu on my desktop recently, which went fine, but now my XP Pro (same disk, different partition) won't boot; instead, I get a second prompt to boot to an old old old XP Home install that was on another HDD which I installed. Before the reformat, the XP Home install didn't show up at all, and I don't care if it ever does, since that HDD is used for something else now. 

How do I go about remedying this? 

Output of relevant files, for the use of ubuntugurus: 

```
$ cat /boot/grub/device.map
(hd0)	/dev/sda
(hd1)	/dev/sdb

```

```
$ sudo fdisk -lu
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x68d068d0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   409593239   204796588+   7  HPFS/NTFS
/dev/sda2       409593240   625137344   107772052+   5  Extended
/dev/sda5       409593303   616285529   103346113+  83  Linux
/dev/sda6       616285593   625137344     4425876   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa7ca49d4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   234436544   117218241    7  HPFS/NTFS

```

The last entry here, on sdb1, is the old XP Home drive. Both having an id of 7 possibly confusing things?

And lastly:
```
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd0,4)

```


As usual when I beg for help on these forums, thanks in advance for any comments. (I have seen [_this thread_]("http://ubuntuforums.org/showthread.php?t=24113") but am worried that the fix is for people whose ubuntu installs are not booting, not their win drives.)


[edit]
So I tried the 'Ubuntu' option -- the one given when I select XP Pro -- and it takes me to a list, like an installer, as though I had an install CD in the tray (I don't) - opens up a command line ('ash') and leaves me to manually reboot.

[edit2]
Removed boot flag from sdb1, looking like it's actually a windows thing (gonna check boot.ini) in which case I'm totally a tard & this message you may disregard.

---

### Post by mikewhatever on 2009-06-06
Please post your menu.lst (cat /boot/grub/menu.lst) if you want people to help you fix it.

---

### Post by presence1960 on 2009-06-06
post the output of this command run in terminal ```
gksu gedit /boot/grub/menu.lst
``` BTW that is a lowercase L

You probably just need to edit your windows entry.

---

### Post by Aped on 2009-06-06
It's a doozey, but here it is:

```
$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=a4bff2cb-5792-46f2-bb70-b58e008522e2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a4bff2cb-5792-46f2-bb70-b58e008522e2

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

title		Ubuntu 8.10, kernel 2.6.27-14-generic
uuid		a4bff2cb-5792-46f2-bb70-b58e008522e2
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=a4bff2cb-5792-46f2-bb70-b58e008522e2 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
uuid		a4bff2cb-5792-46f2-bb70-b58e008522e2
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=a4bff2cb-5792-46f2-bb70-b58e008522e2 ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		a4bff2cb-5792-46f2-bb70-b58e008522e2
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=a4bff2cb-5792-46f2-bb70-b58e008522e2 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		a4bff2cb-5792-46f2-bb70-b58e008522e2
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=a4bff2cb-5792-46f2-bb70-b58e008522e2 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		a4bff2cb-5792-46f2-bb70-b58e008522e2
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```


The more I look at this the more I think it has something to do with the boot.ini on my xp drive, something modified by the installer CD during/before installation. There's even an 'ubuntu' folder and an exceptionally suspicious looking file called wubildr.**mbr** - sigh.

---

### Post by presence1960 on 2009-06-06
I am looking at your menu.lst & fdisk -l outputs. Which windows is on sda1? Is it XP Pro or XP Home?

---

### Post by lindsay7 on 2009-06-07
I think the windows boot section of your grub menu is set to boot off of the second hard drive hd1,0 but the one you want is on hd0,0. Try changing the instructions

From:

```
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```


To:

```
title		Microsoft Windows XP 
root		(hd0,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```



Hopefully, this is all you need to do.


Type sudo gedit /boot/grub/menu.lst in the terminal and make the changes and save the file and reboot and see if this does it.

---

### Post by merlinus on 2009-06-07
If the windows partition is on sda1, then why is a map statement needed in menu.lst?

---

### Post by lindsay7 on 2009-06-07
I wondered about that too, but it was there so, my thought was to leave it there and see if changing the root number fixed the problem without taking the mapping out, as I was not sure this would mess things up.

---

### Post by Aped on 2009-06-08
> **presence1960 said:**
> I am looking at your menu.lst & fdisk -l outputs. Which windows is on sda1? Is it XP Pro or XP Home?

Sorry, sda1 is the XP Pro install that I want to boot from. I've run the windows boot.ini recovery utility from the windows disk repair console, so I don't think that's the issue; trying lindsay's suggestion now.

[edit] Yeaaap, that didn't work. If I can find 2-3 hours of contiguous time later on I'll probably give [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) a shot. Thanks for all the help so far guys, any other ideas?

---

### Post by lindsay7 on 2009-06-08
Did you try taking out the map lines yet.

```
map		(hd0) (hd1)
map		(hd1) (hd0)

```

---

### Post by mikewhatever on 2009-06-08
The map lines are there for the second Windows installation on the second hdd. Right above that entry, there is the correct one that points to an installation on hd0,0. Any ideas why the OP doesn't the grub prompt for that entry?

---

### Post by Polaris96 on 2009-06-08
The more I look at them, the less sense those map statements make.  looks like a double negative.  If XP Pro is on sda1, we expect that as hd0,0 in Grubese.  try commenting out the map lines.  

One easy way to check would be trying to boot from each XP menu selection.  Will the home selection start home, as well?

---

### Post by presence1960 on 2009-06-08
> **mikewhatever said:**
> The map lines are there for the second Windows installation on the second hdd. Right above that entry, there is the correct one that points to an installation on hd0,0. Any ideas why the OP doesn't the grub prompt for that entry?

+1 mikewhatever. I saw that and was confused - that's why I asked what was installed on sda1. It looks like the titles are incorrect in the windows entries, but that shouldn't matter as long as the rest of the entry is correct. Unless the Op has other problems the Windows entry titled XP home (which is really XP Pro) should boot when selected.

---

### Post by lindsay7 on 2009-06-08
Since the poster says > Before the reformat, the XP Home install didn't show up at all, and I don't care if it ever does, since that HDD is used for something else now., could he not just take out the last stanza completely?

---

### Post by Wiebelhaus on 2009-06-08
This is just an example:

$ sudo /sbin/fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa588e9cb

Device Boot Start End Blocks Id System
/dev/sda1 * 1 30071 241545276 83 Linux
/dev/sda2 30072 30401 2650725 5 Extended
/dev/sda5 30072 30401 2650693+ 82 Linux swap / Solaris

In that fdisk example, the root linux partition reside in /dev/sda1
Create a directory /mnt/root and mount the linux partition.

$ sudo mkdir /mnt/root
$ sudo mount /dev/sda1 /mnt/root

Change the root “/” directory to our old root directory the /mnt/root
$ sudo chroot /mnt/root /bin/bash

Execute the grub command
$ sudo grub –config-file=/boot/grub/menbu.lst

GNU GRUB version 0.97 (640K lower / 3072K upper memory)

[ Minimal BASH-like line editing is supported. For
the first word, TAB lists possible command
completions. Anywhere else TAB lists the possible
completions of a device/filename. ]

Now we need to tell grub where are the grub files:
If you don’t know where they are, type:
grub> find /boot/grub/stage1
(hd0,0)

Now type the following, replacing hd0 with the physical drive linux is installed
grub> root (hd0,0)

Remember that for grub (hd0,0) means hda (primary controller master), first partition.
Let’s install the grub on hd0
grub> setup (hd0,0)
grub> quit

$ sudo reboot
Now you can reboot safely, with your linux system.

---

### Post by Aped on 2009-06-08
> **lindsay7 said:**
> Since the poster says , could he not just take out the last stanza completely?

Doing this now.

[edit] Huh-friggin-zah! It did the trick; still throws me into what I assume is the windows bootloader after choosing the XP option, but now it boots properly! All I did was to comment out the entire second block (stanza?) with the mapping and everything, then just renamed the one labeled 'XP Home' - not sure just how all of these tags got screwed up but many many thanks to the people who helped me out here, you gurus are a bunch of damn princes you know that? Much love, guys (and gal(s)) !

---

### Post by lindsay7 on 2009-06-08
Hey, great.

---

### Post by presence1960 on 2009-06-08
Someone said on here if you don't mess things up you will never learn. Welcome to the club.

---

