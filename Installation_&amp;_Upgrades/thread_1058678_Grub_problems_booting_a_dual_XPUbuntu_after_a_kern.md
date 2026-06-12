---
title: "Grub problems booting a dual XP/Ubuntu after a kernel upgrade"
date: 2009-02-03
forum: Installation &amp; Upgrades
---

### Post by plesset on 2009-02-03
At work I have a dual boot with XP first (NTFS, sda1), then Ubuntu (sda2) and a shared FAT32 partition (sda5), which is used to share my music between the two systems. The machines starts from the MBR and from there I can pick either Window$ or Ubuntu. Basically I followed [http://www.matthewjmiller.net/howtos...x-and-windows/](http://www.matthewjmiller.net/howtos...x-and-windows/) and it had worked fine for me. But after the last upgrades, which included a kernel upgrade, I can now longer boot the Ubuntu. It simply hangs the GRUB printed in the upper left hand corner.

I have looked at my menu.lst and fstab files (but I'm certainly no expert) which I can still access by assigning a drive letter from Explorer(!) and at least the UUID number seem the same. Beyond that any ideas are most welcomed.

- Andri


..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..
% menu.lst

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=UUID=2f7085a8-48d1-4bb5-8c86-64e8c3ada4c0 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=2f7085a8-48d1-4bb5-8c86-64e8c3ada4c0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=2f7085a8-48d1-4bb5-8c86-64e8c3ada4c0 ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, kernel 2.6.24-22-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=2f7085a8-48d1-4bb5-8c86-64e8c3ada4c0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=2f7085a8-48d1-4bb5-8c86-64e8c3ada4c0 ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.2, kernel 2.6.24-21-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=2f7085a8-48d1-4bb5-8c86-64e8c3ada4c0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=2f7085a8-48d1-4bb5-8c86-64e8c3ada4c0 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2f7085a8-48d1-4bb5-8c86-64e8c3ada4c0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2f7085a8-48d1-4bb5-8c86-64e8c3ada4c0 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.2, kernel 2.6.24-18-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=2f7085a8-48d1-4bb5-8c86-64e8c3ada4c0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=2f7085a8-48d1-4bb5-8c86-64e8c3ada4c0 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04.2, kernel 2.6.24-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2f7085a8-48d1-4bb5-8c86-64e8c3ada4c0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2f7085a8-48d1-4bb5-8c86-64e8c3ada4c0 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.2, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2f7085a8-48d1-4bb5-8c86-64e8c3ada4c0 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2f7085a8-48d1-4bb5-8c86-64e8c3ada4c0 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04.2, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=2f7085a8-48d1-4bb5-8c86-64e8c3ada4c0 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=2f7085a8-48d1-4bb5-8c86-64e8c3ada4c0 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,1)
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
chainloader	+1

..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..


..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=2f7085a8-48d1-4bb5-8c86-64e8c3ada4c0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=403CC0833CC07586 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=46D2-F1D6  /osshare        vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=0cd9a3b7-5d6a-425a-b744-81d02b5a85b1 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..%..

---

### Post by caljohnsmith on 2009-02-03
So do you get the word "GRUB" on your screen before seeing the Grub menu on start up, or after you get the menu and select to boot Ubuntu? I think it would help to get more info about your setup, so how about booting your Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by plesset on 2009-02-03
> So do you get the word "GRUB" on your screen before seeing the Grub menu on start up, or after you get the menu and select to boot Ubuntu?

When I boot, I get an option to pick either XP or ubuntu. If I choose XP it continues on as normal. If I choose Ubuntu I get the GRUB .. in the upper left hand corner. When I installed the Ubuntu partition originally, I added a line in the boot.ini in Window$ and there is also a ubuntu.bin there on my C:, generated by 

```
dd if=/dev/hda2 of=/mnt/osshare/ubuntu.bin bs=512 count=1
```

I ran the boot_info script ...

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     Grub in the file /ubuntu.bin looks at sector 251943703 
                       of the same hard drive for the stage2 file, but no 
                       stage2 files can be found at this location.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTLDR /NTDETECT.COM /ntdetect.com

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda2 and 
                       looks at sector 314956567 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #2 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda6 starts at sector 422927253.
    Boot file info:     Grub in the file /ubuntu.bin looks at sector 251943703 
                       of the same hard drive for the stage2 file, but no 
                       stage2 files can be found at this location.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x86f586f5

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   163,846,934   163,846,872   7 HPFS/NTFS
/dev/sda2         163,846,935   409,609,304   245,762,370  83 Linux
/dev/sda3         409,609,305   488,392,064    78,782,760   5 Extended
/dev/sda5         409,609,368   422,927,189    13,317,822  82 Linux swap / Solaris
/dev/sda6         422,927,253   488,392,064    65,464,812   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="403CC0833CC07586" TYPE="ntfs" 
/dev/sda2: UUID="2f7085a8-48d1-4bb5-8c86-64e8c3ada4c0" TYPE="ext3" 
/dev/sda5: UUID="0cd9a3b7-5d6a-425a-b744-81d02b5a85b1" TYPE="swap" 
/dev/sda6: UUID="46D2-F1D6" TYPE="vfat" 

=============================== "mount" output: ===============================

tmpfs on / type tmpfs (rw)
/dev/sr0 on /mnt/cdrom type iso9660 (ro,mode=0644)
/dev/loop0 on /mnt/livecd type squashfs (ro)
tmpfs on /mnt/memory type tmpfs (rw)
/proc on /proc type proc (rw,nosuid,nodev,noexec)
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec)
udev on /dev type tmpfs (rw,nosuid,size=10240k,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,gid=5,mode=620)
tmpfs on /lib/firmware type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw,noexec,nosuid,devmode=0664,devgid=85)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
securityfs on /sys/kernel/security type securityfs (rw,noexec,nosuid,nodev)
/dev/sda2 on /mnt/ubuntu type ext3 (rw)

================================ sda1/boot.ini: ================================

[boot loader]
timeout=10
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn
C:\ubuntu.bin="Ubuntu Linux"

=========================== sda2/boot/grub/menu.lst: ===========================

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=UUID=2f7085a8-48d1-4bb5-8c86-64e8c3ada4c0 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title		Ubuntu 8.04.2, kernel 2.6.24-22-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=2f7085a8-48d1-4bb5-8c86-64e8c3ada4c0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=2f7085a8-48d1-4bb5-8c86-64e8c3ada4c0 ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.2, kernel 2.6.24-21-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=2f7085a8-48d1-4bb5-8c86-64e8c3ada4c0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=2f7085a8-48d1-4bb5-8c86-64e8c3ada4c0 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2f7085a8-48d1-4bb5-8c86-64e8c3ada4c0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2f7085a8-48d1-4bb5-8c86-64e8c3ada4c0 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.2, kernel 2.6.24-18-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=2f7085a8-48d1-4bb5-8c86-64e8c3ada4c0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=2f7085a8-48d1-4bb5-8c86-64e8c3ada4c0 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04.2, kernel 2.6.24-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2f7085a8-48d1-4bb5-8c86-64e8c3ada4c0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2f7085a8-48d1-4bb5-8c86-64e8c3ada4c0 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.2, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2f7085a8-48d1-4bb5-8c86-64e8c3ada4c0 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2f7085a8-48d1-4bb5-8c86-64e8c3ada4c0 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04.2, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=2f7085a8-48d1-4bb5-8c86-64e8c3ada4c0 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=2f7085a8-48d1-4bb5-8c86-64e8c3ada4c0 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,1)
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
chainloader	+1


=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=2f7085a8-48d1-4bb5-8c86-64e8c3ada4c0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=403CC0833CC07586 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=46D2-F1D6  /osshare        vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=0cd9a3b7-5d6a-425a-b744-81d02b5a85b1 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

=================== sda2: Location of files loaded by Grub: ===================


 161.2GB: boot/grub/menu.lst
 161.2GB: boot/grub/stage2
 161.2GB: boot/initrd.img-2.6.20-16-generic
 161.3GB: boot/initrd.img-2.6.22-14-generic
 161.2GB: boot/initrd.img-2.6.22-14-generic.bak
 161.3GB: boot/initrd.img-2.6.24-16-generic
 161.2GB: boot/initrd.img-2.6.24-16-generic.bak
 161.3GB: boot/initrd.img-2.6.24-18-generic
 161.3GB: boot/initrd.img-2.6.24-18-generic.bak
 161.2GB: boot/initrd.img-2.6.24-19-generic
 161.2GB: boot/initrd.img-2.6.24-19-generic.bak
 161.2GB: boot/initrd.img-2.6.24-21-generic
 161.3GB: boot/initrd.img-2.6.24-21-generic.bak
 161.2GB: boot/initrd.img-2.6.24-22-generic
 161.3GB: boot/initrd.img-2.6.24-22-generic.bak
 161.3GB: boot/initrd.img-2.6.24-23-generic
 161.3GB: boot/initrd.img-2.6.24-23-generic.bak
 161.2GB: boot/vmlinuz-2.6.20-16-generic
 161.2GB: boot/vmlinuz-2.6.22-14-generic
 161.2GB: boot/vmlinuz-2.6.24-16-generic
 161.2GB: boot/vmlinuz-2.6.24-18-generic
 161.2GB: boot/vmlinuz-2.6.24-19-generic
 161.2GB: boot/vmlinuz-2.6.24-21-generic
 161.3GB: boot/vmlinuz-2.6.24-22-generic
 161.2GB: boot/vmlinuz-2.6.24-23-generic
 161.3GB: initrd.img
 161.2GB: initrd.img.old
 161.2GB: vmlinuz
 161.3GB: vmlinuz.old

=======Devices which don't seem to have a corresponding hard drive==============

 sdb .
 sdc .
 sdd .
 sde .

```

---

### Post by caljohnsmith on 2009-02-03
It looks like the problem is you need to copy the sda2 boot sector again, because your current ubuntu.bin file points to the wrong location for Grub's stage2 file. How about doing:
```
sudo dd if=/dev/[COLOR="Blue"]sda2[/COLOR] of=/mnt/osshare/ubuntu.bin bs=512 count=1
```
And use that ubuntu.bin file instead. Let me know how that goes.

---

### Post by plesset on 2009-02-04
Yes, that worked. I'm just a little bit confused with this stopped working all of the sudden like it did. I made the original ubuntu.bin file on Aug. 28th 2007 - and the drive setup hasn't changed since.

Thanks for the help,
- Andri

---

### Post by caljohnsmith on 2009-02-04
If your Grub was updated or if you ran "grub-install" yourself, that could have changed the physical location of Grub's stage2 file on your HDD, even though the stage2 file is still in your /boot/grub directory. That would have caused the problem you experienced, but I'm not sure what actually changed the physical location of your stage2 file. Anyway, glad to hear the problem is resolved. Cheers and enjoy Windows and Ubuntu. :)

---

