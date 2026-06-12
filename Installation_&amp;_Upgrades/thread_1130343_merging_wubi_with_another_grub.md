---
title: "merging wubi with another grub"
date: 2009-04-19
forum: Installation &amp; Upgrades
---

### Post by musky on 2009-04-19
Got wubi 8.10 humming on a xp setup. Problem is i already had a multi boot setup from the C/ drive using grub with a menu list.

Only way i figured so far to make it work is like this:

If i leave grldr & menu.lst as is, I cannot boot into ubuntu. If I change the file names to 1grldr & 1menu.lst, I then can boot into ubuntu.

It's one or the other & have to change (or remove, put in a folder etc..) as described above.

Anyway to merge the 2? The wubi setup with a prior grub menu.lst setup? tia

---

### Post by meierfra. on 2009-04-19
> Anyway to merge the 2? 


Should be possible. But to get a clearer picture of your setup, I suggest to boot into  Ubuntu  and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post,  highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it.

---

### Post by musky on 2009-04-20
Ok, I think I can give that a shot but maybe I can also try adding a script (dunno what that might be..) to the menu list (in C\) to fire up wubi (or ubuntu)?

Wubi/Ubuntu is setup in sda3 & comes up as a G\ drive (primary partition) in win but pretty sure the wubi start up stuff (wubildr & wubildr.mbr) is in C\.

All the other linux stuff (pups & 1 pclos) are frugal setup.

Menu list sorta goes like this:
(it & grub are in the C\ drive)
(boot ini start for it is C:\grldr="Start Linux") 
```
######################################################
# GvR Sept 30th 2004
	color black/cyan yellow/cyan
	timeout=5
	default=0

title Default Boot on HD 0
	rootnoverify (hd0,0)
	chainloader +1
	boot

title PCLinuxOS 2009
kernel (hd1,0)/boot/vmlinuz livecd=livecd root=/dev/rd/3 acpi=on vga=791 rw changes_dev=/dev/sda8
initrd (hd1,0)/boot/initrd.gz

title Puppy Linux dingo
kernel (hd0,6)/vmlinuz PMEDIA=satahd PDEV1=sda7 psubdir=dingo
initrd (hd0,6)/initrd.gz
boot######################################################

..etc as the above with the other pups & only have one pclos setup.
```
Somehow works in vista on another 'pute but not sure why or how & just lucked into it ..though I only have 1 shot at selecting wubi at the startup boot & if I don't select wubi then, it (or the wubi boot option) goes away (disappears) until the next fresh reboot.

---

### Post by musky on 2009-05-01
Did this in portable ubuntu while in win ..in case it makes a diff.
```
============================= Boot Info Summary: ==============================


=========================== Drive/Partition Info: =============================

no valid partition table found
blkid -c /dev/null: ____________________________________________________________

/dev/cobd0: UUID="d7f13826-867b-410f-a71a-784494a87119" TYPE="ext3" 
/dev/cobd1: UUID="51359717-8050-4a34-b963-8a1fda34f843" TYPE="swap" 
/dev/cobd2: UUID="8919852d-908b-4da7-b7d8-a9044f671d14" TYPE="ext2" 

=============================== "mount" output: ===============================

/dev/cobd0 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/cobd2 on /tmp type ext2 (rw)
cofs0 on /etc/portable_ubuntu type cofs (rw,noexec,nosuid,nodev,dmask=0777,fmask=0666)
cofs1 on /mnt/C type cofs (rw,noexec,nosuid,nodev,dmask=0777,fmask=0666)
gvfs-fuse-daemon on /home/pubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=pubuntu)
```

---

### Post by meierfra. on 2009-05-01
> Did this in portable ubuntu while in win ..in case it makes a diff.
It does make a difference. Please run the script again, either from Wubi or from Ubuntu.

---

### Post by musky on 2009-05-02
Oh maaan.. neat gadget but looong on the info..

Just to be clear, had to mod my normal boot start grldr & menu.lst (renamed to 1grldr & 1menu.lst)  in Sda1 to boot wubi.

Probably have extra junk here & there that does nothing in terms of booting as I was fiddling quite a bit to sort it out.

Main boot stuff (grldr, menu.lst & wubi)  is in Sda1.
```
============================= Boot Info Summary: ==============================

 => HP/Gateway is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com /wubildr.mbr

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /menu.lst /ubuntu/disks/boot/grub/menu.lst 
                       /ubuntu/winboot/menu.lst /grldr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcab10bee

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   269,667,089   269,667,027   7 HPFS/NTFS
/dev/sda2         958,791,330   976,768,064    17,976,735   c W95 FAT32 (LBA)
/dev/sda3         269,667,090   522,883,619   253,216,530   7 HPFS/NTFS
/dev/sda4         522,883,620   958,791,329   435,907,710   f W95 Ext d (LBA)
/dev/sda5         522,883,683   526,980,194     4,096,512  82 Linux swap / Solaris
/dev/sda6         526,980,258   629,394,569   102,414,312   b W95 FAT32
/dev/sda7         629,394,633   731,808,944   102,414,312  83 Linux
/dev/sda8         731,809,008   834,223,319   102,414,312  83 Linux
/dev/sda9         834,223,383   958,791,329   124,567,947  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="AA08E78008E749C1" LABEL="PRESARIO" TYPE="ntfs" 
/dev/sda2: LABEL="PRESARIO_RP" UUID="521A-5F89" TYPE="vfat" 
/dev/sda3: UUID="F21C0E161C0DD68F" TYPE="ntfs" 
/dev/sda5: TYPE="swap" 
/dev/sda6: LABEL="LOCAL DISK" UUID="0A8B-0A8B" TYPE="vfat" 
/dev/sda7: UUID="6368746f-2074-616b-6f65-207575696400" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda8: UUID="6368746f-2074-616b-6f65-207575696400" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda9: UUID="6368746f-2074-616b-6f65-207575696400" SEC_TYPE="ext2" TYPE="ext3" 
/dev/loop0: UUID="fe169fcd-c541-4fb0-a32d-e6509fb7e90b" TYPE="ext3" 

=============================== "mount" output: ===============================

/host/ubuntu/disks/root.disk on / type ext3 (rw,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/sda3 on /host type fuseblk (rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
/host/ubuntu/disks/boot on /boot type none (rw,bind)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/yo/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=yo)
/dev/scd0 on /media/WinXP_MC_LE type iso9660 (ro,nosuid,nodev,uhelper=hal,uid=1000,utf8)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS



[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons

C:\grldr="Start Linux"

C:\wubildr.mbr="Ubuntu"

G:\grldr="Start Linux"


================================ sda2/boot.ini: ================================

[boot loader]

timeout=15

default=C:\CMDCONS\BOOTSECT.DAT

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons

c:\wubildr.mbr="Ubuntu"


================================ sda2/BOOT.INI: ================================

[boot loader]

timeout=15

default=C:\CMDCONS\BOOTSECT.DAT

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons

c:\wubildr.mbr="Ubuntu"


================================ sda3/menu.lst: ================================

######################################################

# GvR Sept 30th 2004

	color black/cyan yellow/cyan

	timeout=5

	default=0



title Default Boot on HD 0

	rootnoverify (hd0,0)

	chainloader +1

	boot



title PCLinuxOS 2009

kernel (hd1,0)/boot/vmlinuz livecd=livecd root=/dev/rd/3 acpi=on vga=791 rw changes_dev=/dev/sda8

initrd (hd1,0)/boot/initrd.gz



title PCLinuxOS 2009

kernel (hd1,0)/isolinux/vmlinuz livecd=livecd root=/dev/rd/3 acpi=on vga=791 rw changes_dev=/dev/sda8

initrd (hd1,0)/isolinux/initrd.gz



title PCLinuxOS 2009

kernel (hd1,0)/boot/isolinux/vmlinuz livecd=livecd root=/dev/rd/3 acpi=on vga=791 rw changes_dev=/dev/sda8

initrd (hd1,0)/boot/isolinux/initrd.gz



title PCLinuxOS 2009

kernel (hd1,0)/boot/vmlinuz livecd=livecd root=/dev/rd/3 acpi=on vga=791 rw

initrd (hd1,0)/boot/initrd.gz



title PCLinuxOS 2009

kernel (hd0,9)/boot/vmlinuz livecd=livecd root=/dev/rd/3 acpi=on vga=791 rw

initrd (hd0,9)/boot/initrd.gz

 

title Puppy Linux 3.01

kernel (hd0,2)/vmlinuz PMEDIA=satahd PDEV1=sda3 psubdir=301

initrd (hd0,2)/initrd.gz

boot



title Puppy Linux muppy

kernel (hd0,2)/vmlinuza PMEDIA=satahd PDEV1=sda3 psubdir=muppy

initrd (hd0,2)/initrda.gz

boot



title Puppy Linux mup02

kernel (hd0,2)/vmlinuzb PMEDIA=satahd PDEV1=sda3 psubdir=mup02

initrd (hd0,2)/initrdb.gz

boot



title Puppy Linux lighth

kernel (hd0,2)/vmlinuzc PMEDIA=satahd PDEV1=sda3 psubdir=lighth

initrd (hd0,2)/initrdc.gz

boot



title Puppy Linux chi

kernel (hd0,2)/vmlinuzd PMEDIA=satahd PDEV1=sda3 psubdir=chi

initrd (hd0,2)/initrdd.gz

boo1



title Puppy Linux dingo

kernel (hd0,2)/vmlinuze PMEDIA=satahd PDEV1=sda3 psubdir=dingo

initrd (hd0,2)/initrde.gz

boot

title Puppy Linux 3.01

kernel (hd0,6)/vmlinuz PMEDIA=satahd PDEV1=sda7 psubdir=301

initrd (hd0,6)/initrd.gz

boot



title Puppy Linux muppy

kernel (hd0,6)/vmlinuza PMEDIA=satahd PDEV1=sda7 psubdir=muppy

initrd (hd0,6)/initrda.gz

boot



title Puppy Linux mup02

kernel (hd0,6)/vmlinuzb PMEDIA=satahd PDEV1=sda7 psubdir=mup02

initrd (hd0,6)/initrdb.gz

boot



title Puppy Linux lighth

kernel (hd0,6)/vmlinuzc PMEDIA=satahd PDEV1=sda7 psubdir=lighth

initrd (hd0,6)/initrdc.gz

boot



title Puppy Linux chi

kernel (hd0,6)/vmlinuzd PMEDIA=satahd PDEV1=sda7 psubdir=chi

initrd (hd0,6)/initrdd.gz

boo1



title Puppy Linux dingo

kernel (hd0,6)/vmlinuze PMEDIA=satahd PDEV1=sda7 psubdir=dingo

initrd (hd0,6)/initrde.gz

boot######################################################




==================== sda3/ubuntu/disks/boot/grub/menu.lst: ====================

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
# kopt=root=UUID=F21C0E161C0DD68F loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=F21C0E161C0DD68F loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=F21C0E161C0DD68F loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=F21C0E161C0DD68F loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=F21C0E161C0DD68F loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows NT/2000/XP
root		(hd0,1)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows NT/2000/XP (loader)
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title		Windows NT/2000/XP
root		(hd1,1)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


======================== sda3/ubuntu/winboot/menu.lst: ========================

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
	find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
	configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
	fallback 2
	find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
	configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
	fallback 3
	find --set-root --ignore-floppies /menu.lst
	configfile /menu.lst

title find /boot/grub/menu.lst
	fallback 4
	find --set-root --ignore-floppies /boot/grub/menu.lst
	configfile /boot/grub/menu.lst

title find /grub/menu.lst
	fallback 5
	find --set-root --ignore-floppies /grub/menu.lst
	configfile /grub/menu.lst

title commandline
	commandline

title reboot
	reboot

title halt
	halt

================================== sda3Wubi: ==================================

Operating System: "Ubuntu 8.10"


proc /proc proc defaults 0 0
/host/ubuntu/disks/root.disk / ext3 loop,errors=remount-ro 0 1
/host/ubuntu/disks/boot /boot none bind 0 0
/host/ubuntu/disks/swap.disk none swap loop,sw 0 0



=================== sda3: Location of files loaded by Grub: ===================


 141.5GB: boot/initrd.gz
 141.5GB: boot/vmlinuz
 138.0GB: initrda.gz
 138.0GB: initrdb.gz
 138.0GB: initrdc.gz
 138.0GB: initrdd.gz
 138.0GB: initrde.gz
 141.5GB: initrd.gz
 141.4GB: menu.lst
 141.2GB: ubuntu/disks/boot/grub/menu.lst
 141.5GB: ubuntu/disks/boot/initrd.img-2.6.27-11-generic
 141.5GB: ubuntu/disks/boot/initrd.img-2.6.27-7-generic
 141.5GB: ubuntu/disks/boot/vmlinuz-2.6.27-11-generic
 141.5GB: ubuntu/disks/boot/vmlinuz-2.6.27-7-generic
 141.5GB: vmlinuz
 138.0GB: vmlinuza
 138.0GB: vmlinuzb
 138.0GB: vmlinuzc
 138.0GB: vmlinuzd
 138.0GB: vmlinuze

=================== sda7: Location of files loaded by Grub: ===================


 322.3GB: initrda.gz
 322.3GB: initrdb.gz
 322.3GB: initrdc.gz
 322.3GB: initrdd.gz
 322.3GB: initrde.gz
 322.3GB: vmlinuza
 322.3GB: vmlinuzb
 322.3GB: vmlinuzc
 322.3GB: vmlinuzd
 322.3GB: vmlinuze

=================== sda9: Location of files loaded by Grub: ===================


 448.4GB: boot/initrd.gz
 448.4GB: boot/vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda6

00000000  eb 58 90 50 41 52 41 47  4f 4e 23 00 02 20 20 00  |.X.PARAGON#..  .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  e8 b7 1a 06 a0 61 00 00  00 00 00 00 02 00 00 00  |.....a..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 8b 0a 8b 0a 00  00 00 00 00 00 00 00 00  |..).............|
00000050  00 00 46 41 54 33 32 20  20 20 8c c8 8e d0 bc ff  |..FAT32   ......|
00000060  7b fb 8e d8 8e c0 fc bf  20 00 33 c0 b9 15 00 af  |{....... .3.....|
00000070  75 05 af 75 04 e2 f8 47  47 81 7d fe 00 c0 72 0a  |u..u...GG.}...r.|
00000080  e2 ed 81 3e 02 01 00 c0  73 0f be 88 7d e8 3f 00  |...>....s...}.?.|
00000090  33 c0 cd 16 3d 00 3b 75  f7 be a7 7c bf a7 7e b9  |3...=.;u...|..~.|
000000a0  71 00 f3 a5 e9 00 02 bb  00 7c b9 01 00 be e1 7e  |q........|.....~|
000000b0  e8 1c 00 33 c0 cd 16 b8  01 02 33 d2 50 cd 13 58  |...3......3.P..X|
000000c0  cd 13 72 e3 81 3e fe 7d  55 aa 75 db e9 31 fd 50  |..r..>.}U.u..1.P|
000000d0  53 51 ac 3c 00 75 04 59  5b 58 c3 b4 0e cd 10 eb  |SQ.<.u.Y[X......|
000000e0  f1 0a 0d 4e 6f 6e 2d 73  79 73 74 65 6d 20 64 69  |...Non-system di|
000000f0  73 6b 20 6f 72 20 64 69  73 6b 20 65 72 72 6f 72  |sk or disk error|
00000100  0a 0d 49 6e 73 65 72 74  20 44 4f 53 20 64 69 73  |..Insert DOS dis|
00000110  6b 65 74 74 65 20 61 6e  64 20 70 72 65 73 73 20  |kette and press |
00000120  61 6e 79 20 6b 65 79 20  2e 2e 2e 0a 0d 00 00 00  |any key ........|
00000130  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000180  00 00 00 00 00 00 00 00  0a 0d 50 6f 73 73 69 62  |..........Possib|
00000190  6c 65 20 62 6f 6f 74 20  56 49 52 55 53 20 64 65  |le boot VIRUS de|
000001a0  74 65 63 74 65 64 21 0a  0d 50 72 65 73 73 20 3c  |tected!..Press <|
000001b0  46 31 3e 20 74 6f 20 63  6f 6e 74 69 6e 75 65 00  |F1> to continue.|
000001c0  0d 0a 50 57 2f 44 42 20  62 79 20 4b 49 52 20 56  |..PW/DB by KIR V|
000001d0  2e 20 28 43 29 20 50 61  72 61 67 6f 6e 20 31 39  |. (C) Paragon 19|
000001e0  39 37 2d 31 39 39 39 00  00 00 00 00 00 00 00 00  |97-1999.........|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by musky on 2009-05-02
delete-double post

---

### Post by meierfra. on 2009-05-02
Just add this


```
title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=F21C0E161C0DD68F loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=F21C0E161C0DD68F loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=F21C0E161C0DD68F loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=F21C0E161C0DD68F loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

```

to  the file "C:\menu.lst" on your Windows partition.

---

### Post by musky on 2009-05-02
loooong story ...short of it is it worked. thx

---

### Post by meierfra. on 2009-05-02
> loooong story ...short of it is it worked. thx

What's the long story?:)

---

### Post by musky on 2009-05-02
The short story of the looong story is... my brain  is about fried.. &
need a break.

Not really sure what happened.. but.. a buncha stuff & when it worked
out, didn't quite play out the way I thought it would.

Adding the above (prior post) ubu stuff to the menu.lst did the trick.. in the end.

Will get back.

---

