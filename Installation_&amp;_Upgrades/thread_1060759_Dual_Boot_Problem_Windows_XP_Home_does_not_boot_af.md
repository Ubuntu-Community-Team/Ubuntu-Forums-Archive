---
title: "Dual Boot Problem: Windows XP Home does not boot after Ubuntu install"
date: 2009-02-05
forum: Installation &amp; Upgrades
---

### Post by hendrel on 2009-02-05
Hi

I have Windows XP Home installed on my third drive on my machine (150gig). I then installed Ubuntu 8.0.4 LTS on my first drive (20gig).
I can boot into Ubuntu just fine, but there is no listing for Windows in my grub menu.
I then edited the grub menu (/boot/grub/menu.lst) with the following entry

```

title		Windows XP Home
map 		(hd0) (hd2) 
map 		(hd2) (hd0)
root 		(hd2,0)
rootnoverify 	(hd2,0) 
makeactive
chainloader +1

```

Now when I boot into Windows i get the following error: NTLDR Missing

Here is a listing of /boot/grub/device.map

```

(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc

```

Here is a listing of fdisk -l

```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x91833dcd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       16708   134206978+   7  HPFS/NTFS

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd86ed86e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2327    18691596   83  Linux
/dev/sdb2            2328        2434      859477+   5  Extended
/dev/sdb5            2328        2434      859446   82  Linux swap / Solaris

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf02eff37

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9728    78140128+   7  HPFS/NTFS

```

Please help!!! I am stuck!!!

---

### Post by hendrel on 2009-02-05
Hi

I am Windows XP Home is on Servide Pack 3. If this helps.

---

### Post by Bigneil on 2009-02-05
you may just need to change the boot order.


read this thread

[http://ubuntuforums.org/showthread.php?t=986611](http://ubuntuforums.org/showthread.php?t=986611)

---

### Post by Bigneil on 2009-02-05
also which disk to boot from in  bios.

---

### Post by konqueror7 on 2009-02-05
did you perhaps deleted that file inside you windows partition? because its a hidden system file in windows, and the last time i encountered "NTLDR Missing" i reformated...

---

### Post by caljohnsmith on 2009-02-05
I think it's important to keep in mind that Grub sees the order of drives differently on start up than when you are in Ubuntu. **On start up, Grub sees the order of drives as your BIOS boot order**, but when you are in Ubuntu, Grub sees the order of drives as Ubuntu orders them, i.e. sda, sdb, sdc, etc. Therefore, on start up, (hd2) is the 3rd BIOS boot drive, and not necessarily the sdc drive. So if you are getting a "NTLDR missing" error when booting, probably (hd2) is your sda drive. Therefore, how about trying the following entries for Windows:
```
title		Windows XP Home
rootnoverify 	(hd1,0)
map 		(hd0) (hd1) 
map 		(hd1) (hd0)
chainloader +1

title		Windows XP Home
rootnoverify 	(hd0,0)
chainloader +1
```
One of those entries should work since you all ready tried the (hd2) entry. If for some reason neither work, please let me know exactly what happens when you choose each of them from the Grub menu, and we can work from there if you want.

---

### Post by hendrel on 2009-02-05
I have tried the following grub configurations:

> 

Option 1:

title		Windows XP Home
rootnoverify 	(hd1,0)
map 		(hd0) (hd1) 
map 		(hd1) (hd0)
chainloader +1

Option 2

title		Windows XP Home
rootnoverify 	(hd0,0)
chainloader +1


With the first option I get this error: Error 13: Invalid or unsupported executable format

With option 2 the machine just restarts without any error message.

Need more help... please...

---

### Post by caljohnsmith on 2009-02-05
OK, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. The results of that script will help clarify your setup and hopefully what the solution to your Windows booting problem might be.

---

### Post by hendrel on 2009-02-05
Here is the Boot Info Scrit result:


> 
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04
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
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /ntldr

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders, total 39102336 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd86ed86e

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    37,383,254    37,383,192  83 Linux
/dev/sda2          37,383,255    39,102,209     1,718,955   5 Extended
/dev/sda5          37,383,318    39,102,209     1,718,892  82 Linux swap / Solaris


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf02eff37

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   156,280,319   156,280,257   7 HPFS/NTFS


Drive sdc: _____________________________________________________________________

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x91833dcd

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   268,414,019   268,413,957   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="27324879-88ac-4c73-b57b-2aea4b29c1b5" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="87662d0c-886f-48ef-8d90-5b45dc802765" 
/dev/sdb1: UUID="6CB8307CB83046BC" LABEL="Data House" TYPE="ntfs" 
/dev/sdc1: UUID="74C0DB36C0DAFCF4" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/hendrel/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=hendrel)

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

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
# kopt=root=UUID=27324879-88ac-4c73-b57b-2aea4b29c1b5 ro

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=27324879-88ac-4c73-b57b-2aea4b29c1b5 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=27324879-88ac-4c73-b57b-2aea4b29c1b5 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

title		Windows XP Home
rootnoverify 	(hd1,0)
map 		(hd0) (hd1) 
map 		(hd1) (hd0)
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=27324879-88ac-4c73-b57b-2aea4b29c1b5 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=87662d0c-886f-48ef-8d90-5b45dc802765 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  17.0GB: boot/grub/menu.lst
  16.9GB: boot/grub/stage2
  16.9GB: boot/initrd.img-2.6.24-16-generic
  17.0GB: boot/initrd.img-2.6.24-16-generic.bak
  17.0GB: boot/vmlinuz-2.6.24-16-generic
  16.9GB: initrd.img
  17.0GB: vmlinuz



---

### Post by caljohnsmith on 2009-02-05
It looks like at least part of the issue is that you don't have two of your necessary Windows boot files. How about downloading the attached "WinXP_boot_files.zip" file to your Ubuntu desktop and do:
```
sudo mount /dev/sdc1 /mnt
cd ~/Desktop
unzip WinXP_boot_files.zip
sudo mv boot.ini NTDETECT.COM /mnt
```
Also, make sure to use the second entry from post #6 for your Windows entry, i.e. the one with (hd0,0). Next reboot, try Windows from Grub, and let me know exactly what happens. We can work from there.

---

### Post by hendrel on 2009-02-06
Mr Smith

Thanks you so much. Your last post solved to problem. A case of beers for you.

hendrel

---

### Post by caljohnsmith on 2009-02-06
Glad to hear that worked OK; cheers and enjoy Ubuntu and Windows. :)

---

### Post by djsephiroth on 2009-02-19
> **konqueror7 said:**
> did you perhaps deleted that file inside you windows partition? because its a hidden system file in windows, and the last time i encountered "NTLDR Missing" i reformated...
You can always make use of the Windows Repair option by booting from a Windows CD/DVD. Also, you can just copy NTLDR from a working system to a flash drive, boot from a repair disk, and copy the NTLDR from the flash drive to the broken system.

---

