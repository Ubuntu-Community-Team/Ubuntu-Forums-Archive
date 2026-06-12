---
title: "Error 17, GRUB loading stage 1.5"
date: 2009-05-07
forum: Hardware
---

### Post by milagros on 2009-05-07
Hello,I'm appreciated if someone help me.I have the following problem
i install xubuntu 9.04 on the first hard drive of laptop Toshiba Satellite A300-211,that have partition it.(there is also Windows Vista in other partition of this drive).When I restart my laptop ,it says 


Grub loading stage 1.5.
 
Grub loading, please wait...
Error 17

I ran  Super Grub Disk[(auto_super_grub_disk_1.5.exe]("file:///C:/Documents%20and%20Settings/Administrator/Desktop/auto_super_grub_disk_1.5.exe")) and i followed this link:[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
but problem exists
thanks in advance

---

### Post by caljohnsmith on 2009-05-08
I think it would help to first get a clearer picture of your setup related to your booting problem, so how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

John

---

### Post by milagros on 2009-05-08
```
=> Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xefb069ce

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2    *      3,074,048   330,754,039   327,679,992   7 HPFS/NTFS
/dev/sda3         394,242,048   781,420,543   387,178,496   7 HPFS/NTFS
/dev/sda4         330,762,285   394,235,099    63,472,815   5 Extended
/dev/sda5         330,762,348   389,351,339    58,588,992  83 Linux
/dev/sda6         389,351,403   394,235,099     4,883,697  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="803003E63003E250" LABEL="WinRE" TYPE="ntfs" 
/dev/sda2: UUID="222405FE2405D627" LABEL="Vista" TYPE="ntfs" 
/dev/sda3: UUID="4E9008209008115F" LABEL="Data" TYPE="ntfs" 
/dev/sda5: UUID="49aa06a2-8d24-41b5-84ac-eeff328574d2" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="fa253903-2240-48d8-9dc2-8f1d9c95fa4e" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sda2 on /media/Vista type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)



sda5/boot/grub/menu.lst:

title        Ubuntu 8.10, kernel 2.6.27-11-generic
uuid        49aa06a2-8d24-41b5-84ac-eeff328574d2
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=49aa06a2-8d24-41b5-84ac-eeff328574d2 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-11-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid        49aa06a2-8d24-41b5-84ac-eeff328574d2
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=49aa06a2-8d24-41b5-84ac-eeff328574d2 ro  single
initrd        /boot/initrd.img-2.6.27-11-generic

title        Ubuntu 8.10, kernel 2.6.27-7-generic
uuid        49aa06a2-8d24-41b5-84ac-eeff328574d2
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=49aa06a2-8d24-41b5-84ac-eeff328574d2 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid        49aa06a2-8d24-41b5-84ac-eeff328574d2
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=49aa06a2-8d24-41b5-84ac-eeff328574d2 ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, memtest86+
uuid        49aa06a2-8d24-41b5-84ac-eeff328574d2
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista/Longhorn (loader)
root        (hd0,1)
savedefault
makeactive
chainloader    +1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=49aa06a2-8d24-41b5-84ac-eeff328574d2 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=fa253903-2240-48d8-9dc2-8f1d9c95fa4e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 190.2GB: boot/grub/menu.lst
 190.1GB: boot/grub/stage2
 190.2GB: boot/initrd.img-2.6.27-11-generic
 190.1GB: boot/initrd.img-2.6.27-7-generic
 190.2GB: boot/vmlinuz-2.6.27-11-generic
 190.2GB: boot/vmlinuz-2.6.27-7-generic
 190.2GB: initrd.img
 190.1GB: initrd.img.old
 190.2GB: vmlinuz
 190.2GB: vmlinuz.old
```
thanks in advance

---

### Post by milagros on 2009-05-08
i forgot to refer that i installed  xubuntu 8.10 ,!!!

---

### Post by caljohnsmith on 2009-05-08
So I guess I'm not understanding your Grub problem, because you were booted into your Ubuntu 8.10 Ubuntu install on sda5 when you ran the Boot Info Script. Are you still getting a Grub error 17 on start up? Please explain your problem in more detail.

John

---

### Post by milagros on 2009-05-08
> **caljohnsmith said:**
> So I guess I'm not understanding your Grub problem, because you were booted into your Ubuntu 8.10 Ubuntu install on sda5 when you ran the Boot Info Script. Are you still getting a Grub error 17 on start up? Please explain your problem in more detail.

John

You' re right,when i boot it says loading stage 1.5,loading please wait..is it a problem??
thanks for your help
if

---

### Post by caljohnsmith on 2009-05-08
> **milagros said:**
> You' re right,when i boot it says loading stage 1.5,loading please wait..is it a problem??
thanks for your help
if
It's not a problem if Grub briefly flashes a message about loading stage 1.5. As long as you aren't still getting a Grub error 17 you should be fine now. 

John

---

### Post by milagros on 2009-05-08
> **caljohnsmith said:**
> It's not a problem if Grub briefly flashes a message about loading stage 1.5. As long as you aren't still getting a Grub error 17 you should be fine now. 

John
thanks thanks thanks!!!!!!!!!!!!

---

### Post by emyemy on 2009-06-20
Pleeeeeeeeeeeeeeeease help me
 i did what you said exactly and got that:
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #9 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda3 and 
                       looks at sector 139337346 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #3 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa241ca69

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    16,691,534    16,691,472   c W95 FAT32 (LBA)
/dev/sda2          16,691,535   135,749,249   119,057,715   f W95 Ext d (LBA)
/dev/sda5          16,691,598    27,053,459    10,361,862   b W95 FAT32
/dev/sda6          27,053,523    68,083,469    41,029,947   b W95 FAT32
/dev/sda7          68,083,533   109,177,739    41,094,207   b W95 FAT32
/dev/sda8         109,177,803   131,749,064    22,571,262   b W95 FAT32
/dev/sda9         131,749,128   135,749,249     4,000,122  82 Linux swap / Solaris
/dev/sda3         135,749,250   156,296,384    20,547,135  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="E443-2619" TYPE="vfat" 
/dev/sda3: UUID="e9c86e06-4b62-4bf5-9eb4-c83590126ff0" TYPE="ext3" 
/dev/sda5: LABEL="HOLLYWOOD" UUID="4818-495F" TYPE="vfat" 
/dev/sda6: LABEL="ORIGINAL" UUID="4818-4B11" TYPE="vfat" 
/dev/sda7: UUID="9030-96DE" TYPE="vfat" 
/dev/sda8: LABEL="SiM-6M-QM-4M-^KM-bM-vM-brM-U" UUID="4818-4C51" TYPE="vfat" 
/dev/sda9: TYPE="swap" UUID="9b6bcd42-e822-464a-8097-3e61c7169fc4" 

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
/dev/sda5 on /media/HOLLYWOOD type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)
/dev/sda6 on /media/ORIGINAL type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)
/dev/sda8 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)
/dev/sda7 on /media/disk-1 type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)
/dev/sda1 on /media/disk-2 type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)
/dev/sda3 on /media/disk-3 type ext3 (rw,nosuid,nodev,uhelper=hal)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="ArabLionZ XP SP3 V1 ( 2007 )" /noexecute=optin /fastdetect 

================================ sda1/BOOT.INI: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="ArabLionZ XP SP3 V1 ( 2007 )" /noexecute=optin /fastdetect 

=========================== sda3/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=e9c86e06-4b62-4bf5-9eb4-c83590126ff0 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e9c86e06-4b62-4bf5-9eb4-c83590126ff0

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
uuid        e9c86e06-4b62-4bf5-9eb4-c83590126ff0
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=e9c86e06-4b62-4bf5-9eb4-c83590126ff0 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        e9c86e06-4b62-4bf5-9eb4-c83590126ff0
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=e9c86e06-4b62-4bf5-9eb4-c83590126ff0 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        e9c86e06-4b62-4bf5-9eb4-c83590126ff0
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        ArabLionZ XP SP3 V1 ( 2007 )
rootnoverify    (hd0,0)
savedefault
chainloader    +1


=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=e9c86e06-4b62-4bf5-9eb4-c83590126ff0 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=9b6bcd42-e822-464a-8097-3e61c7169fc4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


  71.3GB: boot/grub/menu.lst
  71.3GB: boot/grub/stage2
  71.2GB: boot/initrd.img-2.6.28-11-generic
  71.2GB: boot/vmlinuz-2.6.28-11-generic
  71.2GB: initrd.img
  71.2GB: vmlinuz




when I tried to dir this file this what i've got

plain_io: Input/output error
init A: could not read boot sector
Cannot initialize 'A:'



please tell me what is the problem I'm new in UBUNTU

---

