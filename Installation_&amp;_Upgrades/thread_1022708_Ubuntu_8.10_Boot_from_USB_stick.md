---
title: "Ubuntu 8.10 Boot from USB stick"
date: 2008-12-27
forum: Installation &amp; Upgrades
---

### Post by 5BallJuggler on 2008-12-27
I am trying to put a bootable version of Intrepid onto a "SanDisk cruzer 4Gb", i have it on now but am having some problems with the PC when i reboot.

After I made the bootable USB stick, Ubuntu asks to be restarted. I did this but the computer would not boot, it came up with "NTLDR is missing" i removed the USB stick and tried again with the same result. The only way to boot the PC was to alter the boot sequence in Bios so it looked at the Hard drive 2nd...after the CD drive

I copied the NTLDR file from my windows XP home disk into the i386 folder on my PC. this then allowed me to reboot from the USB (after changing Bios)

I then added Compiz-Fusion to the drive and a few other apps to allow me to do stuff on other PC's, but when I rebooted the same problem occurs. 

I'd like to understand what is the issue and what is the fix before I screw someone else's PC up.

I hope you can help

Phil

---

### Post by 5BallJuggler on 2008-12-27
Ok, i've still have the same issue, 

i made a back up of the No good file, but cannot send to the forum as it is an invalid file type, the size of the file is exactly the same as a good NTLDR file, 

i'm going to reboot onto the USB stick and see if i can determine when the file changes by checking the access time in the properties ie at start up or at shutdown.

---

### Post by 5BallJuggler on 2008-12-28
Ok, so i did what i said and still have the same problem, it also looks like the file does not get accessed. see screen shots:-

the 1st shows the file as it is on a fresh install
the 2nd shows the file as it was loaded into the i386 folder manually, it says it was accessed at 12:27.

i reboot my PC to the USB drive at 12:43, 

the 3rd shows the file has not been accessed at start up???????

when i rebooted into Ubuntu on my hard drive i checked the properties again, they had not changed, yet the PC would not boot up with out changing the BIOS.

I'm stuck now, really need some help.

Phil

---

### Post by arubislander on 2008-12-28
Hi,

Could you elaborate a little on how exactly you made the bootable usb? Did you use the 'Create a USB startup disk" from the menu or did you use another method?

And where exactly are you copying the NTLDR to?

---

### Post by 5BallJuggler on 2008-12-28
I used the option in the Ubuntu menus "System"~"administration"~"create a USB start up disk".

as for the "NTLDR" file it is stored in the C:/i386 folder on my XP Partition, to fix the issue i just need to copy straight from the XP installation disk and it starts working again, but only until i shutdown the PC after it has booted from the USB stick.

---

### Post by arubislander on 2008-12-28
Ok, that's clear.

You mentioned that you can reboot your PC from your harddrive without having to copy NTLDR if you change the boot sequence to
CD
Internal Hard drive

I am assuming that when you want to boot from USB you put that second, after CD, and the internal drive comes in third?

Do you by chance have other USB drives connected to your PC?

---

### Post by 5BallJuggler on 2008-12-28
> **arubislander said:**
> Ok, that's clear.

You mentioned that you can reboot your PC from your harddrive without having to copy NTLDR if you change the boot sequence to
CD
Internal Hard drive

I am assuming that when you want to boot from USB you put that second, after CD, and the internal drive comes in third?

Do you by chance have other USB drives connected to your PC?

you're right in your assumptions.

and I do have other USB devices connected:- 

USB sound card (edirol UA 25)
USB wireless Keyboard and mouse dongle
USB hard drive 500Gb Maxtor
USB hard drive 500Gb Freecom
USB hard drive 160Gb
USB Printer HP photosmart C5280

I think that's it...

---

### Post by arubislander on 2008-12-28
Could it then be that when you set your BIOS to try to boot from usb before the internal hd, that it is trying to boot from one of your other external usb drives (none of which are bootable I presume)?

---

### Post by 5BallJuggler on 2008-12-28
> **arubislander said:**
> Could it then be that when you set your BIOS to try to boot from usb before the internal hd, that it is trying to boot from one of your other external usb drives (none of which are bootable I presume)?

I suppose it is possible, but why would it always work the 1st time after i have replaced the "NTLDR" file in the i386 folder and then never again? i'm thinking it is something that Ubuntu is doing to the file, but I can't see how or indeed why.

The other drives are cabable of boot, and i did used to run Ubuntu from the 160Gb drive, but i don't anymore, 

when i boot up the system the error i get is 

NTLDR is missing

that's it, plain and simple. i check and the file is there, but it won't work until i replace it with one from the XP install disk

I'm a little confused.

---

### Post by arubislander on 2008-12-28
> **5BallJuggler said:**
> The other drives are cabable of boot, and i did used to run Ubuntu from the 160Gb drive, but i don't anymore, 

when i boot up the system the error i get is 

NTLDR is missing

that's it, plain and simple. i check and the file is there, but it won't work until i replace it with one from the XP install disk

I'm a little confused.

So am I... But you've mentioned that changing the boot sequence also gets you back in XP. Is this without copying the NTLDR?

If that is the case then I still think it's a case of trying to boot from a different drive than the internal hd. If that is the case then I suggest you leave the boot sequence in the BIOS alone and bring up the boot menu (ESC or F12?) at startup and then select your USB stick to boot from when you want to do that.

---

### Post by 5BallJuggler on 2008-12-28
> **arubislander said:**
> So am I... But you've mentioned that changing the boot sequence also gets you back in XP. Is this without copying the NTLDR?

If that is the case then I still think it's a case of trying to boot from a different drive than the internal hd. If that is the case then I suggest you leave the boot sequence in the BIOS alone and bring up the boot menu (ESC or F12?) at startup and then select your USB stick to boot from when you want to do that.

OK, tried a couple of things.

1st i added a copy of NTLDR into root of the USB drive to see if PC was looking in the wrong place, this did not work, may need to try putting it into a /i386 folder, that's for another time

2nd i tried to boot from the F12 command like you suggested, it still shows up with the "NTLDR is missing" error.

but boots OK this way to the normal hard drive.

:confused:

---

### Post by caljohnsmith on 2008-12-28
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by 5BallJuggler on 2008-12-28
I noticed that there are 2 files that get made, i'll include the 2nd one in the following post

```
============================= Boot Info Summary: ==============================

 => Drive sdb does not have a valid partition table.
 => Drive sdf does not have a valid partition table.
 => Drive sdg does not have a valid partition table.
 => Drive sdh does not have a valid partition table.
 => Drive sdi does not have a valid partition table.
 => Grub is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for its boot files.
 => No known boot loader is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd
 => Windows is installed in the MBR of /dev/sde

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 112455.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda6: _________________________________________________________________________

    File system:       swap

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdc1 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       Extended Partition

sdc5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdc5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdd1 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sde1 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   /ntldr /NTLDR

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      112454       56196   de  Dell Utility
/dev/sda2   *      112455   185309774    92598660    7  HPFS/NTFS
/dev/sda3       185309775   312496379    63593302+   5  Extended
/dev/sda5       185309838   307210994    60950578+  83  Linux
/dev/sda6       307211058   312496379     2642661   82  Linux swap / Solaris

sfdisk -V /dev/sda:

/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

sfdisk -V /dev/sdb:

/dev/sdb: No medium found

sfdisk: cannot open /dev/sdb for reading

Drive sdc: _____________________________________________________________________

fdisk -lu /dev/sdc:

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000616b0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   966534659   483267298+   7  HPFS/NTFS
/dev/sdc2       966534660   976768064     5116702+   f  W95 Ext'd (LBA)
/dev/sdc5       966534723   976768064     5116671    7  HPFS/NTFS

sfdisk -V /dev/sdc:

partition 2: start: (c,h,s) expected (1023,254,63) found (1023,0,1)
partition 5: start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sdc: OK

Drive sdd: _____________________________________________________________________

fdisk -lu /dev/sdd:

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc04f60cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          63   976768064   488384001    7  HPFS/NTFS

sfdisk -V /dev/sdd:

/dev/sdd: OK

Drive sde: _____________________________________________________________________

fdisk -lu /dev/sde:

Disk /dev/sde: 4110 MB, 4110230016 bytes
16 heads, 63 sectors/track, 7964 cylinders, total 8027793 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x90c239e8

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *          63     8027792     4013865    b  W95 FAT32

sfdisk -V /dev/sde:

Warning: partition 1 extends past end of disk

Drive sdf: _____________________________________________________________________

fdisk -lu /dev/sdf:

sfdisk -V /dev/sdf:

/dev/sdf: No medium found

sfdisk: cannot open /dev/sdf for reading

Drive sdg: _____________________________________________________________________

fdisk -lu /dev/sdg:

sfdisk -V /dev/sdg:

/dev/sdg: No medium found

sfdisk: cannot open /dev/sdg for reading

Drive sdh: _____________________________________________________________________

fdisk -lu /dev/sdh:

sfdisk -V /dev/sdh:

/dev/sdh: No medium found

sfdisk: cannot open /dev/sdh for reading

Drive sdi: _____________________________________________________________________

fdisk -lu /dev/sdi:

sfdisk -V /dev/sdi:

/dev/sdi: No medium found

sfdisk: cannot open /dev/sdi for reading

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D6-0A15" TYPE="vfat" 
/dev/sda2: UUID="3E009757009714CD" TYPE="ntfs" 
/dev/sda5: UUID="ba64d952-1c1d-4595-9c0d-4b179bb20f1b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="2c4ded22-49e9-4329-a3d6-34322c6f227d" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 
/dev/sdc1: UUID="EE1CE2161CE1D99B" TYPE="ntfs" 
/dev/sdc5: UUID="1C90428F90426EF8" TYPE="ntfs" 
/dev/sdd1: UUID="4A903A67903A5A21" LABEL="NewHardDisk" TYPE="ntfs" 
/dev/sde1: UUID="4B53-00E7" TYPE="vfat" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdd1 on /media/NewHardDisk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc1 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sde1 on /media/disk-1 type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)
/dev/sdc5 on /media/disk-2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

================================ sda2/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


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
color cyan/blue white/blue

#A splash image for the menu
splashimage=/boot/grub/splashimages/ABSTRACT-FlamesProjectNo4_1280x1024.xpm.gz

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
# kopt=root=UUID=ba64d952-1c1d-4595-9c0d-4b179bb20f1b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ba64d952-1c1d-4595-9c0d-4b179bb20f1b

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
# defoptions=splash quiet

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
uuid		ba64d952-1c1d-4595-9c0d-4b179bb20f1b
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=ba64d952-1c1d-4595-9c0d-4b179bb20f1b ro splash quiet 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		ba64d952-1c1d-4595-9c0d-4b179bb20f1b
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=ba64d952-1c1d-4595-9c0d-4b179bb20f1b ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		ba64d952-1c1d-4595-9c0d-4b179bb20f1b
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ba64d952-1c1d-4595-9c0d-4b179bb20f1b ro splash quiet 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		ba64d952-1c1d-4595-9c0d-4b179bb20f1b
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ba64d952-1c1d-4595-9c0d-4b179bb20f1b ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		ba64d952-1c1d-4595-9c0d-4b179bb20f1b
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Dell Utility Partition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=ba64d952-1c1d-4595-9c0d-4b179bb20f1b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=2c4ded22-49e9-4329-a3d6-34322c6f227d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sda5/boot: ==================================

total 23788
drwxr-xr-x  3 root root    4096 2008-12-16 21:39 .
drwxr-xr-x 20 root root    4096 2008-12-01 08:24 ..
-rw-r--r--  1 root root  507665 2008-11-04 21:00 abi-2.6.27-7-generic
-rw-r--r--  1 root root  507665 2008-11-20 23:46 abi-2.6.27-9-generic
-rw-r--r--  1 root root   91364 2008-11-04 21:00 config-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-11-20 23:46 config-2.6.27-9-generic
drwxr-xr-x  3 root root    4096 2008-12-20 18:26 grub
-rw-r--r--  1 root root 8191413 2008-11-26 15:25 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8191854 2008-12-16 21:39 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root    4420 2008-05-04 02:10 invaders
-rw-r--r--  1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-11-04 21:00 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1029585 2008-11-20 23:46 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1073 2008-11-04 21:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-11-20 23:48 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2244464 2008-11-04 21:00 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2244304 2008-11-20 23:46 vmlinuz-2.6.27-9-generic

=============================== sda5/boot/grub: ===============================

total 236
drwxr-xr-x 3 root root   4096 2008-12-20 18:26 .
drwxr-xr-x 3 root root   4096 2008-12-16 21:39 ..
-rw-r--r-- 1 root root    197 2008-11-26 15:11 default
-rw-r--r-- 1 root root     60 2008-11-26 15:11 device.map
-rw-r--r-- 1 root root   8108 2008-11-26 15:11 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-11-26 15:11 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-11-26 15:11 installed-version
-rw-r--r-- 1 root root   8712 2008-11-26 15:11 jfs_stage1_5
-rw-r--r-- 1 root root   5382 2008-12-20 18:26 menu.lst
-rw-r--r-- 1 root root   5383 2008-12-20 18:26 menu.lst~
-rw-r--r-- 1 root root   4796 2008-11-27 07:43 menu.lst.backup
-rw-r--r-- 1 root root   7352 2008-11-26 15:11 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-11-26 15:11 reiserfs_stage1_5
drwxr-xr-x 2 root root   4096 2008-11-27 07:47 splashimages
-rw-r--r-- 1 root root    512 2008-11-26 15:11 stage1
-rw-r--r-- 1 root root 121460 2008-11-26 15:11 stage2
-rw-r--r-- 1 root root   9556 2008-11-26 15:11 xfs_stage1_5

=============================== StdErr Messages: ===============================

Unknown MBR on /dev/sdc

00000000  fa b8 00 10 8e d0 bc 00  b0 b8 00 00 8e d8 8e c0  |................|
00000010  fb be 00 7c bf 00 06 b9  00 02 f3 a4 ea 21 06 00  |...|.........!..|
00000020  00 be be 07 38 04 75 0b  83 c6 10 81 fe fe 07 75  |....8.u........u|
00000030  f3 eb 16 b4 02 b0 01 bb  00 7c b2 80 8a 74 01 8b  |.........|...t..|
00000040  4c 02 cd 13 ea 00 7c 00  00 eb fe 00 00 00 00 00  |L.....|.........|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  00 00 00 00 00 00 00 00  b0 16 06 00 00 00 80 01  |................|
000001c0  01 00 07 fe ff ff 3f 00  00 00 c5 25 9c 39 00 00  |......?....%.9..|
000001d0  c1 ff 0f fe ff ff 04 26  9c 39 3d 26 9c 00 00 00  |.......&.9=&....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on /dev/sda1

00000000  eb 4a 90 44 65 6c 6c 20  38 2e 30 00 02 04 01 00  |.J.Dell 8.0.....|
00000010  02 00 02 00 00 f8 6e 00  3f 00 ff 00 3f 00 00 00  |......n.?...?...|
00000020  08 b7 01 00 80 00 29 15  0a d6 07 44 65 6c 6c 55  |......)....DellU|
00000030  74 69 6c 69 74 79 46 41  54 31 36 20 20 20 00 00  |tilityFAT16   ..|
00000040  00 00 00 00 00 00 00 00  00 00 00 30 33 c0 8e d0  |...........03...|
00000050  bc 00 07 fc b9 80 00 8e  d8 be 00 7c b8 00 20 8e  |...........|.. .|
00000060  c0 33 ff f3 66 a5 ea 6b  00 00 20 8e d8 b8 01 02  |.3..f..k.. .....|
00000070  b9 01 00 b6 00 8a 16 24  00 bb 00 02 cd 13 0f 82  |.......$........|
00000080  e0 00 80 3e c2 03 06 74  0e c6 06 c2 03 06 b8 01  |...>...t........|
00000090  03 cd 13 0f 82 cb 00 66  0f b7 06 16 00 66 d1 e0  |.......f.....f..|
000000a0  66 40 66 03 06 1c 00 66  a3 3e 00 8b 2e 11 00 89  |f@f....f.>......|
000000b0  2e 44 00 c1 ed 04 e8 cb  00 4d 75 fa b9 0b 00 be  |.D.......Mu.....|
000000c0  ea 01 8b fd f3 a6 74 0f  83 c5 20 ff 0e 44 00 75  |......t... ..D.u|
000000d0  eb be e0 01 e9 8e 00 26  8b 46 1a a3 46 00 66 a1  |.......&.F..F.f.|
000000e0  1c 00 66 40 66 a3 3e 00  c7 06 48 00 00 00 8b 2e  |..f@f.>...H.....|
000000f0  16 00 e8 8f 00 4d 75 fa  c7 06 4a 00 70 00 c7 06  |.....Mu...J.p...|
00000100  48 00 00 00 66 0f b7 06  46 00 66 83 e8 02 66 0f  |H...f...F.f...f.|
00000110  b6 0e 0d 00 66 f7 e1 66  0f b7 0e 16 00 66 d1 e1  |....f..f.....f..|
00000120  66 41 66 03 0e 1c 00 66  03 c1 66 0f b7 0e 11 00  |fAf....f..f.....|
00000130  66 c1 e9 04 66 03 c1 66  a3 3e 00 0f b6 2e 0d 00  |f...f..f.>......|
00000140  e8 41 00 4d 75 fa 8b 36  46 00 b8 00 30 d1 e6 73  |.A.Mu..6F...0..s|
00000150  03 05 00 10 8e c0 26 ad  3d f8 ff 73 0d a3 46 00  |......&.=..s..F.|
00000160  eb a2 be d5 01 e8 0d 00  eb fe 8a 16 24 00 33 ed  |............$.3.|
00000170  ea 00 00 70 00 ac 3c 00  74 09 b4 0e bb 07 00 cd  |...p..<.t.......|
00000180  10 eb f2 c3 66 a1 3e 00  66 33 d2 66 0f b7 0e 18  |....f.>.f3.f....|
00000190  00 66 f7 f1 fe c2 88 16  25 00 32 d2 66 0f b7 0e  |.f......%.2.f...|
000001a0  1a 00 66 f7 f1 8a f2 8b  c8 b8 01 02 c0 e5 06 0a  |..f.............|
000001b0  2e 25 00 86 e9 8a 16 24  00 c4 1e 48 00 cd 13 72  |.%.....$...H...r|
000001c0  a1 66 ff 06 3e 00 81 06  48 00 00 02 75 06 81 06  |.f..>...H...u...|
000001d0  4a 00 00 10 c3 44 69 73  6b 20 65 72 72 6f 72 00  |J....Disk error.|
000001e0  4e 6f 20 6c 6f 61 64 65  72 00 44 45 4c 4c 42 49  |No loader.DELLBI|
000001f0  4f 20 42 49 4e 00 00 00  00 00 00 00 00 00 55 aa  |O BIN.........U.|
00000200

/dev/sdb: No medium found

sfdisk: cannot open /dev/sdb for reading
/dev/sdf: No medium found

sfdisk: cannot open /dev/sdf for reading
/dev/sdg: No medium found

sfdisk: cannot open /dev/sdg for reading
/dev/sdh: No medium found

sfdisk: cannot open /dev/sdh for reading
/dev/sdi: No medium found

sfdisk: cannot open /dev/sdi for reading
```

---

### Post by 5BallJuggler on 2008-12-28
the previous post was of RESULTS.txt, this is the other file, it's called boot_info_script.txt

```

Boot_Codes_Dir="
    /
    /NST/
    "

Boot_Dir="
    /Boot
    /boot
    /BOOT
    /boot/grub
    /grub
    /ubuntu/disks
    /ubuntu/disks/boot/
    /ubuntu/disks/boot/grub
    /ubuntu/disks/install/boot
    /ubuntu/disks/boot/grub
    /NST
    "

Boot_Prog="
    /bootmgr
    /BOOTMGR
    /grldr
    /GRLDR
    /ntldr
    /NTLDR
    /NTDETECT.COM
    /ntdetect.com
    /NTBOOTDD.SYS
    /ntbootdd.sys
    /wubildr.mbr
    /ubuntu/winboot/wubildr.mbr
     "

Boot_Files="
    /boot/grub/menu.lst
    /grub/menu.lst
    /NST/menu.lst
    /menu.lst
    /ubuntu/disks/boot/grub/menu.lst
    /ubuntu/disks/install/boot/grub/menu.lst
    /boot/grub/grub.conf
    /grub/grub.conf
    /grub.conf
    /boot.ini
    /etc/fstab
    "


## "titlebar_gen" generates the $name$file title bar to always be either 79 or 80 chars total in length:
titlebar_gen () {
		name_file="$1$2:"; name_file_length=${#name_file}
		equal_signs_line_length=$(((80-name_file_length)/2-1)); equal_signs_line=""
		for length in $(seq $equal_signs_line_length); do
  			equal_signs_line='='$equal_signs_line
		done
		echo "$equal_signs_line $name_file $equal_signs_line" >> $Log1; }

Dir=$(cd $(dirname $0);pwd);

LogFile=$Dir/RESULTS
while ( [ -e $LogFile$j.txt ] )
    do  
      ((j++))
      wait;
    done
LogFile=$LogFile$j.txt



exec 6>&1   
exec >$LogFile

Folder=/tmp/BootInfo
while (! mkdir $Folder$i 2>/dev/null)
    do  
      ((i++))
      wait;
    done
Folder=$Folder$i

cd $Folder

Log1=$Folder/Log1
Error_Log=$Folder/Error_Log
Trash=$Folder/Trash
Mount_Error=$Folder/Mount_Error
Unknown_MBR=$Folder/Unknown_MBR
Tmp_Log=$Folder/Tmp_Log
exec 2>$Error_Log


All_Hard_Drives=$(ls /dev/hd? /dev/sd? 2>>$Trash );

echo '============================= Boot Info Summary: =============================='; echo
for drive in  $All_Hard_Drives;
do
        size=$(sfdisk -s $drive);        
        if [ 0 -lt $size 2>>$Trash ];
	then
	 Hard_Drives=$Hard_Drives" "$drive; 
        else
          echo " => Drive $(basename $drive) does not have a valid partition table."
    fi;
done;

for drive in $Hard_Drives;
  do 
    Message=$(echo is installed in the MBR of $drive)
    case $(hexdump -v -n  2 -e '/1 "%x"' $drive) in
	eb48) BL=Grub
             dr=$(hexdump -s 0x40 -n 1 -e '"%d"' $drive);
             offset=$(hexdump -s 0x44 -n 4 -e '"%u"' $drive);
              if  [ "$offset" != 1 ];
	      then
                  pa=-1
                  for hdd in $Hard_Drives;
		  do
                      if [[ $offset -lt $((2*$(sfdisk -s $hdd))) ]]
			      then
		      tmp=$(dd if=$hdd skip=$offset count=1 2>>$Trash | hexdump    -n 4 -e '"%x"');
                      if [ "$tmp" = 3be5652 ]; then
                      pa=$(dd if=$hdd skip=$((offset+1)) count=1 2>>$Trash | hexdump  -s 0xa  -n 1 -e '"%d"');
                      stage2_hdd=$hdd
                      fi;
                      fi;
                  done;
                  let dr-127
                  Message=$(echo $Message and looks at sector $offset)         
                  if [ "$dr" = 128 ];
                      then
                          Message=$(echo $Message of the same hard drive) 
                      else
                           Message=$(echo $Message on boot drive \#$dr)
		  fi;
                    Message=$(echo $Message for the stage2 file);
                    
                        if [ "$pa" = -1  ]
		     then
		         Message=$(echo $Message, but no stage2 files can be found at this location); 
                     else
                       pa=$((pa+1))
                        Message=$(echo $Message \(a stage2 file is at this location on $stage2_hdd\) and on)
                        if [ $pa = 256 ];
                        then
                            Message=$(echo $Message the same partition) 
                        else
                           Message=$(echo $Message partition \#$pa) 
	                fi;
                       Message=$(echo $Message for menu.lst.)
                     fi;
		 
	      else
	      pa=$(hexdump -s 0x419 -n 1 -e '"%d"' $drive);
              dr=$(hexdump -s 0x41a -n 1 -e '"%d"' $drive);
              if [ $pa$dr = 4649 ]; 
		then
		BL=SuperGrub
                pa=$(hexdump -s 0x41e -n 1 -e '"%d"' $drive);
                dr=$(hexdump -s 0x41f -n 1 -e '"%d"' $drive);
 	      fi
              dr=$((dr-127))
              pa=$((pa+1))
              if [ $dr = 128 ];
               then
                Message=$(echo $Message and looks on the same drive in partition \#$pa for its boot files.)
              else
               Message=$(echo $Message and looks  on boot drive \#$dr in partition \#$pa for its boot files.)
            fi;
	    fi;; 
 	33c0) BL=Windows;;
	fa31) BL=Syslinux;;
	faeb) BL=Lilo;; 
	fc31) BL=Testdisk;;
	eb5e) BL=Grub4Dos;;
	b800) BL=Plop;;
	33ff) BL=Gateway?;;
	fceb) BL=Bootit;;
          00) BL="No boot loader";;
	   *) BL="No known boot loader"
              echo "Unknown MBR on $drive" >> $Unknown_MBR;
              echo >> $Unknown_MBR;
              hexdump -n 512 -C $drive >> $Unknown_MBR;
              echo >> $Unknown_MBR;;
        esac;
        ##Output message at beginning of summary that gives MBR info for each drive:
        echo -n " => "
        echo "$BL $Message" | fold -s -w 75 | sed -e '2~1s/.*/    &/'   
 
    done
    echo;

for drive in $Hard_Drives;
 do
for part  in  $(ls $drive?* 2>>$Trash)
   do
      BSI=""      
      part_number=${part:8}
      part_type=$(sfdisk -c $drive $part_number)
      name=$(basename $part);
      echo $name: _________________________________________________________________________; echo
      mkdir $name 
      type=$( /lib/udev/vol_id -t $part 2>$Tmp_Log );
      if [ $part_type = 5 ] || [ $part_type = f ] && [ "$type" = "" ] ;
         then
	 type="Extended Partition";
	 cat $Tmp_Log>>$Trash;
	 else
         cat $Tmp_Log>>$Error_Log
      fi;
      echo "    File system:       "$type;
      if [ "$type" != "swap" ]  && [ "$type" != "Extended Partition"  ] && [ "$type" != "unknown volume type" ] && [ "$type" != "LVM2_member" ]  ;
       then 

          Bytes8081=$(hexdump -v -s 0x80 -n  2 -e '/1 "%x"'  $part)
          case $Bytes8081  in
             8cd) BST="Windows XP";;
            b6d1) BST="Windows XP: Fat32";;
            fa33) BST="Windows XP";;
	    55aa) BST="Windows Vista";;           
	    5272) BST=Grub;
                  offset=$(hexdump -s 0x44 -n 4 -e '4 "%u"' $part 2>>$Trash);
                  dr=$(hexdump -s 0x40 -n 1 -e '"%d"' $part);
                  pa=-1
                  for hdd in $Hard_Drives;
		  do
                      if [ $offset -lt  $((2*$(sfdisk -s $hdd))) ];
			      then
		      tmp=$(dd if=$hdd skip=$offset count=1 2>>$Trash | hexdump    -n 4 -e '"%x"');
                      if [ "$tmp" = 3be5652 ]; then
                      pa=$(dd if=$hdd skip=$((offset+1)) count=1 2>>$Trash | hexdump  -s 0xa  -n 1 -e '"%d"');
                      stage2_hdd=$hdd
                      fi;
		      fi;
                  done;
                  dr=$((dr-127))
                  BSI=$(echo $BSI Grub is installed to the boot sector of $part and looks at sector $offset )        
                  if [ "$dr" = 128 ];
                      then
                          BSI=$(echo $BSI of the same hard drive) 
                      else
                          BSI=$(echo $BSI on boot drive \#$dr)
		  fi;
                  BSI=$(echo $BSI for the stage2 file);
                    
                        if [ "$pa" = T  ]
		     then
		        BSI=$(echo $BSI, but no stage2 files can be found at this location); 
                     else
                       pa=$((pa+1))
                       BSI=$(echo $BSI  \(a  stage2 file is  at this location on $stage2_hdd\)  and on )                       
                        if [ "$pa" = 256 ];
                        then
                           BSI=$(echo $BSI the same partition) 
                        else
                            BSI=$(echo $BSI  partition \#$pa )
	                fi;
                      BSI=$(echo $BSI for menu.lst.)
                     fi;;
                  
                   
            7cc6) BST=Win_98;;
            7304) BST=Dos_1.0;;
            2d5e) BST=Dos_1.1;;
	    7815) BST=Fat32;;
            6f74) BST=Fat32;;
            696e) BST=Fat16;;
            6616) BST=Fat16;;
 	      00) sig2=$(hexdump -v -s 0x80 -n  2 -e '/1 "%x"'  $part)
                      if [ "$sig2" = 00 ];
		      then
                      BST="No Boot Loader";
		      else
		      BST="Unknown"
                      echo "Unknown BootLoader  on $part" >> $Unknown_MBR;
                      echo >> $Unknown_MBR;
                      hexdump -n 512 -C $part >> $Unknown_MBR;
                      echo >> $Unknown_MBR;
                  fi;;
                *) BST="Unknown"
                   echo "Unknown BootLoader  on $part" >> $Unknown_MBR;
                   echo >> $Unknown_MBR;
                   hexdump -n 512 -C $part >> $Unknown_MBR;
                   echo >> $Unknown_MBR;
            esac;
           if [[ "$type" = "ntfs"  ||   "$Bytes8081" = "7cc6" ||  "$Bytes8081" = "7815"  ||  "$Bytes8081" = "B6D1"   ]] ;
         then
         offset=$(hexdump -s 0x1c -n 4 -e '"%d\n"' $part);
         BSI=$(echo  According to the info in the boot sector, $name starts at sector $offset.)   
      fi;


            echo "    Boot sector type:  "$BST
       if  mount $part $name 2>$Mount_Error; then
       OS=""
       [ -e $name"/Windows/System32/config/BCD-Template" ] ||  [ -e $name"/windows/system32/config/bcd-template" ] || [ -e $name"/WINDOWS/System32/config/BCD-Template" ] ||
  [ -e $name"/WINDOWS/system32/config/BCD-Template" ] && OS="Windows Vista"

       [ -e $name"/Windows/System32/config/SecEvent.Evt" ] ||  [ -e $name"/WINDOWS/system32/config/SecEvent.Evt" ] || [ -e $name"/WINDOWS/system32/config/secevent.evt" ] || [ -e $name"/windows/system32/config/secevent.evt" ] && OS="Windows XP"
  
       [ -e $name"/etc" ] && OS=$(cat $name/etc/issue) && OS=${OS%%\\*}
     

       BootFiles=""
       for file in $Boot_Files;
       do
           if [ -f $name$file ];
              then BootFiles=$(echo $BootFiles"  "$file);
	      echo >> $Log1
              titlebar_gen $name $file	##generates a titlebar above each file/dir listed
              echo >> $Log1
              if ! [ -h $name$file ];
              then
                 cat $name$file >> $Log1;
              fi;
	   fi;
       done;

       for file in $Boot_Prog;
       do
           if [ -f $name$file ];
              then BootFiles=$(echo $BootFiles"  "$file);          
	   fi;
       done;


       for file in $Boot_Dir;
       do
          if [ -d $name$file ];
          then
	      BootFiles=$(echo $BootFiles"  "$file); 
	      echo >> $Log1
              titlebar_gen $name $file	##generates a titlebar above each file/dir listed
              echo >> $Log1
              ls -la  $name$file >> $Log1 ; 
             
	  fi;
       done;

       for file in $Boot_Codes_Dir
       do
	   if [ -d $name$file ];
	   then  
		  for loader in $( ls  $name$file );
		  do
                   if [ -f $name$file$loader ];
		   then		     
                      sig=$(hexdump -s 0x101 -n 8  -e '8/1 "%_p"' $name$file$loader)
                      if [ "$sig"  = "BootPart" ]
			  then
                          offset=$(hexdump -s 0xf1 -n 4 -e '"%d"' $name$file$loader);
                              dr=$(hexdump -s 0x6f -n 1 -e '"%d"' $name$file$loader);
			      dr=$((dr -127))
 			  BSI=$(echo $BSI "  "BootPart in the file $file$loader is trying to chain load sector \#$offset on boot drive \#$dr);
		       fi;
		      sig=$(hexdump -s 0x17f -n 4  -e '4/1 "%_p"' $name$file$loader)
                      if [ "$sig"  = "GRUB" ];
                      then
                          offset=$(hexdump -s 0x44 -n 4 -e '4 "%u"' $name$file$loader 2>>$Trash);
                          dr=$(hexdump -s 0x40 -n 1 -e '"%d"' $name$file$loader);
                          pa=-1
                          for hdd in $Hard_Drives;
		          do
                             if [ $offset -lt  $((2*$(sfdisk -s $hdd))) ];
			     then
		                  tmp=$(dd if=$hdd skip=$offset count=1 2>>$Trash | hexdump    -n 4 -e '"%x"');
                                  if [ "$tmp" = 3be5652 ];
                                  then
                                      pa=$(dd if=$hdd skip=$((offset+1)) count=1 2>>$Trash | hexdump  -s 0xa  -n 1 -e '"%d"');
                                       stage2_hdd=$hdd
                                   fi;
		              fi;
                           done;
                           dr=$((dr-127))
                            BSI=$(echo $BSI Grub in the file $file$loader  looks at sector $offset )        
                           if [ "$dr" = 128 ];
                           then
                                BSI=$(echo $BSI of the same hard drive) 
                           else
                                BSI=$(echo $BSI on boot drive \#$dr)
		           fi;
                           BSI=$(echo $BSI for the stage2 file);
                    
                           if [ "$pa" = T  ]
		           then
		                BSI=$(echo $BSI, but no stage2 files can be found at this location); 
                           else
                                 pa=$((pa+1))
                                 BSI=$(echo $BSI  \(a stage2 file is at this location on $stage2_hdd\)  and on )                       
                                 if [ "$pa" = 256 ];
                                 then
                                     BSI=$(echo $BSI the same partition) 
                                 else
                                       BSI=$(echo $BSI partition \#$pa )
	                         fi;
                                 BSI=$(echo $BSI for menu.lst.)
                            fi;
                         fi;
 		       fi;
		  done;
              fi;
           done
 
      echo -n "    Boot sector info:  "
      echo $BSI | fold -s -w 55 |  sed -e '2~1s/.*/                       &/'
      echo "    Operating System:  "$OS
      echo -n "    Boot files/dirs:   "
      echo $BootFiles | fold -s -w 55 |  sed -e '2~1s/.*/                       &/'
     
     umount $name || umount -l $name; 
     else
     echo "    Mounting failed:  ";  
     cat   $Mount_Error;
     fi;
     fi;
     echo;
 
     done;
     done;

echo '=========================== Drive/Partition Info: ============================='; echo
for drive in $All_Hard_Drives;
 do
     echo "Drive $(basename $drive): _____________________________________________________________________"
     echo
     echo "fdisk -lu $drive:"
     fdisk -lu $drive;
     echo;
     echo "sfdisk -V $drive:"; echo
     sfdisk -V $drive 2>&1
     echo   
 done
echo "blkid -c /dev/null: ____________________________________________________________"; echo
blkid -c /dev/null
echo;
echo '=============================== "mount" output: ==============================='; echo
mount
echo >> $Log1
echo "=============================== StdErr Messages: ===============================">>$Log1
echo >> $Log1
cat $Log1
[ -e $Unknown_MBR ] && cat $Unknown_MBR
[ -s $Error_Log ] && cat $Error_Log || echo "No errors were reported."
chown $(basename ~) $LogFile
exec 1>&-
exec 1>&6
exec 6>&-
echo Finished. The results are in the file $(basename $LogFile) located in $Dir
```

I noticed that at the start of this 2nd file there is are 2 occurences of NTLDR & ntldr

will the case make a difference??

```
Boot_Prog="
    /bootmgr
    /BOOTMGR
    /grldr
    /GRLDR
    /ntldr
    /NTLDR
    /NTDETECT.COM
    /ntdetect.com
    /NTBOOTDD.SYS
    /ntbootdd.sys
    /wubildr.mbr
    /ubuntu/winboot/wubildr.mbr
     "
```

---

### Post by caljohnsmith on 2008-12-28
It looks like you currently have Grub correctly installed to your Windows/Ubuntu drive, so you are able to boot into Ubuntu and Windows OK, true? As far as your 4 GB USB stick goes, it still has a Windows MBR (Master Boot Record), which would boot the FAT partition on the stick and give you that NTLDR missing error. I would try reinstalling Intrepid to your USB stick and see if that fixes the problem. If not, I would recommend instead trying UNetBootin to install Intrepid to your USB stick:

[http://maketecheasier.com/how-to-boot-install-ubuntu-ibex-from-a-usb-thumb-drive/2008/09/22](http://maketecheasier.com/how-to-boot-install-ubuntu-ibex-from-a-usb-thumb-drive/2008/09/22)

How about giving that a shot and let me know how it goes.

---

### Post by arubislander on 2008-12-28
The second file is probably the script that generated the first file or something like that. caljohnsmith has contributed to the file you downloaded so he can explain the output better than I could.

But I see that there are several XP's installed on the various external USB drives, but not all the installations contain an NTLDR, so my guess remains that when it says it can't find NTLDR the machine is trying to boot one of those other XP's

---

### Post by caljohnsmith on 2008-12-28
> **arubislander said:**
> The second file is probably the script that generated the first file or something like that. caljohnsmith has contributed to the file you downloaded so he can explain the output better than I could.

But I see that there are several XP's installed on the various external USB drives, but not all the installations contain an NTLDR, so my guess remains that when it says it can't find NTLDR the machine is trying to boot one of those other XP's
You're right, 5BallJuggler posted the script in his last post. I think you might be slightly misinterpreting the output of the script though; 5BallJuggler has several NTFS/FAT partitions that all have a Windows XP boot sector, but they don't actually have Windows XP installed. According to the script, only sda2 actually has Windows XP installed. :)

---

### Post by arubislander on 2008-12-28
Indeed! I was focussing on the entry labeled Boot sector type and completely missed the one labeled Operating system.

Thanks for the clarification.

Btw, I will have to rethink my theory in light of this :)

---

### Post by 5BallJuggler on 2008-12-28
Thank you both for your help, i will try these suggestions tomorrow, by first formatting the USB and then re-installing Ubuntu on it, i'll let you know how i get on with the process.

once again thanks

Phil.

---

### Post by 5BallJuggler on 2008-12-29
> **caljohnsmith said:**
> It looks like you currently have Grub correctly installed to your Windows/Ubuntu drive, so you are able to boot into Ubuntu and Windows OK, true? As far as your 4 GB USB stick goes, it still has a Windows MBR (Master Boot Record), which would boot the FAT partition on the stick and give you that NTLDR missing error. I would try reinstalling Intrepid to your USB stick and see if that fixes the problem. If not, I would recommend instead trying UNetBootin to install Intrepid to your USB stick:

[http://maketecheasier.com/how-to-boot-install-ubuntu-ibex-from-a-usb-thumb-drive/2008/09/22](http://maketecheasier.com/how-to-boot-install-ubuntu-ibex-from-a-usb-thumb-drive/2008/09/22)

How about giving that a shot and let me know how it goes.

I tried the basic re-install and i'm getting the same error, i'm in the process of the UNetBootin method, i'll let you know how it goes.
is it worth formatting the drive in question?

---

### Post by 5BallJuggler on 2008-12-29
OK, i tried the 2nd method too, after the initial install it booted up OK, when i tried to do it a 2nd time it got to the boot loader, I selected default, then it just sat there after it's preload checks.

I tried it on the laptop and it just came up with boot error.

I'm gonna try to format the drive on the laptop and try this method again as I think the boot loader option is the way forward.

---

### Post by 5BallJuggler on 2008-12-29
OK, now it's getting interesting.

I can get it to boot from the USB stick,but....

if i make changes to the layout of the desktop, it reverts back when i reboot.
if i add a program ie CCSM, it is not there when I reboot.
when I try to reboot, the PC hangs....
       goes to a black screen
       USB stick is still being accessed - light stays on.:confused:
       does not turn off - left for 15 minutes to see.:confused:

i'm going to try to use gParted to fully format the stick to FAT32 and try the 1st method again, hopefully it won't look for a windows MBR.

If anyone has any other ideas, please let me know....


.....petrol and matches are not an option....


....yet!

---

### Post by 5BallJuggler on 2008-12-29
Well that didn't work either.:(

---

### Post by caljohnsmith on 2008-12-29
OK, I didn't realize you were also looking for "persistence", or having your settings and changes carry over between reboots; in that case UNetBootin won't work I think because UNetBootin simply makes your USB stick the same thing as a Live CD. Have you tried using the Ubuntu installer from the Live CD to do a normal Intrepid install to your USB stick? That might work for your situation.

---

### Post by 5BallJuggler on 2008-12-29
yeah, I tried that, it was the 1st thing i did.

i've tried a few ather things too, the closest to getting it to work is this:-
Remove all software from USB stick
Format to EXT3 using gParted
Remove "Lost + Found" folder using sudo nautilos in Terminal
Run "Create USB disk" - this then tells you that the format is wrong, click format in the creation window
locate the ISO file and then click on "Make start up disk"
Reboot - all OK
Reboot again - just to check - all OK
make small change to desktop ie increase workspaces to 4 and Reboot - all OK
add Software sources - Universe and Multiverse, and update, update did not complete, fault with nautilus and a 2nd fault saying that a file couldn't be filled with packing, when it does it again i'll get a screen capture and add to the posts
Reboot - NOW NO GOOD, 

i lost the option to boot USB ZIP from the boot menu

Just about to try again on my laptop to see if the PC is the issue.

---

### Post by 5BallJuggler on 2008-12-29
I checked the Error report more closely, if you look at the Terminal screen when the program is updating, you eventually see an error that says there is no space left on the drive, 

I thought 4Gb would be enough. off to get a 16Gb USB drive, gonna try again tomorrow

:(:confused::(

---

### Post by arubislander on 2008-12-30
I've got Ubuntu running on a 4 GB stick. It works fine. 

I've found though that the secret to a happy USB experience is to **not** update! I know it sounds wrong, but that's what I've learnt the hard way. 

It's perfectly OK to install some additional apps as long as you keep a close eye on diskspace, but updating is a definite negative.

---

### Post by 5BallJuggler on 2008-12-30
Thanks for that arubislander, I'm waiting for a 16Gb stick to drop through my door, hopefully it will allow updates, it should have arrived this morning, but will probably be tomorrow now.

but I still don't understand why it gets so big during an update:confused:

---

### Post by arubislander on 2008-12-30
> **5BallJuggler said:**
> but I still don't understand why it gets so big during an update:confused:

I guess the downloaded packages take up additional space. Unpacking them for installation takes up some more probably.

---

### Post by Pumalite on 2008-12-30
I agree that updating ruins the whole thing.

---

### Post by 5BallJuggler on 2009-01-02
Happy New Year All, 

i've installed Ubuntu 8.10 onto a 16Gb stick, the persistance is working, and it's been updated, but....


....it says that it hasn't updated the linux kernel to the latest version.

I'm waiting on a launchpad reply.

---

### Post by 10011010 on 2009-01-03
Parallel to this, is there a straightforward way to create and load the bootable USB stick from a Win32 machine and not ubuntu?

I have XP SP3, and am moving completely to Xubuntu -- need to make a bootable usb drive to work it, no Optical drive on the machine.

---

### Post by Pumalite on 2009-01-03
[http://www.pendrivelinux.com/2008/04/09/usb-ubuntu-804-installation-from-windows/](http://www.pendrivelinux.com/2008/04/09/usb-ubuntu-804-installation-from-windows/)
[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)

---

