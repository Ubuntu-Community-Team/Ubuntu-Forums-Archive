---
title: "Installed 9.04 and lost Windows Hdd in Grub"
date: 2009-06-20
forum: Installation &amp; Upgrades
---

### Post by wanderingarticfox on 2009-06-20
I had made a big mess trying to config. 8.10; finally bought von Hagen's 8.10 bible.  I have 2 hard drives and installed a clean instal on the one 8.10 was on but now my GRUB menu no longer shows my XP Home. Thought I would ask for help with reconfiguring GRUB if possible.](*,)](*,)
I have just installed gparted 0.4.3-0ubuntu and grub-doc 0.97-29ubuntu53 via Synaptic and continue doing research; any help would be appreciated.

---

### Post by merlinus on 2009-06-20
Post results of:

```

sudo fdisk -l
cat /boot/grub/menu.lst

```

and indicate which hdd and partition is windows, if you have more than one ntfs partition.

---

### Post by presence1960 on 2009-06-20
fox, post the output of those commands Merlin gave you so he can give you the proper entry for Windows in your menu.lst...

---

### Post by wanderingarticfox on 2009-06-20
OK merlin; I'm a trying here so bear with me as I'm noobie+ on learning. I grabbed this info of G-Parted and I hope it willl help you to help me:) 
/dev/sdal  is ntfs at 33.37 GB and the drive matches my {use to be} Primary HDD it is flagged BOOT but Staus is   Not Mounted. I know enough to know that is why it is not in the GRUB listing when I start/restart. How do I mount this drive.   I did not want to install grub-pc or grub-rescue-pc unless someone says I need them.  I'll work on that command line thing now.
Oh, and thanks for the help:)
  Just saw prescence note; I'm a noob and you need to walk me through.

---

### Post by wanderingarticfox on 2009-06-20
articfox@PolarWatcher:~$ sudo fdisk -1cat /boot/grub/menu.lst
[sudo] password for articfox: 
fdisk: invalid option -- '1'

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
articfox@PolarWatcher:~$ 



I think that's got it

---

### Post by presence1960 on 2009-06-20
Open a terminal - Applications > Accessories > Terminal
when the terminal window opens type > sudo fdisk -l BTW that is a lowercase L. Post the output of that command here.

Then run terminal and use this command > cat /boot/grub/menu.lstThat is a lowercase L in .lst
Post the output of that here also. This should give the info necessary to get windows booting from GRUB

P.S. Just saw your output, you used the number 1 (one) instead of lowercase L (l) Don't feel bad most people do that at first. And use sudo or it won't work.

---

### Post by wanderingarticfox on 2009-06-20
I'm learning on the fly, I do not think I did that correctly, trying to figure out screen shot via Gimp

---

### Post by wanderingarticfox on 2009-06-20
sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb74510e2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4356    34987648+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            4356        4865     4088543    f  W95 Ext'd (LBA)
/dev/sda5            4357        4865     4088542+   b  W95 FAT32

Disk /dev/sdb: 30.7 GB, 30736613376 bytes
255 heads, 63 sectors/track, 3736 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x09aae0b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3577    28732221   83  Linux
/dev/sdb2            3578        3736     1277167+   5  Extended
/dev/sdb5            3578        3736     1277136   82  Linux swap / Solaris
articfox@PolarWatcher:~$

---

### Post by wanderingarticfox on 2009-06-20
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

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		0f930882-7220-4fe4-b488-5bce06e8a8ac
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=0f930882-7220-4fe4-b488-5bce06e8a8ac ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		0f930882-7220-4fe4-b488-5bce06e8a8ac
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=0f930882-7220-4fe4-b488-5bce06e8a8ac ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		0f930882-7220-4fe4-b488-5bce06e8a8ac
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=0f930882-7220-4fe4-b488-5bce06e8a8ac ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		0f930882-7220-4fe4-b488-5bce06e8a8ac
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=0f930882-7220-4fe4-b488-5bce06e8a8ac ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		0f930882-7220-4fe4-b488-5bce06e8a8ac
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
articfox@PolarWatcher:~$

---

### Post by merlinus on 2009-06-20
Add this to the end of menu.lst:

title Windows
rootnoverify    (hd0,0)
makeactive
chainloader    +1

---

### Post by wanderingarticfox on 2009-06-20
I have two HDD's, NTFS is tthe C drive for windows on drive 0,0 with a sav partition in Fat32
Ubuntu should occupy all of the second drive 0,1

---

### Post by wanderingarticfox on 2009-06-20
Listed above

---

### Post by presence1960 on 2009-06-20
> **wanderingarticfox said:**
> I'm learning on the fly, I do not think I did that correctly, trying to figure out screen shot via Gimp

you are doing fine, that is how we all learn! Just one tip, linux does not use the same nomenclature for drives as Windows (C;, D:, E: etc). In here so we can communicate better remember to use this system to refer to drives/partitions:

first drive = sda
first partition on first drive = sda1, second partition on first drive = sda2

second drive = sdb
first partition on second drive = sdb1, second partition on second drive = sdb2

There will be no misunderstandings this way.

In GRUB the first drive starts at 0, as does the first partition start at 0. thus the second partition of your first drive would be (hd0,1).

---

### Post by wanderingarticfox on 2009-06-20
I'm not quite clear on this command Merlin, I think you mean to add a  : after lst then string everything else together? I have a lot to learn for this command stuff to be intuative as you can see, please rewrite accross a larger windowpane so I do not try another gazzilion times; thank you:)



I got a syntax error near unexpected token'('    what ever that means
I entered it like this
cat /boot/grub/menu.lst:title windows rootnoverify (hd0,0) makeactive chainloader+1

please help

---

### Post by merlinus on 2009-06-20
It is usually much better to copy-and-paste commands into the terminal.  Use the terminal menu Edit/Paste for pasting, or Ctrl+Insert.

cat /boot/grub/menu.lst will place the contents of that file into the terminal window.  You can use your mouse to highlight the text, use the menu to copy it, and then paste it into a forum message window using Crl+v.

---

### Post by wanderingarticfox on 2009-06-20
cat /boot/grub/menu.lst:title windows rootnoverify (hd0,0) makeactive chainloader+1
bash: syntax error near unexpected token `('
articfox@PolarWatcher:~$

---

### Post by wanderingarticfox on 2009-06-20
My server connection was lost; looking for help in this thread

Gonna sleep on it and hope merlinus and presence1960 are up tomorrow:)

---

### Post by merlinus on 2009-06-21
Type in the commands one at a time.  You are doing them all at once.

Press the Enter key after each one.

Also, this is text to add to the end of the menu.lst file, not for the terminal:

title windows 
rootnoverify (hd0,0) 
makeactive 
chainloader+1

---

### Post by merlinus on 2009-06-21
There is excellent information available at:

[https://help.ubuntu.com/9.04/index.html](https://help.ubuntu.com/9.04/index.html)

[https://help.ubuntu.com/community](https://help.ubuntu.com/community)

If you are serious about learning and using ubuntu, these are good places to start.

---

### Post by wanderingarticfox on 2009-06-21
at the end of the menu.lst file I am looking at my 'computer name' with a prompt at the end of  cat /boot/grub/menu.lst
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
# kopt=root=UUID=0f930882-7220-4fe4-b488-5bce06e8a8ac ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=0f930882-7220-4fe4-b488-5bce06e8a8ac

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

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		0f930882-7220-4fe4-b488-5bce06e8a8ac
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=0f930882-7220-4fe4-b488-5bce06e8a8ac ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		0f930882-7220-4fe4-b488-5bce06e8a8ac
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=0f930882-7220-4fe4-b488-5bce06e8a8ac ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		0f930882-7220-4fe4-b488-5bce06e8a8ac
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=0f930882-7220-4fe4-b488-5bce06e8a8ac ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		0f930882-7220-4fe4-b488-5bce06e8a8ac
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=0f930882-7220-4fe4-b488-5bce06e8a8ac ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		0f930882-7220-4fe4-b488-5bce06e8a8ac
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
articfox@PolarWatcher:~$ #title   windows  xp
articfox@PolarWatcher:~$ #rootnoverify   (hd0,0)
articfox@PolarWatcher:~$ #makeactive
articfox@PolarWatcher:~$ #chainloader   +1
articfox@PolarWatcher:~$ 
articfox@PolarWatcher:~$ 
articfox@PolarWatcher:~$ 

when I hit enter it just rolls for more data.
I know there is a lot of info on this but I could use a little help so I can get back into windows and turn some settings off in the power management.  Kinda crazy to have a hibernation start when not set for in Ubuntu:confused:](*,)

---

### Post by merlinus on 2009-06-21
```

gksudo gedit /boot/grub/menu.lst

```

will open an editor and the file.  Add the lines I posted to the very end.  Save and restart.

---

### Post by wanderingarticfox on 2009-06-21
I'm still doing something wrong; this is what I did but winows still does not show when I hit 'esc' during boot to view listings:confused:


## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		0f930882-7220-4fe4-b488-5bce06e8a8ac
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=0f930882-7220-4fe4-b488-5bce06e8a8ac ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		0f930882-7220-4fe4-b488-5bce06e8a8ac
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=0f930882-7220-4fe4-b488-5bce06e8a8ac ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		0f930882-7220-4fe4-b488-5bce06e8a8ac
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=0f930882-7220-4fe4-b488-5bce06e8a8ac ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		0f930882-7220-4fe4-b488-5bce06e8a8ac
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=0f930882-7220-4fe4-b488-5bce06e8a8ac ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		0f930882-7220-4fe4-b488-5bce06e8a8ac
kernel		/boot/memtest86+.bin
quiet

title           Windows
rootnoverify    (hd0,0)
makeactive
chainloader     +1
### END DEBIAN AUTOMAGIC KERNELS LIST


Am I entering this in the proper place and order? :confused:

---

### Post by merlinus on 2009-06-21
See my reply to your new post in the General Help forum.

FWIW, double posting mostly creates confusion for those wishing to be of assistance.

---

