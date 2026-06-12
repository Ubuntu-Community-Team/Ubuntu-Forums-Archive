---
title: "grub doesn't show up"
date: 2006-02-10
forum: Installation &amp; Upgrades
---

### Post by dexter on 2006-02-10
Hey,

I'm running ubuntu about a half year now on my old computer and wanted to install it to my other one. Setup:

- nForce 3 based motherbord
- Athlon64
- SATA 120 GB (win xp + data)
- SATA 200 GB (data)
- PATA 200 GB (linux + data)

I want linux on the 200 GB PATA disk, when installing everything seems to go fine, the installer finds all of my harddisks installed, I can create a new linux partition and Ubuntu installs itselfs. Afterwards grub setup is started, it detects that i have a win xp install and suggests that grub should be installed to be able to boot both OS. I let grub install itself and afterwards i need to reboot. My computer starts up and instead of showing me grub it directly goes to windows (not even grub loader or something like that it boots xp immediatly). I'm guessing that grub is installed on the wrong disk (the PATA instead of the SATA). I've tried re-installing grub using Knoppix but that didn't help. Ubuntu is installed fine that is not the problem, i just can't boot it. Anyone here that can help me installing grub in the right place, without losing xp (yet ;)).

---

### Post by Derek Djons on 2006-02-10
If I'm correct you have to install GRUB on the harddrive where your Windows MBR (Master Boot Record) is located. If you choose an other disc, than you will have to specify extra parameters in order to overrule the Windows MBR and being able to boot all Operating Systems.

I think the easiest thing to do would be to reinstall Ubuntu and choose the right MBR setup once you get there. This all ofcourse if it ain't already how you have done it.

---

### Post by dexter on 2006-02-10
While installing grub at the ubuntu installation it doesn't give you a choice where to install it. hd0 is my PATA disk (Knoppix told me that) and i think that's where grub is installed. But i don't know how to install it on the sata disk (sda/sdb?).

---

### Post by lha on 2006-02-10
[QUOTE=dexter]While installing grub at the ubuntu installation it doesn't give you a choice where to install it. hd0 is my PATA disk (Knoppix told me that) and i think that's where grub is installed. But i don't know how to install it on the sata disk (sda/sdb?).[/QUOTE]
IMHO you should set bios to use that pata drive as primary boot device. Messing with sata drives isn't as safe. If grub and Ubuntu are completely on one disk and Windows (including its boot loader) is on another drive, your system will be more error resistant. Even if one drive failed, the would still contain a fully working system.

(BTW, Ubuntu does let you select where you want to install grub.)

---

### Post by dexter on 2006-02-11
I've changed the boot order in the bios, setting the PATA disk first and now grub is loading. However i'm getting error 18 which means 

"This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general)."

My system isn't that old so there has to be some other reason, any ideas ?

---

### Post by lha on 2006-02-11
[QUOTE=dexter]I've changed the boot order in the bios, setting the PATA disk first and now grub is loading. However i'm getting error 18 which means 

"This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general)."

My system isn't that old so there has to be some other reason, any ideas ?[/QUOTE]
Check [ATA Interface limit]("http://www.storagereview.com/guide2000/ref/hdd/bios/sizeGB128.html") on StorageReview. How have you partitioned your pata drive? All in one big partition?

---

### Post by dexter on 2006-02-11
[QUOTE=lha]Check [ATA Interface limit]("http://www.storagereview.com/guide2000/ref/hdd/bios/sizeGB128.html") on StorageReview. How have you partitioned your pata drive? All in one big partition?[/QUOTE]

The pata drive is partitioned as follows:
1. 75 GiB (data)
2. 20 GiB (data)
3. 10 GiB (data)
4. 82 GiB (linux root)
5. 3 GiB (linux swap)

I think the linux partitions should be in the beginning of the hard drive, should that solve it ?

---

### Post by lha on 2006-02-11
[QUOTE=dexter]The pata drive is partitioned as follows:
1. 75 GiB (data)
2. 20 GiB (data)
3. 10 GiB (data)
4. 82 GiB (linux root)
5. 3 GiB (linux swap)

I think the linux partitions should be in the beginning of the hard drive, should that solve it ?[/QUOTE]

Yes, if the problem is caused by that 137GB boundary - issue.

[COLOR="Gray"](You didn't ask for it, but still want to comment your partitions...
Since you want to use multiple partitions, why create a large root partition? You could make it smaller, say 5GB and store your data on separate partition(s). If you want to reinstall Ubuntu or switch to another distro, you can wipe out everything on root and still have all your data intact on another partition. And why create 3 partitions for data? I'd understand /home and a fat32 for sharing data between Windows and Ubuntu, but three partitions for data and a 82 GB root? Also, three gigs of swap is usually exaggeration, IHMO. On the other hand, you do have a lot of disk space so why not... Well, maybe you have a good reason for those partitions.)[/COLOR]

---

### Post by dexter on 2006-02-11
[QUOTE=lha]Yes, if the problem is caused by that 137GB boundary - issue.

[COLOR="Gray"](You didn't ask for it, but still want to comment your partitions...
Since you want to use multiple partitions, why create a large root partition? You could make it smaller, say 5GB and store your data on separate partition(s). If you want to reinstall Ubuntu or switch to another distro, you can wipe out everything on root and still have all your data intact on another partition. And why create 3 partitions for data? I'd understand /home and a fat32 for sharing data between Windows and Ubuntu, but three partitions for data and a 82 GB root? Also, three gigs of swap is usually exaggeration, IHMO. On the other hand, you do have a lot of disk space so why not... Well, maybe you have a good reason for those partitions.)[/COLOR][/QUOTE]

Well i backed up the harddisk and going to repartion it now. 
About all those partitions: i just find it easier (in windows) to use more partitions the to use one big divided in subfolders. For instance that 200 GiB Pata has one partition for movies (75 GiB), one backup partition (20 GiB) and one shared (Fat32, 10 GiB). I'm also going to follow your advise, a smaller root partition and one seperate for all my data :).

---

### Post by dexter on 2006-02-11
OK, we are getting a lot closer. I've installed Ubuntu again on the totaly free hd, set the linux partitions in the beginning of the disk, installed grub. When i turn on my computer i see grub and i can get into ubuntu just fine :). However grub is not able to boot windows, it says NTLDR is missing. However when ik change the boot order in the bios so the SATA disk containing windows is primary i get into windows like usual. 

So i can get into both Linux and Windows, however a bit clumsy... I don't have time today or tomorrow but after then i'm gonna try to modify grub in some way so that it is able to boot windows. I will let you know how it ends. Thx guys :).

---

### Post by lha on 2006-02-11
You'll probably have to add
```
map (hd0) (hd1)
map (hd1) (hd0)
```
to your Windows entry in menu.lst. If you post the output of
```
cat /boot/grub/menu.lst
```
I can confirm it.

---

### Post by dexter on 2006-02-11
The output of 
```
cat /boot/grub/menu.lst
```
is
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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hdc1 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-10-amd64-generic Default 
root		(hd0,0)
kernel		/boot/vmlinuz root=/dev/hdc1 ro quiet splash
initrd		/boot/initrd.img
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-amd64-generic Default (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz root=/dev/hdc1 ro single
initrd		/boot/initrd.img
boot

title		Ubuntu, kernel 2.6.12-9-amd64-generic Previous 
root		(hd0,0)
kernel		/boot/vmlinuz.old root=/dev/hdc1 ro quiet splash
initrd		/boot/initrd.img.old
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-amd64-generic Previous (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz.old root=/dev/hdc1 ro single
initrd		/boot/initrd.img.old
boot

title		Ubuntu, kernel 2.6.12-10-amd64-generic 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-amd64-generic root=/dev/hdc1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-amd64-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-amd64-generic root=/dev/hdc1 ro single
initrd		/boot/initrd.img-2.6.12-10-amd64-generic
boot

title		Ubuntu, kernel 2.6.12-9-amd64-generic 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-amd64-generic root=/dev/hdc1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-amd64-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-amd64-generic root=/dev/hdc1 ro single
initrd		/boot/initrd.img-2.6.12-9-amd64-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1


```

---

### Post by lha on 2006-02-11
[QUOTE=dexter]The output of 
```
cat /boot/grub/menu.lst
```
is
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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hdc1 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-10-amd64-generic Default 
root		(hd0,0)
kernel		/boot/vmlinuz root=/dev/hdc1 ro quiet splash
initrd		/boot/initrd.img
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-amd64-generic Default (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz root=/dev/hdc1 ro single
initrd		/boot/initrd.img
boot

title		Ubuntu, kernel 2.6.12-9-amd64-generic Previous 
root		(hd0,0)
kernel		/boot/vmlinuz.old root=/dev/hdc1 ro quiet splash
initrd		/boot/initrd.img.old
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-amd64-generic Previous (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz.old root=/dev/hdc1 ro single
initrd		/boot/initrd.img.old
boot

title		Ubuntu, kernel 2.6.12-10-amd64-generic 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-amd64-generic root=/dev/hdc1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-amd64-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-amd64-generic root=/dev/hdc1 ro single
initrd		/boot/initrd.img-2.6.12-10-amd64-generic
boot

title		Ubuntu, kernel 2.6.12-9-amd64-generic 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-amd64-generic root=/dev/hdc1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-amd64-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-amd64-generic root=/dev/hdc1 ro single
initrd		/boot/initrd.img-2.6.12-9-amd64-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1


```[/QUOTE]

Try if replaceing
```
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1
```
with
```
title		Microsoft Windows XP Professional
root		(hd**1**,0)
savedefault
makeactive
map		(hd0) (hd**1**)
map		(hd**1**) (hd0)
chainloader	+1
```
helps. It's not easy for grub to guess how your drives are mapped, so it may have those drive numbers wrong.

---

### Post by dexter on 2006-02-12
Allright! grub is now booting linux and windows :cool:.

Thx a lot guys!

---

