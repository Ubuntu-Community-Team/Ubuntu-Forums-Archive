---
title: "Need help bad!!"
date: 2009-09-12
forum: Installation &amp; Upgrades
---

### Post by Jcpinny22 on 2009-09-12
alright well i downloaded ubuntu the other day and decided to try kubuntu as well..so i did kubuntu and i tried getting programs but said i didnt have enough space..so i did it again and selected the partitions manually and i did my external hard drive..well when i did that it made me have space..so i went back to my main OS(windows xp) and tried running Utorrent well it said my files could not be found(which are on the external hard drive) so i went to my computer and my external hard drive cannot be found..i tried all the usb ports on my computer and nothing...I have about 450gigs of items on the hard drive..pleas help me figure out how to read my hard drive again. i would like to be able to use it without formatting it but if thats what i have to do then ill do it...please help me!!

---

### Post by presence1960 on 2009-09-12
Let's get a better look at your setup. Boot the Ubuntu Live CD with the external plugged in.. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by rob-ward on 2009-09-12
If you boot into your ubuntu install and run the commands

mount

and 

sudo fdisk -l

and print the results here it may help diagnose the problem

---

### Post by presence1960 on 2009-09-12
> **rob-ward said:**
> If you boot into your ubuntu install and run the commands

mount

and 

sudo fdisk -l

and print the results here it may help diagnose the problem

The boot info script will include those plus a whole lot more. try running it on your machine and see how much info it gives you about your setup & boot process.

---

### Post by Jcpinny22 on 2009-09-12
there is the mount and sudo fdisk if i did it correct..the RESULTS.txt is a little lower

```
justin@justin-desktop:~$ mount
/dev/sdb4 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sr0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=justin)
justin@justin-desktop:~$ sudo fdisk -|
> sudo fdisk





and here is the RESULTS.txt file..cant add as attachment as it is to large of a file..


============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #4 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdg

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /BOOTMGR /Boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdg1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xce6507f8

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    20,434,679    20,434,617   7 HPFS/NTFS
/dev/sda2    *     20,434,680   625,140,399   604,705,720   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xffaac65e

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 1,757,816,234 1,757,814,187  82 Linux swap / Solaris
/dev/sdb2       1,943,061,750 1,953,520,064    10,458,315   5 Extended
/dev/sdb5       1,948,299,003 1,953,166,634     4,867,632  83 Linux
/dev/sdb6       1,953,166,698 1,953,520,064       353,367  82 Linux swap / Solaris
/dev/sdb7       1,943,061,876 1,947,945,509     4,883,634  83 Linux
/dev/sdb8       1,947,945,573 1,948,298,939       353,367  82 Linux swap / Solaris
/dev/sdb3       1,935,222,030 1,943,061,749     7,839,720  82 Linux swap / Solaris
/dev/sdb4       1,757,816,235 1,935,222,029   177,405,795  83 Linux


Drive: sdg ___________________ _____________________________________________________

Disk /dev/sdg: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7856127 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00a95a4f

Partition  Boot         Start           End          Size  Id System

/dev/sdg1    *             63     7,856,126     7,856,064   e W95 FAT16 (LBA)


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="BE58869458864B5B" LABEL="RECOVERY" TYPE="ntfs" 
/dev/sda2: UUID="162C0E412C0E1C7D" TYPE="ntfs" 
/dev/sdb1: UUID="fe756f54-0fce-4405-b99a-6af111ab3559" TYPE="swap" 
/dev/sdb3: UUID="be290b1c-6c22-4b04-86d3-3980e9764265" TYPE="swap" 
/dev/sdb4: UUID="28803cb3-7d79-404b-8c4c-183bc34ad5e1" TYPE="ext3" 
/dev/sdb5: UUID="45b7c7a1-e389-4f14-80e8-309b2e7685c5" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb6: UUID="24b83cd1-1932-49ba-ad6c-8df01b38ea51" TYPE="swap" 
/dev/sdb7: UUID="bb93fcd7-36b9-4954-b7c5-549eac95a96b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb8: UUID="ed64f54e-15a8-474a-84c1-800cc909c382" TYPE="swap" 
/dev/sdg1: SEC_TYPE="msdos" LABEL="IPREP_V009" UUID="3403-9419" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sdb4 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sr0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=justin)


================================ sda2/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

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
# kopt=root=UUID=45b7c7a1-e389-4f14-80e8-309b2e7685c5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=45b7c7a1-e389-4f14-80e8-309b2e7685c5

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		45b7c7a1-e389-4f14-80e8-309b2e7685c5
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=45b7c7a1-e389-4f14-80e8-309b2e7685c5 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		45b7c7a1-e389-4f14-80e8-309b2e7685c5
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=45b7c7a1-e389-4f14-80e8-309b2e7685c5 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		45b7c7a1-e389-4f14-80e8-309b2e7685c5
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=45b7c7a1-e389-4f14-80e8-309b2e7685c5 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=24b83cd1-1932-49ba-ad6c-8df01b38ea51 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by Jcpinny22 on 2009-09-12
here is the rest of the results.txt file
```



=================== sdb5: Location of files loaded by Grub: ===================


 998.8GB: boot/grub/menu.lst
 998.8GB: boot/grub/stage2
 998.3GB: boot/initrd.img-2.6.28-11-generic
 998.7GB: boot/vmlinuz-2.6.28-11-generic
 998.3GB: initrd.img
 998.7GB: vmlinuz

=========================== sdb7/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=bb93fcd7-36b9-4954-b7c5-549eac95a96b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=bb93fcd7-36b9-4954-b7c5-549eac95a96b

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		bb93fcd7-36b9-4954-b7c5-549eac95a96b
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=bb93fcd7-36b9-4954-b7c5-549eac95a96b ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		bb93fcd7-36b9-4954-b7c5-549eac95a96b
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=bb93fcd7-36b9-4954-b7c5-549eac95a96b ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		bb93fcd7-36b9-4954-b7c5-549eac95a96b
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=45b7c7a1-e389-4f14-80e8-309b2e7685c5 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=45b7c7a1-e389-4f14-80e8-309b2e7685c5 ro single 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu 9.04, memtest86+ (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sdb7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb7 during installation
UUID=bb93fcd7-36b9-4954-b7c5-549eac95a96b /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb8 during installation
UUID=ed64f54e-15a8-474a-84c1-800cc909c382 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb7: Location of files loaded by Grub: ===================


 996.3GB: boot/grub/menu.lst
 996.4GB: boot/grub/stage2
 995.3GB: boot/initrd.img-2.6.28-11-generic
 995.3GB: boot/vmlinuz-2.6.28-11-generic
 995.3GB: initrd.img
 995.3GB: vmlinuz

=========================== sdb4/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=28803cb3-7d79-404b-8c4c-183bc34ad5e1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=28803cb3-7d79-404b-8c4c-183bc34ad5e1

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		28803cb3-7d79-404b-8c4c-183bc34ad5e1
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=28803cb3-7d79-404b-8c4c-183bc34ad5e1 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		28803cb3-7d79-404b-8c4c-183bc34ad5e1
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=28803cb3-7d79-404b-8c4c-183bc34ad5e1 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		28803cb3-7d79-404b-8c4c-183bc34ad5e1
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=45b7c7a1-e389-4f14-80e8-309b2e7685c5 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=45b7c7a1-e389-4f14-80e8-309b2e7685c5 ro single 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu 9.04, memtest86+ (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb7.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sdb7)
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=bb93fcd7-36b9-4954-b7c5-549eac95a96b ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb7.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sdb7)
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=bb93fcd7-36b9-4954-b7c5-549eac95a96b ro single 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb7.
title		Ubuntu 9.04, memtest86+ (on /dev/sdb7)
root		(hd1,6)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sdb4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb4 during installation
UUID=28803cb3-7d79-404b-8c4c-183bc34ad5e1 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb1 during installation
UUID=fe756f54-0fce-4405-b99a-6af111ab3559 none            swap    sw              0       0
# swap was on /dev/sdb3 during installation
UUID=be290b1c-6c22-4b04-86d3-3980e9764265 none            swap    sw              0       0
# swap was on /dev/sdb6 during installation
UUID=24b83cd1-1932-49ba-ad6c-8df01b38ea51 none            swap    sw              0       0
# swap was on /dev/sdb8 during installation
UUID=ed64f54e-15a8-474a-84c1-800cc909c382 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb4: Location of files loaded by Grub: ===================


 947.5GB: boot/grub/menu.lst
 947.5GB: boot/grub/stage2
 947.6GB: boot/initrd.img-2.6.28-11-generic
 947.5GB: boot/vmlinuz-2.6.28-11-generic
 947.6GB: initrd.img
 947.5GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdg1

00000000  eb 3c 90 4d 53 57 49 4e  34 2e 31 00 02 80 08 00  |.<.MSWIN4.1.....|
00000010  02 00 02 00 00 f8 f0 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  c0 df 77 00 80 00 29 19  94 03 34 4e 4f 20 4e 41  |..w...)...4NO NA|
00000030  4d 45 20 20 20 20 46 41  54 31 36 20 20 20 fa 33  |ME    FAT16   .3|
00000040  c9 8e d1 bc fc 7b 16 07  bd 78 00 c5 76 00 1e 56  |.....{...x..v..V|
00000050  16 55 bf 22 05 89 7e 00  89 4e 02 b1 0b fc f3 a4  |.U."..~..N......|
00000060  06 1f bd 00 7c c6 45 fe  0f 8b 46 18 88 45 f9 38  |....|.E...F..E.8|
00000070  4e 24 7d 22 8b c1 99 e8  77 01 72 1a 83 eb 3a 66  |N$}"....w.r...:f|
00000080  a1 1c 7c 66 3b 07 8a 57  fc 75 06 80 ca 02 88 56  |..|f;..W.u.....V|
00000090  02 80 c3 10 73 ed 33 c9  8a 46 10 98 f7 66 16 03  |....s.3..F...f..|
000000a0  46 1c 13 56 1e 03 46 0e  13 d1 8b 76 11 60 89 46  |F..V..F....v.`.F|
000000b0  fc 89 56 fe b8 20 00 f7  e6 8b 5e 0b 03 c3 48 f7  |..V.. ....^...H.|
000000c0  f3 01 46 fc 11 4e fe 61  bf 00 07 e8 23 01 72 39  |..F..N.a....#.r9|
000000d0  38 2d 74 17 60 b1 0b be  d8 7d f3 a6 61 74 39 4e  |8-t.`....}..at9N|
000000e0  74 09 83 c7 20 3b fb 72  e7 eb dd be 7f 7d ac 98  |t... ;.r.....}..|
000000f0  03 f0 ac 84 c0 74 17 3c  ff 74 09 b4 0e bb 07 00  |.....t.<.t......|
00000100  cd 10 eb ee be 82 7d eb  e5 be 80 7d eb e0 98 cd  |......}....}....|
00000110  16 5e 1f 66 8f 04 cd 19  be 81 7d 8b 7d 1a 8d 45  |.^.f......}.}..E|
00000120  fe 8a 4e 0d f7 e1 03 46  fc 13 56 fe b1 04 e8 c1  |..N....F..V.....|
00000130  00 72 d6 ea 00 02 70 00  b4 42 eb 2d 60 66 6a 00  |.r....p..B.-`fj.|
00000140  52 50 06 53 6a 01 6a 10  8b f4 74 ec 91 92 33 d2  |RP.Sj.j...t...3.|
00000150  f7 76 18 91 f7 76 18 42  87 ca f7 76 1a 8a f2 8a  |.v...v.B...v....|
00000160  e8 c0 cc 02 0a cc b8 01  02 8a 56 24 cd 13 8d 64  |..........V$...d|
00000170  10 61 72 0a 40 75 01 42  03 5e 0b 49 75 77 c3 03  |.ar.@u.B.^.Iuw..|
00000180  18 01 27 0d 0a 49 6e 76  61 6c 69 64 20 73 79 73  |..'..Invalid sys|
00000190  74 65 6d 20 64 69 73 6b  ff 0d 0a 44 69 73 6b 20  |tem disk...Disk |
000001a0  49 2f 4f 20 65 72 72 6f  72 ff 0d 0a 52 65 70 6c  |I/O error...Repl|
000001b0  61 63 65 20 74 68 65 20  64 69 73 6b 2c 20 61 6e  |ace the disk, an|
000001c0  64 20 74 68 65 6e 20 70  72 65 73 73 20 61 6e 79  |d then press any|
000001d0  20 6b 65 79 0d 0a 00 00  49 4f 20 20 20 20 20 20  | key....IO      |
000001e0  53 59 53 4d 53 44 4f 53  20 20 20 53 59 53 7f 01  |SYSMSDOS   SYS..|
000001f0  00 41 bb 00 07 80 7e 02  0e e9 40 ff 00 00 55 aa  |.A....~...@...U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf
```

---

### Post by presence1960 on 2009-09-12
well you sure have a mess there on your partitions. You have 3 swap partitions and 3 Ubuntu partitions. you only need one of each.

> alright well i downloaded ubuntu the other day and decided to try kubuntu as well..so i did kubuntu and i tried getting programs but said i didnt have enough space..so i did it again and selected the partitions manually and [COLOR="Red"]i did my external hard drive[/COLOR]

What does the text in red mean exactly when you say "i did my external hard drive". Exactly what did you do to it?

I am not being smart but you need to word a little more specifically and explicitly exactly the steps you did from beginning to end. Your narrative there is a little ambiguous to me.

---

### Post by Jcpinny22 on 2009-09-13
well i had tried ubuntu and didnt like it..so i tried kubuntu..and when i idd it twice bc the first time i did it. it said i didnt have enough space. so i tried again and tried to maunuall do the partitions..well when i clicked to manually do it it shows i had two ntsc(or nts or something in that nature) on my main hard drive...then right under it showed 2 swap spaced a ntsc space and 2 etc3 or et3 or that which was on my external hard drive which i thought was very weird so i just went with it. so i had 996gb of data on of the the ntsc space so i took about 96gb of data off and made it free space..then made that swap space or ntsc space i think i cannot remember fully.so i figured everything would be alright then after that when i went to download on Utorrent it said Error:Files are missing. and then i couldnt locate my external hard drive

---

### Post by presence1960 on 2009-09-13
If you know which is your "good" kubuntu that you use (I would say it is sdb4) then I would use gparted off the Live CD to remove all the Ubuntu's except sdb4 and all the swaps except sdb1.

As far as your external I would boot the Live Cd and see if you can access the files and move them. Then format your external disk and set it up again with your data. If the Live CD will not access the files here is a link for Backtrack Linux. very nifty for a lot of stuff including file access. Download the iso and burn a CD. I had a friends machine that the Live Cd could not access her recovery partition to copy. Used Backtrack Linux and first try moved that whole partition over to flash disk.

P.S. forgot the link : [http://www.remote-exploit.org/backtrack.html](http://www.remote-exploit.org/backtrack.html)

---

### Post by Jcpinny22 on 2009-09-13
well when i go to boot menu and click my internal hard drive it has xp ubuntu and 2 kubuntu options...but when i click my external it just goes to kubuntu without asking. but i am sure i know which is good. and what is gparted? how do i access it? do i just boot off the live cd and its there? or what?

---

### Post by presence1960 on 2009-09-13
> **Jcpinny22 said:**
> well when i go to boot menu and click my internal hard drive it has xp ubuntu and 2 kubuntu options...but when i click my external it just goes to kubuntu without asking. but i am sure i know which is good. and what is gparted? how do i access it? do i just boot off the live cd and its there? or what?

access gparted by booting the ubuntu live cd and choosing "try ubuntu without any changes". when the desktop loads go System > Administration > Partition Editor. That is gparted.

---

### Post by Jcpinny22 on 2009-09-14
where is system? i see system settings? but i couldn't find administration there

---

### Post by Jcpinny22 on 2009-09-14
i also see system...but no administration...

---

### Post by presence1960 on 2009-09-14
System is top left. Click on it and go Administration. Then choose Partition Editor.

---

### Post by Jcpinny22 on 2009-09-14
alright well i tried booting into the cd...but i couldnt conect to my wireless internet for some reason..so i booted into my good kubuntu and downloaded and ran gparted..and i could only do 2 of them...which is why i figured i needed to boot on the cd..so i put gparted on a flash drive..i then booted onto the cd open the gparted folder that i unzipped(idk archived whatever its called in kubuntu) then i opened the unzipped folder and clicked on everything...but nothing opened so idk how i open it off the flash drive cause i can't connect to the internet for some reason off the cd.

---

### Post by presence1960 on 2009-09-15
> **Jcpinny22 said:**
> alright well i tried booting into the cd...but i couldnt conect to my wireless internet for some reason..so i booted into my good kubuntu and downloaded and ran gparted..and i could only do 2 of them...which is why i figured i needed to boot on the cd..so i put gparted on a flash drive..i then booted onto the cd open the gparted folder that i unzipped(idk archived whatever its called in kubuntu) then i opened the unzipped folder and clicked on everything...but nothing opened so idk how i open it off the flash drive cause i can't connect to the internet for some reason off the cd.

You can't unzip an iso and click on it to run an iso, this is not windows. You must make a bootable CD by burning the iso as an image to CD or create a bootable USB from the iso.

I think you should read all [this]("https://help.ubuntu.com/9.04/switching/index.html") as it pertains to you right now. You have some misconceptions that you need to straighten out before you can proceed.

---

### Post by Jcpinny22 on 2009-09-15
no i have the cd burnt..and booted off of it. then i tried to get gparted on my kubuntu live cd..but since i couldnt connect to the internet i couldn't accomplish that.

---

### Post by presence1960 on 2009-09-15
> **Jcpinny22 said:**
> no i have the cd burnt..and booted off of it. then i tried to get gparted on my kubuntu live cd..but since i couldnt connect to the internet i couldn't accomplish that.

you don't need the internet to run gparted from the Live Cd!

Please don't take this the wrong way but I suggest you do some reading and studying to increase your knowledge of basic computing tasks. It seems that for whatever reason you do not have the ability to follow the simplest directions.

That is not to say that you never will. It is just that your present knowledge seems inadequate. I (and the rest of the community) want you to use ubuntu if you so desire, but you must be able to do some basic things from following suggestions. We are not present to help you along.

---

