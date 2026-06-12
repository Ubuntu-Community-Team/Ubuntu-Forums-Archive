---
title: "Messed up GRUB after windows 7 install. Need Help!"
date: 2009-07-26
forum: Installation &amp; Upgrades
---

### Post by J.Byram on 2009-07-26
I have run into a predicament.  I was dual booting Ubuntu Studio (the latest one, 9 I believe) and XP.  I had some room left over on my secondary hard drive (on which Ubuntu Studio is installed) and decided to try the new Windows 7 Release Client (build 7100).  I installed 7 and now my grub is all messed up.  I used the Super Grub Disk to fix my grub, but it does not recognize 7 as an independent installation on the computer.  The only thing it sees is XP and when I boot into that, it boots the windows boot loader and I have to choose between xp and 7.  If it helps, I have XP installed on my primary hard drive and my secondary drive has two partitions of roughly equal size and has Ubuntu Studio and Windows 7 installed on it.

My question: How do I get 7 to show up on the grub with xp and no windows boot loader coming up after selecting either XP or 7.

Thanks in advance!
-John

---

### Post by presence1960 on 2009-07-26
Boot off the Ubuntu Live CD and choose "Try Ubuntu without any changes...", when the desktop loads open Firefox and download to the desktop the boot info script 0.32 from here: [http://sourceforge.net/projects/bootinfoscript/files/](http://sourceforge.net/projects/bootinfoscript/files/) 
After downloading to desktop open a terminal and run this command: ```
sudo bash ~/Desktop/boot_info_script*.sh
```
This will create a RESULTS.txt file on your desktop. paste the entire contents of that file back here. After pasting here highlight all text and click the # sign on the toolbar to place code tags around the text. This file will have all the info about your setup and boot process.

---

### Post by J.Byram on 2009-07-27
As requested: My system info.

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => ThinkPad is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

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

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa36af163

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   490,223,474   490,223,412   6 FAT16


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 40.0 GB, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78156288 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1f6f1f6e

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    29,302,559    29,302,497  83 Linux
/dev/sdb2          29,302,560    39,070,079     9,767,520   5 Extended
/dev/sdb5          29,302,623    39,070,079     9,767,457  82 Linux swap / Solaris
/dev/sdb3          39,070,080    78,140,159    39,070,080   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="00000000448D2B7B" TYPE="ntfs" 
/dev/sdb1: UUID="9a708808-9c7a-4b3d-be68-ad40cd7a182e" TYPE="ext3" 
/dev/sdb3: UUID="107CD2747CD25456" TYPE="ntfs" 
/dev/sdb5: UUID="3fdec88c-9971-43ca-a914-4fed16467241" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-3-rt/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/m51/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=m51)


================================ sda1/boot.ini: ================================

;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=0

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT


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
# kopt=root=UUID=9a708808-9c7a-4b3d-be68-ad40cd7a182e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9a708808-9c7a-4b3d-be68-ad40cd7a182e

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

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

title		Ubuntu 9.04, kernel 2.6.28-3-rt
uuid		9a708808-9c7a-4b3d-be68-ad40cd7a182e
kernel		/boot/vmlinuz-2.6.28-3-rt root=UUID=9a708808-9c7a-4b3d-be68-ad40cd7a182e ro quiet splash 
initrd		/boot/initrd.img-2.6.28-3-rt
quiet

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

title		Ubuntu 9.04, kernel 2.6.28-3-rt (recovery mode)
uuid		9a708808-9c7a-4b3d-be68-ad40cd7a182e
kernel		/boot/vmlinuz-2.6.28-3-rt root=UUID=9a708808-9c7a-4b3d-be68-ad40cd7a182e ro  single
initrd		/boot/initrd.img-2.6.28-3-rt

title		Ubuntu 9.04, memtest86+
uuid		9a708808-9c7a-4b3d-be68-ad40cd7a182e
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST







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
UUID=9a708808-9c7a-4b3d-be68-ad40cd7a182e /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=3fdec88c-9971-43ca-a914-4fed16467241 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .9GB: boot/grub/menu.lst
    .8GB: boot/grub/stage2
    .8GB: boot/initrd.img-2.6.28-3-rt
    .9GB: boot/vmlinuz-2.6.28-3-rt
    .8GB: initrd.img
    .9GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc 
```

---

### Post by philcamlin on 2009-07-27
Code:
 	sudo grub 
This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands

 	Code:
 	find /boot/grub/stage1 
This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)

 	Code:
 	root (hd?,?) 
Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

 	Code:
 	setup (hd0) 
Finally exit the grub shell
 	Code:
 	quit 
That is it. Grub will be installed to the mbr.
When you reboot, you will have the grub menu at startup.

try reinstalling grub

---

### Post by merlinus on 2009-07-27
There is no entry for win7 in /boot/grub/menu.lst.  You will have to add one, because reinstalling grub will not do it.

---

### Post by J.Byram on 2009-07-27
How does one add the entry for Windows 7?

---

### Post by J.Byram on 2009-07-27
I have no problem with the Grub being there.  It is.  What I want to do is eliminate the need for this sequence of boot: 
1. GRUB
1.a: Windows XP -> Windows Bootloader -> choose between Windows 7 or Earlier version of Windows.
1.b-e: Ubuntu Studio boot options

I would like there to be a option for 7 in the grub and the windows bootloader NOT be there when I select XP or 7 from the GRUB.

---

### Post by merlinus on 2009-07-27
Is win7 on sdb3?  And what is the boot order of your hdds in bios?

It looks like sda1 is a fat filesystem from fdisk, but if you look at the report, it says it is vista on ntfs.

FWIW, I would never use that method of reporting information.

---

### Post by J.Byram on 2009-07-27
> **merlinus said:**
> Is win7 on sdb3?  And what is the boot order of your hdds in bios?

It looks like sda1 is a fat filesystem from fdisk, but if you look at the report, it says it is vista on ntfs.

FWIW, I would never use that method of reporting information.

yes...win7 is on sdb3.  sdb holds both linux and win7.  sda is only XP and is in a NTFS file format.  I don't know why it recognizes as a vista system though.  The other sdb partitions hold Ubuntu Studio 9.04

The boot order:
1. IDE CD: Optical Drive
2. IDE 2: WDC WD2500 (sda)
3. IDE 3: WDC WD400 (sdb)

---

### Post by merlinus on 2009-07-27
Try adding this to the end of menu.lst:

title Win7
rootnoverify (hd1,2)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1

---

### Post by J.Byram on 2009-07-27
> **merlinus said:**
> Try adding this to the end of menu.lst:

title Win7
rootnoverify (hd1,2)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1

I got this error: 
"Error 11: Unrecognized device string
Press any key to continue..."

---

### Post by merlinus on 2009-07-27
To be sure, let's review.  You are booting from sda as the first hdd in bios, and win7 is on sdb3.

---

### Post by J.Byram on 2009-07-27
> **merlinus said:**
> To be sure, let's review.  You are booting from sda as the first hdd in bios, and win7 is on sdb3.

win7 is definitely on sdb3.  I am pretty sure that I am booting from sda, almost positive considering it is the first of the two HDDs in the boot sequence.

---

### Post by oldfred on 2009-07-27
I believe you installed Windows in an extended partition. This complicates it greatly and most of us believed Windows could only boot from primary partitions.
this is Herman's answer to a similiar issue.
[http://ubuntuforums.org/showpost.php?p=7488261&postcount=17](http://ubuntuforums.org/showpost.php?p=7488261&postcount=17)

---

### Post by J.Byram on 2009-07-27
> **oldfred said:**
> I believe you installed Windows in an extended partition. This complicates it greatly and most of us believed Windows could only boot from primary partitions.
this is Herman's answer to a similiar issue.
[http://ubuntuforums.org/showpost.php?p=7488261&postcount=17](http://ubuntuforums.org/showpost.php?p=7488261&postcount=17)

Thank you for the heads up.  I believe though, that I did not.  I took a look at my second disk (disk with ubuntu and win7 on it) and the partitions are as follows:

13.97 GB Healthy (Active) Marked Primary Partition   <-- This is Ubuntu
4.66 GB Healthy (Unknown Partition) Marked Extended Partition and a logical drive <-- This is swap
18.63 GB Healthy Marked Primary Partition   <-- This is Win7

This is from the Disk Management in WinXP.  From here, it looks as though the only extended partition is that of the swap for Ubuntu Studio

---

### Post by presence1960 on 2009-07-27
when you install 2 versions of windows that is how they boot. The bootloader from the newer version takes over the older version and gives you a choice between the two versions of windows. Unfortunately that is how windows works and contact Bill Gates with any complaints. I know it probably irks you but it isn't too much of a hassle to choose whether you want XP or win 7 from a menu. There really isn't much you can do about it.

P.S. this is half serious & half joke: I can not imagine more than one version of windows on any machine. The one version I have now is more than enough!

---

