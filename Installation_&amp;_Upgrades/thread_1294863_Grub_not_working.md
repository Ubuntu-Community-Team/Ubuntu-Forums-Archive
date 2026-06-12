---
title: "Grub not working"
date: 2009-10-18
forum: Installation &amp; Upgrades
---

### Post by Mitch9654 on 2009-10-18
I had grub working on my PC with Win XP and Win 7 beta. Now, I removed Win 7, reinstalled the XP MBR, and tried to reinstall the grub. Installation worked fine, but when my comp. boots, grub doesn't. only XP.

Is it because whatever comes first on the hd is booted? 

How can I fix it?

mitch9654

---

### Post by Treepwood on 2009-10-19
I have just encountered the exact same problem, so I am listening in here :-)

---

### Post by Mitch9654 on 2009-10-20
Any answers?

mitch

---

### Post by darco on 2009-10-20
You can try this:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

good luck

darco

---

### Post by Mitch9654 on 2009-10-20
How about keeping Windows **and** linux?

---

### Post by v79 on 2009-10-21
I have the same problem. I made numerous attempts to install Ubuntu 9.10 Beta, always throwing up Grub issues.

Eventually I deleted all my Linux partitions, and performed a completely clean install of the Beta. Reboot, and the machine goes straight into Windows Vista. No Grub menu at all.

So as far as I can tell Ubuntu is installed, just not accessible...

I've tried booting into the live CD and manually reinstalling Grub but it always fails at the first hurdle.

---

### Post by Mitch9654 on 2009-10-21
Maybe this will work?

Make a small bogus partition, install ubuntu on it (go through the entire installation), when the last step comes up, click advanced and make sure that the grub will install on (hd0)?

mitch9654

gonna try it

---

### Post by Niko Johnson on 2009-10-21
are you sure you mounted your partitions correctly during the install process?

---

### Post by Mark Phelps on 2009-10-21
> **v79 said:**
> I have the same problem. I made numerous attempts to install Ubuntu 9.10 Beta, always throwing up Grub issues.

A new install of 9.10 uses GRUB2, not GRUB.

That reference is for reinstalling GRUB -- not GRUB2.  You can tell that by the references to menu.lst -- which is not used anymore in GRUB2.

---

### Post by presence1960 on 2009-10-21
> **Mitch9654 said:**
> I had grub working on my PC with Win XP and Win 7 beta. Now, I removed Win 7, reinstalled the XP MBR, and tried to reinstall the grub. Installation worked fine, but when my comp. boots, grub doesn't. only XP.

Is it because whatever comes first on the hd is booted? 

How can I fix it?

mitch9654

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Mitch9654 on 2009-10-22
here it is:

it is a lot! 

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No known boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xccb3ccb3

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   188,860,139   188,860,077   7 HPFS/NTFS
/dev/sda2         188,860,140   234,436,544    45,576,405   f W95 Ext d (LBA)
/dev/sda5         188,860,266   225,006,389    36,146,124  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa94ba94b

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   156,296,384   156,296,322   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="AC3400B234008196" LABEL="Fuzzwuzzle" TYPE="ntfs" 
/dev/sda5: UUID="b8ad7360-c6b2-4f66-a1c4-9c9daabac6bf" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="E6101B66101B3D4D" LABEL="Banana" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


================================ sda1/boot.ini: ================================

;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /FASTDETECT /NOEXECUTE=OPTIN


=========================== sda5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=b8ad7360-c6b2-4f66-a1c4-9c9daabac6bf ro

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

title		Ubuntu 9.04, kernel 2.6.28-15-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=b8ad7360-c6b2-4f66-a1c4-9c9daabac6bf ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=b8ad7360-c6b2-4f66-a1c4-9c9daabac6bf ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=b8ad7360-c6b2-4f66-a1c4-9c9daabac6bf ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=b8ad7360-c6b2-4f66-a1c4-9c9daabac6bf ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.27-14-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=b8ad7360-c6b2-4f66-a1c4-9c9daabac6bf ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-14-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=b8ad7360-c6b2-4f66-a1c4-9c9daabac6bf ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 9.04, kernel 2.6.24-19-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b8ad7360-c6b2-4f66-a1c4-9c9daabac6bf ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 9.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b8ad7360-c6b2-4f66-a1c4-9c9daabac6bf ro  single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 9.04, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=b8ad7360-c6b2-4f66-a1c4-9c9daabac6bf /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=711f07cc-bb4a-48a9-8ac5-a56ff4249cce none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 113.3GB: boot/grub/menu.lst
 113.2GB: boot/grub/stage2
 113.2GB: boot/initrd.img-2.6.24-19-generic
 113.2GB: boot/initrd.img-2.6.27-14-generic
 113.3GB: boot/initrd.img-2.6.28-11-generic
 106.5GB: boot/initrd.img-2.6.28-15-generic
 113.2GB: boot/vmlinuz-2.6.24-19-generic
 113.2GB: boot/vmlinuz-2.6.27-14-generic
 113.2GB: boot/vmlinuz-2.6.28-11-generic
 102.6GB: boot/vmlinuz-2.6.28-15-generic
 106.5GB: initrd.img
 113.3GB: initrd.img.old
 102.6GB: vmlinuz
 113.2GB: vmlinuz.old

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
# kopt=root=UUID=b8ad7360-c6b2-4f66-a1c4-9c9daabac6bf ro

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

title		Ubuntu 9.04, kernel 2.6.28-15-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=b8ad7360-c6b2-4f66-a1c4-9c9daabac6bf ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=b8ad7360-c6b2-4f66-a1c4-9c9daabac6bf ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=b8ad7360-c6b2-4f66-a1c4-9c9daabac6bf ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=b8ad7360-c6b2-4f66-a1c4-9c9daabac6bf ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.27-14-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=b8ad7360-c6b2-4f66-a1c4-9c9daabac6bf ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-14-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=b8ad7360-c6b2-4f66-a1c4-9c9daabac6bf ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 9.04, kernel 2.6.24-19-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b8ad7360-c6b2-4f66-a1c4-9c9daabac6bf ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 9.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b8ad7360-c6b2-4f66-a1c4-9c9daabac6bf ro  single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 9.04, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=b8ad7360-c6b2-4f66-a1c4-9c9daabac6bf /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=711f07cc-bb4a-48a9-8ac5-a56ff4249cce none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/menu.lst
    .0GB: boot/grub/stage2
   2.8GB: boot/initrd.img-2.6[1].24-19-generic
   2.9GB: boot/initrd.img-2.6[1].27-14-generic
   2.9GB: boot/initrd.img-2.6[1].28-11-generic
   2.9GB: boot/initrd.img-2.6[1].28-15-generic
    .0GB: boot/initrd.img-2.6.24-19-generic
    .0GB: boot/initrd.img-2.6.27-14-generic
    .0GB: boot/initrd.img-2.6.28-11-generic
    .0GB: boot/initrd.img-2.6.28-15-generic
   2.8GB: boot/vmlinuz-2.6[1].24-19-generic
   2.8GB: boot/vmlinuz-2.6[1].27-14-generic
   2.9GB: boot/vmlinuz-2.6[1].28-11-generic
   2.9GB: boot/vmlinuz-2.6[1].28-15-generic
    .0GB: boot/vmlinuz-2.6.24-19-generic
    .0GB: boot/vmlinuz-2.6.27-14-generic
    .0GB: boot/vmlinuz-2.6.28-11-generic
    .0GB: boot/vmlinuz-2.6.28-15-generic
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdb

00000000  45 52 02 00 09 50 f8 b0  00 00 00 00 00 00 00 00  |ER...P..........|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000030  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000070  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000100  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000130  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  4b a9 4b a9 00 00 00 01  |........K.K.....|
000001c0  01 00 07 fe ff ff 3f 00  00 00 82 e4 50 09 00 00  |......?.....P...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by presence1960 on 2009-10-22
```
## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-15-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=b8ad7360-c6b2-4f66-a1c4-9c9daabac6bf ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=b8ad7360-c6b2-4f66-a1c4-9c9daabac6bf ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=b8ad7360-c6b2-4f66-a1c4-9c9daabac6bf ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=b8ad7360-c6b2-4f66-a1c4-9c9daabac6bf ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.27-14-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=b8ad7360-c6b2-4f66-a1c4-9c9daabac6bf ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-14-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=b8ad7360-c6b2-4f66-a1c4-9c9daabac6bf ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 9.04, kernel 2.6.24-19-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b8ad7360-c6b2-4f66-a1c4-9c9daabac6bf ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 9.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b8ad7360-c6b2-4f66-a1c4-9c9daabac6bf ro  single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 9.04, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet
```

I've noticed a couple things from your menu.lst above. Your menu.lst has kernels that are not from 9.04 as well as some that are from 9.04.

Your menu.lst uses (hdx,y) which is pre 9.04. Jaunty 9.04 uses UUID in the second line for kernels. here is a snippet from my menu.lst:
```

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-16-generic
uuid		f31336b1-0908-4580-aad2-6b04ac995b9b
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=f31336b1-0908-4580-aad2-6b04ac995b9b ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid		f31336b1-0908-4580-aad2-6b04ac995b9b
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=f31336b1-0908-4580-aad2-6b04ac995b9b ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		f31336b1-0908-4580-aad2-6b04ac995b9b
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=f31336b1-0908-4580-aad2-6b04ac995b9b ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		f31336b1-0908-4580-aad2-6b04ac995b9b
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=f31336b1-0908-4580-aad2-6b04ac995b9b ro  single
initrd		/boot/initrd.img-2.6.28-15-generic
```

Note the difference on the second line of each kernel stanza compared to yours.

Also you have (hd0,5) in the second line of the kernel stanzas. Your ubuntu is on sda5 which translates to (hd0,4).

Your fstab has sda6 & sda5 as ubuntu devices but no sda6 exists.

So you have multiple problems here. Was this an upgrade from 8.04 or 8.10 that went awry?

Personally I would back up all my files and start over with a clean install of Ubuntu. I would also add a swap partition. If you intend on using the hibernation feature you must make swap equal in size to the amount of RAM you have installed or the feature will not work.

By the way you have Legacy GRUB installed not GRUB 2.

P.S. Don't take this the wrong way but I suspect that there is a little more to the story than you are telling us. Where are those other kernels from? What happened to sda6? I seriously doubt whether installing XP after removing windows 7 and then reinstalling GRUB would do those things. Plus your partition on sdb1 says it is NTFS but the OS says Ubuntu and it has Ubuntu boot files on that sdb1 partition. Something else was run by you or happened.

---

### Post by Mitch9654 on 2009-10-22
Ya, there is more stuff. I had windows XP installed, and then I installed win 7 beta. After that, I put ubuntu 8.04 on, and later upgraded it to 9.04.
Win XP and ubuntu were on first hd, and win 7 the 2nd. Later, I repartitioned 2nd hd with MacDrive, and tried to install some macintosh on it. After I would boot and I would have my list of ubuntu kernels, I would have windows Vista/Longhorn boot thing, but when tried to boot, an error would come up. THEN, I made ubuntu 9.04 swap space smaller to reinstall ubuntu in order to reinstall GRUB. I only had a bunch of ubuntu 9.04 kernels then, and 1 8.04 kernel. also, the unbootable Vista/longhorn kernel.
I tried going into win XP boot disk and tried fmbr. That didn't solve anything. Then fixboot. So now I had only win XP booting. I tried installing 8.04 again and again. Later, I went into Windows Disk manager and formatted what used to be mac disk, (it didn't work) into win partition. also, tried to get rid of temporary 8.04 patition and resize swap area. It deleted both SWAP and 8.04. I forgot to remake swap. Here I am, and now I have ubuntu 9.04 kernels that don't boot (grub error, something about no partition) and a bootable windows Vista/Longhorn that  boots to win XP.

What the heck did I do?

mitch9654

---

### Post by presence1960 on 2009-10-23
```
#title		Ubuntu 9.04, kernel 2.6.27-14-generic
#root		(hd0,5)
#kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=b8ad7360-c6b2-4f66-a1c4-9c9daabac6bf ro quiet splash 
#initrd		/boot/initrd.img-2.6.27-14-generic
#quiet

#title		Ubuntu 9.04, kernel 2.6.27-14-generic (recovery mode)
#root		(hd0,5)
#kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=b8ad7360-c6b2-4f66-a1c4-9c9daabac6bf ro  single
#initrd		/boot/initrd.img-2.6.27-14-generic

#title		Ubuntu 9.04, kernel 2.6.24-19-generic
#root		(hd0,5)
#kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b8ad7360-c6b2-4f66-a1c4-9c9daabac6bf ro quiet splash 
#initrd		/boot/initrd.img-2.6.24-19-generic
#quiet

#title		Ubuntu 9.04, kernel 2.6.24-19-generic (recovery mode)
#root		(hd0,5)
#kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b8ad7360-c6b2-4f66-a1c4-9c9daabac6bf ro  single
#initrd		/boot/initrd.img-2.6.24-19-generic
```

for starters I would comment out the above kernels by using # as I did above this way those Hardy or Intrepid kernels do not show in the GRUB menu.

Then I would change all the (hd0,5) in the remaining kernel stanzas to (hd0,4)

That may get Ubuntu booting, but then again your fstab file may be a problem.

Your best bet is to download gparted Live CD [here]("http://gparted.sourceforge.net/livecd.php"), burn it to CD and format both hard disks and set up new partitions for Windows, Ubuntu and any storage partitions you may want. Boot off the gparted Live CD to do so. Once ypour partitions are set up install windows to the intended windows partition (must be primary & NTFS), then install Ubuntu

---

### Post by Mitch9654 on 2009-10-23
where do I comment out this info
?

---

### Post by Mitch9654 on 2009-10-23
Yahoo!

I wasn't installing grub on (hd0)!
I am writing this message from ubuntu 9.04, and will delete the 8.04 partition and turn it into SWAP!

Windows still works!

[solved]

mitch9654

---

