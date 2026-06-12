---
title: "Problems with grub"
date: 2008-10-12
forum: General Help
---

### Post by renezerg on 2008-10-12
hellow guys, im new at this forum, and as you can see my english is quite poor,, anyway this is my problem..

first of all i have ubuntu 8.04 and windows xp home
I have  reinstalled ubuntu (after some problems with it, i removed it and installed it again),,,the problem is that when i try to enter to windows, the scrren show me the following mesagge: invalid partition table.

Im really confused and worried, because i dont know if i have lost windows xp (and all my files). Is there a way to know if i have lost it? and How can i solve this problem?? :confused:

---

### Post by spiderbatdad on 2008-10-12
can you log into ubuntu? when you do run this command in a terminal and paste the results here, please;
```
sudo fdisk -l
```

---

### Post by renezerg on 2008-10-12
thx for your answer,, this is the report:

rene@rene-desktop:~$ sudo fdisk -l
[sudo] password for rene: 

Disco /dev/sda: 40.0 GB, 40020664320 bytes
255 cabezas, 63 sectores/pista, 4865 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x128f128f

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        4865    18595237+   f  W95 Ext'd (LBA)
/dev/sda5            2551        2956     3261163+   7  HPFS/NTFS
/dev/sda6            2957        4779    14643216   83  Linux
/dev/sda7            4780        4865      690763+  82  Linux swap / Solaris
rene@rene-desktop:~$

---

### Post by renezerg on 2008-10-12
sorry that was in spanish ,,, this is the report in english:

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x128f128f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        4865    18595237+   f  W95 Ext'd (LBA)
/dev/sda5            2551        2956     3261163+   7  HPFS/NTFS
/dev/sda6            2957        4779    14643216   83  Linux
/dev/sda7            4780        4865      690763+  82  Linux swap / Solaris

---

### Post by spiderbatdad on 2008-10-12
ok that looks promising. Now can we see ```
cat /boot/grub/menu.lst
```

---

### Post by renezerg on 2008-10-12
ok this is the report::

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
# kopt=root=UUID=ce53bfc0-1929-48f1-8c17-6bb0065d54f0 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=ce53bfc0-1929-48f1-8c17-6bb0065d54f0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=ce53bfc0-1929-48f1-8c17-6bb0065d54f0 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

title Windows XP
root (hd0,0)
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST



as you can see i added the last 3 lines because thw windows option didnt appear at grub at first.

---

### Post by dburnett77 on 2008-10-12
I searched on google for an answer: "grub menu.lst" and one of the posts I encountered gave the advice of using System Rescue CD.  Here's the site:

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

I've never used it myself, but it looks like it has the tools you need.
Hope that helps.

---

### Post by spiderbatdad on 2008-10-12
> **renezerg said:**
> ok this is the report::

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
# kopt=root=UUID=ce53bfc0-1929-48f1-8c17-6bb0065d54f0 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=ce53bfc0-1929-48f1-8c17-6bb0065d54f0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=ce53bfc0-1929-48f1-8c17-6bb0065d54f0 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

title Windows XP
root (hd0,0)
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST



as you can see i added the last 3 lines because thw windows option didnt appear at grub at first.

the windows option should be outside (below) the ###END DEBIAN AUTOMAGIC KERNELS LIST. It doesn't look quite right...as (hd,0,0) is your ntfs boot partition according to fdisk... sda1=hd0,0

Also you need the line makeactive...something like this (below the debian kernels:

```
### END DEBIAN AUTOMAGIC KERNELS LIST
title Windows XP
root (hd0,0)(hd0,4)
makeactive
chainloader +1

``` Not 100% sure on the syntax...will try to find you a better example or maybe someone else will chime in.


SEE here:[http://www.linuxquestions.org/questions/linux-software-2/how-do-i-add-windows-xp-to-grub-boot-loader-375198/](http://www.linuxquestions.org/questions/linux-software-2/how-do-i-add-windows-xp-to-grub-boot-loader-375198/)

---

### Post by renezerg on 2008-10-12
ok i dont know if i did it correct, but this is the menu.lst now:

this is the last part:

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=ce53bfc0-1929-48f1-8c17-6bb0065d54f0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=ce53bfc0-1929-48f1-8c17-6bb0065d54f0 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Windows XP
root (hd0,0)
chainloader +1


however, when i try to log in windows, the next message appear :

invalid partition table

T_T

---

### Post by caljohnsmith on 2008-10-12
What is on partition sda5? Is that for your data? I assume Windows is in sda1--is that correct? Also, do you have your Windows Install CD? I would begin by booting that, and run the following two commands from the "recovery console":
```
fixboot
chkdsk /r
```
And because you are getting an invalid partition table error, I would recommend checking to see if your HDD's partition table is corrupt. You can do that with "testdisk." First enable all your repositories in System > Prefs > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen.

---

### Post by renezerg on 2008-10-12
thank you for your answer caljohnsmith,, first of all, i dont have a windows cd, it was installed in my computer when i bought it...

i think sda5, is the place where my files are, because my windows system had two partitions.


i will try to do what you said at this moment, i am quite newbie at linux but i will try to do my best

---

### Post by spiderbatdad on 2008-10-12
title Other operating systems:

title
root

title WindowsXP
rootnoverify (hd0,0)
makeactive
chainloader +1

---

### Post by renezerg on 2008-10-12
okay i dont know if i did it correctly but this is the report of testdisk:

TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 40 GB / 37 GiB - CHS 4866 255 63
     Partition               Start        End    Size in sectors
L HPFS - NTFS           2550   1  1  2955 254 63    6522327 [RENE]
L Linux                 2956   1  1  4778 254 63   29286432
L Linux Swap            4779   1  1  4864 254 63    1381527










Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
NTFS, 3339 MB / 3184 MiB

---

### Post by caljohnsmith on 2008-10-12
Renezerg, can you post the screen in testdisk that comes before the screen you posted? It should show all your partitions.

---

### Post by renezerg on 2008-10-12
is this??

TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 40 GB / 37 GiB - CHS 4866 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

Invalid NTFS boot
 1 * HPFS - NTFS              0   1  1  2549 254 63   40965687
 1 * HPFS - NTFS              0   1  1  2549 254 63   40965687
 2 E extended LBA          2550   0  1  4864 254 63   37190475
 5 L HPFS - NTFS           2550   1  1  2955 254 63    6522327 [RENE]
   X extended              2956   0  1  4778 254 63   29286495
 6 L Linux                 2956   1  1  4778 254 63   29286432
   X extended              4779   0  1  4864 254 63    1381590
 7 L Linux Swap            4779   1  1  4864 254 63    1381527





*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
[Proceed ]  [ Backup ]
                            Try to locate partition

---

### Post by renezerg on 2008-10-12
and after that screen the program asks

Should TestDisk search for partition created under Vista ? [Y/N] (answer Yes if
unsure)



i put yes

---

### Post by caljohnsmith on 2008-10-12
OK, before we go further, let's see if Ubuntu can mount your Windows partition so we can check on your files:
```
sudo mount /dev/sda1 /mnt
ls -l /mnt
```
Please post the output.

---

### Post by renezerg on 2008-10-12
well, when i put :

sudo mount /dev/sda1 /mnt

it says:

mount: you must specify the filesystem type

---

### Post by caljohnsmith on 2008-10-12
OK, that's not a good sign at all, because mount should be able to detect that sda1 is NTFS. Try:
```
sudo mount -t ntfs-3g /dev/sda1 /mnt -o force
ls -l /mnt
```

---

### Post by renezerg on 2008-10-12
ok :::

rene@rene-desktop:~$ sudo mount -t ntfs-3g /dev/sda1 /mnt -o force
NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

---

### Post by caljohnsmith on 2008-10-12
OK, since you don't have a Windows XP Install CD, you can download a Windows Recovery CD from [here]("http://www.webtree.ca/windowsxp/tools/bootdiscs/xp_rec_con.zip"). You'll need to run those two commands I gave in post #10:
```
fixboot
chkdsk /r
```
Let's see how much that helps, but we may have to work on your partition table with testdisk.

---

### Post by renezerg on 2008-10-12
thank you for youre help,,,, i have some doubts,,
is it necesary to burn the windows recovery in a cd???
and which program can i use to burn it in ubuntu?

---

### Post by caljohnsmith on 2008-10-12
Yes, you'll need to burn it to a CD, and you can use a CD-RW if you want to use that CD later for something else. There are at least a few good CD burning programs in Linux, and the one that happens to work best with my CD-ROM is "k3b". Other good CD burners are "brasero" and "gnomebaker". You can install any of them using Synaptic Package Manager if you like (System > Admin > Synaptic Package Manager). Once you install them they will show up in one of your menus under the main "Applications" menu on your desktop. Let me know how it goes.

---

### Post by renezerg on 2008-10-12
ok i suppose i have have to burn it as image right?

plz wait some minutes because i have to buy one cd xD

thx

---

### Post by renezerg on 2008-10-12
omg it took a lot of time but it seems that the problem is solved,,
after using

fixboot
chkdsk /r

now i can log in windows, thxthxthxthxthx   Thanks :D :guitar:

---

### Post by renezerg on 2008-10-12
however i just have a bit problem,,, that is that i have to press ESC in order to go to the systems selection screen of grub, so how can i avoid that

---

### Post by caljohnsmith on 2008-10-12
Glad you can boot into Windows now. :) To make your Grub menu show up without having to hit escape, first open up your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And near the top where the line says "hiddenmenu", just put a pound sign in front of it:
```
#hiddenmenu
```
Also, you can change the amount of time before Grub boots the default OS by changing the line with "timeout <number>" where <number> is in seconds. Anyway, cheers and have fun. :)

---

### Post by renezerg on 2008-10-12
:guitar::guitar::guitar::guitar::guitar:

Youre amazing man,, i cannot really find a word in my poor english vocabulary to express how happy i feel right now,, i really thought i would lose all my files...

All is okay now  :):)

Ubuntu rocks (if you know how to use it xD, so i have to learn)
you rock man

thx thx

---

