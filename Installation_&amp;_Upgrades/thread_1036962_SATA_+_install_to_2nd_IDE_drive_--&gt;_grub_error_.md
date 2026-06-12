---
title: "SATA + install to 2nd IDE drive --&gt; grub error 22"
date: 2009-01-11
forum: Installation &amp; Upgrades
---

### Post by ran_talbott on 2009-01-11
NOTE: This is *sort of* "solved", but I didn't find this problem when I searched the forum. So I'm posting this so others will find clues. Plus I'd like a better solution than the kluge I came up with.

I got a Dell Dimension XPS Gen 2 dirt cheap because it was in "uncertain" condition.  I tested it for a while by putting gutsy on a single IDE drive, and found it's "working".  Now I'm building it into a multiboot system.

The plan is to put Windoze on the primary master IDE drive, various Linux distros on the primary slave,  and add a third drive of some sort for bulk storage shared among the Linux systems.  This could go either on the secondary IDE channel,  or one of the Dell's SATA channels,  depending on what I find cheap.  At the moment,  I have a SATA drive a friend loaned me,  which is how I found this problem.

I fdisk'ed the primary slave IDE drive from the gutsy system and did a badblocks test on it to make sure it was clean.  Then I booted from an 8.04.1 Server CD and did an install to /dev/sdb5 that went smoothly.

When I rebooted without the CD,  I got a grub error 22.

I tried the various things that people have suggested in other threads (like a grub re-install) to no avail.  One thing I thought might be the problem (but wasn't) is that fdisk used a geometry of 64 heads and 32 sectors for making the partition table.  This caused sfdisk to complain that the extended partition doesn't start on an even cylinder boundary,  because sfdisk likes a geometry of 255 heads and 63 sectors/track.

The real problem is that Linux sees the drives as:

   /dev/sda  Primary master IDE
   /dev/sdb  Primary slave IDE
   /dev/sdc  SATA drive

So,  when you run grub utilities,  they see the Linux partitions as "(hd0,1)" and "(hd1,4)".  The "find /boot/grub/stage1" returns the results that I expected,  and everything *seems* to work.

But,  at boot time,  the BIOS is actually seeing the SATA drive as "drive 1",  and the primary slave IDE as "drive 2".  Whatever mechanism the grub tools are using to determine BIOS drive designations isn't working on my system.

I've kluged my way around this by having grub go to the primary IDE drive for its /boot/grub directory,  and putting "SATA" and "no SATA" entries in menu.lst that tell grub that /dev/sdb is "hd2" or "hd1" (respectively).

But this kluge will break if I install Windoze on the primary IDE,  might break if I install two SATA drives,  and will be a real PITA when I have several different distros installed on /dev/sdb (for those wondering why one would do such a thing:  I do cross-development for embedded Linux systems that don't have enough horsepower to do compiles natively).

Also,  this kluge isn't very user-friendly for Linux newbies who might encounter the same problem on their systems.  So,  if anyone has a better solution,  I'm sure I won't be the only one who will appreciate it.

Thanks,

Ran

---

### Post by caljohnsmith on 2009-01-11
Sounds like some interesting Grub hacking you did. :) In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and maybe what might be a better solution for your Grub problems.

---

### Post by ran_talbott on 2009-01-11
Once I figured out what the problem is, this was actually pretty simple compared to,  say,  using a Redhat desktop PC to build a Debian drive on a USB cable so lilo will boot it correctly when installed in a laptop ;-)

I've attached the RESULTS.txt, fwiw.  I've since discovered that this is a known problem with grub,  tha manifests itself in different ways,  depending on both the distro and the motherboard (as usual,  google has the answer if you can just figure out the right question...):

[http://www.mepis.org/docs/en/index.php/Grub_with_IDE_and_SATA_Drives]("http://www.mepis.org/docs/en/index.php/Grub_with_IDE_and_SATA_Drives")

Based on that article,  there doesn't seem to be a simple,  newbie-friendly solution.  But I think what I'll do is just create a small partition for /boot/grub on the first IDE drive,  with two different menu.lst files for with/without SATA.  If I have a problem,  I can just boot from CD and do a little renaming to match the changed drive configuration.

btw,  although it might not have helped in this case,  the bootinfo script should probably capture the device.map file into RESULTS.txt,  because it may provide a useful clue for some problems.

Thanks,

Ran


```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb
 => HP/Gateway is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst /grub

sda2: _________________________________________________________________________

    File system:       swap

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 7.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: you must specify the filesystem type

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 8622 MB, 8622931968 bytes
255 heads, 63 sectors/track, 1048 cylinders, total 16841664 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x82b70c03

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      192779       96358+  83  Linux
/dev/sda2          192780      706859      257040   82  Linux swap / Solaris
/dev/sda3   *      706860    12048749     5670945   83  Linux
/dev/sda4        12048750    16836119     2393685   16  Hidden FAT16

sfdisk -V /dev/sda:

/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 61.4 GB, 61492838400 bytes
64 heads, 32 sectors/track, 58644 cylinders, total 120103200 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              32    19533823     9766896   83  Linux
/dev/sdb2        19533824   120102911    50284544    5  Extended
/dev/sdb5        19533856    48832511    14649328   83  Linux

sfdisk -V /dev/sdb:

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: partition 2 extends past end of disk

Drive sdc: _____________________________________________________________________

fdisk -lu /dev/sdc:

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf9d10e91

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   234436544   117218241   83  Linux

sfdisk -V /dev/sdc:

Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
/dev/sdc: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="7ac5c656-8f07-4320-8720-d0a1e543fc64" TYPE="ext2" 
/dev/sda2: TYPE="swap" UUID="ea3126be-13c2-44ee-85f9-9f93cfe4e512" 
/dev/sda3: UUID="69e4142f-b096-4c18-bf44-3537c8f266ca" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="42568363-c86e-4595-a078-b6351c3c6c9f" TYPE="ext3" 
/dev/sdb5: UUID="03ce6f72-9b9d-4151-aaee-a9af90e3f7fd" TYPE="ext3" 
/dev/sdc1: UUID="774d5394-e6a9-4878-a067-e3d9d66731ed" SEC_TYPE="ext2" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sdb5 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/sdb1 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)

============================= sda1/grub/menu.lst: =============================

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
# kopt=root=UUID=3e03e66c-7508-431e-8b76-a3e72207d1bd ro

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

title		Ubuntu 7.10, kernel 2.6.22-14-server
root		(hd0,0)
kernel		/vmlinuz-2.6.22-14-server root=UUID=3e03e66c-7508-431e-8b76-a3e72207d1bd ro quiet splash
initrd		/initrd.img-2.6.22-14-server
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-server (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.22-14-server root=UUID=3e03e66c-7508-431e-8b76-a3e72207d1bd ro single
initrd		/initrd.img-2.6.22-14-server

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=16d65d0f-40b7-4e55-89b4-28e32de94774 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=16d65d0f-40b7-4e55-89b4-28e32de94774 ro single 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 7.10, memtest86+ (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


================================== sda1/grub: ==================================

total 176
drwxr-xr-x 2 root root   1024 2008-04-15 17:54 .
drwxr-xr-x 4 root root   1024 2008-04-15 17:54 ..
-rw-r--r-- 1 root root    197 2008-04-15 17:54 default
-rw-r--r-- 1 root root     30 2008-04-15 17:54 device.map
-rw-r--r-- 1 root root   8660 2008-04-15 17:54 e2fs_stage1_5
-rw-r--r-- 1 root root   8452 2008-04-15 17:54 fat_stage1_5
-rw-r--r-- 1 root root     15 2008-04-15 17:54 installed-version
-rw-r--r-- 1 root root   9152 2008-04-15 17:54 jfs_stage1_5
-rw-r--r-- 1 root root   5283 2008-04-15 17:54 menu.lst
-rw-r--r-- 1 root root   7860 2008-04-15 17:54 minix_stage1_5
-rw-r--r-- 1 root root  10132 2008-04-15 17:54 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-04-15 17:54 stage1
-rw-r--r-- 1 root root 110292 2008-04-15 17:54 stage2
-rw-r--r-- 1 root root   9980 2008-04-15 17:54 xfs_stage1_5

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
# kopt=root=UUID=03ce6f72-9b9d-4151-aaee-a9af90e3f7fd ro

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-server [SATA]
root		(hd2,4)
kernel		/boot/vmlinuz-2.6.24-19-server root=UUID=03ce6f72-9b9d-4151-aaee-a9af90e3f7fd ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-server
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-server (recovery mode) [SATA]
root		(hd2,4)
kernel		/boot/vmlinuz-2.6.24-19-server root=UUID=03ce6f72-9b9d-4151-aaee-a9af90e3f7fd ro single
initrd		/boot/initrd.img-2.6.24-19-server

title		Ubuntu 8.04.1, memtest86+ [SATA]
root		(hd2,4)
kernel		/boot/memtest86+.bin
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-server [no SATA]
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-19-server root=UUID=03ce6f72-9b9d-4151-aaee-a9af90e3f7fd ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-server
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-server (recovery mode) [no SATA]
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-19-server root=UUID=03ce6f72-9b9d-4151-aaee-a9af90e3f7fd ro single
initrd		/boot/initrd.img-2.6.24-19-server

title		Ubuntu 8.04.1, memtest86+ [no SATA]
root		(hd1,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 7.10, kernel 2.6.22-14-server (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-server root=UUID=69e4142f-b096-4c18-bf44-3537c8f266ca ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-server
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 7.10, kernel 2.6.22-14-server (recovery mode) (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-server root=UUID=69e4142f-b096-4c18-bf44-3537c8f266ca ro single 
initrd		/boot/initrd.img-2.6.22-14-server
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 7.10, memtest86+ (on /dev/sda3)
root		(hd0,2)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=69e4142f-b096-4c18-bf44-3537c8f266ca /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=7ac5c656-8f07-4320-8720-d0a1e543fc64 /media/sda1     ext2    defaults        0       2
# /dev/sda2
UUID=ea3126be-13c2-44ee-85f9-9f93cfe4e512 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

================================== sda3/boot: ==================================

total 16952
drwxr-xr-x  3 root root    4096 2008-12-26 05:46 .
drwxr-xr-x 21 root root    4096 2008-12-25 18:46 ..
-rw-r--r--  1 root root  424317 2007-10-14 18:42 abi-2.6.22-14-server
-rw-r--r--  1 root root   75416 2007-10-14 18:42 config-2.6.22-14-server
drwxr-xr-x  2 root root    4096 2009-01-10 16:12 grub
-rw-r--r--  1 root root 7263369 2008-12-26 05:46 initrd.img-2.6.22-14-server
-rw-r--r--  1 root root 6800764 2008-12-25 18:46 initrd.img-2.6.22-14-server.bak
-rw-r--r--  1 root root  103204 2007-09-28 03:06 memtest86+.bin
-rw-r--r--  1 root root  828819 2007-10-14 18:42 System.map-2.6.22-14-server
-rw-r--r--  1 root root 1787224 2007-10-14 18:42 vmlinuz-2.6.22-14-server

=============================== sda3/boot/grub: ===============================

total 228
drwxr-xr-x 2 root root   4096 2009-01-10 16:12 .
drwxr-xr-x 3 root root   4096 2008-12-26 05:46 ..
-rw-r--r-- 1 root root    197 2008-12-25 19:02 default
-rw-r--r-- 1 root root     15 2008-12-25 19:02 device.map
-rw-r--r-- 1 root root   8660 2008-12-25 19:02 e2fs_stage1_5
-rw-r--r-- 1 root root   8452 2008-12-25 19:02 fat_stage1_5
-rw-r--r-- 1 root root     15 2008-12-25 19:02 installed-version
-rw-r--r-- 1 root root   9152 2008-12-25 19:02 jfs_stage1_5
-rw-r--r-- 1 root root   5868 2009-01-10 16:12 menu.lst
-rw-r--r-- 1 root root   5308 2009-01-10 16:12 menu.lst~
-rw-r--r-- 1 root root   4259 2008-12-25 19:02 menu.lst.0
-rw-r--r-- 1 root root   7860 2008-12-25 19:02 minix_stage1_5
-rw-r--r-- 1 root root  10132 2008-12-25 19:02 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-25 19:02 stage1
-rw-r--r-- 1 root root 110292 2008-12-25 19:02 stage2
-rw-r--r-- 1 root root   9980 2008-12-25 19:02 xfs_stage1_5

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
# kopt=root=UUID=03ce6f72-9b9d-4151-aaee-a9af90e3f7fd ro

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-server
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-19-server root=UUID=03ce6f72-9b9d-4151-aaee-a9af90e3f7fd ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-server
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-server (recovery mode)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-19-server root=UUID=03ce6f72-9b9d-4151-aaee-a9af90e3f7fd ro single
initrd		/boot/initrd.img-2.6.24-19-server

title		Ubuntu 8.04.1, memtest86+
root		(hd1,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 7.10, kernel 2.6.22-14-server (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-server root=UUID=69e4142f-b096-4c18-bf44-3537c8f266ca ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-server
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 7.10, kernel 2.6.22-14-server (recovery mode) (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-server root=UUID=69e4142f-b096-4c18-bf44-3537c8f266ca ro single 
initrd		/boot/initrd.img-2.6.22-14-server
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 7.10, memtest86+ (on /dev/sda3)
root		(hd0,2)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb5
UUID=03ce6f72-9b9d-4151-aaee-a9af90e3f7fd /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb1
UUID=42568363-c86e-4595-a078-b6351c3c6c9f /home           ext3    relatime        0       2
# /dev/sda2
UUID=ea3126be-13c2-44ee-85f9-9f93cfe4e512 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sdb5/boot: ==================================

total 18192
drwxr-xr-x  3 root root    4096 2009-01-10 17:07 .
drwxr-xr-x 21 root root    4096 2009-01-10 10:59 ..
-rw-r--r--  1 root root  426444 2008-06-18 11:15 abi-2.6.24-19-server
-rw-r--r--  1 root root   80181 2008-06-18 11:15 config-2.6.24-19-server
drwxr-xr-x  2 root root    4096 2009-01-10 11:16 grub
-rw-r--r--  1 root root 7939169 2009-01-10 17:07 initrd.img-2.6.24-19-server
-rw-r--r--  1 root root 7085136 2009-01-10 10:59 initrd.img-2.6.24-19-server.bak
-rw-r--r--  1 root root  103204 2007-09-28 03:06 memtest86+.bin
-rw-r--r--  1 root root  933458 2008-06-18 11:15 System.map-2.6.24-19-server
-rw-r--r--  1 root root 1987000 2008-06-18 11:15 vmlinuz-2.6.24-19-server

=============================== sdb5/boot/grub: ===============================

total 204
drwxr-xr-x 2 root root   4096 2009-01-10 11:16 .
drwxr-xr-x 3 root root   4096 2009-01-10 17:07 ..
-rw-r--r-- 1 root root    197 2009-01-10 11:16 default
-rw-r--r-- 1 root root     45 2009-01-10 11:16 device.map
-rw-r--r-- 1 root root   8056 2009-01-10 11:16 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2009-01-10 11:16 fat_stage1_5
-rw-r--r-- 1 root root     18 2009-01-10 11:16 installed-version
-rw-r--r-- 1 root root   8608 2009-01-10 11:16 jfs_stage1_5
-rw-r--r-- 1 root root   5308 2009-01-10 11:16 menu.lst
-rw-r--r-- 1 root root   7324 2009-01-10 11:16 minix_stage1_5
-rw-r--r-- 1 root root   9632 2009-01-10 11:16 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-10 11:16 stage1
-rw-r--r-- 1 root root 108356 2009-01-10 11:16 stage2
-rw-r--r-- 1 root root   9276 2009-01-10 11:16 xfs_stage1_5

=========================== Unknown MBRs or Boot Sectors =======================

Unknown BootLoader  on /dev/sda4

00000000  7c 75 6e 74 72 6f 75 62  6c 65 64 20 28 73 69 6d  ||untroubled (sim|
00000010  69 6c 61 72 20 74 65 72  6d 29 0a 28 61 64 6a 29  |ilar term).(adj)|
00000020  7c 75 6e 69 6e 76 6f 6c  76 65 64 20 28 73 69 6d  ||uninvolved (sim|
00000030  69 6c 61 72 20 74 65 72  6d 29 0a 75 6e 63 6f 6e  |ilar term).uncon|
00000040  64 69 74 69 6f 6e 61 6c  7c 33 0a 28 61 64 6a 29  |ditional|3.(adj)|
00000050  7c 61 62 73 6f 6c 75 74  65 20 28 73 69 6d 69 6c  ||absolute (simil|
00000060  61 72 20 74 65 72 6d 29  7c 74 6f 74 61 6c 20 28  |ar term)|total (|
00000070  73 69 6d 69 6c 61 72 20  74 65 72 6d 29 7c 75 6e  |similar term)|un|
00000080  63 6f 6e 64 69 74 69 6f  6e 65 64 20 28 73 69 6d  |conditioned (sim|
00000090  69 6c 61 72 20 74 65 72  6d 29 7c 62 6c 75 6e 74  |ilar term)|blunt|
000000a0  20 28 73 69 6d 69 6c 61  72 20 74 65 72 6d 29 7c  | (similar term)||
000000b0  63 72 75 64 65 20 28 73  69 6d 69 6c 61 72 20 74  |crude (similar t|
000000c0  65 72 6d 29 7c 73 74 61  72 6b 20 28 73 69 6d 69  |erm)|stark (simi|
000000d0  6c 61 72 20 74 65 72 6d  29 7c 69 6e 64 65 70 65  |lar term)|indepe|
000000e0  6e 64 65 6e 74 20 28 73  69 6d 69 6c 61 72 20 74  |ndent (similar t|
000000f0  65 72 6d 29 7c 76 65 73  74 65 64 20 28 73 69 6d  |erm)|vested (sim|
00000100  69 6c 61 72 20 74 65 72  6d 29 7c 75 6e 71 75 61  |ilar term)|unqua|
00000110  6c 69 66 69 65 64 20 28  72 65 6c 61 74 65 64 20  |lified (related |
00000120  74 65 72 6d 29 7c 63 6f  6e 64 69 74 69 6f 6e 61  |term)|conditiona|
00000130  6c 20 28 61 6e 74 6f 6e  79 6d 29 0a 28 61 64 6a  |l (antonym).(adj|
00000140  29 7c 63 61 74 65 67 6f  72 69 63 7c 63 61 74 65  |)|categoric|cate|
00000150  67 6f 72 69 63 61 6c 7c  66 6c 61 74 7c 75 6e 71  |gorical|flat|unq|
00000160  75 61 6c 69 66 69 65 64  20 28 73 69 6d 69 6c 61  |ualified (simila|
00000170  72 20 74 65 72 6d 29 0a  28 61 64 6a 29 7c 69 6e  |r term).(adj)|in|
00000180  64 65 70 65 6e 64 65 6e  74 20 28 73 69 6d 69 6c  |dependent (simil|
00000190  61 72 20 74 65 72 6d 29  0a 75 6e 63 6f 6e 64 69  |ar term).uncondi|
000001a0  74 69 6f 6e 61 6c 6c 79  7c 32 0a 28 61 64 76 29  |tionally|2.(adv)|
000001b0  7c 63 6f 6e 64 69 74 69  6f 6e 61 6c 6c 79 20 28  ||conditionally (|
000001c0  61 6e 74 6f 6e 79 6d 29  0a 28 61 64 76 29 7c 66  |antonym).(adv)|f|
000001d0  6c 61 74 6c 79 7c 63 61  74 65 67 6f 72 69 63 61  |latly|categorica|
000001e0  6c 6c 79 0a 75 6e 63 6f  6e 64 69 74 69 6f 6e 65  |lly.unconditione|
000001f0  64 7c 32 0a 28 61 64 6a  29 7c 61 62 73 6f 6c 75  |d|2.(adj)|absolu|
00000200


=============================== StdErr Messages: ===============================

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

```

---

### Post by caljohnsmith on 2009-01-11
Actually, I don't think there is any problem with how Grub is working with your 3 HDD setup. The thing to remember is that the Grub you get on start up is not the same as the Grub you work with when you are in linux as far as the ordering of drives goes. On start up, Grub always sees the order of drives as your BIOS boot order so that:
```
(hd0) = 1st boot drive
(hd1) = 2nd boot drive
(hd2) = 3rd boot drive
...etc.

```
So if you change your BIOS boot order, that will change how Grub numbers the drives on start up. But when you boot into linux and run Grub commands, as you all ready know the following is generally true:
```
(hd0) = sda
(hd1) = sdb
(hd2) = sdc
...etc. 
```
So that means if you run Grub commands in linux to install Grub to your sdc drive for example, you would use (hd2). But if on start up you change your BIOS boot order so that the sdc drive is booted first, then sdc on start up is then (hd0) in Grub's eyes. So the bottom line is when you run Grub commands in linux, the second case above holds, but when it comes to modifying your Grub's menu.lst, the first case above holds since Grub only uses the menu.lst on start up. 

So in your particular case, you have Grub installed to sda and it uses the boot files in the sda3 Ubuntu 7.10 partition. Also note that the Ubuntu 7.10 entries in the sda3 menu.lst use (hd0,2) which is good, because when you boot the sda drive on start up it will be (hd0). But your sdb drive with Ubuntu 8.10 is another story. You could continue to boot 8.10 from your Ubuntu Grub menu on your sda drive like you are currently doing, or you could install Grub to the MBR of your sdb drive, point it to the sdb5 Ubuntu 8.10 partition, modify your sdb5 menu.lst Ubuntu entries to use (hd0,4) instead of (hd1,4), and then you should be able to boot the sdb Ubuntu drive independent of the other drives. If you want any specifics of how to do any of that, let me know, but that's the general idea. Anyway, good luck and have fun with your Ubuntu installs.

---

