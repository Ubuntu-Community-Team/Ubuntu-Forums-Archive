---
title: "Re: Recovering deleted directories/folders"
date: 2009-02-11
forum: Installation &amp; Upgrades
---

### Post by Adock on 2009-02-11
Hello,
1:The following is a previous post I've made a few weeks ago,
with the reply, and instructions on what to do.

This concerns the recovery of Ubuntu files, which I've
deleted.

Before I ran the bash script; I reinstalled Ubuntu.

Here are the results of the "RESULTS.txt" file posted
below the two previous posts.

2:I don't know on which drive Ubuntu is installed on?
  I tried: sudo fdisk - 1; and received this result:
  fdisk: Invalid option -- 1.

3:If the boot info summary is O.K. I want to get on the internet
  with Ubuntu.I've used the "listMdm" utility, got the modem info,
  then went to:"linuxant- linux drivers for conexant chipsets,"
  and downloaded the file:HCFP_WinXP.

  Where do I extract this file to; and what do I do next?
  I hope this is an appropriate post.

  Thank you.
______________________________________________________________
	
Recovering deleted directories/folders

Hello,
I'm running Ubuntu 8.04 LTS Hardy Heron Desktop CD 32 bit,
on a multi-boot system.
I'm not able to get on the internet with it as yet.

After it installed; I realized I was in over my head,
being a new user on this platform.

There were four or five directories/folders, including
the uninstall icon, on my "E" drive; plus Ubuntu was
installed in control panel of Win' XP- Pro, on my "D"
drive.

I've uninstalled it, and deleted the directories/folders;
to my surprise it still remained on the bootstrap, and
I'm able to boot into it.

Question? Is there a way that I can recover these
directories/folders, through the terminal?

Your help will be much appreciated.

Thank you.

____________________________________________________________
-- 
 
caljohnsmith's Avatar
 
Join Date: Mar 2008
Location: California, USA
Posts: 6,223
	
Re: Recovering deleted directories/folders
Was your Ubuntu a Wubi install? In other words, was it installed inside of Windows? If so, you might be still seeing it in your Windows boot loader on start up. Do you have a Ubuntu Live CD you can boot and use? If so, how about booting that, download the Boot Info Script to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
Code:

sudo bash ~/Desktop/boot_info_script*.sh

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup related to any booting problems you might have.
_________________________________________________________________________________________________________________________________________

```
[CODE]============================= 
```[/CODE]Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No known boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTLDR /NTDETECT.COM /ntdetect.com

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     
    Operating System:  Windows XP
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     
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
    Boot file info:     
    Operating System:  Ubuntu 8.04
    Boot files/dirs:   /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Boot file info:     
    Operating System:  Ubuntu 8.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTLDR /NTDETECT.COM /ntdetect.com

sdb2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     
    Operating System:  Windows XP
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     
    Operating System:  
    Boot files/dirs:   

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Boot file info:     
    Operating System:  Ubuntu 8.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x85579427

Partition  Boot        Start          End         Size  Id System

/dev/sda1    *            63   41,945,714   41,945,652   c W95 FAT32 (LBA)
/dev/sda2         41,945,715  176,168,789  134,223,075   c W95 FAT32 (LBA)
/dev/sda3        176,168,790  177,470,054    1,301,265   c W95 FAT32 (LBA)
/dev/sda4        177,470,055  312,576,704  135,106,650   5 Extended
/dev/sda5        310,391,928  312,351,794    1,959,867  83 Linux
/dev/sda6        312,351,858  312,576,704      224,847  82 Linux swap / Solaris
/dev/sda7        177,470,181  305,845,469  128,375,289  83 Linux
/dev/sda8        305,845,533  310,391,864    4,546,332  82 Linux swap / Solaris


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 30.7 GB, 30750031872 bytes
255 heads, 63 sectors/track, 3738 cylinders, total 60058656 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x90359035

Partition  Boot        Start          End         Size  Id System

/dev/sdb1    *            63   16,787,924   16,787,862   c W95 FAT32 (LBA)
/dev/sdb2         16,787,925   44,066,294   27,278,370   c W95 FAT32 (LBA)
/dev/sdb3         44,066,295   54,556,739   10,490,445   c W95 FAT32 (LBA)
/dev/sdb4         54,556,740   60,050,969    5,494,230   5 Extended
/dev/sdb5         54,556,803   59,681,474    5,124,672  83 Linux
/dev/sdb6         59,681,538   60,050,969      369,432  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="WIN98" UUID="58E8-0D4E" TYPE="vfat" 
/dev/sda2: LABEL="WINXP" UUID="6120-6E39" TYPE="vfat" 
/dev/sda3: UUID="AE32-C207" TYPE="vfat" 
/dev/sda5: UUID="b5628a68-9063-46d3-b81e-10bab99f4cce" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="1451a801-23a3-4987-94a4-9f06da10dae7" TYPE="swap" 
/dev/sda7: UUID="db847159-7b68-4257-bdc3-d66eb6a9a273" TYPE="ext3" 
/dev/sda8: UUID="7ff7da77-ad60-4e0b-882f-c96f3ea58a39" TYPE="swap" 
/dev/sdb1: UUID="1C45-13E0" TYPE="vfat" 
/dev/sdb2: UUID="8BB1-8BB1" TYPE="vfat" 
/dev/sdb3: UUID="8BB1-8BB2" TYPE="vfat" 
/dev/sdb5: UUID="017dbe3a-2380-4ace-aca3-8ae5da8781c4" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb6: TYPE="swap" UUID="4047f6b1-56de-4323-9779-a02f9e8eb561" 

=============================== "mount" output: ===============================

/dev/sda7 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/pellum/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=pellum)
/dev/sda2 on /media/WINXP type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

================================ sda1/boot.ini: ================================

[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
C:\ = "Microsoft Windows 98"

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=b5628a68-9063-46d3-b81e-10bab99f4cce /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=1451a801-23a3-4987-94a4-9f06da10dae7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location  of files loaded by Grub: ===================


 159.6GB: boot/initrd.img-2.6.24-16-generic.bak
 159.6GB: boot/vmlinuz-2.6.24-16-generic
 159.6GB: vmlinuz

=========================== sda7/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=db847159-7b68-4257-bdc3-d66eb6a9a273 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=db847159-7b68-4257-bdc3-d66eb6a9a273 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=db847159-7b68-4257-bdc3-d66eb6a9a273 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,6)
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
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04 (8.04) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sda5 
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu 8.04, kernel 2.6.24-16-generic (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=017dbe3a-2380-4ace-aca3-8ae5da8781c4 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode) (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=017dbe3a-2380-4ace-aca3-8ae5da8781c4 ro single 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu 8.04, memtest86+ (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=db847159-7b68-4257-bdc3-d66eb6a9a273 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=7ff7da77-ad60-4e0b-882f-c96f3ea58a39 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda7: Location  of files loaded by Grub: ===================


 104.6GB: boot/grub/menu.lst
 104.7GB: boot/grub/stage2
 104.6GB: boot/initrd.img-2.6.24-16-generic
 104.7GB: boot/initrd.img-2.6.24-16-generic.bak
 104.7GB: boot/vmlinuz-2.6.24-16-generic
 104.6GB: initrd.img
 104.7GB: vmlinuz

================================ sdb1/boot.ini: ================================

[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
C:\ = "Microsoft Windows"

=========================== sdb5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=017dbe3a-2380-4ace-aca3-8ae5da8781c4 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,4)

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=017dbe3a-2380-4ace-aca3-8ae5da8781c4 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=017dbe3a-2380-4ace-aca3-8ae5da8781c4 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,4)
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
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb5
UUID=017dbe3a-2380-4ace-aca3-8ae5da8781c4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb6
UUID=4047f6b1-56de-4323-9779-a02f9e8eb561 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location  of files loaded by Grub: ===================


  28.1GB: boot/grub/menu.lst
  28.1GB: boot/grub/stage2
  28.1GB: boot/initrd.img-2.6.24-16-generic
  28.0GB: boot/initrd.img-2.6.24-16-generic.bak
  28.0GB: boot/vmlinuz-2.6.24-16-generic
  28.1GB: initrd.img
  28.0GB: vmlinuz

=========================== Unknown MBRs or Boot Sectors =======================

Unknown MBR on /dev/sdb

00000000  eb 31 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |.1..............|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000030  00 00 80 fa 33 c0 8e d8  8e d0 bc 00 7c b8 e0 07  |....3.......|...|
00000040  8e c0 fb b8 00 b8 8e e8  e8 1d 00 b9 03 00 b8 28  |...............(|
00000050  02 32 f6 2e 8a 16 32 7c  bb 00 01 50 cd 13 72 03  |.2....2|...P..r.|
00000060  58 cd 13 ea 00 01 e0 07  60 b9 e8 03 33 db 66 65  |X.......`...3.fe|
00000070  c7 07 00 00 00 00 83 c3  04 e2 f3 b4 02 32 ff 33  |.............2.3|
00000080  d2 cd 10 61 c3 60 b4 a0  f6 e4 32 ff d1 e3 03 d8  |...a.`....2.....|
00000090  8a 14 0a d2 74 09 65 89  17 46 83 c3 02 eb f1 61  |....t.e..F.....a|
000000a0  c3 37 74 6f 6f 6c 73 00  4c 6f 61 64 69 6e 67 2e  |.7tools.Loading.|
000000b0  2e 2e 2e 00 4d 42 52 20  52 65 76 69 73 69 6f 6e  |....MBR Revision|
000000c0  20 30 00 ef ee fe ff ef  ee fe ff ef ee fe ff ef  | 0..............|
000000d0  ee fe ff ef ee fe ff ef  ee fe ff ef ee fe ff ef  |................|
*
000001a0  00 00 00 00 00 00 00 00  70 69 9f cb 4f 1e 99 db  |........pi..O...|
000001b0  02 00 00 00 3b 59 2e 1f  35 90 35 90 00 00 80 01  |....;Y..5.5.....|
000001c0  01 00 0c fe ff ff 3f 00  00 00 96 29 00 01 00 00  |......?....)....|
000001d0  c1 ff 0c fe ff ff d5 29  00 01 22 3c a0 01 00 00  |.......).."<....|
000001e0  c1 ff 0c fe ff ff f7 65  a0 02 4d 12 a0 00 00 fe  |.......e..M.....|
000001f0  ff ff 05 fe ff ff 44 78  40 03 d6 d5 53 00 55 aa  |......Dx@...S.U.|
00000200

Unknown BootLoader  on sda2

00000000  eb 58 90 50 41 52 41 47  4f 4e 23 00 02 40 20 00  |.X.PARAGON#..@ .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 73 0a 80 02  |........?...s...|
00000020  da 14 00 08 fd 3f 00 00  00 00 00 00 02 00 00 00  |.....?..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 39 6e 20 61 20  20 20 20 20 20 20 20 20  |..)9n a         |
00000050  20 20 46 41 54 33 32 20  20 20 8c c8 8e d0 bc ff  |  FAT32   ......|
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

Unknown BootLoader  on sda3

00000000  eb 58 90 4d 53 57 49 4e  34 2e 31 00 02 10 62 00  |.X.MSWIN4.1...b.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 56 1f 80 0a  |........?...V...|
00000020  11 db 13 00 7c 02 00 00  00 00 00 00 02 00 00 00  |....|...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 07 c2 32 ae 4e  4f 20 4e 41 4d 45 20 20  |..)..2.NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 8c c8 8e d0 bc ff  |  FAT32   ......|
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

Unknown BootLoader  on sdb2

00000000  eb 58 90 50 41 52 41 47  4f 4e 23 00 02 10 20 00  |.X.PARAGON#... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 d5 29 00 01  |........?....)..|
00000020  22 3c a0 01 fb 33 00 00  00 00 00 00 02 00 00 00  |"<...3..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 b1 8b b1 8b 20  20 20 20 20 20 20 20 20  |..)....         |
00000050  20 20 46 41 54 33 32 20  20 20 8c c8 8e d0 bc ff  |  FAT32   ......|
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

Unknown BootLoader  on sdb3

00000000  eb 58 90 50 41 52 41 47  4f 4e 23 00 02 08 20 00  |.X.PARAGON#... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 f7 65 a0 02  |........?....e..|
00000020  4d 12 a0 00 f1 27 00 00  00 00 00 00 02 00 00 00  |M....'..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 b2 8b b1 8b 20  20 20 20 20 20 20 20 20  |..)....         |
00000050  20 20 46 41 54 33 32 20  20 20 8c c8 8e d0 bc ff  |  FAT32   ......|
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


=============================== StdErr Messages: ===============================

umount: /tmp/BootInfo/sdb3: device is busy
umount: /tmp/BootInfo/sdb3: device is busy

---

