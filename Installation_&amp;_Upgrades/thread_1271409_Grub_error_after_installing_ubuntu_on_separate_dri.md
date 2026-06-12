---
title: "Grub error after installing ubuntu on separate drive from vista Help!"
date: 2009-09-20
forum: Installation &amp; Upgrades
---

### Post by mlebaron on 2009-09-20
I had Vista installed on a drive (drive 1).  I have two other drives for data only.  I consolidated all data to drive 2 and cleared everything off drive 3.  I installed Ubuntu onto drive 3.  Now I get a Grub loading ... Grub error 17 no matter what drive I try to boot from.  How do I fix this?

Thanks for you help.

---

### Post by mlebaron on 2009-09-20
Hello? Can anybody help me with this?

---

### Post by scrooge_74 on 2009-09-20
Seems  your system is not recognizing one of your drives.

Can you boot in ubuntu safe mode to fix it?

If not 
You should use the live CD so you can fix your grub


Check the links for more info
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
[http://www.cyberciti.biz/faq/howto-boot-ubuntu-linux-rescue-mode/](http://www.cyberciti.biz/faq/howto-boot-ubuntu-linux-rescue-mode/)

---

### Post by presence1960 on 2009-09-20
> **mlebaron said:**
> I had Vista installed on a drive (drive 1).  I have two other drives for data only.  I consolidated all data to drive 2 and cleared everything off drive 3.  I installed Ubuntu onto drive 3.  Now I get a Grub loading ... Grub error 17 no matter what drive I try to boot from.  How do I fix this?

Thanks for you help.

Let's get a better look at your setup. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by louieb on 2009-09-20
Not enough information to even guess. Do you get the Grub menu? 
What GRUB error? 
Do you have 3 physical hard drives or 3 partitions on the same hard drive?

It would be of great if you would follow the  [Boot Info Script Instructions]("http://ubuntuforums.org/showpost.php?p=6725571&postcount=3") and put the RESULTS.TXT file in your next post. Its long be sure to wrap it in code tags. (the #).

lol - got beaten to the [Boot Info Script Instructions]("http://ubuntuforums.org/showpost.php?p=6725571&postcount=3") request.

---

### Post by mlebaron on 2009-09-20
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #3 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /ntldr /ntdetect.com

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x90e2b108

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    20,466,809    20,466,747  27 Hidden HPFS/NTFS
/dev/sda2    *     20,466,810   488,393,849   467,927,040   6 FAT16


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xeaacbd7c

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   976,771,071   976,769,024   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x10171017

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   149,838,254   149,838,192  83 Linux
/dev/sdc2         149,838,255   156,296,384     6,458,130   5 Extended
/dev/sdc5         149,838,318   156,296,384     6,458,067  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="D8006A1216D9B5D2" LABEL="PQSERVICE" TYPE="ntfs" 
/dev/sda2: UUID="D8303ED7303EBC76" LABEL="ACER" TYPE="ntfs" 
/dev/sdb1: UUID="D0AADE96AADE7884" LABEL="500GigHitachi" TYPE="ntfs" 
/dev/sdc1: UUID="476ae97a-1e2c-4722-bcc9-1916ff437fcd" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc5: UUID="7bb9f70b-9289-4552-9c68-c26aab8c2264" TYPE="swap" 

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


=========================== sdc1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=476ae97a-1e2c-4722-bcc9-1916ff437fcd ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=476ae97a-1e2c-4722-bcc9-1916ff437fcd

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
uuid		476ae97a-1e2c-4722-bcc9-1916ff437fcd
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=476ae97a-1e2c-4722-bcc9-1916ff437fcd ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		476ae97a-1e2c-4722-bcc9-1916ff437fcd
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=476ae97a-1e2c-4722-bcc9-1916ff437fcd ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		476ae97a-1e2c-4722-bcc9-1916ff437fcd
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista (loader)
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1


=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc1 during installation
UUID=476ae97a-1e2c-4722-bcc9-1916ff437fcd /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=7bb9f70b-9289-4552-9c68-c26aab8c2264 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


  28.3GB: boot/grub/menu.lst
  28.3GB: boot/grub/stage2
  66.0GB: boot/initrd.img-2.6.28-11-generic
  74.3GB: boot/vmlinuz-2.6.28-11-generic
  66.0GB: initrd.img
  74.3GB: vmlinuz

---

### Post by mlebaron on 2009-09-20
More info:
Vista was already on the "Acer" partition.  When I installed Unbuntu, I told the intaller to take the entire 80 gigabyte sdc.
When I rebooted I get the "Loading Grub...."
Then I get "Error 17" and it just sits there.

Also, based on another post, I changed the order of the drives in a file in the grub directory. It was the device.map file under /boot/grub.

.... and thank you SO much for helping.

---

### Post by louieb on 2009-09-20
IF the boot order is 1st - the 250GB, 2nd - 500GB ,and 3rd - 80GB. Then it looks like it should work. 

Are your drives a mix of sata and pata? Sometimes that will confuse the grub installer.  Grub uses boot order to decided which drives is which. If boot order changes then there is a good chance GRUB will get confused and won't work.

Anyway for now get a [Super Grub Disk]("http://forjamari.linex.org/projects/supergrub/") it should be able to boot the Linux install and the windows install in sda2 (Vista).   

And it would help to know the drive types internal / external. and if internal if sata or pata or a mix.

---

### Post by mlebaron on 2009-09-21
The 500 gig and the 250 gig drives are SATA and (as far as I know) are being used by Vista.

The 80 gig drive is an IDE drive of drive.  I have to admit that I've never even heard of a PATA drive.

Before doing anything else, I'll make sure the boot order is as you specify above and then I'll go for the super grub disc if that doesn't work.

---

### Post by mlebaron on 2009-09-21
I set the boot order in the BIOS to 250 Gig, 500 Gig, 80 Gig.  But still have the same exact Grub error on boot.  These are all internal drives
Reposting new results text just in case changing the boot order in the bios has any effect on it:

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #3 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /ntldr /ntdetect.com

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x90e2b108

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    20,466,809    20,466,747  27 Hidden HPFS/NTFS
/dev/sda2    *     20,466,810   488,393,849   467,927,040   6 FAT16


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xeaacbd7c

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   976,771,071   976,769,024   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x10171017

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   149,838,254   149,838,192  83 Linux
/dev/sdc2         149,838,255   156,296,384     6,458,130   5 Extended
/dev/sdc5         149,838,318   156,296,384     6,458,067  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="D8006A1216D9B5D2" LABEL="PQSERVICE" TYPE="ntfs" 
/dev/sda2: UUID="D8303ED7303EBC76" LABEL="ACER" TYPE="ntfs" 
/dev/sdb1: UUID="D0AADE96AADE7884" LABEL="500GigHitachi" TYPE="ntfs" 
/dev/sdc1: UUID="476ae97a-1e2c-4722-bcc9-1916ff437fcd" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc5: UUID="7bb9f70b-9289-4552-9c68-c26aab8c2264" TYPE="swap" 

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


=========================== sdc1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=476ae97a-1e2c-4722-bcc9-1916ff437fcd ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=476ae97a-1e2c-4722-bcc9-1916ff437fcd

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
uuid		476ae97a-1e2c-4722-bcc9-1916ff437fcd
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=476ae97a-1e2c-4722-bcc9-1916ff437fcd ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		476ae97a-1e2c-4722-bcc9-1916ff437fcd
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=476ae97a-1e2c-4722-bcc9-1916ff437fcd ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		476ae97a-1e2c-4722-bcc9-1916ff437fcd
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista (loader)
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1


=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc1 during installation
UUID=476ae97a-1e2c-4722-bcc9-1916ff437fcd /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=7bb9f70b-9289-4552-9c68-c26aab8c2264 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


  28.3GB: boot/grub/menu.lst
  28.3GB: boot/grub/stage2
  66.0GB: boot/initrd.img-2.6.28-11-generic
  74.3GB: boot/vmlinuz-2.6.28-11-generic
  66.0GB: initrd.img
  74.3GB: vmlinuz

---

### Post by louieb on 2009-09-21
PATA (parallel ata) another name for IDE. 

Hope just getting the boot order right will fix the problem. But if not - once you get the Ubuntu hard drive install booting with SuperGrub, Then I can go over how to use the **grub>** prompt to get grub straightened out and booting from the hard drive.

---

### Post by mlebaron on 2009-09-21
I can't see a link on forjamari.linex.org/projects/supergrub to download Super Grub.  How do I download it?

---

### Post by presence1960 on 2009-09-21
here is what I would do> i would put GRUB on MBR of 80 GB (sdc) and then reboot & switch the order of hard disk booting in BIOS to 80 GB, 250 Gb & 500 GB. Boot from Ubuntu Live CD and choose "try ubuntu without any changes". When the desktop loads do this:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd2,0)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd2,0)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd2)", to install GRUB to MBR, 
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

Reboot and go into BIOS and make your 80 GB boot first followed by 250 GB and lastly 500GB. Save changes to CMOS and exit BIOS. You should get the GRUB menu on boot. Boot into Ubuntu and open a terminal and run this command ```
gksu gedit /boot/grub/menu.lst
```
that is a lowercase L in .lst

Scroll down to the bottom and change your Vista entry to:

```
title         Vista
rootnoverify  (hd1,1)
map           (hd0) (hd1)
map           (hd1) (hd0)
chainloader   +1

```
Click Save on the toobar, close file. Reboot.

---

### Post by mlebaron on 2009-09-21
OK, I've got it booting into Ubuntu now.  I'm trying out this last part.  Rebooting.... and I will let you know how it goes.

---

### Post by mlebaron on 2009-09-21
It worked!!!  Thank you all so much for helping.  I've booted both to Vista and to Ubuntu 64.

---

### Post by louieb on 2009-09-21
> It worked!!!

Great. 

> **mlebaron said:**
> I can't see a link on forjamari.linex.org/projects/supergrub to download Super Grub.  How do I download it?

Did not realize what a pain in the butt it was to find the download from that link. Thanks for the heads up. Have changed the link to Softpedia [Super Grub Disk ]("http://linux.softpedia.com/progDownload/Super-Grub-Disk-Download-8071.html")

---

### Post by presence1960 on 2009-09-21
Great! Enjoy Ubuntu!

---

