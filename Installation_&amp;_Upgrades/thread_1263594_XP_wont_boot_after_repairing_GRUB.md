---
title: "XP wont boot after repairing GRUB"
date: 2009-09-11
forum: Installation &amp; Upgrades
---

### Post by fourtyseven on 2009-09-11
I've been running an Ubuntu/XP dual boot system at work for about a year. Physically I have two drives, one with Ubuntu and the other with XP.
A few days ago I got a copy of Kubuntu and since Ive never seen it I thought I'd install a third hard drive and install Kubuntu on that.
This however messed up GRUB. I removed the third harddrive (Kubuntu) and eventually managed to repair GRUB so that I can now boot into Ubuntu.
Problem is that now I cant boot into XP, even though it appears in the boot menu. If I try to boot into XP all I get is the message: Starting Up... and thats where it hangs. I have edited the menu.lst file numerous times and have changed the root entry to just about every number I can think of. Still cant boot into XP. Please advise.
:guitar:

---

### Post by TobiasV on 2009-09-11
Could we see your menu.lst file please?

And a ```
sudo fdisk -l
``` please?

---

### Post by louieb on 2009-09-11
Sounds like in your attempt to fix GRUB you may have overwritten the Windows partition boot record. It can be easily fixed, but 1st  want to be sure thats what happened.

Please get the [Boot Info Script - SourceForge.net]("http://sourceforge.net/projects/bootinfoscript/") and put the resultst.txt in your next post. 

to run 
```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop;  It's long - Please use code tags.

---

### Post by TobiasV on 2009-09-11
> **louieb said:**
> Sounds like in your attempt to fix GRUB you may have overwritten the Windows partition boot record. It can be easily fixed, but 1st  want to be sure thats what happened.

Please get the [Boot Info Script - SourceForge.net]("http://sourceforge.net/projects/bootinfoscript/") and put the resultst.txt in your next post. 

to run 
```
sudo bash ~/Desktop/boot_info_script*.sh
```That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop;  It's long - Please use code tags.

Nice script... definitely  going to use that in the future, thanks.

Back on topic, it does sound like Windows' own boot loader isn't working.

---

### Post by fourtyseven on 2009-09-11
Pretty cool script. I believe the results have everything everyone asked for.

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #1 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /ubuntu/winboot/menu.lst /boot.ini /ntldr 
                       /NTDETECT.COM /wubildr.mbr /ubuntu/winboot/wubildr.mbr

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sdb1 and 
                       looks at sector 130842751 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 8.04.3 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x86848684

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   156,280,319   156,280,257   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe102e102

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   150,464,789   150,464,727  83 Linux
/dev/sdb2         150,464,790   156,296,384     5,831,595   5 Extended
/dev/sdb5         150,464,853   156,296,384     5,831,532  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="DC5450745450537E" TYPE="ntfs" 
/dev/sdb1: UUID="881039a7-f687-4ecb-9806-bd1b55ea92fc" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="efe6cac7-7e5f-42b4-be2b-4566ada0c322" 

=============================== "mount" output: ===============================

/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-24-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/alan/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=alan)


======================== sda1/ubuntu/winboot/menu.lst: ========================

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

================================ sda1/boot.ini: ================================

[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
c:\wubildr.mbr="Ubuntu"

=================== sda1: Location of files loaded by Grub: ===================


  14.0GB: boot/grub/stage2

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
# kopt=root=UUID=881039a7-f687-4ecb-9806-bd1b55ea92fc ro

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
# defoptions=xforcevesa

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

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=881039a7-f687-4ecb-9806-bd1b55ea92fc ro xforcevesa
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=881039a7-f687-4ecb-9806-bd1b55ea92fc ro single
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=881039a7-f687-4ecb-9806-bd1b55ea92fc ro xforcevesa
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=881039a7-f687-4ecb-9806-bd1b55ea92fc ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=881039a7-f687-4ecb-9806-bd1b55ea92fc ro xforcevesa
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=881039a7-f687-4ecb-9806-bd1b55ea92fc ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.3 LTS, memtest86+
root		(hd1,0)
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


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=881039a7-f687-4ecb-9806-bd1b55ea92fc /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=efe6cac7-7e5f-42b4-be2b-4566ada0c322 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  67.0GB: boot/grub/menu.lst
  67.1GB: boot/grub/stage2
  67.0GB: boot/initrd.img-2.6.24-19-generic
  67.0GB: boot/initrd.img-2.6.24-19-generic.bak
  67.0GB: boot/initrd.img-2.6.24-23-generic
  66.9GB: boot/initrd.img-2.6.24-23-generic.bak
  67.1GB: boot/initrd.img-2.6.24-24-generic
  67.0GB: boot/initrd.img-2.6.24-24-generic.bak
  67.0GB: boot/vmlinuz-2.6.24-19-generic
  67.0GB: boot/vmlinuz-2.6.24-23-generic
  67.0GB: boot/vmlinuz-2.6.24-24-generic
  54.1GB: grub/stage2
  67.1GB: initrd.img
  67.0GB: initrd.img.old
  67.0GB: vmlinuz
  67.0GB: vmlinuz.old

```

---

### Post by TobiasV on 2009-09-11
> **fourtyseven said:**
> Pretty cool script. I believe the results have everything everyone asked for.

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #1 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /ubuntu/winboot/menu.lst /boot.ini /ntldr 
                       /NTDETECT.COM /wubildr.mbr /ubuntu/winboot/wubildr.mbr

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sdb1 and 
                       looks at sector 130842751 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 8.04.3 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x86848684

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   156,280,319   156,280,257   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe102e102

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   150,464,789   150,464,727  83 Linux
/dev/sdb2         150,464,790   156,296,384     5,831,595   5 Extended
/dev/sdb5         150,464,853   156,296,384     5,831,532  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="DC5450745450537E" TYPE="ntfs" 
/dev/sdb1: UUID="881039a7-f687-4ecb-9806-bd1b55ea92fc" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="efe6cac7-7e5f-42b4-be2b-4566ada0c322" 

=============================== "mount" output: ===============================

/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-24-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/alan/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=alan)


======================== sda1/ubuntu/winboot/menu.lst: ========================

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

================================ sda1/boot.ini: ================================

[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
c:\wubildr.mbr="Ubuntu"

=================== sda1: Location of files loaded by Grub: ===================


  14.0GB: boot/grub/stage2

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
# kopt=root=UUID=881039a7-f687-4ecb-9806-bd1b55ea92fc ro

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
# defoptions=xforcevesa

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
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=881039a7-f687-4ecb-9806-bd1b55ea92fc ro xforcevesa
initrd        /boot/initrd.img-2.6.24-24-generic
quiet

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=881039a7-f687-4ecb-9806-bd1b55ea92fc ro single
initrd        /boot/initrd.img-2.6.24-24-generic

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=881039a7-f687-4ecb-9806-bd1b55ea92fc ro xforcevesa
initrd        /boot/initrd.img-2.6.24-23-generic
quiet

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=881039a7-f687-4ecb-9806-bd1b55ea92fc ro single
initrd        /boot/initrd.img-2.6.24-23-generic

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-19-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=881039a7-f687-4ecb-9806-bd1b55ea92fc ro xforcevesa
initrd        /boot/initrd.img-2.6.24-19-generic
quiet

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-19-generic (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=881039a7-f687-4ecb-9806-bd1b55ea92fc ro single
initrd        /boot/initrd.img-2.6.24-19-generic

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
# on /dev/sda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=881039a7-f687-4ecb-9806-bd1b55ea92fc /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=efe6cac7-7e5f-42b4-be2b-4566ada0c322 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  67.0GB: boot/grub/menu.lst
  67.1GB: boot/grub/stage2
  67.0GB: boot/initrd.img-2.6.24-19-generic
  67.0GB: boot/initrd.img-2.6.24-19-generic.bak
  67.0GB: boot/initrd.img-2.6.24-23-generic
  66.9GB: boot/initrd.img-2.6.24-23-generic.bak
  67.1GB: boot/initrd.img-2.6.24-24-generic
  67.0GB: boot/initrd.img-2.6.24-24-generic.bak
  67.0GB: boot/vmlinuz-2.6.24-19-generic
  67.0GB: boot/vmlinuz-2.6.24-23-generic
  67.0GB: boot/vmlinuz-2.6.24-24-generic
  54.1GB: grub/stage2
  67.1GB: initrd.img
  67.0GB: initrd.img.old
  67.0GB: vmlinuz
  67.0GB: vmlinuz.old

```

Well, your menu.lst seems alright. And well, the way I read the result.txt, you've installed GRUB on both your harddrives, which could probably do something to the Windows boot loader thingy, which the next part indicates as well. The bootfiles/dir seems completely messed up. So I'd suggest repairing the master boot record from the XP CD.

Now I can't remember for sure how to do that.

I think it's something like booting off the installation media, entering a recovery console, and then I THINK the command is "/fixmbr" or something like that... (Google it). Just in case, I'd disable your Linux harddrive first.

---

### Post by ronparent on 2009-09-11
If you are finding /boot/grub/stage2 you are apparently booting on sdb (set a first in boot order in bios). That being the case, your windows booting instruction should be as follows:
[B]
title		Microsoft Windows XP Professional
rootnoverify		(hd1,0)
map (hdo) (hd1)
map (hd1) (hd0)
chainloader	+1[/B]

Windows has to boot on (hd0) and if it is not located there (in grub terms as found at boot time) it is necessary to foll it into thinking it is on (hd0). Thus the reason for the map commands.

---

### Post by TobiasV on 2009-09-11
As far as I read, /boot/grub/stage2 exists on both drives, so how do you know he's booting off the sdb?

Anyway, you seem to know this better than me, so I'll just leave it to you. :)

---

### Post by fourtyseven on 2009-09-11
> **ronparent said:**
> 
title		Microsoft Windows XP Professional
rootnoverify		(hd1,0)
map (hdo) (hd1)
map (hd1) (hd0)
chainloader	+1

That did the trick! I can now boot into both OS's again. Thank you for your help.

---

### Post by presence1960 on 2009-09-11
> **TobiasV said:**
> As far as I read, /boot/grub/stage2 exists on both drives, so how do you know he's booting off the sdb?

Anyway, you seem to know this better than me, so I'll just leave it to you. :)

if you look at the boot info summary on the script output you will see that GRUB installed on sda points to a windows partition. if that sda is the disk booting first in BIOS there would be a GRUB error because menu.lst does not exist in the windows partition. 

**EDIT:** actually after rereading the script GRUB in sda tells you it looks in boot drive #1 for 1st partition. So that tells you sda does not boot first-sdb does. When using (hdx,y) in GRUB it is the order of booting in BIOS which gives devices there x designation. Since sdb boots first it is (hd0) and sda becomes (hd1). Ubuntu & fdisk sometimes assign order differently than BIOS.

See:

```
============================= Boot Info Summary: ==============================

 =[COLOR="Red"]> Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #1 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.[/COLOR]
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /ubuntu/winboot/menu.lst /boot.ini /ntldr 
                       /NTDETECT.COM /wubildr.mbr /ubuntu/winboot/wubildr.mbr


```

---

### Post by ronparent on 2009-09-11
Great to hear you are up and running. Your posting of the boot info script was extremely helpful in pin pointing the problem - good inititive. Good luck and have fun.

Ron

---

### Post by TobiasV on 2009-09-11
Well thanks for the explanation. :) Learning new things is always good.

But how come the "boot files/dirs" include "/ubuntu/winboot/menu.lst" and "/ubuntu/winboot/wubildr.mbr"? :S

---

### Post by presence1960 on 2009-09-11
> **TobiasV said:**
> Well thanks for the explanation. :) Learning new things is always good.

But how come the "boot files/dirs" include "/ubuntu/winboot/menu.lst" and "/ubuntu/winboot/wubildr.mbr"? :S

It looks like the OP had a wubi installation. When wubi is uninstalled the boot.ini must be edited to remove the reference to wubi.

---

### Post by TobiasV on 2009-09-11
Ah right, thanks for explaining that. I never experimented with Wubi. :)

---

### Post by louieb on 2009-09-11
> **TobiasV said:**
>  I never experimented with Wubi. :)
lol - well somebody has  - anyway bring up windows add/remove programs and see if its still there. 

Nice to see you got dual boot working again.

---

### Post by fourtyseven on 2009-09-14
Thanks to everyone who replied to this post; your help has been invaluable. My pc is now up and running again as normal.

---

