---
title: "Help please! :("
date: 2009-06-05
forum: Installation &amp; Upgrades
---

### Post by lawson012 on 2009-06-05
Ok i recently installed ubuntu onto my laptop on my hard drive which also has vista on it. I only really wanted ubuntu to test it out so I set it to take up 10GB's.
 
So I all went well and i started messing around with ubuntu but i had forgotten my internet passwork which was saved on my windows vista section. I restarted my comp and got a grub menu showing:
Ubuntu
Ubuntu recovery
Ubuntu mem test 
 
And under other OS i found windows loader -.-
Went on windows loader and found myself choosing whether to switch my system back to factory settings.
 
SO please help I want to get my windows data back, I want to back on windows! 
How do i get the option on the Grub menu.
1 other thing i think i know that i havnt overwritten all my hard drive with ubuntu because i only have 10gb space on it.

---

### Post by merlinus on 2009-06-05
Boot into ubuntu and open a terminal (Applications/Accessories/Terminal), enter this command, and post the results:

```

sudo fdisk -l

```It will ask for your ubuntu password.

It will tell you what partitions exist on your hdd.

---

### Post by lawson012 on 2009-06-05
Ok im a noob at this so im not sure what im looking for heres what it says.
 
fdisk: invalid option -- '1'
 
Usage: fdisk [-b SSZ] [-u] disk change partition table
Fdisk -l [-b SSZ] [-u] List partition table (s)
fdisk -s PARTITION Give partition sizes (s) in blocks
fdisk -v Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give start and end in secor (instead of cylinder) units
-b 2048: (for ceertain M0 disks) use 2048-byte sectors

---

### Post by merlinus on 2009-06-05
l is a lowercase L

---

### Post by lawson012 on 2009-06-05
oh **** sorry

---

### Post by paulb42 on 2009-06-05
sudo fdisk -l ( that's l ( lower case L  ) not 1 (one) )

---

### Post by lawson012 on 2009-06-05
Disk /dev/sda: 160.0 BD, 160041885696 bytes
255 heads, 63 sectors/tracks, 19457 cylinders
units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1ff16d35
 
Device boot                   Start                End                 Blocks        Id    System
/dev/sda1                         1                     16677      133951372      7   Hpfs/ntfs
/dev/sda2     *            17952                 19457            12096945    7    Hpfs/ntfs
/dev/sda3                   16678                17951             10233405     5  Extended
/dev/sda5                   16678                17891            9751423+     83  Linux
/dev/sda6              17892               17951                 481918+    82 linuxswap/solaris
 
Partition table entries are not in disk order

---

### Post by yaroto98 on 2009-06-05
now when grub boots up hit "e" to edit, and change the windows boot from /dev/sda2 to /dev/sda1
*or vice versa*

does that work?

---

### Post by merlinus on 2009-06-05
From what I can see, windows is on sda2.

Post results of:

```

cat boot/grub/menu.lst

```

---

### Post by yaroto98 on 2009-06-05
Also you can use the live cd to boot to an existing os, you could try that. it may be easier for you, grub can be a pain sometimes.

---

### Post by philinux on 2009-06-05
Open a terminal and post back the output of this.

```
cat /boot/grub/menu.lst
```

---

### Post by Heeter on 2009-06-05
Well your NTFS partitions are still there, so that's good news.

What I would recommend: Mount your ntfs partitions onto Ubuntu and retrieve your files and continue using Ubuntu happily.


Heeter

---

### Post by lawson012 on 2009-06-05
Says there is no such directory for cat /boot/grub/menu.1st

---

### Post by lawson012 on 2009-06-05
There is no windows section
Only windows (loader) which basically loads up system restore

---

### Post by merlinus on 2009-06-05
menu.lst, not menu.1st  -- once again, a lowercase L

Best to copy-and-paste -- fewer errors that way.  ;)

---

### Post by lawson012 on 2009-06-05
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
default  0
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout  10
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
# title  Windows 95/98/NT/2000
# root  (hd0,0)
# makeactive
# chainloader +1
#
# title  Linux
# root  (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=22cc7de1-8f02-4427-b364-a4610b11b068 ro
## default grub root device
## e.g. groot=(hd0,0)
# groot=22cc7de1-8f02-4427-b364-a4610b11b068
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
title  Ubuntu 9.04, kernel 2.6.28-11-generic
uuid  22cc7de1-8f02-4427-b364-a4610b11b068
kernel  /boot/vmlinuz-2.6.28-11-generic root=UUID=22cc7de1-8f02-4427-b364-a4610b11b068 ro quiet splash 
initrd  /boot/initrd.img-2.6.28-11-generic
quiet
title  Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid  22cc7de1-8f02-4427-b364-a4610b11b068
kernel  /boot/vmlinuz-2.6.28-11-generic root=UUID=22cc7de1-8f02-4427-b364-a4610b11b068 ro  single
initrd  /boot/initrd.img-2.6.28-11-generic
title  Ubuntu 9.04, memtest86+
uuid  22cc7de1-8f02-4427-b364-a4610b11b068
kernel  /boot/memtest86+.bin
quiet
### END DEBIAN AUTOMAGIC KERNELS LIST
# This is a divider, added to separate the menu items below from the Debian
# ones.
title  Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title  Windows Vista (loader)
rootnoverify (hd0,1)
savedefault
makeactive
chainloader +1

---

### Post by merlinus on 2009-06-05
From what I can see, menu.lst is correct.  It references vista on sda2.

So this woluld seem to be a vista problem.  Depending upon what you are wanting, you may need to restore the windows bootloader to the mbr, which can be done from the vista cd by selecting recovery from the opening menu.

How did you shrink the vista partition to make room for ubuntu?

---

### Post by lawson012 on 2009-06-05
i made my own partition on vista before.
Then on the select partition menu on the ubuntu disc i selected largest free space

---

### Post by merlinus on 2009-06-05
So you used vista's disk manager to shrink its partition and free up space for ubuntu?  Did you defrag beforehand?

I am trying to figure out what is going on, hence the questions.

---

### Post by philinux on 2009-06-05
Reboot, press ESC key when grub appears. Use the down arrow key to highlight the vista entry. Boot vista. Note all messages from vista and post them back here.

---

### Post by lawson012 on 2009-06-06
ok i defragged like 2 days before making the partition on vista
 
and on the Grub menu when i press esc it lasts about 1 second

---

### Post by lawson012 on 2009-06-06
1 more thing this is what menu i get but vista insted of xp. and its windows loader so its not acutally any use 
[http://members.iinet.net.au/~herman546/p15.html](http://members.iinet.net.au/~herman546/p15.html)

---

### Post by merlinus on 2009-06-06
The graphic of grub looks correct.  Have you had any success booting into either vista or ubuntu?

Have you tried supergrub to at lest access these?

---

### Post by lawson012 on 2009-06-10
I am using ubuntu at the moment and is fine but what I really need is my documents/games and the safety of knowing windows is safe. ubuntu seems to of overwritten the start up thing off vista

---

### Post by yaroto98 on 2009-06-10
Have you gone to Places-> Computer and mounting your windows partition? you can still access all your documents.

---

### Post by lawson012 on 2009-06-10
will it take them off windows?

I want windows exactly how it was before i installed ubuntu.

I think i have found a solution but it requires getting the vista dvd. I have no idea where to get it. Any ideas?

---

