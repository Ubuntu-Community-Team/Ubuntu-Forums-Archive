---
title: "GRUB issue after move from WUBI"
date: 2009-01-20
forum: Installation &amp; Upgrades
---

### Post by IainPurdie on 2009-01-20
As with a lot of other people, I seem to be struggling with the Grub file. I pretty much understand it, but the problem I currently have is as follows:

I've edited the /boot/grub/menu.lst file to reflect the correct partitions for my now-moved installation. However, when I reboot my machine the system uses the Windows boot.ini file in the first instance. From here, I choose Ubuntu... and it refers to the old WUBI Grub file (d:\ubuntu\disks\boot\grub\menu.lst). From *this* one, I can select the "new" version of Ubuntu.

My question is - how do I get Grub to be my primary boot manager? And specifically, the Grub installation that's tied to me "proper" ext3 installation. That way, I'd have the correct Ubuntu as my default OS with Windows still available as an option.

Right now, I'm worried about uninstalling the WUBI version within Windows in case it removes Grub as part of the uninstall and leaves my new version unbootable!

Any ideas? Would I be safe to just uninstall the old version without worrying about it taking Grub away as well? Alternatively, how do I convince c:\wubildr.mbr to point at the correct (new) installation? That would be satisfactory as I don't want to ditch Windows entirely anyway.

Thanks in advance, folks

---

### Post by caljohnsmith on 2009-01-20
In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup. Also, it should be safe to uninstall Wubi, because that will just remove the Wubi Ubuntu option from your Windows boot loader, so it shouldn't affect any other Ubuntu installations you might have.

---

### Post by IainPurdie on 2009-01-20
Hey Cal (can I call you Cal? :) )

The reason for my concern with removing the Wubi install from Windows is *exactly* that it will take the Wubi option out of my Windows loader. At present, when I boot my machine I get the Windows boot loader which offers me a choice of XP or Ubuntu. I have to select Ubuntu to get the menu from my Wubi install, the bottom option of which is my new standalone installation.

Therefore, if I remove the Wubi install, I remove the initial menu and the secondary menu which prevents me getting to the third (!) menu from where I can load Intrepid.

What I'm aiming for is either Grub being my initial bootloader, with an option for Intrepid or XP; or alternatively the Windows bootloader offering me a choice of XP or Ubuntu which leads to my standalone installation. The former is preferable, the second perfectly acceptable.

The details you requested follow:

```
============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTLDR /NTDETECT.COM /ntdetect.com 
                       /wubildr.mbr

sda3: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/disks/boot/grub/menu.lst /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks 
                       /ubuntu/disks/boot/ /ubuntu/disks/boot/grub 
                       /ubuntu/disks/boot/grub

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda7: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:
omitting empty partition (5)

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x34fe34fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63     6152894     3076416   12  Compaq diagnostics
/dev/sda2   *     6152895    48050414    20948760    c  W95 FAT32 (LBA)
/dev/sda3        48050415   234441647    93195616+   f  W95 Ext'd (LBA)
/dev/sda5        48050478   199013219    75481371    b  W95 FAT32
/dev/sda6       199013283   231303869    16145293+  83  Linux
/dev/sda7       231303933   234441647     1568857+  82  Linux swap / Solaris

sfdisk -V /dev/sda:

Warning: partition 3 extends past end of disk

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="PQSERVICE" UUID="3007-17F2" TYPE="vfat" 
/dev/sda2: LABEL="ACER" UUID="1569-13D7" TYPE="vfat" 
/dev/sda5: LABEL="ACERDATA" UUID="1619-1AEA" TYPE="vfat" 
/dev/sda6: UUID="42f61c87-42b0-478d-975b-019ae5091760" TYPE="ext3" 
/dev/sda7: UUID="1068adbb-ec1c-4a01-9b2f-9944ce09224f" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/iain/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=iain)
/dev/sda2 on /media/ACER type vfat (rw,nosuid,nodev,uid=1000,gid=100,umask=000)
/dev/sda5 on /media/ACERDATA type vfat (rw,nosuid,nodev,uid=1000,gid=100,umask=000)

================================ sda2/boot.ini: ================================

[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

c:\wubildr.mbr="Ubuntu"


==================== sda5/ubuntu/disks/boot/grub/menu.lst: ====================

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

# kopt=root=/dev/disk/by-uuid/1619-1AEA loop=/ubuntu/disks/root.disk ro



## Setup crashdump menu entries

## e.g. crashdump=1

# crashdump=0



## default grub root device

## e.g. groot=(hd0,0)

# groot=(hd0,0)



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



title		Ubuntu 8.04.1, kernel 2.6.24-22-generic

root            (hd0,5)/ubuntu/disks

kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=1619-1AEA loop=/ubuntu/disks/root.disk ro quiet splash

initrd		/boot/initrd.img-2.6.24-22-generic



title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)

root            (hd0,5)/ubuntu/disks

kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=1619-1AEA loop=/ubuntu/disks/root.disk ro single

initrd		/boot/initrd.img-2.6.24-22-generic



#title		Ubuntu 8.04.1, kernel 2.6.24-21-generic

#root		(hd0,1)/ubuntu/disks

#kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=1619-1AEA loop=/ubuntu/disks/root.disk ro quiet splash

#initrd		/boot/initrd.img-2.6.24-21-generic



#title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)

#root		(hd0,1)/ubuntu/disks

#kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=1619-1AEA loop=/ubuntu/disks/root.disk ro single

#initrd		/boot/initrd.img-2.6.24-21-generic



#title		Ubuntu 8.04.1, kernel 2.6.24-19-generic

#root		(hd0,1)/ubuntu/disks

#kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=1619-1AEA loop=/ubuntu/disks/root.disk ro quiet splash

#initrd		/boot/initrd.img-2.6.24-19-generic



#title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)

#root		(hd0,1)/ubuntu/disks

#kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=1619-1AEA loop=/ubuntu/disks/root.disk ro single

#initrd		/boot/initrd.img-2.6.24-19-generic



#title		Ubuntu 8.04.1, kernel 2.6.24-18-generic

#root		(hd0,1)/ubuntu/disks

#kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=1619-1AEA loop=/ubuntu/disks/root.disk ro quiet splash

#initrd		/boot/initrd.img-2.6.24-18-generic



#title		Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode)

#root		(hd0,1)/ubuntu/disks

#kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=1619-1AEA loop=/ubuntu/disks/root.disk ro single

#initrd		/boot/initrd.img-2.6.24-18-generic



title		Ubuntu 8.04.1, memtest86+

root            (hd0,5)/ubuntu/disks

kernel		/boot/memtest86+.bin



### END DEBIAN AUTOMAGIC KERNELS LIST



# This is a divider, added to separate the menu items below from the Debian

# ones.

title		Other operating systems:

root





# This entry automatically added by the Debian installer for a non-linux OS

# on /dev/sda2

title		Microsoft Windows XP Professional

root		(hd0,1)

savedefault

chainloader	+1





title Ubuntu-on-/dev/sda6
root (hd0,5)
configfile /boot/grub/menu.lst



============================== sda5/ubuntu/disks: ==============================

total 12695408
drwxrwxrwx 4 iain users      16384 2009-01-19 20:09 .
drwxrwxrwx 6 iain users      16384 2009-01-19 20:09 ..
drwxrwxrwx 3 iain users      16384 2009-01-19 22:36 boot
-rwxrwxrwx 1 iain users 4000000000 2009-01-20 00:49 home.disk
-rwxrwxrwx 1 iain users 4000000000 2008-06-24 02:04 root.disk
drwxrwxrwx 2 iain users      16384 2009-01-19 20:27 shared
-rwxrwxrwx 1 iain users 1000000000 2008-06-14 21:04 swap.disk
-rwxrwxrwx 1 iain users 4000000000 2009-01-20 00:49 usr.disk

=========================== sda5/ubuntu/disks/boot/: ===========================

total 37408
drwxrwxrwx 3 iain users   16384 2009-01-19 22:36 .
drwxrwxrwx 4 iain users   16384 2009-01-19 20:09 ..
-rwxrwxrwx 1 iain users  422838 2008-11-24 23:47 abi-2.6.24-22-generic
-rwxrwxrwx 1 iain users  422838 2008-11-27 22:13 abi-2.6.24-23-generic
-rwxrwxrwx 1 iain users   80062 2008-11-24 23:47 config-2.6.24-22-generic
-rwxrwxrwx 1 iain users   80051 2008-11-27 22:13 config-2.6.24-23-generic
drwxrwxrwx 2 iain users   16384 2009-01-20 01:06 grub
-rwxrwxrwx 1 iain users 7938620 2009-01-17 15:24 initrd.img-2.6.24-22-generic
-rwxrwxrwx 1 iain users 7760061 2008-12-09 23:30 initrd.img-2.6.24-22-generic.bak
-rwxrwxrwx 1 iain users 7759910 2009-01-17 15:27 initrd.img-2.6.24-23-generic
-rwxrwxrwx 1 iain users 7938460 2009-01-17 15:23 initrd.img-2.6.24-23-generic.bak
-rwxrwxrwx 1 iain users  103204 2007-09-28 11:06 memtest86+.bin
-rwxrwxrwx 1 iain users  905617 2008-11-24 23:47 System.map-2.6.24-22-generic
-rwxrwxrwx 1 iain users  905633 2008-11-27 22:13 System.map-2.6.24-23-generic
-rwxrwxrwx 1 iain users 1921176 2008-11-24 23:47 vmlinuz-2.6.24-22-generic
-rwxrwxrwx 1 iain users 1921976 2008-11-27 22:13 vmlinuz-2.6.24-23-generic

========================= sda5/ubuntu/disks/boot/grub: =========================

total 112
drwxrwxrwx 2 iain users 16384 2009-01-20 01:06 .
drwxrwxrwx 3 iain users 16384 2009-01-19 22:36 ..
-rwxrwxrwx 1 iain users   191 2008-06-14 22:11 default
-rwxrwxrwx 1 iain users    45 2008-06-14 22:11 device.map
-rwxrwxrwx 1 iain users  6301 2009-01-20 01:06 menu.lst
-rwxrwxrwx 1 iain users  6301 2009-01-19 23:24 menu.lst~
-rwxrwxrwx 1 iain users  6098 2009-01-09 01:29 menu.lst.bak

========================= sda5/ubuntu/disks/boot/grub: =========================

total 112
drwxrwxrwx 2 iain users 16384 2009-01-20 01:06 .
drwxrwxrwx 3 iain users 16384 2009-01-19 22:36 ..
-rwxrwxrwx 1 iain users   191 2008-06-14 22:11 default
-rwxrwxrwx 1 iain users    45 2008-06-14 22:11 device.map
-rwxrwxrwx 1 iain users  6301 2009-01-20 01:06 menu.lst
-rwxrwxrwx 1 iain users  6301 2009-01-19 23:24 menu.lst~
-rwxrwxrwx 1 iain users  6098 2009-01-09 01:29 menu.lst.bak

=========================== sda6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=42f61c87-42b0-478d-975b-019ae5091760 ro

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=42f61c87-42b0-478d-975b-019ae5091760 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=42f61c87-42b0-478d-975b-019ae5091760 ro  single

initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST


# This is a divider, added to separate the menu items below from the Debian

# ones.

title		Other operating systems:

root



# This entry automatically added by the Debian installer for a non-linux OS

# on /dev/sda2

title		Microsoft Windows XP Professional

root		(hd0,1)

savedefault

chainloader	+1


=============================== sda6/etc/fstab: ===============================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc        defaults    0   0
# Ubuntu
/dev/sda6     /               ext3        defaults,errors=remount-ro,relatime    0   1
# Swap
/dev/sda7      none            swap        sw          0   0
# ACER
/dev/sda2       /media/ACER       vfat         defaults,user,exec,uid=1000,gid=100,umask=000      0   0
# ACERDATA
/dev/sda5       /media/ACERDATA       vfat         defaults,user,exec,uid=1000,gid=100,umask=000      0   0


================================== sda6/boot: ==================================

total 11912
drwxr-xr-x  3 root root    4096 2009-01-20 13:14 .
drwxr-xr-x 22 root root    4096 2009-01-20 11:11 ..
-rw-r--r--  1 root root  507665 2008-11-20 23:46 abi-2.6.27-9-generic
-rw-r--r--  1 root root   91364 2008-11-20 23:46 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2009-01-20 13:14 grub
-rw-r--r--  1 root root 8139015 2009-01-20 11:08 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 21:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-11-20 23:46 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1073 2008-11-20 23:48 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2244304 2008-11-20 23:46 vmlinuz-2.6.27-9-generic

=============================== sda6/boot/grub: ===============================

total 328
drwxr-xr-x 2 root root   4096 2009-01-20 13:14 .
drwxr-xr-x 3 root root   4096 2009-01-20 13:14 ..
-rwxr-xr-x 1 root root    191 2009-01-19 23:22 default
-rwxr-xr-x 1 root root     45 2009-01-19 23:22 device.map
-rwxr-xr-x 1 root root   8056 2009-01-19 23:24 e2fs_stage1_5
-rwxr-xr-x 1 root root   7904 2009-01-19 23:24 fat_stage1_5
-rwxr-xr-x 1 root root   8608 2009-01-19 23:24 jfs_stage1_5
-rwxr-xr-x 1 root root   4544 2009-01-20 13:14 menu.lst
-rw-r--r-- 1 root root   4544 2009-01-20 13:14 menu.lst~
-rwxr-xr-x 1 root root   6098 2009-01-19 23:22 menu.lst.bak
-rwxr-xr-x 1 root root   7324 2009-01-19 23:24 minix_stage1_5
-rwxr-xr-x 1 root root   9632 2009-01-19 23:24 reiserfs_stage1_5
-rwxr-xr-x 1 root root    512 2009-01-19 23:24 stage1
-rwxr-xr-x 1 root root 108356 2009-01-19 23:24 stage2
-rwxr-xr-x 1 root root 108356 2009-01-19 23:24 stage2_eltorito
-rwxr-xr-x 1 root root   9276 2009-01-19 23:24 xfs_stage1_5

=========================== Unknown MBRs or Boot Sectors =======================

Unknown MBR on /dev/sda

00000000  31 c0 8e d0 bc 00 7c fb  50 07 50 1f fc be 1b 7c  |1.....|.P.P....||
00000010  bf 1b 06 50 57 b9 e5 01  f3 a4 cb bf 05 00 31 c0  |...PW.........1.|
00000020  b2 80 cd 13 73 07 4f 74  02 eb f3 eb fe bd 79 07  |....s.Ot......y.|
00000030  80 7e 00 5a 74 41 f8 b8  10 96 b3 15 cd 15 72 16  |.~.ZtA........r.|
00000040  81 f9 00 00 74 2e f8 b8  10 96 b3 16 cd 15 72 06  |....t.........r.|
00000050  81 f9 01 00 74 1e f8 b8  10 96 b3 18 cd 15 72 06  |....t.........r.|
00000060  81 f9 01 00 75 11 f8 b8  81 ca cd 15 80 fa 01 74  |....u..........t|
00000070  06 e9 68 00 e9 65 00 bd  be 07 66 8b 5e 08 60 68  |..h..e....f.^.`h|
00000080  00 00 68 00 00 66 53 68  00 00 68 00 7c 68 01 00  |..h..fSh..h.|h..|
00000090  68 10 00 b4 42 b2 80 89  e6 cd 13 61 61 73 0b 4f  |h...B......aas.O|
000000a0  74 08 30 e4 b2 80 cd 13  eb cd e8 7f 00 bd be 7f  |t.0.............|
000000b0  c6 46 00 80 c6 46 10 00  c6 46 04 0b a0 7a 7f a8  |.F...F...F...z..|
000000c0  04 74 04 80 4e 24 10 a0  7a 7f a8 08 74 04 80 4e  |.t..N$..z...t..N|
000000d0  34 10 e8 7a 00 68 00 00  68 00 7c cb bd be 07 66  |4..z.h..h.|....f|
000000e0  8b 5e 18 60 68 00 00 68  00 00 66 53 68 00 00 68  |.^.`h..h..fSh..h|
000000f0  00 7c 68 01 00 68 10 00  b4 42 b2 80 89 e6 cd 13  |.|h..h...B......|
00000100  61 61 73 0b 4f 74 08 30  e4 b2 80 cd 13 eb cd e8  |aas.Ot.0........|
00000110  1a 00 bd be 7f 80 7e 04  12 74 ba c6 46 00 00 c6  |......~..t..F...|
00000120  46 10 80 c6 46 04 12 e8  25 00 eb a9 bf 05 00 31  |F...F...%......1|
00000130  c0 8e c0 bb 00 7e b8 01  02 b5 00 b1 01 b6 00 b2  |.....~..........|
00000140  80 cd 13 73 09 4f 74 06  30 e4 cd 0d eb de c3 bf  |...s.Ot.0.......|
00000150  05 00 31 c0 8e c0 bb 00  7e b8 01 03 b5 00 b1 01  |..1.....~.......|
00000160  b6 00 b2 80 cd 13 73 09  4f 74 06 30 e4 cd 0d eb  |......s.Ot.0....|
00000170  de c3 00 00 41 63 65 72  0c 33 00 00 73 79 73 74  |....Acer.3..syst|
00000180  65 6d 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |em..............|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  00 00 00 00 00 00 00 00  fd 34 fe 34 00 00 00 01  |.........4.4....|
000001c0  01 00 12 fe 7f 7e 3f 00  00 00 80 e2 5d 00 80 00  |.....~?.....]...|
000001d0  41 7f 0c fe ff ff bf e2  5d 00 30 4e 7f 02 00 fe  |A.......].0N....|
000001e0  ff ff 0f fe ff ff ef 30  dd 02 c1 1a 1c 0b 00 00  |.......0........|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

No errors were reported.
```

---

### Post by caljohnsmith on 2009-01-20
Sure, you can call me Cal if you want, or simply John is OK too. :) About your booting conundrum, unfortunately you have a problem that needs to be corrected first before we can go any further:
[QUOTE=IainPurdie]```
fdisk -lu /dev/sda:
[COLOR="Red"]omitting empty partition (5)[/COLOR]

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x34fe34fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63     6152894     3076416   12  Compaq diagnostics
/dev/sda2   *     6152895    48050414    20948760    c  W95 FAT32 (LBA)
/dev/sda3        48050415   234441647    93195616+   f  W95 Ext'd (LBA)
/dev/sda5        48050478   199013219    75481371    b  W95 FAT32
/dev/sda6       199013283   231303869    16145293+  83  Linux
/dev/sda7       231303933   234441647     1568857+  82  Linux swap / Solaris
```[/QUOTE]
As highlighted above, any time you get an "omitting empty partition(X)" error from fdisk, that's unfortunately a sure sign your partition table is corrupt. In your case, since you don't have any overlapping partitions, most likely the cause is that one of the EBRs (Extended Boot Records) points to another EBR that doesn't exist any more (the EBRs are associated with your logical partitions). But the good news is that problem is usually easy to fix, so how about doing the following command:
```
sudo fdisk /dev/sda
```
And then simply type "w" at the fdisk prompt so that fdisk rewrites your partition table with the original partition table, except that fdisk will not include the false EBR reference. Next reboot, and please post the output of:
```
sudo fdisk -lu
sudo parted /dev/sda print
```
And if the fdisk command does not give you the "omitting empty partition(5)" error any more, proceed with:
```
sudo grub
grub> root (hd0,5)
grub> setup (hd0)
grub> quit

```
And please post the output prior to doing "quit". Then reboot, and let me know how far you get. We can work from there. :)

---

### Post by IainPurdie on 2009-01-20
Looking good! I think the error would have been due to all the messing I did with partitions to create the swap space and resize/move everything around. In fairness, with all the b*ggering about, I'm surprised there was only one minor error...

Booted up just now and Grub for the Intrepid install came up. I checked the XP link and it takes me to Windows' usual bootloader, where the Wubi link still exists - and is now safe to remove.

All seems incredibly hunky-dory!

Details you asked for posted below, but I think everything's sorted now (at least related to this problem... got another couple of unrelated niggles).

Thanks a *lot*! One pint earned and owed. Or a coffee is we're staying on-theme for the board ;)

```
FDISK:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x34fe34fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63     6152894     3076416   12  Compaq diagnostics
/dev/sda2   *     6152895    48050414    20948760    c  W95 FAT32 (LBA)
/dev/sda3        48050415   234441647    93195616+   f  W95 Ext'd (LBA)
/dev/sda5        48050478   199013219    75481371    b  W95 FAT32
/dev/sda6       199013283   231303869    16145293+  83  Linux
/dev/sda7       231303933   234441647     1568857+  82  Linux swap / Solaris

PARTED:

Model: ATA SAMSUNG HM121HC (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags    
 1      32.3kB  3150MB  3150MB  primary   fat32                 
 2      3150MB  24.6GB  21.5GB  primary   fat32        boot, lba
 3      24.6GB  120GB   95.4GB  extended               lba      
 5      24.6GB  102GB   77.3GB  logical   fat32                 
 6      102GB   118GB   16.5GB  logical   ext3                  
 7      118GB   120GB   1607MB  logical   linux-swap            

GRUB SETUP:

Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,5)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

```

---

### Post by caljohnsmith on 2009-01-20
Great, looks like you're in business. Cheers and have fun with Windows and Ubuntu. :)

---

### Post by Ammammata on 2009-01-24
> **caljohnsmith said:**
> In order to get a clearer picture of your setup, how about downloading the Boot Info Script to your Ubuntu desktop, open a terminal (cut)

Hello. It looks like I have a similar problem :(
I ran the script but found anything strange.

Anyway, here it is (sorry for some italian messages inside):

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /ubuntu/disks/boot/grub/menu.lst /boot.ini /ntldr 
                       /NTDETECT.COM /wubildr.mbr /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/disks /ubuntu/disks/boot/ 
                       /ubuntu/disks/boot/grub /ubuntu/disks/boot/grub

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       swap

sdb3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disco /dev/sda: 80.0 GB, 80060424192 byte
255 testine, 63 settori/tracce, 9733 cilindri, totale 156368016 settori
Unità = settori di 1 * 512 = 512 byte
Identificativo disco: 0x914083d9

/dev/sda1     *           63  156,344,579  156,344,517   7 HPFS/NTFS

Drive sdb: _____________________________________________________________________

Disco /dev/sdb: 81.9 GB, 81964302336 byte
255 testine, 63 settori/tracce, 9964 cilindri, totale 160086528 settori
Unità = settori di 1 * 512 = 512 byte
Identificativo disco: 0xe627e627

/dev/sdb1     *           63   81,931,499   81,931,437   7 HPFS/NTFS
/dev/sdb2         81,931,500   84,036,014    2,104,515  82 Linux swap / Solaris
/dev/sdb3         84,036,015  160,071,659   76,035,645  83 Linux

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="3E90B32C90B2EA13" LABEL="System" TYPE="ntfs" 
/dev/sdb1: UUID="1CBCF558BCF52D40" LABEL="test" TYPE="ntfs" 
/dev/sdb2: TYPE="swap" UUID="a8a17198-e876-416b-8bd1-0b31c574737b" 
/dev/sdb3: UUID="1647d431-17aa-48c3-a831-0a4d5c8d1d93" SEC_TYPE="ext2" TYPE="ext3" 
/dev/loop0: UUID="b9d9c01b-98b9-4dac-b69d-de29e9e09fb0" TYPE="ext3" 

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
/dev/sda1 on /host type fuseblk (rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
/host/ubuntu/disks/boot on /boot type none (rw,bind)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/giovanni/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=giovanni)

==================== sda1/ubuntu/disks/boot/grub/menu.lst: ====================

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
# kopt=root=UUID=3E90B32C90B2EA13 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=3E90B32C90B2EA13 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=3E90B32C90B2EA13 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=3E90B32C90B2EA13 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=3E90B32C90B2EA13 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
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
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
chainloader	+1



title Ubuntu-on-/dev/sdb3
root (hd1,2)
configfile /boot/grub/menu.lst



================================ sda1/boot.ini: ================================

[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn

c:\wubildr.mbr="Ubuntu"


============================== sda1/ubuntu/disks: ==============================

totale 9765636
drwxrwxrwx 1 root root          0 2009-01-07 12:44 .
drwxrwxrwx 1 root root       4096 2009-01-07 12:37 ..
drwxrwxrwx 1 root root       4096 2009-01-07 13:31 boot
-rwxrwxrwx 2 root root 9000000000 2009-01-22 23:20 root.disk
drwxrwxrwx 1 root root          0 2009-01-07 12:37 shared
-rwxrwxrwx 2 root root 1000000000 2009-01-07 12:47 swap.disk

=========================== sda1/ubuntu/disks/boot/: ===========================

totale 24240
drwxrwxrwx 1 root root    4096 2009-01-07 13:31 .
drwxrwxrwx 1 root root       0 2009-01-07 12:44 ..
-rwxrwxrwx 1 root root  507665 2008-11-04 22:00 abi-2.6.27-7-generic
-rwxrwxrwx 1 root root  507665 2008-11-21 00:46 abi-2.6.27-9-generic
-rwxrwxrwx 1 root root   91364 2008-11-04 22:00 config-2.6.27-7-generic
-rwxrwxrwx 1 root root   91364 2008-11-21 00:46 config-2.6.27-9-generic
drwxrwxrwx 1 root root       0 2009-01-07 13:31 grub
-rwxrwxrwx 1 root root 8459139 2009-01-07 13:30 initrd.img-2.6.27-7-generic
-rwxrwxrwx 1 root root 8459757 2009-01-07 13:31 initrd.img-2.6.27-9-generic
-rwxrwxrwx 1 root root  124152 2008-09-11 22:11 memtest86+.bin
-rwxrwxrwx 1 root root 1029585 2008-11-04 22:00 System.map-2.6.27-7-generic
-rwxrwxrwx 1 root root 1029585 2008-11-21 00:46 System.map-2.6.27-9-generic
-rwxrwxrwx 1 root root    1073 2008-11-04 22:02 vmcoreinfo-2.6.27-7-generic
-rwxrwxrwx 1 root root    1073 2008-11-21 00:48 vmcoreinfo-2.6.27-9-generic
-rwxrwxrwx 1 root root 2244464 2008-11-04 22:00 vmlinuz-2.6.27-7-generic
-rwxrwxrwx 1 root root 2244304 2008-11-21 00:46 vmlinuz-2.6.27-9-generic

========================= sda1/ubuntu/disks/boot/grub: =========================

totale 21
drwxrwxrwx 1 root root    0 2009-01-07 13:31 .
drwxrwxrwx 1 root root 4096 2009-01-07 13:31 ..
-rwxrwxrwx 1 root root  191 2009-01-07 12:58 default
-rwxrwxrwx 1 root root   30 2009-01-07 12:58 device.map
-rwxrwxrwx 1 root root 5152 2009-01-22 22:43 menu.lst
-rwxrwxrwx 1 root root 4994 2009-01-07 13:31 menu.lst~

========================= sda1/ubuntu/disks/boot/grub: =========================

totale 21
drwxrwxrwx 1 root root    0 2009-01-07 13:31 .
drwxrwxrwx 1 root root 4096 2009-01-07 13:31 ..
-rwxrwxrwx 1 root root  191 2009-01-07 12:58 default
-rwxrwxrwx 1 root root   30 2009-01-07 12:58 device.map
-rwxrwxrwx 1 root root 5152 2009-01-22 22:43 menu.lst
-rwxrwxrwx 1 root root 4994 2009-01-07 13:31 menu.lst~

=================== sda1: Location  of files loaded by Grub: ===================


   2.3GB: ubuntu/disks/boot/grub/menu.lst
   5.2GB: ubuntu/disks/boot/initrd.img-2.6.27-7-generic
   5.2GB: ubuntu/disks/boot/initrd.img-2.6.27-9-generic
   4.8GB: ubuntu/disks/boot/vmlinuz-2.6.27-7-generic
   5.0GB: ubuntu/disks/boot/vmlinuz-2.6.27-9-generic

=========================== sdb3/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=1647d431-17aa-48c3-a831-0a4d5c8d1d93  ro ROOTFLAGS=syncio

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=1647d431-17aa-48c3-a831-0a4d5c8d1d93  ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=1647d431-17aa-48c3-a831-0a4d5c8d1d93  ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1647d431-17aa-48c3-a831-0a4d5c8d1d93  ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1647d431-17aa-48c3-a831-0a4d5c8d1d93  ro ROOTFLAGS=syncio  single
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
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
chainloader	+1


# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


title Windows
root (hd0,0)
makeactive
chainloader +1
boot


title Microsoft Windows XP Home Edition
root (hd0,0)
makeactive
chainloader +1
boot


=============================== sdb3/etc/fstab: ===============================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc        defaults    0   0
# /dev/sdb3
UUID=1647d431-17aa-48c3-a831-0a4d5c8d1d93     /               ext3        defaults,errors=remount-ro    0   1
# /dev/sda1
UUID=3E90B32C90B2EA13       /media/drv0       ntfs-3g         defaults      0   0


# /dev/sdb2
UUID=a8a17198-e876-416b-8bd1-0b31c574737b      none            swap        sw          0   0


================================== sdb3/boot: ==================================

totale 24056
drwxr-xr-x  3 root root    4096 2009-01-22 22:43 .
drwxr-xr-x 21 root root    4096 2009-01-07 13:30 ..
-rwxr-xr-x  1 root root  507665 2009-01-22 22:41 abi-2.6.27-7-generic
-rwxr-xr-x  1 root root  507665 2009-01-22 22:41 abi-2.6.27-9-generic
-rwxr-xr-x  1 root root   91364 2009-01-22 22:41 config-2.6.27-7-generic
-rwxr-xr-x  1 root root   91364 2009-01-22 22:41 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2009-01-22 22:43 grub
-rwxr-xr-x  1 root root 8459139 2009-01-22 22:41 initrd.img-2.6.27-7-generic
-rwxr-xr-x  1 root root 8198422 2009-01-22 22:43 initrd.img-2.6.27-9-generic
-rwxr-xr-x  1 root root  124152 2009-01-22 22:41 memtest86+.bin
-rwxr-xr-x  1 root root 1029585 2009-01-22 22:41 System.map-2.6.27-7-generic
-rwxr-xr-x  1 root root 1029585 2009-01-22 22:41 System.map-2.6.27-9-generic
-rwxr-xr-x  1 root root    1073 2009-01-22 22:41 vmcoreinfo-2.6.27-7-generic
-rwxr-xr-x  1 root root    1073 2009-01-22 22:41 vmcoreinfo-2.6.27-9-generic
-rwxr-xr-x  1 root root 2244464 2009-01-22 22:41 vmlinuz-2.6.27-7-generic
-rwxr-xr-x  1 root root 2244304 2009-01-22 22:41 vmlinuz-2.6.27-9-generic

=============================== sdb3/boot/grub: ===============================

totale 344
drwxr-xr-x 2 root root   4096 2009-01-22 22:43 .
drwxr-xr-x 3 root root   4096 2009-01-22 22:43 ..
-rwxr-xr-x 1 root root    191 2009-01-22 22:41 default
-rwxr-xr-x 1 root root     47 2009-01-22 22:43 device.map
-rwxr-xr-x 1 root root   8108 2009-01-22 22:43 e2fs_stage1_5
-rwxr-xr-x 1 root root   7856 2009-01-22 22:43 fat_stage1_5
-rwxr-xr-x 1 root root   8712 2009-01-22 22:43 jfs_stage1_5
-rwxr-xr-x 1 root root   5307 2009-01-22 22:43 menu.lst
-rwxr-xr-x 1 root root   4994 2009-01-22 22:41 menu.lst~
-rwxr-xr-x 1 root root   7352 2009-01-22 22:43 minix_stage1_5
-rwxr-xr-x 1 root root   9756 2009-01-22 22:43 reiserfs_stage1_5
-rwxr-xr-x 1 root root    512 2009-01-22 22:43 stage1
-rwxr-xr-x 1 root root 121460 2009-01-22 22:43 stage2
-rwxr-xr-x 1 root root 121460 2009-01-22 22:43 stage2_eltorito
-rwxr-xr-x 1 root root   9556 2009-01-22 22:43 xfs_stage1_5

=================== sdb3: Location  of files loaded by Grub: ===================


  55.6GB: boot/grub/menu.lst
  55.6GB: boot/grub/stage2
  55.5GB: boot/initrd.img-2.6.27-7-generic
  55.5GB: boot/initrd.img-2.6.27-9-generic
  55.5GB: boot/vmlinuz-2.6.27-7-generic
  55.5GB: boot/vmlinuz-2.6.27-9-generic
  55.5GB: initrd.img
  55.5GB: initrd.img.old
  55.5GB: vmlinuz
  55.5GB: vmlinuz.old

=============================== StdErr Messages: ===============================

No errors were reported.

```

Now the description of my problem:

In the first boot menu I select Ubuntu (that's wubi actually)
I press Esc to get the second menu, here I select
Ubuntu-on-/dev/sdb3

I get another boot menu and I select the 1st:
Ubuntu 8.10, kernel 2.6.27-9-generic

It says Booting Ubuntu 8.10 etc etc then stops with the following message:

```
The current working directory is /ubuntu/disks
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=1647d431-17aa-48c3-a831-0a4d5c8d1d93 ro ROOTFLAGS=syncio quiet splash

Error 15: file not found

Press any key...


```

please help, thankyou

If I can't sort out, is not a true problem: ubuntu is fresh install (just added OpenOffice3) so I can reinstall the whole matter

---

### Post by IainPurdie on 2009-01-24
In the both "menu.lst" files, you seem to have a problem. The "Root" lines don't have any information on which partition the system should be booting from. Your lines all look like:

```
root		()/ubuntu/disks
```

Whereas they should look similar to:

```
root		(0,1)/ubuntu/disks
```

Note that the numbers in the brackets may not need to be (0,1) as they will vary from system to system. I note that this fault is also in your WUBI install's menu.lst file so I'm surprised that version boots (although I'm an amateur!).

What I'd recommend doing, is if your WUBI version does boot up, get into that. Then I assume you can see the ext3 partition that your "full" version is installed on? Navigate on that and:

sudo gedit /sdb3/boot/grub/menu.lst

You may need to mount this drive first to access it.

Locate the "Root" lines and enter the correct numbers between the brackets. I *think* this should be (1,2) as you have two drives (sda1 and sdb1) so the first figure is 1 (counting from zero). Likewise, three partitions on the second drive, so counting from zero gives 0,1,*2* for the second digit.

Hope that makes sense. And is right...

---

### Post by caljohnsmith on 2009-01-24
**Ammammata**, did you manually edit your sdb3 Ubuntu's menu.lst to be "Wubi" style? It looks like you did. Your sdb3 Ubuntu install appears to be a standard, full install, not a Wubi install, so the syntax in the menu.lst will be a little different. How about from your Live CD, try the following:
```
sudo mkdir /mnt/sda1 /mnt/sdb3
sudo mount /dev/sda1 /mnt/sda1
sudo mount /dev/sdb3 /mnt/sdb3
gksudo gedit /mnt/sda1/ubuntu/disks/boot/grub/menu.lst
```
and change your "Ubuntu on /dev/sdb3" entry to:
```
title Ubuntu on /dev/sdb3
rootnoverify (hd1)
map (hd1) (hd0)
map (hd0) (hd1)
chainloader +1
```
Next open up your sdb3 menu.lst:
```
gksudo gedit /mnt/sdb3/boot/grub/menu.lst
```
And change the Ubuntu entries by replacing the "root" line with a "uuid" line, and also delete the "ROOTFLAGS=syncio" highlighted in red:
```
title		Ubuntu 8.10, kernel 2.6.27-9-generic
[COLOR="Blue"]uuid            1647d431-17aa-48c3-a831-0a4d5c8d1d93[/COLOR]
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=1647d431-17aa-48c3-a831-0a4d5c8d1d93  ro [COLOR="Red"]ROOTFLAGS=syncio[/COLOR] quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
```
Then reboot, and let me know how far you get when booting "Ubuntu on /dev/sdb3". We can work from there if you want.

---

