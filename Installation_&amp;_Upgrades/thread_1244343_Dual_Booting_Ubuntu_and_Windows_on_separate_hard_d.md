---
title: "Dual Booting Ubuntu and Windows on separate hard drives"
date: 2009-08-19
forum: Installation &amp; Upgrades
---

### Post by martini1179 on 2009-08-19
I'm a relative Linux noob. 

Restating the subject, I want to dual boot Ubuntu and Vista (for the games), and I'd like to place each OS *on its own hard drive* instead of just putting them on seperate partitions. I've already installed Ubuntu on one of the drives, and as soon as I wipe the other, I plan on installing Vista. 

Since they will be on separate drives, will I have any conflicts with the Linux/Windows bootloaders after I re-setup GRUB after installing Windows?

---

### Post by Bucky Ball on 2009-08-19
If you haven't done much on Ubuntu yet, you might want to install Vista first and then let Ubuntu pick it up when it installs second. It is a darn sight easier. The grub will probably setup automatically that way. Installing Windows second you will probably need to set the grub menu up manually and map the drive/partition that Vista is on (as the drive Ubuntu is on is probably the first one).

Something to remember: Windows (any flavour) must be on a Primary Partition (Ubuntu doesn't care) on the FIRST drive to be co-operative. When you install Vista it will probably attempt to change the drive order from what you have at the moment so keep your eyes open and take note of what is where before you start. Quick translation. Ubuntu uses sd? and windows hd?, as in:

hd**0 **= sd**a** = first hard drive. Windows consider zero (0) to be one and starts counting from zero. Ubuntu starts from one (1).

0 = 1, a = 1 so first hard drive. With that in mind:

For Windows, (hd0,0) = first drive, first partition = sda1 for Ubuntu (sd**a**=first drive, sda**1**=first partition).

Hope that makes sense and helps a bit. You will probably need to map the drive and will need some understanding of these concepts to do it. :)

---

### Post by presence1960 on 2009-08-19
when you install vista boot into BIOS and switch the Vista disk to first in the order of hard disk booting. You will have no problems this way with Vista overwriting GRUB on the other disk, GRUB will be safe. if you fail to switch the boot order of the disks Vista will attempt to write it's bootloader to the disk that is first boot in BIOS.

When completed Vista install reboot and insure Vista boots. Then reboot again and change the Ubuntu disk to first boot in BIOS so the GRUB menu comes up at boot. You may have to edit your menu.lst to get Vista on there as an option to boot but that is a simple matter. if you don't know how to do that post back after the install.

P.S. windows does not need to be on the first primary partition, it just needs to be on a primary partition. mine is on sda4. Here's my fdisk output:
> 
raz@raz-desktop:~$ sudo fdisk -l
[sudo] password for raz: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000d179

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5222    41945683+   5  Extended
/dev/sda2            5223       19843   117443182+  83  Linux
/dev/sda3           19844       25064    41937682+   7  HPFS/NTFS
/dev/sda4           25065       30401    42869452+   7  HPFS/NTFS
/dev/sda5               1        2350    18876312   83  Linux
/dev/sda6            2351        2872     4192933+  82  Linux swap / Solaris
/dev/sda7            2873        5222    18876343+  83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa7a57e45

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       16193   130070241   83  Linux
/dev/sdb2           16194       19457    26218080   83  Linux
raz@raz-desktop:~$ 

sda1 is extended
sda5 is Ubuntu 9.04 logical
sda7 is Mint 5 logical
sda6 is swap logical
sda2 is ext 3 data partition  primary
sda3 is NTFS data partition   primary
sda4 is windows 7 RC  primary
sdb1 is ext 3 data partition  primary
sdb2 is sabayon 4.1  primary

as you can see windows is on the last primary partition of disk sda.

You already have Ubuntu installed so there is no need to remove Ubuntu only to reinstall it again. You can install windows after linux.

---

### Post by martini1179 on 2009-08-20
I appreciate the quick replies to my question. So guys, generally speaking, Windows needs to be installed on a primary partition, and primary partition = "first" hard drive? 

And since I only have one drive physically installed, logically it will be the primary partition. 

So it seems to me that all I would have to do is to install the second drive but set it up to be the primary partition and afterwords just reassert GRUB's authoritah over the boot process? Is that possible?  

How is it done? Just through the BIOS? Through position on the SATA cable? 

We're talking about two SATA drives here.

---

### Post by martini1179 on 2009-08-20
> **presence1960 said:**
> You already have Ubuntu installed so there is no need to remove Ubuntu only to reinstall it again. You can install windows after linux.

Presence1960, could you clarify what you mean by this, as it is confusing to me. I'm taking it as "you already have Ubuntu installed so there is no need to remove Ubuntu only to reinstall UBUNTU again." Except that makes little sense to me and doesn't jive with everything else in your post.

---

### Post by cascade9 on 2009-08-20
martini1179- there are 2 types of partitions, "primary partitions" and "extended partition". An "extended" partition can then be cut up into "logical drives". Windows really needs a primary partition, while linux runs fine from primary partitions or logical drives. 

A primary partition is just a partition type, and is not tied to any particular hdd in your system (any hdd can have primary partitions and logical drives)

More info-
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)

 What presence1960 meant by "you already have Ubuntu installed so there is no need to remove Ubuntu only to reinstall UBUNTU again." is just that. You dont have to reinstall ubuntu, even if GRUB was overwritten by windows. 

To put what he was saying a different way-

Install your 2nd hdd. (or format it, whatever you need to do) 
Go to BIOS. 
Make the just installed hdd (vista drive) boot 1st.
Install vista.
Make sure vista works. 
Reboot, go back to BIOS.
Make the Ubuntu Hdd boot 1st.
Edit your menu.lst to get Vista into GRUB

You may find this handy guide helpfull-
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by presence1960 on 2009-08-20
> **martini1179 said:**
> Presence1960, could you clarify what you mean by this, as it is confusing to me. I'm taking it as "you already have Ubuntu installed so there is no need to remove Ubuntu only to reinstall UBUNTU again." Except that makes little sense to me and doesn't jive with everything else in your post.

 > Dual Booting Ubuntu and Windows on separate hard drives
I'm a relative Linux noob.

Restating the subject, I want to dual boot Ubuntu and Vista (for the games), and I'd like to place each OS on its own hard drive instead of just putting them on seperate partitions. I've already installed Ubuntu on one of the drives, and as soon as I wipe the other, I plan on installing Vista.

Since they will be on separate drives, will I have any conflicts with the Linux/Windows bootloaders after I re-setup GRUB after installing Windows?this quote is from from your original post

you said you already have ubuntu installed. BuckyBall suggested you install windows first, which means you would have to remove Ubuntu. it is not necessary to remove Ubuntu to install windows. It is even easier since you have 2 separate hard disks and plan on installing each OS on a separate disk. I would like to bring to your attention that original post did not specify that the second disk was not in your machine. Please be very specific when asking for help as we only know what you tell us.

---

### Post by presence1960 on 2009-08-20
> **cascade9 said:**
> martini1179- there are 2 types of partitions, "primary partitions" and "extended partition". An "extended" partition can then be cut up into "logical drives". Windows really needs a primary partition, while linux runs fine from primary partitions or logical drives. 

A primary partition is just a partition type, and is not tied to any particular hdd in your system (any hdd can have primary partitions and logical drives)

more info-
[http://en.wikipedia.org/wiki/disk_partitioning](http://en.wikipedia.org/wiki/disk_partitioning)

 what presence1960 meant by "you already have ubuntu installed so there is no need to remove ubuntu only to reinstall ubuntu again." is just that. You dont have to reinstall ubuntu, even grub was overwritten by windows. 

To put what he was saying a different way-

install your 2nd hdd. (or format it, whatever you need to do) 
go to bios. 
Make the just installed hdd (vista drive) boot 1st.
Install vista.
Make sure vista works. 
Reboot, go back to bios.
Make the ubuntu hdd boot 1st.
Edit your menu.lst to get vista into grub

you may find this handy guide helpfull-
[https://help.ubuntu.com/community/windowsdualboot](https://help.ubuntu.com/community/windowsdualboot)

+1

---

### Post by martini1179 on 2009-08-25
> **presence1960 said:**
> this quote is from from your original post

you said you already have ubuntu installed. BuckyBall suggested you install windows first, which means you would have to remove Ubuntu. it is not necessary to remove Ubuntu to install windows. It is even easier since you have 2 separate hard disks and plan on installing each OS on a separate disk. I would like to bring to your attention that original post did not specify that the second disk was not in your machine. Please be very specific when asking for help as we only know what you tell us.


Sorry about that. I'm usually guilty of giving too much non-relevant information so I try to get down to the "meat" of the issue. 

Yeah, I have two drives, one of which is not in the system currently. I should also mention that the drives are an identical make/model. Will this pose a problem if I want to keep my Ubuntu install? I've never fiddled with the partition settings in the Windows installer, so I hope it will be courteous enough to inform me whether or not the selected partition on one of the twin drives is EXT3 so I can tell them apart.

---

### Post by gwoodruff on 2009-08-25
The drives being the same will not make a difference. I would disconnect the drive with Ubuntu when you install the vista drive and OS. Then connect Ubuntu and update grub to boot Vista also.

---

### Post by Mark Phelps on 2009-08-25
> **gwoodruff said:**
> the drives being the same will not make a difference. I would disconnect the drive with ubuntu when you install the vista drive and os. Then connect ubuntu and update grub to boot vista also.

+1

---

### Post by Bucky Ball on 2009-08-26
> **martini1179 said:**
>  I've never fiddled with the partition settings in the Windows installer, so I hope it will be courteous enough to inform me whether or not the selected partition on one of the twin drives is EXT3 so I can tell them apart.

It most definitely will not. It will label them 'unknown' from memory. As suggested, you are better off unplugging the Ubuntu drive then setting up grub later.

---

### Post by dgladst on 2009-09-05
[B]I have a similar problem.

After loading Ubuntu I cannot access my Windows environment and therefore all my applications.  
[/B] 			  			  			 		 		  		  		My machine has two internal Hard Disc Drives identified by Ubuntu (v9.04) as SDA & SDB and Windows is on SDA. I installed Ububtu on the SDB drive in order to try it out. 
 
 The bios is set to attempt firstly to boot from SDA which has Windows. However the machine boots up in Ubuntu. If I interrupt the machine boot although it displays me a choice of operating system I am unable to select any of the options.
 
 If the SDB drive (the one with Ubuntu) is removed the machine stops thru' the boot sequence showing the message:
 [I]Grub loading please wait
error 21 [/I]
 (My www searches suggest that this is because the Master Boot Record on the SDA drive points to Ubuntu). 
 
 How please can I "adjust" my system so that I can use Windows?
 
 Thanks
 Dave

---

### Post by presence1960 on 2009-09-05
> **dgladst said:**
> [B]I have a similar problem.

After loading Ubuntu I cannot access my Windows environment and therefore all my applications.  
[/B] 			  			  			 		 		  		  		My machine has two internal Hard Disc Drives identified by Ubuntu (v9.04) as SDA & SDB and Windows is on SDA. I installed Ububtu on the SDB drive in order to try it out. 
 
 The bios is set to attempt firstly to boot from SDA which has Windows. However the machine boots up in Ubuntu. If I interrupt the machine boot although it displays me a choice of operating system I am unable to select any of the options.
 
 If the SDB drive (the one with Ubuntu) is removed the machine stops thru' the boot sequence showing the message:
 [I]Grub loading please wait
error 21 [/I]
 (My www searches suggest that this is because the Master Boot Record on the SDA drive points to Ubuntu). 
 
 How please can I "adjust" my system so that I can use Windows?
 
 Thanks
 Dave

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by dgladst on 2009-09-05
Here we are "presence1960".      Dave

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe141e141

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   380,467,394   380,467,332   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x89a85e00

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   230,275,709   230,275,647  83 Linux
/dev/sdb2         230,275,710   240,107,489     9,831,780   5 Extended
/dev/sdb5         230,275,773   240,107,489     9,831,717  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="E0D04944D0492260" LABEL="TFM27T8" TYPE="ntfs" 
/dev/sdb1: UUID="d71ce4ae-7a87-4931-b0a1-d0c26a538c98" TYPE="ext3" 
/dev/sdb5: UUID="63c52f62-752f-4384-968a-01f754ee787d" TYPE="swap" 

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
/dev/sdb1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sda1 on /media/TFM27T8 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=d71ce4ae-7a87-4931-b0a1-d0c26a538c98 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d71ce4ae-7a87-4931-b0a1-d0c26a538c98

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        d71ce4ae-7a87-4931-b0a1-d0c26a538c98
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=d71ce4ae-7a87-4931-b0a1-d0c26a538c98 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        d71ce4ae-7a87-4931-b0a1-d0c26a538c98
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=d71ce4ae-7a87-4931-b0a1-d0c26a538c98 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        d71ce4ae-7a87-4931-b0a1-d0c26a538c98
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=d71ce4ae-7a87-4931-b0a1-d0c26a538c98 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=63c52f62-752f-4384-968a-01f754ee787d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  71.1GB: boot/grub/menu.lst
  71.1GB: boot/grub/stage2
  71.1GB: boot/initrd.img-2.6.28-11-generic
  71.2GB: boot/vmlinuz-2.6.28-11-generic
  71.1GB: initrd.img
  71.2GB: vmlinuz
```

---

### Post by presence1960 on 2009-09-05
> **dgladst said:**
> Here we are "presence1960".      Dave

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe141e141

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   380,467,394   380,467,332   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x89a85e00

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   230,275,709   230,275,647  83 Linux
/dev/sdb2         230,275,710   240,107,489     9,831,780   5 Extended
/dev/sdb5         230,275,773   240,107,489     9,831,717  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="E0D04944D0492260" LABEL="TFM27T8" TYPE="ntfs" 
/dev/sdb1: UUID="d71ce4ae-7a87-4931-b0a1-d0c26a538c98" TYPE="ext3" 
/dev/sdb5: UUID="63c52f62-752f-4384-968a-01f754ee787d" TYPE="swap" 

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
/dev/sdb1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sda1 on /media/TFM27T8 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=d71ce4ae-7a87-4931-b0a1-d0c26a538c98 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d71ce4ae-7a87-4931-b0a1-d0c26a538c98

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        d71ce4ae-7a87-4931-b0a1-d0c26a538c98
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=d71ce4ae-7a87-4931-b0a1-d0c26a538c98 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        d71ce4ae-7a87-4931-b0a1-d0c26a538c98
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=d71ce4ae-7a87-4931-b0a1-d0c26a538c98 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        d71ce4ae-7a87-4931-b0a1-d0c26a538c98
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=d71ce4ae-7a87-4931-b0a1-d0c26a538c98 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=63c52f62-752f-4384-968a-01f754ee787d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  71.1GB: boot/grub/menu.lst
  71.1GB: boot/grub/stage2
  71.1GB: boot/initrd.img-2.6.28-11-generic
  71.2GB: boot/vmlinuz-2.6.28-11-generic
  71.1GB: initrd.img
  71.2GB: vmlinuz
```

OK, your boot info script output looks good. it would seem to me the problem of not being able to use your keyboard at the GRUB menu is the problem. Do you have a USB keyboard? If so you need to go into BIOS and look for a setting to enable USB keyboard support or Legacy USB support. Your GRUB menu options are all correct. So you need keyboard to work to choose options in the GRUB menu.

---

### Post by dgladst on 2009-09-05
:D :D:D:DAll I can say "presence1960" is that you are a complete and utter star. Thank you. :D:D:D:D
(Interestingly I selected the bios option to change by using the arrow keys!)
 
Dare I impose on you or anyone else further?
 
[FONT=Arial][SIZE=2]My problem is unfortunately not completely solved as [/SIZE][/FONT][FONT=Arial][SIZE=2]the second drive (the one with Ubuntu) is in a caddy and most of my data is on another drive which normally occupies that caddy.[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]So I need somehow to change the boot sequence so it goes into Windows without accessing that second drive.[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]Thanks,[/SIZE][/FONT]
[FONT=Arial][SIZE=2]Dave[/SIZE][/FONT]

---

### Post by presence1960 on 2009-09-05
> **dgladst said:**
> :D :D:D:DAll I can say "presence1960" is that you are a complete and utter star. Thank you. :D:D:D:D
(Interestingly I selected the bios option to change by using the arrow keys!)
 
Dare I impose on you or anyone else further?
 
[FONT=Arial][SIZE=2]My problem is unfortunately not completely solved as [/SIZE][/FONT][FONT=Arial][SIZE=2]the second drive (the one with Ubuntu) is in a caddy and most of my data is on another drive which normally occupies that caddy.[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]So I need somehow to change the boot sequence so it goes into Windows without accessing that second drive.[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]Thanks,[/SIZE][/FONT]
[FONT=Arial][SIZE=2]Dave[/SIZE][/FONT]

can't you choose windows from the GRUB menu and when windows boots switch the drive in the caddy? The other way of doing this involves switching the order of disks in BIOS depending on which OS you want to boot. That will also involve installing GRUB to MBR of the Ubuntu disk and restoring windows bootloader to the MBR of sda. It can work. personally I would not want to go into BIOS each time i wanted to boot a different OS. it makes more sense to boot windows from GRUB then switch the disk in the caddy once windows boots.

---

### Post by dgladst on 2009-09-05
I fully accept your point but unfortunately for the moment Windows is still my main working OS. Its going to take me a bit of time and a great deal of care before I migrate to Ubuntu. 
 
The Pc is used by several folk in the house and is therefore started up several times a 
day and not only is it a bit of a hassle but I'm also not sure, but don't know, that its a particularily good idea to change fixed drives whilst the PC is up and running
 
What's involved please and how difficult is it to "installing GRUB to MBR of the Ubuntu disk and restoring windows bootloader to the MBR of sda." ?
 
Many thanks,
 
Dave

---

### Post by presence1960 on 2009-09-05
> **dgladst said:**
> I fully accept your point but unfortunately for the moment Windows is still my main working OS. Its going to take me a bit of time and a great deal of care before I migrate to Ubuntu. 
 
The Pc is used by several folk in the house and is therefore started up several times a 
day and not only is it a bit of a hassle but I'm also not sure, but don't know, that its a particularily good idea to change fixed drives whilst the PC is up and running
 
What's involved please and how difficult is it to "installing GRUB to MBR of the Ubuntu disk and restoring windows bootloader to the MBR of sda." ?
 
Many thanks,
 
Dave

Ok boot from your Windows install disk and follow [this]("http://ubuntuforums.org/showthread.php?t=1014708") to restore windows bootloader to sda. When completed reboot and you should boot directly into windows.

next boot off the Ubuntu Live CD. Choose "try Ubuntu without any changes". When the desktop loads do this:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "grub"
5. Type "find /boot/grub/stage1". You'll get a response like "(hd1,0)". 
   Use whatever your computer spits out for the following lines.
6. Type "root (hd1,0)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
7. Type "setup (hd1)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
8. Quit grub by typing "quit".
9. Reboot and remove the bootable CD.

In #6 use setup (hd1)




```

This will put GRUB on the MBR of sdb(Ubuntu's disk). You already will have windows on MBR of sda, so when you boot you will go right into windows.

When you want to boot Ubuntu you will have to GO into BIOS and switch the Ubuntu disk (sdb) to first boot in the hard disk boot order to bring up GRUB.

Just remember after using Ubuntu to reboot and go back in BIOS and reset sda as first boot so the others can boot directly into Windows.

This should allow you to do what you want.

---

### Post by trinadhm on 2009-09-05
supposingly if we have two drives hd0 and hd1 , with ubuntu on hd0 and windows on hd1, grub is installed on hd0, cant we boot to windows by adding it to the menu.lst in grub as
 
title windows
root hd(1,0)
makeactive
chainloader +1
 
....

---

### Post by dgladst on 2009-09-05
Again a very big thank you again for sharing your expertise.
 
After further thought I have moved to the idea of moving all the data across to my external drive. Thus encouraging me to carry out some much needed housekeeping on the data. This would then enable me to migrate my applications hazzle free singly across to the Ubuntu environment.
 
However I shall keep your info for use should I idly postpone the data move.
 
Thank you very very much,
 
Dave

---

### Post by presence1960 on 2009-09-05
> **trinadhm said:**
> supposingly if we have two drives hd0 and hd1 , with ubuntu on hd0 and windows on hd1, grub is installed on hd0, cant we boot to windows by adding it to the menu.lst in grub as
 
title windows
root hd(1,0)
makeactive
chainloader +1
 
....

I think you need to read dgladst's posts to see his setup & how he wanted to use it.

---

### Post by trinadhm on 2009-09-06
it was more of a question than a reply to his post...., sry if i have asked at a wrong place..... :)

---

### Post by Bucky Ball on 2009-09-06
> **trinadhm said:**
> supposingly if we have two drives hd0 and hd1 , with ubuntu on hd0 and windows on hd1, grub is installed on hd0, cant we boot to windows by adding it to the menu.lst in grub as
 
title windows
root hd(1,0)
makeactive
chainloader +1
 
....

One would think so but Windows would probably require you to map the hard drive to (hd0,0) as I said in post #2!! Something like:

```
title windows
root hd(1,0)
map (hd1,0) (hd0,0)
map (hd0,0) (hd1,0)
makeactive
chainloader +1
```
 
... or something like that, from memory. Anyone feel free to jump in and correct it. Windows needs to think it is on first drive, first partition or you need to trick it.

---

### Post by trinadhm on 2009-09-06
Thank you.. :)

---

### Post by Bucky Ball on 2009-09-06
> **trinadhm said:**
> Thank you.. :)
  
A pleasure.

---

