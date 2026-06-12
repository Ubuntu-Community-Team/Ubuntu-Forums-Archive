---
title: "cannot boot windows xp after ubuntu installation"
date: 2009-04-17
forum: Installation &amp; Upgrades
---

### Post by shlteater on 2009-04-17
It happens to me that I selected to install my grub in the windows xp partition when I'm installing Ubuntu 8.04, and then I cannot boot 
windows xp. Then I tried to reinstall Ubuntu, this time I install grub
in the ubuntu partition. But now I cannot boot windows either.
I've tried this post [http://ubuntuforums.org/showthread.php?t=1074973](http://ubuntuforums.org/showthread.php?t=1074973)
and find my situation deferent from that.

when I press windows
It displays
 
starting...
GRUB stage2

and doing nothing

---------------------------------------
My menu.lst is here
## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=6e381f3a-44b1-4c9e-97e9-a8078bc08262 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=6e381f3a-44b1-4c9e-97e9-a8078bc08262 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,7)
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

---------------------------------
and I tried this [https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)
and find there are 2 grubs in my system
<code>
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #8 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda1 and 
                       looks at sector 1 on boot drive #119 for the stage2 
                       file. A stage2 file is at this location on /dev/sda. 
                       Stage2 looks on the same partition for 
                       /boot/grub/stage2. No errors found in the Boot 
                       Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda8 and 
                       looks at sector 22041013 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #8 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf0b1ebb0

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    18,426,554    18,426,492   7 HPFS/NTFS
/dev/sda3          18,426,555   108,422,684    89,996,130   f W95 Ext d (LBA)
/dev/sda5          40,965,813    81,931,499    40,965,687   b W95 FAT32
/dev/sda6          81,931,563   108,422,684    26,491,122   b W95 FAT32
/dev/sda7          18,426,681    20,402,549     1,975,869  82 Linux swap / Solaris
/dev/sda8          20,402,613    40,965,749    20,563,137  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="80C2F69090FA0800" LABEL="SYSTEM" TYPE="ntfs" 
/dev/sda5: LABEL="M-HM-mM-<M-~" UUID="6692-03B4" TYPE="vfat" 
/dev/sda6: LABEL="M-FM-dM-KM-{" UUID="7ADD-7711" TYPE="vfat" 
/dev/sda7: TYPE="swap" UUID="8a455d27-defb-44ab-9798-99c57f78c92a" 
/dev/sda8: UUID="6e381f3a-44b1-4c9e-97e9-a8078bc08262" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda8 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/shlteater/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=shlteater)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=3

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda8/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=6e381f3a-44b1-4c9e-97e9-a8078bc08262 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,7)

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=6e381f3a-44b1-4c9e-97e9-a8078bc08262 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=6e381f3a-44b1-4c9e-97e9-a8078bc08262 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,7)
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


=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=6e381f3a-44b1-4c9e-97e9-a8078bc08262 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=8a455d27-defb-44ab-9798-99c57f78c92a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda8: Location of files loaded by Grub: ===================


  11.3GB: boot/grub/menu.lst
  11.2GB: boot/grub/stage2
  11.3GB: boot/initrd.img-2.6.24-19-generic
  11.3GB: boot/vmlinuz-2.6.24-19-generic
  11.3GB: initrd.img
  11.3GB: vmlinuz
=============================== StdErr Messages: ===============================

umount: /tmp/BootInfo/sda5: device is busy
umount: /tmp/BootInfo/sda5: device is busy
</code>



---------------------------------------
can anyone help me with the problem??
Thanks a lot

---

### Post by Herman on 2009-04-17
You can install GRUB to the MBR of any hard disk.
You can install GRUB to the first sector, (boot sector) of a Linux partition.
You shouldn't install GRUB to the first sector (boot sector) of any Windows partition.

Never mind and don't worry, it's easy to fix, just boot your Windows XP 'Installation CD', open a  [Windows XP Recovery Console]("http://www.kellys-korner-xp.com/win_xp_rec.htm") and run FIXBOOT, and that should fix your Windows boot sector for you.

Don't run 'FIXMBR though, because that will overwrite the GRUB boot code in your MBR, which will mean you'll only be able to boot Windows then, and you'll need to re-install GRUB again.

Another way, in case you don't have a Windows XP 'Installation Disc', is to use TestDisc in Ubuntu.
```
sudo apt-get install testdisk  
``````
sudo testdisk 
```... and follow the steps detailed in this link: [12 NTFS Boot sector recovery]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery")

Regards, Herman :)

---

### Post by shlteater on 2009-04-19
Thanks for your helping:D
sorry I've been out these days:P
when I follow the step in fix NTFS partition
and press [Rebuild BS]
it says 'Extrapolated boot sector and current boot sector are identical'
and I cannot get any further to rebuild my boot sector
but still I cannot boot windows
Is there something wrong here??

---

### Post by shlteater on 2009-04-19
Oh I see there's no backup BS for me 
so I have to use the windows CD:)

---

### Post by meierfra. on 2009-04-20
> when I follow the step in fix NTFS partition
and press [Rebuild BS]
> Oh I see there's no backup BS for me 

Just for future reference. Never use "RebuildBS" before "Backup BS".  
RebuildBS only changes the  Boot Parameter Block (the first 80 bytes of the Boot sector) and then  copies the whole boot sector to last sector of the partition. This erases the backup boot sector and "BackUp BS" no longer works, 

> so I have to use the windows CD

If "fixboot" from the Windows CD does not work, come back here. There are  other options available.

---

