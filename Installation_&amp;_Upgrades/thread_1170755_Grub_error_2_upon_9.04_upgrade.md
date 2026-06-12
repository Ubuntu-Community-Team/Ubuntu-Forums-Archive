---
title: "Grub error 2 upon 9.04 upgrade"
date: 2009-05-26
forum: Installation &amp; Upgrades
---

### Post by MedellinManDem on 2009-05-26
I've just upgraded to Ubuntu 9.04 and now it won't boot up giving me "Error 2".

Here is the info shown from the "Results.txt" document:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sdb1 and 
                       looks at sector 187172943 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  [H[2J Arch Linux () ()
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00007fce

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   268,414,019   268,413,957   7 HPFS/NTFS
/dev/sda2         268,414,020   398,283,479   129,869,460   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2ad8e1c9

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   363,454,559   363,454,497  83 Linux
/dev/sdb2         363,454,560   384,419,384    20,964,825  83 Linux
/dev/sdb3         384,419,385   390,716,864     6,297,480  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="EEAC2526AC24EB33" TYPE="ntfs" 
/dev/sda2: UUID="0A90EE3690EE27C1" LABEL="Backup" TYPE="ntfs" 
/dev/sdb1: UUID="3b643562-bb75-4f72-996b-e06fa2d5222c" TYPE="ext3" 
/dev/sdb2: UUID="10f2b587-9ddf-4d61-93dc-d926672ea1ca" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb3: TYPE="swap" UUID="bc84efeb-4ded-4eb5-a8e9-466d29edebb1" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /media/disk-1 type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sda1 on /mnt type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /mnt type ext3 (rw)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn


=================== sda1: Location of files loaded by Grub: ===================


  20.4GB: boot/grub/stage2

=========================== sdb1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=3b643562-bb75-4f72-996b-e06fa2d5222c ro

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
# defoptions=quiet splash vga=795

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

title		Ubuntu 9.04, kernel 2.6.28-12-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=3b643562-bb75-4f72-996b-e06fa2d5222c ro quiet splash vga=795 
initrd		/boot/initrd.img-2.6.28-12-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-12-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=3b643562-bb75-4f72-996b-e06fa2d5222c ro  single
initrd		/boot/initrd.img-2.6.28-12-generic

title		Ubuntu 9.04, memtest86+
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


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=3b643562-bb75-4f72-996b-e06fa2d5222c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb2
UUID=f71e5f4e-751f-4fa4-976c-3816fc9c4433 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  95.8GB: boot/grub/menu.lst
  95.8GB: boot/grub/stage2
  95.9GB: boot/initrd.img-2.6.24-21-generic
  95.8GB: boot/initrd.img-2.6.24-21-generic.bak
  96.1GB: boot/initrd.img-2.6.27-14-generic
 144.9GB: boot/initrd.img-2.6.28-12-generic
  95.8GB: boot/vmlinuz-2.6.24-21-generic
 127.7GB: boot/vmlinuz-2.6.27-14-generic
  96.1GB: boot/vmlinuz-2.6.28-12-generic
 144.9GB: initrd.img
  96.1GB: initrd.img.old
  96.1GB: vmlinuz
 127.7GB: vmlinuz.old

=========================== sdb2/boot/grub/menu.lst: ===========================

# Config file for GRUB - The GNU GRand Unified Bootloader
# /boot/grub/menu.lst

# DEVICE NAME CONVERSIONS 
#
#  Linux           Grub
# -------------------------
#  /dev/fd0        (fd0)
#  /dev/sda        (hd0)
#  /dev/sdb2       (hd1,1)
#  /dev/sda3       (hd0,2)
#

#  FRAMEBUFFER RESOLUTION SETTINGS
#     +-------------------------------------------------+
#          | 640x480    800x600    1024x768   1280x1024
#      ----+--------------------------------------------
#      256 | 0x301=769  0x303=771  0x305=773   0x307=775
#      32K | 0x310=784  0x313=787  0x316=790   0x319=793
#      64K | 0x311=785  0x314=788  0x317=791   0x31A=794
#      16M | 0x312=786  0x315=789  0x318=792   0x31B=795
#     +-------------------------------------------------+
#  for more details and different resolutions see
#  http://wiki.archlinux.org/index.php/GRUB#Framebuffer_Resolution 

# general configuration:
timeout   5
default   0
color light-blue/black light-cyan/blue

# boot sections follow
# each is implicitly numbered from 0 in the order of appearance below
#
# TIP: If you want a 1024x768 framebuffer, add "vga=773" to your kernel line.
#
#-*

# (0) Arch Linux
title  Arch Linux  [/boot/vmlinuz26]
root   (hd0,0)
kernel /vmlinuz26 root=/dev/sda3 ro
initrd /kernel26.img

# (1) Windows
#title Windows
#rootnoverify (hd0,0)
#makeactive
#chainloader +1

=============================== sdb2/etc/fstab: ===============================

# 
# /etc/fstab: static file system information
#
# <file system>        <dir>         <type>    <options>          <dump> <pass>
none                   /dev/pts      devpts    defaults            0      0
none                   /dev/shm      tmpfs     defaults            0      0

#/dev/cdrom             /media/cd   auto    ro,user,noauto,unhide   0      0
#/dev/dvd               /media/dvd  auto    ro,user,noauto,unhide   0      0
#/dev/fd0               /media/fl   auto    user,noauto             0      0

UUID=10f2b587-9ddf-4d61-93dc-d926672ea1ca / ext3 defaults 0 1
UUID=bc84efeb-4ded-4eb5-a8e9-466d29edebb1 swap swap defaults 0 0
UUID=10f2b587-9ddf-4d61-93dc-d926672ea1ca / ext3 defaults 0 1
UUID=bc84efeb-4ded-4eb5-a8e9-466d29edebb1 swap swap defaults 0 0

=================== sdb2: Location of files loaded by Grub: ===================


 194.3GB: boot/grub/menu.lst
 194.3GB: boot/kernel26-fallback.img
 194.3GB: boot/kernel26.img
 194.3GB: boot/vmlinuz26
```

Can anyone help?

---

### Post by presence1960 on 2009-05-26
your menu.lst looks like Hardy's in that is uses root (hd1,0) instead of UUID. see my clip from jaunty's menu.lst
```

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-12-generic
uuid		8319981e-03bb-4bd9-9d2e-276da66b4f1c
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=8319981e-03bb-4bd9-9d2e-276da66b4f1c ro quiet splash vga=789 
initrd		/boot/initrd.img-2.6.28-12-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-12-generic (recovery mode)
uuid		8319981e-03bb-4bd9-9d2e-276da66b4f1c
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=8319981e-03bb-4bd9-9d2e-276da66b4f1c ro  single
initrd		/boot/initrd.img-2.6.28-12-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		8319981e-03bb-4bd9-9d2e-276da66b4f1c
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=8319981e-03bb-4bd9-9d2e-276da66b4f1c ro quiet splash vga=789 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		8319981e-03bb-4bd9-9d2e-276da66b4f1c
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=8319981e-03bb-4bd9-9d2e-276da66b4f1c ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		8319981e-03bb-4bd9-9d2e-276da66b4f1c
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

It looks like your GRUB didn't update during the upgrade.

---

### Post by lindsay7 on 2009-05-27
I helped another person with this this weekend. This is what I told him to do. I am almost certain that you need to map you drives, but I am not sure as Presence 1960 pointed out that you may need to fix the uuid in place of the hd1,0 reference in you grub menu. I would add the map lines to your grub menu first and see if that fixes the problem. You can also try the sudo grub commands and see if that fixes the uuid/hd1,0 issue. Doing so may mess up your mbr so the lilo commands will fix that. If that still does not fix you problem you may need to go into the grub menu and replace the 

(root    (hd1,0)) line with (uuid  3b643562-bb75-4f72-996b-e06fa2d5222c) so that each entry for Ubuntu looks like this

title		Ubuntu 9.04, kernel 2.6.28-12-generic
uuid            3b643562-bb75-4f72-996b-e06fa2d5222c
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=3b643562-bb75-4f72-996b-e06fa2d5222c ro quiet splash vga=795 
initrd		/boot/initrd.img-2.6.28-12-generic
quiet


To edit the grub menu, type sudo gedit /boot/grub/menu.lst in the terminal. that is the letter l not the number 1 in menu.lst

 



You need to map the drive in the grub menu it should look like this.

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Professional
rootnoverify (hd0,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1


Do this and see it that fixes things. We may need to fix you grub menu too and or the windows mbr. Let me know.

To get in you grub menu type "sudo gedit /boot/grub/menu.lst"
add the lines I gave you and save the file. Do not change anything else.


In case Ubuntu does not start do this, type in the terminal

Sudo grub
find /boot/grub/stage1
(it will give a (hdx,y)
root (hdx,y)
setup(hd0)
quit

---

### Post by MedellinManDem on 2009-05-27
> **lindsay7 said:**
> I helped another person with this this weekend. This is what I told him to do. I am almost certain that you need to map you drives, but I am not sure as Presence 1960 pointed out that you may need to fix the uuid in place of the hd1,0 reference in you grub menu. **I would add the map lines to your grub menu first and see if that fixes the problem.** You can also try the sudo grub commands and see if that fixes the uuid/hd1,0 issue. Doing so may mess up your mbr so the lilo commands will fix that. If that still does not fix you problem you may need to go into the grub menu and replace the 


Sorry to be obtuse, but is that a simple matter of:

map (hdx,y)
map (hdy,x)

??

Thanks so much for your help so far...I'm at work at the moment so I can't try it out...

---

### Post by lindsay7 on 2009-05-27
Yup, that could be all there is to the problem. I gave you the other info just in case you need more help.  You need to map these drives regardless of any other problems that you may have so start with this and go from there. The newer versions of Ubuntu use th uuid designation for drive partitions so I do not know if what you have is ok or not therefore, the info for editing the uuid vs. hd(x,y) stuff.

Be sure to put a space between the two brackets (hd0) and (hd1) in 


map (hd0) (hd1)
map (hd1) (hd0)

Without the mapping your drive does not know how to work between the two OS's on the two drives at start up.

---

### Post by MedellinManDem on 2009-05-27
> **lindsay7 said:**
> 

To get in you grub menu type "sudo gedit /boot/grub/menu.lst"


When I type in this, it gives me a blank document cos I'm using the Live CD/. What do I do?
 
I edited it by typing "Sudo Nautilus" and finding the HDD with Ubuntu on it, but it did nothing different except that the Windows partition just said "Starting up..." and didn't move.

---

### Post by lindsay7 on 2009-05-27
See if this will do the trick.



[http://www.daniweb.com/blogs/entry708.html#](http://www.daniweb.com/blogs/entry708.html#)


Here is some more info

[http://ubuntuforums.org/archive/index.php/t-784742.html](http://ubuntuforums.org/archive/index.php/t-784742.html)

Let me know how it goes.

---

### Post by lindsay7 on 2009-05-27
I did some more looking on how to mount and edit the grub file with the live cd and tried it myself. This is what you need to do.

If you open /boot/grub/menu.lst while using a Live CD, and depending on the Live CD you are using, that file either won't exist or it will be the menu.lst for the Live CD, not your Ubuntu on your HDD. Are you sure you edited the menu.lst in your Ubuntu install? How about doing:
Code:
sudo fdisk -l
And find which is your Ubuntu partition in the form sdaX (like sda5 for example), and then do:
Code:
sudo mount /dev/sdaX /mnt
gksudo gedit /mnt/boot/grub/menu.lst
But replace sdaX with the Ubuntu partition. Then you should get your Ubuntu menu.lst. How about giving that a shot and let me know how it goes.


I know that you Ubuntu installation is on sdb so in the terminal you type

sudo mount /dev/sdb1 /mnt
gksudo gedit /mnt/boot/grub/menu.lst

You can edit you grub menu and save and exit.

---

### Post by presence1960 on 2009-05-27
or you can open a terminal and run > gksu nautiluswhich will open nautilus with root priveledge. In the left pane highlight the partition Ubuntu is on and then in the right file browser navigate to your /boot/grub/menu.lst file. Double click to open it and do your editing. Click save and then close. then restart and see if it works.

---

### Post by MedellinManDem on 2009-05-27
> **lindsay7 said:**
> See if this will do the trick.



[http://www.daniweb.com/blogs/entry708.html#](http://www.daniweb.com/blogs/entry708.html#)


Here is some more info

[http://ubuntuforums.org/archive/index.php/t-784742.html](http://ubuntuforums.org/archive/index.php/t-784742.html)

Let me know how it goes.

No luck with the first link, and the second link doesn't really tell me much.

I need to take it back to square one...

---

### Post by MedellinManDem on 2009-05-27
> **presence1960 said:**
> or you can open a terminal and run which will open nautilus with root priveledge. In the left pane highlight the partition Ubuntu is on and then in the right file browser navigate to your /boot/grub/menu.lst file. Double click to open it and do your editing. Click save and then close. then restart and see if it works.

This is what I did...and it didn't work.

I put the map lines in as was suggested and nothing.

Lindsay: I can mount my drives simply by clicking "Places > 186.1gb media" 

When I type the sudo mount command it actually stops me from seeing the drive in "Places"...weird.

---

### Post by MedellinManDem on 2009-05-27
> **lindsay7 said:**
> I did some more looking on how to mount and edit the grub file with the live cd and tried it myself. This is what you need to do.

If you open /boot/grub/menu.lst while using a Live CD, and depending on the Live CD you are using, that file either won't exist or it will be the menu.lst for the Live CD, not your Ubuntu on your HDD. Are you sure you edited the menu.lst in your Ubuntu install? How about doing:
Code:
sudo fdisk -l
And find which is your Ubuntu partition in the form sdaX (like sda5 for example), and then do:
Code:
sudo mount /dev/sdaX /mnt
gksudo gedit /mnt/boot/grub/menu.lst
But replace sdaX with the Ubuntu partition. Then you should get your Ubuntu menu.lst. How about giving that a shot and let me know how it goes.


I know that you Ubuntu installation is on sdb so in the terminal you type

sudo mount /dev/sdb1 /mnt
gksudo gedit /mnt/boot/grub/menu.lst

You can edit you grub menu and save and exit.

I am gonna try this step by step now.

EDIT: Got the menu.lst open...this is exactly how it looks now:

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
# kopt=root=UUID=3b643562-bb75-4f72-996b-e06fa2d5222c ro

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
# defoptions=quiet splash vga=795

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

title		Ubuntu 9.04, kernel 2.6.28-12-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=3b643562-bb75-4f72-996b-e06fa2d5222c ro quiet splash vga=795 
initrd		/boot/initrd.img-2.6.28-12-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-12-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=3b643562-bb75-4f72-996b-e06fa2d5222c ro  single
initrd		/boot/initrd.img-2.6.28-12-generic

title		Ubuntu 9.04, memtest86+
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
rootnoverify	(hd0,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader	+1

```

And still nothing.

---

### Post by lindsay7 on 2009-05-27
Well, it maybe that the problem goes back to the uuid and root designation in the grub menu. You can try what was in an earlier reply and see if that works.

> If that still does not fix you problem you may need to go into the grub menu and replace the

(root (hd1,0)) line with (uuid 3b643562-bb75-4f72-996b-e06fa2d5222c) so that each entry for Ubuntu looks like this

title Ubuntu 9.04, kernel 2.6.28-12-generic
uuid 3b643562-bb75-4f72-996b-e06fa2d5222c
kernel /boot/vmlinuz-2.6.28-12-generic root=UUID=3b643562-bb75-4f72-996b-e06fa2d5222c ro quiet splash vga=795
initrd /boot/initrd.img-2.6.28-12-generic
quiet


To edit the grub menu, type sudo gedit /boot/grub/menu.lst in the terminal. that is the letter l not the number 1 in menu.lst



---

### Post by MedellinManDem on 2009-05-28
> **lindsay7 said:**
> Well, it maybe that the problem goes back to the uuid and root designation in the grub menu. You can try what was in an earlier reply and see if that works.

Nope, still nothing.

---

### Post by MedellinManDem on 2009-05-29
Bump

---

### Post by MedellinManDem on 2009-05-31
Update:

I can now get into the 9.04 install thanks to me downloading SuperGrubDisk...but it still gives me Error 22 without that disk. I just need to figure out how to do that, so I can get my dual boot GRUB back and working again.

---

