---
title: "Grub not loading!"
date: 2009-06-08
forum: Installation &amp; Upgrades
---

### Post by mrmichael on 2009-06-08
Greetings,
I 've just installed the new ubuntu 9.04 but I have some problems booting it. Actually my grub is not loading. I have two partitions on my hard drive, one with windows xp and the second one carries ubuntu. I have had this problem previously and someone told me to post the menu.lst file so here it is. Can you tell me please what should I change for making grub load properly ?

Cheers,
Mike :)

[HTML]# menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=793aa0f3-19c7-4aa3-acae-3f5367ed1528 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=793aa0f3-19c7-4aa3-acae-3f5367ed1528

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		793aa0f3-19c7-4aa3-acae-3f5367ed1528
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=793aa0f3-19c7-4aa3-acae-3f5367ed1528 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		793aa0f3-19c7-4aa3-acae-3f5367ed1528
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=793aa0f3-19c7-4aa3-acae-3f5367ed1528 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		793aa0f3-19c7-4aa3-acae-3f5367ed1528
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
rootnoverify	(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdd1
title		Microsoft Windows XP Professional
rootnoverify	(hd3,0)
savedefault
makeactive
map		(hd0) (hd3)
map		(hd3) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdf1
title		Microsoft Windows XP Professional
rootnoverify	(hd5,0)
savedefault
makeactive
map		(hd0) (hd5)
map		(hd5) (hd0)
chainloader	+1
[/HTML]

---

### Post by torgrot on 2009-06-08
Something is definitely amiss there.  According to you menu.lst you have three copies of Wndow XP running in three seperate partitions.  I think some more info will be needed before any suggestions can be made.  Would you post the output of the following command:
 
fdisk -l
 
That is a lower case "L" not a one or an i.
 
torgort

---

### Post by ajgreeny on 2009-06-08
> **torgrot said:**
> Something is definitely amiss there.  According to you menu.lst you have three copies of Wndow XP running in three seperate partitions.  I think some more info will be needed before any suggestions can be made.  Would you post the output of the following command:
 
fdisk -l
 
That is a lower case "L" not a one or an i.
 
torgort
Not just on separate partitions but on separate disks according to your menu.lst.

As torgrot says, there is something very wrong with the listings if you only have one disk, and I wonder if you have already edited the file as the various mapping of drives shown in each windows entry is not usually added by the system, as far as I'm aware, but has to be added manually when problems rear there heads.

---

### Post by mrmichael on 2009-06-08
Hullo and thank you for your replies!
My fdisk -l logs are:

[HTML]Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3a903a91

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       77825   625129281    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x01ac01ac

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdc: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3a903a90

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       77825   625129281    7  HPFS/NTFS

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60801   488384001    7  HPFS/NTFS

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8968b3ed

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       46938   377029453+   7  HPFS/NTFS
/dev/sde2           46939       60163   106229812+  83  Linux
/dev/sde3           60164       60801     5124735   82  Linux swap / Solaris

Disk /dev/sdf: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffb3bb2d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1       24320   195350368+   7  HPFS/NTFS
[/HTML]

About the three windows partitions I have absolutely no idea why there are that way. Is it necessary to keep all three of them ?

Thanks a lot!!!
Mike

---

### Post by torgrot on 2009-06-08
Whoa there dude, do you know how many hard drives you have? According to that list there are six(6) disk drives 
/sda is a 640GB 
/sdb is a 500GB
/sdc is a 640GB
/sdd is a 500GB
/sde is a 500GB 
/sdf is a 200GB 
 
Do you actually have six hard drives connected?
Was this configured as a raid array under windows?
 
torgrot

---

### Post by mrmichael on 2009-06-08
Hey there!
Yeap there are six hard drives. It's not false what it says. Nop not raid array connection. Just sata connected!
Is this a problem? Should I change something else, or just the menu.lst ?

Cheers,
Mike

---

### Post by ajgreeny on 2009-06-08
So you have 6 hard disks?  WOW! What a setup.  However it has made the job of sorting out the disks rather difficult.  

Have you got known data or OSs on all the disks or are you baffled about what is on each?  With all the hard disks mounted, can you run ```
df -h
``` which will show the space free on each disk which may give a clue about what is on each of them.  It certainly is a lot of space to fill, but if *fdisk -l* shows it, I suppose it must be there, so lets keep trying to sort it all out.

---

### Post by torgrot on 2009-06-08
I will bow out here and let ajgreeny help you.  You don't need multiple people yammering at you.
 
torgrot

---

### Post by mrmichael on 2009-06-08
Hey!
I use the "win xp" labeled disk for my OS's. All the other are for data and backup. I noticed a strange thing in my media. I have a "File System" disk and a "108.8GB" volume that contains ubuntu files too. I have installed my ubuntu only once at a 108gb partition.

Here are the df -l logs:
[HTML]Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 1.6G  2.4M  1.6G   1% /lib/modules/2.6.28-11-generic/volatile
tmpfs                 1.6G  2.4M  1.6G   1% /lib/modules/2.6.28-11-generic/volatile
tmpfs                 1.6G     0  1.6G   0% /lib/init/rw
varrun                1.6G  104K  1.6G   1% /var/run
varlock               1.6G     0  1.6G   0% /var/lock
udev                  1.6G  208K  1.6G   1% /dev
tmpfs                 1.6G   76K  1.6G   1% /dev/shm
rootfs                1.6G   45M  1.6G   3% /
/dev/sr2              699M  699M     0 100% /cdrom
/dev/loop0            676M  676M     0 100% /rofs
tmpfs                 1.6G   12K  1.6G   1% /tmp
/dev/sde2             100G  2.2G   93G   3% /media/disk
/dev/sde1             360G   15G  345G   5% /media/win xp
/dev/sdc1             597G  521G   76G  88% /media/&#931;&#949;&#953;&#961;&#941;&#962;
/dev/sdf1             187G   75G  112G  41% /media/&#917;&#966;&#945;&#961;&#956;&#959;&#947;&#941;&#962;
/dev/sdb1             466G  372G   95G  80% /media/&#932;&#945; &#941;&#947;&#947;&#961;&#945;&#966;&#940; &#956;&#959;&#965;
/dev/sda1             597G  209G  388G  36% /media/&#932;&#945;&#953;&#957;&#943;&#949;&#962;
/dev/sdd1             466G  376G   91G  81% /media/&#932;&#945; &#941;&#947;&#947;&#961;&#945;&#966;&#940; &#956;&#959;&#965; &#914;
[/HTML]

---

### Post by zubin71 on 2009-06-08
repair the grub. its easy.
1. boot in using a live cd
2. open up a terminal and do the following:-

$ grub

then you get the grub prompt

grub>

execute the following commands

1. find /boot/grub/menu.lst
this will return a partition number; the partition with linux installed. im assuming it to be "1" here.
2. root (hd0,1)
3. setup (hd0)

typing out the above commands at the grub prompt sequentially should solve the problem. what it does is, it installs a new grub on the partition. 

hope it helps!!!

cheers!

---

### Post by mrmichael on 2009-06-08
Hello!
That's exactly what I've done previously, but grub is still not loading.
I've done it again for the recording without any success!
Is there anything else that might help me?

Thanks you!
Mike

---

### Post by merlinus on 2009-06-08
```

sudo grub
root (hd4,1)
setup (hd4)
quit

```

---

### Post by mrmichael on 2009-06-08
Hey!
I tried that twice already but without success...
Any alternative please?

Mike

---

### Post by merlinus on 2009-06-08
From what you posted, it seems that ubuntu is on sde2, so these grub commands *should* have installed it to the boot sector on that hdd.

Since it did not work, I suggest trying supergrub.

---

### Post by dnairb on 2009-06-08
If, as you say, GRUB is installed to the root of hd4 (/dev/sde in the fdisk -l listing), then you might check that this disk is set as the first boot device in your machine's BIOS

---

### Post by boof1988 on 2009-06-08
> **merlinus said:**
> From what you posted, it seems that ubuntu is on sde2, so these grub commands *should* have installed it to the boot sector on that hdd.

Since it did not work, I suggest trying supergrub.

Here are links to the website...

Website: [Super GrUB Disk](http://www.supergrubdisk.org/)
CD image download: [CDROM image mirrors](http://www.supergrubdisk.org/index.php?pid=5)

---

### Post by mrmichael on 2009-06-08
Okay I located the problem at the hard drive boot priority!
It's running smoothly now!

Thanks a lot guys!!!!

---

### Post by mrmichael on 2009-06-08
Actually I spoke too early :P
Now when grub loads I have 3 xp choices but none of them can boot the OS.
Any ideas with that one ?
Should I remove something from my menu.lst ?

---

### Post by merlinus on 2009-06-08
Post menu.lst, and we can have a look.

---

### Post by mrmichael on 2009-06-08
[HTML]# menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=793aa0f3-19c7-4aa3-acae-3f5367ed1528 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=793aa0f3-19c7-4aa3-acae-3f5367ed1528

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		793aa0f3-19c7-4aa3-acae-3f5367ed1528
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=793aa0f3-19c7-4aa3-acae-3f5367ed1528 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		793aa0f3-19c7-4aa3-acae-3f5367ed1528
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=793aa0f3-19c7-4aa3-acae-3f5367ed1528 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		793aa0f3-19c7-4aa3-acae-3f5367ed1528
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
rootnoverify	(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdd1
title		Microsoft Windows XP Professional
rootnoverify	(hd3,0)
savedefault
makeactive
map		(hd0) (hd3)
map		(hd3) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdf1
title		Microsoft Windows XP Professional
rootnoverify	(hd5,0)
savedefault
makeactive
map		(hd0) (hd5)
map		(hd5) (hd0)
chainloader	+1
[/HTML]

---

### Post by merlinus on 2009-06-08
Try changing this:

title        Microsoft Windows XP Professional
rootnoverify    (hd5,0)
savedefault
makeactive
map        (hd0) (hd5)
map        (hd5) (hd0)
chainloader    +1

to 

title        Microsoft Windows XP Professional
rootnoverify    (hd4,0)
savedefault
makeactive
chainloader    +1

and deleting all the other windows entries.

Make sure to save a copy first!

---

### Post by mrmichael on 2009-06-08
Tried it but no luck. It still says NBR is missing ctr alt del to restart...

---

### Post by merlinus on 2009-06-08
I may have missed your previous post on this, but it would seem to be a windows problem, not grub nor ubuntu.

Also, is the error with NBR, not MBR?

---

### Post by mrmichael on 2009-06-08
Actually was NTLDR. I am very sorry for the mistake...

---

### Post by merlinus on 2009-06-08
That is the windows bootloader.  Here is a suggestion, now that you know that windows is on sde1 and ubuntu on sde2, and your hdds are loading in correct order.

Use your xp disk, boot into recovery mode, and fixmbr.  Then reinstall grub.

---

### Post by merlinus on 2009-06-08
More info here:

[http://pcsupport.about.com/od/fixthe...drntdetect.htm]("http://pcsupport.about.com/od/fixtheproblem/ht/ntldrntdetect.htm")

---

### Post by mrmichael on 2009-06-09
Thanks once more but no luck again...
Still the ntldr message appears!
Shoooosh

---

