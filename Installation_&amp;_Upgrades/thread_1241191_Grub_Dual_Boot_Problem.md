---
title: "Grub Dual Boot Problem"
date: 2009-08-15
forum: Installation &amp; Upgrades
---

### Post by simonrose on 2009-08-15
Hi all,

I am having some difficulties with grub. I have two SATA drives one with XP installed and one with Ubuntu installed. The ubuntu drive was installed first and the xp drive is a new addition for gaming.

I have got ubuntu booting first (swapped the sata cables to get this) as i use that drive most often...i then searched around and found the lines i needed to add to menu.lst in order to let grub load xp

title Microsoft Windows XP Professional
root (hd1,0)
map (hd1,hd0)
map (hd0,hd1)
chainloader +1

However this hasn't worked. when i select the windows option i get a black screen with the text 'Starting...' but nothing loads.

One thing i have noticed when ubuntu boots is there is a line that appears on screen taht says 'booting from (hd0,0) ext3' so i assume hd0,0 is where ubuntu is and therefore the code above should work.

several sites have said i can get the data i need by running sudo fdisk -l
output from which is this:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a0bf5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29650   238163593+  83  Linux
/dev/sdb2           29651       30401     6032407+   f  W95 Ext'd (LBA)
/dev/sdb5           29651       30401     6032376   82  Linux swap / Solaris

SDA1 being the windows drive and SDB being the ubuntu drive.

Anyone got any ideas?

Thanks in advance,

Simon

---

### Post by oldfred on 2009-08-15
Even thought your second drive is Ubuntu GRUB is usually installed on the first drive. You are probably booting grub from sda1 which goes to your Ubuntu install on sdb1.

If so your window entry should be
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Professional
rootnoverify (hd0,0)
savedefault
chainloader +1

---

### Post by simonrose on 2009-08-15
thanks for the quick reply, i changed the menu.lst entry to match what you suggested but when i tried to boot windows i got the following error:

error 13: invalid or unsupported executable format

---

### Post by presence1960 on 2009-08-15
let's get an exact picture of your setup and boot process. Boot into Ubuntu and download the Boot Info Script 0.32 from my signature line to the desktop. Once on the desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
```
This will create a RESULTS.txt file on the desktop. paste the entire contents of that file back here. Once pasted here highligh all text & click the # sign on the toolbar to place code tags around the text.

---

### Post by simonrose on 2009-08-16
Here is the output from the RESULTS.txt file...
Thanks for your help!

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
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

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   976,768,064   976,768,002   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000a0bf5

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   476,327,249   476,327,187  83 Linux
/dev/sdb2         476,327,250   488,392,064    12,064,815   f W95 Ext d (LBA)
/dev/sdb5         476,327,313   488,392,064    12,064,752  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="FA8C12978C124E8F" LABEL="Windows" TYPE="ntfs" 
/dev/sdb1: UUID="f03f4e35-30b0-4a34-bbb0-a0cd5e3e70b4" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="2dd733c3-a320-4e16-8d04-1d3b8d2ccb04" 

=============================== "mount" output: ===============================

/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-14-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/simon/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=simon)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn


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
# kopt=root=UUID=f03f4e35-30b0-4a34-bbb0-a0cd5e3e70b4 ro acpi=off

## default grub root device
## e.g. groot=(hd0,0)
# groot=f03f4e35-30b0-4a34-bbb0-a0cd5e3e70b4

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

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		f03f4e35-30b0-4a34-bbb0-a0cd5e3e70b4
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=f03f4e35-30b0-4a34-bbb0-a0cd5e3e70b4 ro acpi=off quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		f03f4e35-30b0-4a34-bbb0-a0cd5e3e70b4
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=f03f4e35-30b0-4a34-bbb0-a0cd5e3e70b4 ro acpi=off  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, memtest86+
uuid		f03f4e35-30b0-4a34-bbb0-a0cd5e3e70b4
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.


title Microsoft Windows XP Professional
rootnoverify (hd1,0)
savedefault
chainloader +1



=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=f03f4e35-30b0-4a34-bbb0-a0cd5e3e70b4 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=2dd733c3-a320-4e16-8d04-1d3b8d2ccb04 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


 227.0GB: boot/grub/menu.lst
 227.0GB: boot/grub/stage2
 226.9GB: boot/initrd.img-2.6.28-11-generic
 227.0GB: boot/initrd.img-2.6.28-13-generic
 227.0GB: boot/initrd.img-2.6.28-14-generic
 226.9GB: boot/vmlinuz-2.6.28-11-generic
 226.9GB: boot/vmlinuz-2.6.28-13-generic
 227.0GB: boot/vmlinuz-2.6.28-14-generic
 227.0GB: initrd.img
 227.0GB: initrd.img.old
 227.0GB: vmlinuz
 226.9GB: vmlinuz.old
```

---

### Post by mhgsys on 2009-08-16
Am  I correct to think when you change boot prior in your bios to the other disk windows will boot up correctly?

If so 
You should change 
```
title Microsoft Windows XP Professional
rootnoverify (hd0,0)
savedefault
chainloader +1 
```

to 

```

title Microsoft Windows XP Professional
rootnoverify (hd1,0)
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
chainloader +1

```

---

### Post by presence1960 on 2009-08-16
```
title         Microsoft Windows XP Professional
rootnoverify (hd1,0)
map          (hd0) (hd1)
map          (hd1) (hd0)
chainloader  +1
```

Make this your windows entry in menu.lst. Sometimes Ubuntu and BIOS read the order of drives differently. Even though sda is listed first in output of sudo fdisk -l it is actually the second drive in boot order. So when using root or rootnoverify in menu.lst you need to use the drives in the orber of booting in BIOS. Thus even though windows is on sda1 it is actually (hd1,0) because of the boot order of your drives. Keep your sdb 250 GB (Ubuntu disk) as first in hard disk boot order in BIOS so GRUB will take over when you boot.

---

