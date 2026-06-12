---
title: "Vista no longer loading"
date: 2009-01-07
forum: Installation &amp; Upgrades
---

### Post by Sikul on 2009-01-07
When I select my Windows Vista option in grub it goes to a screen and says "Grub Loading Stage2..." and then it goes back to grub boot options.

Here's the output for sudo fdisk -l:
```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5424a154

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1925    15462531    7  HPFS/NTFS
/dev/sda2   *        1926       31246   235520000    7  HPFS/NTFS
/dev/sda3           31246       33678    19535040   83  Linux
/dev/sda4           33678       38913    42050208+   5  Extended
/dev/sda5           33678       33927     2000061   82  Linux swap / Solaris
/dev/sda6           33927       38913    40050084+  83  Linux

```

Here's my settings for Windows Vista in /boot/grub/menu.lst:
```

title Windows Vista
rootnoverify (hd0,1)
makeactive
chainloader +1

```

---

### Post by ajmorris on 2009-01-07
hi there, 
you have 2 windows partitions... im assuming the other is XP? or is it just an ntfs partition with no OS? does it boot fine? -- GRUB used to have some issues with vista... although i thought they had been rectified... If the other partition is another windows OS, you could add vista to it's boot loader, then upon choosing it, you would have the option to choose vista in that windows boot loader... alternatively, if, or if not the other partition is another windows OS, you could try a boot manager, such as Acronis...


AJ

---

### Post by Noel96 on 2009-01-07
This little program will probably fix your dual booting problem. Download the CD ROM ISO (version 0.9974) is the latest. It's called Supergrub and it's a boot recovery program. 

Once you have d'loaded the ISO, burn the image to CD and boot your computer up from the CD. Menus will then guide you.

I find SuperGrub is a great tool to have on hand to help fix problems. It doesn't always work, but mostly it does.

[http://www.supergrubdisk.org/index.php?pid=5](http://www.supergrubdisk.org/index.php?pid=5)

---

### Post by lakersforce on 2009-01-07
> **Sikul said:**
> 
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1925    15462531    7  HPFS/NTFS
/dev/sda2   *        1926       31246   235520000    7  HPFS/NTFS


```

```

title Windows Vista
rootnoverify (hd0,1)
makeactive
chainloader +1

```

From the looks of it, your Vista partion might be on sda1.

Try changing (hd0,1) to (hd0,0) and boot. If it does not work change sda1 to bootable in your favorite partition manager.

---

### Post by caljohnsmith on 2009-01-07
If booting Vista causes you to loop back to the Grub menu, sometimes that's a case of accidentally having Grub installed to the boot sector of your Vista partition. In order to see if that is the problem, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your Vista booting problem might be.

---

### Post by Sikul on 2009-01-07
> **caljohnsmith said:**
> If booting Vista causes you to loop back to the Grub menu, sometimes that's a case of accidentally having Grub installed to the boot sector of your Vista partition.

I'm pretty sure this is what happened.  Here's the output of the script you had me run:
```
============================= Boot Info Summary: ==============================

 => Drive sdb does not have a valid partition table.
 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /BOOTMGR /Boot

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of /dev/sda2 
                       and looks at sector 533473416 of the same hard drive 
                       for the stage2 file and on partition #3 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: you must specify the filesystem type

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  [H[2J Arch Linux () ()
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda4: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       swap

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5424a154

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    30925124    15462531    7  HPFS/NTFS
/dev/sda2   *    30926848   501966847   235520000    7  HPFS/NTFS
/dev/sda3       501966848   541036927    19535040   83  Linux
/dev/sda4       541036928   625137344    42050208+   5  Extended
/dev/sda5       541036991   545037112     2000061   82  Linux swap / Solaris
/dev/sda6       545037176   625137344    40050084+  83  Linux

sfdisk -V /dev/sda:

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: partition 2 does not start at a cylinder boundary

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

sfdisk -V /dev/sdb:

/dev/sdb: No medium found

sfdisk: cannot open /dev/sdb for reading

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="50CC1B45CC1B24AE" LABEL="Recovery" TYPE="ntfs" 
/dev/sda3: UUID="a4b5938a-186f-467c-a3e0-665407cc4bc0" TYPE="ext3" 
/dev/sda5: UUID="983894ee-d54b-4c19-9d08-0a6e6180881f" TYPE="swap" 
/dev/sda6: UUID="68e67ea1-af5c-4ebf-953b-a9b674748200" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda3 on / type ext3 (rw)
none on /dev type ramfs (rw)
none on /proc type proc (rw)
none on /sys type sysfs (rw)
none on /dev/pts type devpts (rw)
none on /dev/shm type tmpfs (rw)
/dev/sda6 on /home type ext3 (rw)

================================== sda1/Boot: ==================================

total 4120
dr-x------ 1 root root    4096 2008-03-21 22:31 .
dr-x------ 1 root root    8192 2009-01-06 13:51 ..
-r-------- 1 root root    8121 2003-06-12 07:52 Folder.htt
-r-------- 1 root root      53 2004-04-30 04:01 autorun.inf
-r-------- 1 root root  262144 2009-01-07 03:20 bcd
-r-------- 1 root root  262144 2009-01-07 03:20 bcd.LOG
-r-------- 1 root root 3170304 2006-07-26 01:46 boot.sdi
-r-------- 1 root root    1024 2006-07-26 22:34 bootfix.bin
-r-------- 1 root root     102 2003-10-04 03:06 desktop.ini
-r-------- 1 root root    2048 2006-07-26 22:34 etfsboot.com
dr-x------ 1 root root       0 2008-03-21 22:29 fonts
-r-------- 1 root root   73728 2004-11-30 01:01 info.exe
-r-------- 1 root root  319545 2003-06-12 06:41 protect.ed
-r-------- 1 root root   96774 2003-06-12 07:43 warning.bmp

=========================== sda3/boot/grub/menu.lst: ===========================

# Config file for GRUB - The GNU GRand Unified Bootloader
# /boot/grub/menu.lst

# DEVICE NAME CONVERSIONS 
#
#  Linux           Grub
# -------------------------
#  /dev/fd0        (fd0)
#  /dev/hda        (hd0)
#  /dev/hdb2       (hd1,1)
#  /dev/hda3       (hd0,2)
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

# general configuration:
timeout   15
default   0
color light-blue/black light-cyan/blue

# boot sections follow
# each is implicitly numbered from 0 in the order of appearance below
#
# TIP: If you want a 1024x768 framebuffer, add "vga=773" to your kernel line.
#
#-*

# (0) Windows Vista
title Windows Vista
rootnoverify (hd0,1)
makeactive
chainloader +1


# (1) Arch Linux
title  Arch Linux
root   (hd0,2)
kernel /boot/vmlinuz26 root=/dev/disk/by-uuid/a4b5938a-186f-467c-a3e0-665407cc4bc0 ro
initrd /boot/kernel26.img

# (2) Arch Linux
title  Arch Linux Fallback
root   (hd0,2)
kernel /boot/vmlinuz26 root=/dev/disk/by-uuid/a4b5938a-186f-467c-a3e0-665407cc4bc0 ro
initrd /boot/kernel26-fallback.img

# (1) Windows
#title Windows
#rootnoverify (hd0,0)
#makeactive
#chainloader +1

=============================== sda3/etc/fstab: ===============================

# 
# /etc/fstab: static file system information
#
# <file system>        <dir>         <type>    <options>          <dump> <pass>
none                   /dev/pts      devpts    defaults            0      0
none                   /dev/shm      tmpfs     defaults            0      0


/dev/cdrom /media/cdrom   auto    ro,user,noauto,unhide   0      0
/dev/dvd /media/dvd   auto    ro,user,noauto,unhide   0      0
UUID=68e67ea1-af5c-4ebf-953b-a9b674748200 /home ext3 defaults 0 1
UUID=983894ee-d54b-4c19-9d08-0a6e6180881f swap swap defaults 0 0
UUID=a4b5938a-186f-467c-a3e0-665407cc4bc0 / ext3 defaults 0 1

================================== sda3/boot: ==================================

total 7664
drwxr-xr-x  3 root root    4096 2009-01-06 22:21 .
drwxr-xr-x 20 root root    4096 2009-01-06 22:22 ..
-rw-r--r--  1 root root  773329 2008-12-21 04:34 System.map26
-rw-r--r--  1 root root    5040 2007-11-15 14:59 diag1.img
drwxr-xr-x  2 root root    4096 2009-01-07 01:41 grub
-rw-r--r--  1 root root 4766951 2009-01-06 22:22 kernel26-fallback.img
-rw-r--r--  1 root root  568088 2009-01-06 22:21 kernel26.img
-rw-r--r--  1 root root 1688368 2008-12-21 04:34 vmlinuz26

=============================== sda3/boot/grub: ===============================

total 320
drwxr-xr-x 2 root root   4096 2009-01-07 01:41 .
drwxr-xr-x 3 root root   4096 2009-01-06 22:21 ..
-rw-r--r-- 1 root root   8024 2008-03-18 06:15 e2fs_stage1_5
-rw-r--r-- 1 root root   7864 2008-03-18 06:15 fat_stage1_5
-rw-r--r-- 1 root root   7112 2008-03-18 06:15 ffs_stage1_5
-rw-r--r-- 1 root root   7108 2008-03-18 06:15 iso9660_stage1_5
-rw-r--r-- 1 root root   8576 2008-03-18 06:15 jfs_stage1_5
-rw-r--r-- 1 root root   1544 2009-01-07 00:30 menu.lst
-rw-r--r-- 1 root root   1355 2008-12-28 14:26 menu.lst.pacnew
-rw-r--r-- 1 root root   7296 2008-03-18 06:15 minix_stage1_5
-rw-r--r-- 1 root root   9604 2008-03-18 06:15 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-03-18 06:15 stage1
-rw-r--r-- 1 root root 100390 2008-03-18 06:15 stage2
-rw-r--r-- 1 root root 100390 2008-03-18 06:15 stage2_eltorito
-rw-r--r-- 1 root root   7452 2008-03-18 06:15 ufs2_stage1_5
-rw-r--r-- 1 root root   6680 2008-03-18 06:15 vstafs_stage1_5
-rw-r--r-- 1 root root   9264 2008-03-18 06:15 xfs_stage1_5

=============================== StdErr Messages: ===============================

/dev/sdb: No medium found

sfdisk: cannot open /dev/sdb for reading
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
```

I should note that I setup the partitions myself and took care of grub myself.  I'm pretty sure I installed it to the Vista partition as you said.

Also I guess I should note this isn't Ubuntu, but I'm pretty sure it's a linux-wide issue.

---

### Post by caljohnsmith on 2009-01-07
[QUOTE=Sikul]```
sda2: _________________________________________________________________________

    File system:       
    [COLOR="Red"]Boot sector type:  Grub[/COLOR]
    Boot sector info:  Grub0.97 is installed in the boot sector of /dev/sda2 
                       and looks at sector 533473416 of the same hard drive 
                       for the stage2 file and on partition #3 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: you must specify the filesystem type

```[/QUOTE]
As you can see from the script output above, unfortunately it does look like you accidentally installed Grub to your Vista boot sector, which will make Vista unbootable and also the partition will be unmountable. Do you have your Vista Install CD? If so, how about booting that, go to the command line (recovery console) and do:
```
bootrec /fixboot
```
And that should fix your Vista's boot sector. If you don't have a Vista Install CD, you can instead download and use a Vista Recovery CD from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"). Good luck and let me know how it goes.

---

### Post by Sikul on 2009-01-07
> **caljohnsmith said:**
> f so, how about booting that, go to the command line (recovery console) and do:
```
bootrec /fixboot
```
And that should fix your Vista's boot sector.

I have a vista install dvd, but when I run it I can't get to the part that allows me to click on "open command prompt" button.  Is there a key sequence I can hit while I'm repairing that will let me bring up a command prompt at any time?

Edit:  Some quick googling looks like it might be Windows Key+R.  Going to go try that out.

---

### Post by Sikul on 2009-01-07
It worked!  Thanks a ton caljohnsmith and the rest of you, also.  You guys are the best.  I learned a lot during this experience :D

---

### Post by caljohnsmith on 2009-01-07
Glad that did the trick and Vista is booting again; cheers and have fun with your OSes. :)

---

### Post by RJARRRPCGP on 2009-01-07
> **ajmorris said:**
> hi there, 


LOL @ your avatar!

---

### Post by DrGNU on 2009-05-13
> **Sikul said:**
> I have a vista install dvd, but when I run it I can't get to the part that allows me to click on "open command prompt" button.  Is there a key sequence I can hit while I'm repairing that will let me bring up a command prompt at any time?

Edit:  Some quick googling looks like it might be Windows Key+R.  Going to go try that out.

Did the "Windows Key+R" work to get to the command prompt?
I think I'll need to follow caljohnsmith's excellent instructions in this link to help diagnose and potentially fix our issues.

Kudos to caljohnsmith for the script for posting the diagnostics!
Will give that a try.

I'm trying to guide my parents in fixing their system in order to retrieve files in a Vista partition that will not mount.  
The situation and current status is described here:

[http://ubuntuforums.org/showthread.php?p=7252450](http://ubuntuforums.org/showthread.php?p=7252450)

Thanks,

DrGNU (Steve)

---

### Post by madestro on 2009-05-14
I have a similar problem in this post [http://ubuntuforums.org/showthread.php?p=7278598#post7278598]("http://ubuntuforums.org/showthread.php?p=7278598#post7278598") and after I followed caljohnsmiths's advice the script gave me this output

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc1d800be

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   416,758,229   416,758,167   7 HPFS/NTFS
/dev/sda3         416,758,230 1,166,078,024   749,319,795   f W95 Ext d (LBA)
/dev/sda5         416,758,293   826,833,419   410,075,127   7 HPFS/NTFS
/dev/sda6         918,644,958 1,166,078,024   247,433,067   7 HPFS/NTFS
/dev/sda7         826,833,483   918,644,894    91,811,412  83 Linux
/dev/sda4       1,250,001,585 1,250,258,624       257,040  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="54CE2DE1CE2DBBDC" TYPE="ntfs" 
/dev/sda4: UUID="c42d18f7-898f-4f6a-8e59-24bb01d879cf" TYPE="swap" 
/dev/sda5: UUID="01C9AB49D652E950" LABEL="Downloads" TYPE="ntfs" 
/dev/sda6: UUID="01C9AB49D73C37E0" LABEL="Multimedia" TYPE="ntfs" 
/dev/sda7: UUID="4dfd024f-341e-4e71-ab5b-c5a9d56ad761" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda7 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jsn/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jsn)
/dev/sr0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=jsn)
/dev/sda1 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5 on /media/Downloads type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

=========================== sda7/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=4dfd024f-341e-4e71-ab5b-c5a9d56ad761 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=4dfd024f-341e-4e71-ab5b-c5a9d56ad761

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
```

I did use my Vista DVD to try to restore the mbr and now I can get as far as the little loading screen from Vista but after a few seconds the PC reboots, I'm assuming there has to be something corrupted IN the vista filesystem itself and that is why I can go no further. Is there any way to repair the Vista filesystem from a working Ubuntu partition on the same HD ?

---

