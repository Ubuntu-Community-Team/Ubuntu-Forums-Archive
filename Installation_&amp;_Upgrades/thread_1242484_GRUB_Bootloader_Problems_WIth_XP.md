---
title: "GRUB Bootloader Problems WIth XP"
date: 2009-08-17
forum: Installation &amp; Upgrades
---

### Post by firemansam87 on 2009-08-17
Been google searching, but no success... well very little.

I have two separate HDDs installed in my PC, 250gig with XP which I have been using and an 80gig with Ubuntu.

Now the current situation I am in is that I have Ubuntu installed and working, but it is not recognizing the XP HDD. I have tried adding it to the menu.lst in grub folder with no success. I have tried different variations of root with no success.

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=68ae7b91-1829-4a7f-9e48-caf5700ece60 ro quiet splash
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=68ae7b91-1829-4a7f-9e48-caf5700ece60 ro single
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 8.04.3 LTS, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

title		Windows XP Professional
root		(hd1,0)
savedefault
makeactive
chainloader	+1
map (hd0) (hd1)
map (hd1) (hd0)

Found the above on forums, but I am not sure if it is exactly meant for my situation.

XP is in SATA slot 0 and Ubuntu in 1.

Samuel

---

### Post by Dithers on 2009-08-17
install the NTFS configuration tool in add/remove
it makes it mush easier to access NTFS harddrives

after you install the tool and find the drive it will take a reboot before it is accessible

---

### Post by firemansam87 on 2009-08-17
I am getting a error when trying to select XP to boot, "NTLDR is missing"

---

### Post by dstew on 2009-08-17
Try moving the map statements ahead of the chainload statement, like this:```
title Windows XP Professional
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```If that doesn't work, then enter the command```
sudo fdisk -l
```and post the output to the forum.

---

### Post by fela on 2009-08-17
Did you say that XP is in sata0, Ubuntu in sata1? In which case the grub entry for XP would be:

```
root (hd0,0)
```

Assuming that it's on the first partition.

Could you please post the output of

```
fdisk -l
```

That's a letter l not a number 1 by the way ;)

EDIT: you'll probably need to put sudo in front of that command by the way.

That will make everything much clearer. I take it the XP partition is NTFS?

Basically in GRUB, hd0,0 means sda1/hda1, hd1,1 means sdb2/hdb2, you get the idea.

I've never actually needed the map statements in my grub entries, I'm not sure what they're for and just from my experience with multiple boot drives and multiple partitions, they're not necessary.

Everything will be much clearer once I see the output of fdisk -l though ;)

---

### Post by firemansam87 on 2009-08-17
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd95fd95f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30400   244187968+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x961daa4e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          61      489951   82  Linux swap / Solaris
/dev/sdb2   *          62        9729    77658210   83  Linux
samuel@samuel:~$

---

### Post by fela on 2009-08-17
Your XP partition is on /dev/sda1. Therefore you need to get rid of the map bits in the menu.lst and change the root (hdx,x) to root (hd0,0). That should work anyway :)

EDIT: I'm surprised the ubuntu entry works - surely it should be root (hd1,1)? If the boot partition is on /dev/sdb2. :confused:

---

### Post by firemansam87 on 2009-08-17
Error 13: Invalid or unsupported executable format

---

### Post by confused57 on 2009-08-17
> **firemansam87 said:**
> Error 13: Invalid or unsupported executable format

If you haven't already, try copying & pasting the entry dstew gave you into your /boot/grub/menu.lst, rather than typing it from scratch.

---

### Post by presence1960 on 2009-08-17
We are missing some pieces of info like is boot.ini & NTLDR actually installed to sda1. Let's get a clear look at that & all your setup & boot process. Boot into Ubuntu and come back here. Download the Boot Info Script 0.32 from my signature line to the desktop. Once on desktop open a terminal & run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
```
This will create a RESULTS.txt file on the desktop. paste the entire contents of that file here, then highlight all the text & click the # sign on the toolbar to place code tags around the text.

---

### Post by presence1960 on 2009-08-17
> **fela said:**
> Your XP partition is on /dev/sda1. Therefore you need to get rid of the map bits in the menu.lst and change the root (hdx,x) to root (hd0,0). That should work anyway :)

EDIT: I'm surprised the ubuntu entry works - surely it should be root (hd1,1)? If the boot partition is on /dev/sdb2. :confused:

(hd0,1) works to boot Ubuntu because even though it is sdb2, the sdb drive is set to boot first in BIOS. When using root or rootnoverify to designate partitions it is the BIOS order that you must use. This does cause some confusion and that is probably why in 9.04 UUID was used for these lines. Unfortunately for chainloading that does not help, you must still use the BIOS hard disk order.

---

### Post by firemansam87 on 2009-08-18
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #3 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 1. But according to the info from fdisk, 
                       sda1 starts at sector 63. According to the info in the 
                       boot sector, sda1 has 0 sectors.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.3 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd95fd95f

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   488,375,999   488,375,937   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x961daa4e

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63       979,964       979,902  82 Linux swap / Solaris
/dev/sdb2             979,965   156,296,384   155,316,420  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: SEC_TYPE="msdos" UUID="0000-0000" TYPE="vfat" 
/dev/sdb1: TYPE="swap" UUID="2291d68e-26c5-456a-90bf-4cab457dd601" 
/dev/sdb2: UUID="68ae7b91-1829-4a7f-9e48-caf5700ece60" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sdb2 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-24-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/samuel/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=samuel)


=========================== sdb2/boot/grub/menu.lst: ===========================

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
timeout        30

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=68ae7b91-1829-4a7f-9e48-caf5700ece60 ro

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

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=68ae7b91-1829-4a7f-9e48-caf5700ece60 ro quiet splash
initrd        /boot/initrd.img-2.6.24-24-generic
quiet

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=68ae7b91-1829-4a7f-9e48-caf5700ece60 ro single
initrd        /boot/initrd.img-2.6.24-24-generic

title        Ubuntu 8.04.3 LTS, memtest86+
root        (hd0,1)
kernel        /boot/memtest86+.bin
quiet

title Windows XP Professional
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sdb2 :
UUID=68ae7b91-1829-4a7f-9e48-caf5700ece60 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sdb1 :
UUID=2291d68e-26c5-456a-90bf-4cab457dd601 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0

=================== sdb2: Location of files loaded by Grub: ===================


  71.9GB: boot/grub/menu.lst
  72.0GB: boot/grub/stage2
  71.9GB: boot/initrd.img-2.6.24-24-generic
  72.0GB: boot/vmlinuz-2.6.24-24-generic
  71.9GB: initrd.img
  72.0GB: vmlinuz
```

Confused57, no it did not work.

---

### Post by presence1960 on 2009-08-18
Your sdb drive is set in BIOS as first hard disk boot which is why root (hd0,1) works for Ubuntu. But you have a problem with windows, see here:

```
sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 1. But according to the info from fdisk, 
                       sda1 starts at sector 63. According to the info in the 
                       boot sector, sda1 has 0 sectors.
    [COLOR="Red"]Operating System:  
    Boot files/dirs:  [/COLOR] 

```

You have no operating system or boot files listed on sda1 which is where your windows OS is. it will never boot. You can try restoring the windows bootloader to MBR of sda. it is a 2 step process:

1. Boot your machine and go into BIOS. Set sda (250GB) to first in hard disk boot order. This is very important because windows will always write it's bootloader to the first disk that boots. if you fail to take this step it will try to write to sdb- you don't want that.

2. Boot from the windows installation CD and do [this]("http://ubuntuforums.org/showthread.php?t=1014708") to restore windows bootloader. When complete reboot and see if windows boots. it should boot directly into windows. Then reboot one more time and go into BIOS and set sdb as first disk in hard disk boot order. This will bring up GRUB when booting. try your windows entry in the GRUB menu. The entry looks good. personally I don't use savedefault or makeactive in the windows entry of menu.lst but that should work. Let us know what happens.

You may have to wind up reinstalling windows if restoring the bootloader does not work. You want to do the same thing in BIOS when reinstalling windows which is set the sda drive as first hard disk to boot!

---

### Post by firemansam87 on 2009-08-19
I tried fixboot and fixmbr again, after I fixed the HDD boot order in the BIOS.

NTLDR Missing...

I copied ntldr via the cd and tried booting with no success.

I have gone to the install section of the cd to see if I can reinstall the system and keep my files, but I cannot find the bit where you just install the system. And according to the HDDs displayed C drive has 2mb free and is FAT file system. Making me think its all gone corrupt. What do you think? Just reinstall a new copy of XP?

EDIT--

Thanks for your help, but I think I have screwed it up somehow. I tried sticking it into my Mac and NTFS-3g couldn't read it. It said it was Master Boot Record, so I think it installed something where it shouldn't have gone.
I have kept a backup of various things so it is no big loss.

I will reinstall a fresh copy and keep the HDD configuration as is, SATA0 for the XP and SATA1 for the Ubuntu drive. And have 0 as the master boot HDD set in the BIOS.

Gotta love technology!

Thanks again, you have been very helpful!!!

Samuel

---

