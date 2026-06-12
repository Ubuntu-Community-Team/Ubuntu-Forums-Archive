---
title: "Grub Error 17 after fresh 8.04 install"
date: 2009-10-07
forum: Installation &amp; Upgrades
---

### Post by damnated on 2009-10-07
I had some problems with nvidia drivers under Jaunty, and i figured i'll try an earlier version to see if the problem persists. 
I installed 8.04 64 bit from a usb on a separate sata hard drive, installation went just fine, and after the necessary reboot, grub said there was error 17, and the drive couldn't be loaded.

This must be something stupid as the drive is connected, appears in the bios just fine, i used it before, Jaunty had no problems with it ie. 

I didn't want to mess around, as i'm not experienced with linux in general, all i could do was to reinstall the system, without luck however. Please give me a hand.

---

### Post by dstew on 2009-10-07
It is possible that the environment under which grub was installed is different from the environment under which you are now booting. The BIOS disk enumeration may have changed. Grub uses the BIOS to find the partiton that has its stage 2 and menu. So, if the BIOS enumeration of the disks changes, grub will get lost.

Try booting with the USB drive plugged in, but change the BIOS boot order so the hard disk boots first. Sometimes this works.

---

### Post by damnated on 2009-10-07
It didn't work.

---

### Post by dstew on 2009-10-07
The [boot info script]("http://sourceforge.net/projects/bootinfoscript/") can help figure out what is wrong. We could go back and forth about things to try, but this should get all the information, and we can look at it together. See [this thread]("http://ubuntuforums.org/showthread.php?t=1284402&highlight=boot+info+script").

---

### Post by damnated on 2009-10-08
Here it is
```
============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/hda
 => Grub0.97 is installed in the MBR of /dev/hdb and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc

hdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, hdb1 has 
                       398282751 sectors, but according to the info from 
                       fdisk, it has 398283417 sectors.
    Operating System:  
    Boot files/dirs:   

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.3 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdc1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc1 starts at sector 32.
    Mounting failed:
mount: /dev/sdc1 already mounted or sdc1 busy

=========================== Drive/Partition Info: =============================

Drive: hda ___________________ _____________________________________________________
Note: sector size is 2048 (not 512)

Disk /dev/hda: 4658 MB, 4658429952 bytes
255 heads, 63 sectors/track, 141 cylinders, total 2274624 sectors
Units = sectors of 1 * 2048 = 2048 bytes

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found


Drive: hdb ___________________ _____________________________________________________

Disk /dev/hdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x660e5e91

Partition  Boot         Start           End          Size  Id System

/dev/hdb1    *             63   398,283,479   398,283,417  42 SFS


Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb2f3e63d

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   149,838,254   149,838,192  83 Linux
/dev/sda2         149,838,255   156,296,384     6,458,130   5 Extended
/dev/sda5         149,838,318   156,296,384     6,458,067  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0c540c54

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   488,375,999   488,375,937   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 2092 MB, 2092695552 bytes
8 heads, 32 sectors/track, 15966 cylinders, total 4087296 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x221e5780

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             32     4,087,295     4,087,264   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="0f6191cb-bbfd-480b-884c-46d1ed050b0e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="ac83f864-0db3-4ccc-a40f-36afc36cae4f" 
/dev/sdb1: UUID="7258B27C58B23F23" TYPE="ntfs" 
/dev/hdb1: UUID="B0041FF2041FB9F4" LABEL="Zene" TYPE="ntfs" 
/dev/sdc1: UUID="30A3-239E" TYPE="vfat" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-24-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-24-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/hda on /media/Blues Collection type iso9660 (ro,nosuid,nodev,uhelper=hal,uid=999,utf8)


=========================== sda1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=0f6191cb-bbfd-480b-884c-46d1ed050b0e ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=0f6191cb-bbfd-480b-884c-46d1ed050b0e ro quiet splash
initrd        /boot/initrd.img-2.6.24-24-generic
quiet

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=0f6191cb-bbfd-480b-884c-46d1ed050b0e ro single
initrd        /boot/initrd.img-2.6.24-24-generic

title        Ubuntu 8.04.3 LTS, memtest86+
root        (hd1,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Windows NT/2000/XP (loader)
root        (hd2,0)
savedefault
makeactive
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader    +1


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0f6191cb-bbfd-480b-884c-46d1ed050b0e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=ac83f864-0db3-4ccc-a40f-36afc36cae4f none            swap    sw              0       0
/dev/sdc1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/hda        /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  14.3GB: boot/grub/menu.lst
  14.4GB: boot/grub/stage2
  14.4GB: boot/initrd.img-2.6.24-24-generic
  14.4GB: boot/vmlinuz-2.6.24-24-generic
  14.4GB: initrd.img
  14.4GB: vmlinuz

================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=0 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer /TUTag=LHD6XM /Kernel=TUKernel.exe 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional (TuneUp Backup)" /noexecute=optin /fastdetect /usepmtimer /TUTag=LHD6XM-BAK 
=======Devices which don't seem to have a corresponding hard drive==============

sdd 
```

---

### Post by dstew on 2009-10-08
There is something unusual about your disk environment. There is a disk /dev/hda that does not have an MBR or a file system. Is this possibly an encrypted disk? This disk may or may not be counted in the BIOS, especially if you have BIOS-enabled encryption. That might be throwing off grub. Or, is /dev/hda just a bad disk?

You have two grub boot loaders in your system, one in the MBR of /dev/hdb, and the other in the MBR of /dev/sdc. It is probably the one in /dev/hdb that is loading, and becoming lost. It is looking for its stage 2 and menu.lst files in the first partition of the second boot disk (that could be either the second disk in your BIOS boot order, or the second disk detected by your BIOS). It looks like the only Linux system is installed in /dev/sda1, so I assume that is the intended target of your grub boot loaders.

One thing to try is to change the boot order so that /dev/sda boots before /dev/hdb. Since the grub boot loader in /dev/sda is targeting that same disk, you might not have any problems with the disk enumeration.

Otherwise, it would be best to re-install grub. To do that, you boot a live CD, and at a terminal command line, enter```
sudo grub
```That should get you the grub prompt **grub>**. At the grub prompt, enter```
find /boot/grub/menu.lst
```It should return something like (hd1,0). That is the disk and partition that has the stage 2 and menu.lst file, in grub notation. (hd1,0) would probably be equivalent to the Linux notation /dev/sda1. However, the strange /dev/hda disk might mean that Linux and grub (really the BIOS) will see the disks differently.

Whatever it returns, use as the argument in a grub root command:```
root (hd1,0)
```Then, to re-install the grub boot loader into the MBR of the first boot disk do```
setup (hd0)
```Shutdown the Live CD system, remove the disk and reboot.

---

### Post by presence1960 on 2009-10-08
+1 changing sda to first in hard disk boot order in BIOS will boot Ubuntu 8.04 (hardy)

---

### Post by damnated on 2009-10-08
I have 3 hard disks, a 80 sata, a 200 ata, and a 250 sata. The smallest hard disk is the one with the ubuntu install, and that is the one that boots first, the other sata is with the windows install, that is the last in the boot order. 

I've tried reinstalling the grub, but it didn't change anything. I'm beginning to think this is because i installed from a usb. I'll reinstall it tomorrow from a cd, hope that helps.

---

### Post by presence1960 on 2009-10-08
> **damnated said:**
> I have 3 hard disks, a 80 sata, a 200 ata, and a 250 sata. The smallest hard disk is the one with the ubuntu install, and that is the one that boots first, the other sata is with the windows install, that is the last in the boot order. 

I've tried reinstalling the grub, but it didn't change anything. I'm beginning to think this is because i installed from a usb. I'll reinstall it tomorrow from a cd, hope that helps.

that is not why. I have 3 hard disks and installed via USB and GRUB works.

---

### Post by presence1960 on 2009-10-08
restore GRUB like this:

```
1. Boot your computer up with Ubuntu CD or USB
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd1,0)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd1,0)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd1)", to install GRUB to MBR
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

When rebooting make sure your hard disk boot order in BIOS is sda, sdb & lastly hda. The order must be precise! save changes to CMOS and exit BIOS.

Boot into Ubuntu & open a terminal & run ```
gksu gedit /boot/grub/menu.lst
```
That is a lowercase L in .lst

Scroll down to your OSs and change to this:
```

## ## End Default Options ##

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=0f6191cb-bbfd-480b-884c-46d1ed050b0e ro quiet splash
initrd        /boot/initrd.img-2.6.24-24-generic
quiet

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=0f6191cb-bbfd-480b-884c-46d1ed050b0e ro single
initrd        /boot/initrd.img-2.6.24-24-generic

title        Ubuntu 8.04.3 LTS, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Windows NT/2000/XP (loader)
root        (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1
```

Click Save on toolbar, exit file and reboot.

When using (hdx,y) in GRUB x= device and y= partition. X is determined by the boot order in BIOS. fdisk and Ubuntu read the order of disks differently, but it is the order in BIOS that matters because that is the actual order in which your disks boot- regardless of what Ubuntu & fdisk say!

---

### Post by damnated on 2009-10-08
> **presence1960 said:**
> that is not why. I have 3 hard disks and installed via USB and GRUB works.
i've installed Jaunty from a cd previously and there was nothing similar. that is why i'm thinking there is something wrong with the installation.

---

### Post by presence1960 on 2009-10-08
> **damnated said:**
> i've installed Jaunty from a cd previously and there was nothing similar. that is why i'm thinking there is something wrong with the installation.

there is nothing wrong. your (hdx,y) in menu.lst is wrong. It should be (hd0,0) because sda boots first so that makes sda (hd0) not (hd1). You have (hd1,0) for Ubuntu and that is wrong!

---

### Post by presence1960 on 2009-10-08
> **damnated said:**
> i've installed Jaunty from a cd previously and there was nothing similar. that is why i'm thinking there is something wrong with the installation.

jaunty uses UUID instead of (hdx,y)
hardy uses (hdx,y)

why don't you just try what i suggested, what do you have to lose? Except maybe a reinstallation that isn't necessary!

---

### Post by damnated on 2009-10-08
> **presence1960 said:**
> jaunty uses UUID instead of (hdx,y)
hardy uses (hdx,y)

why don't you just try what i suggested, what do you have to lose? Except maybe a reinstallation that isn't necessary!
I didn't see your second post; i'm definitely trying your suggestion, that is why i opened this thread :)

---

### Post by damnated on 2009-10-08
Holly ****, this was so easy it makes me mad. 

All i did was press 'e' at the grub menu, and change the root(hd1,0) to root(hd0,0). And ubuntu loaded straight away. 

Thank you for your help guys.

---

### Post by presence1960 on 2009-10-08
> **damnated said:**
> Holly ****, this was so easy it makes me mad. 

All i did was press 'e' at the grub menu, and change the root(hd1,0) to root(hd0,0). And ubuntu loaded straight away. 

Thank you for your help guys.

Glad you got it working! Enjoy Ubuntu

---

