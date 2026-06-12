---
title: "Dual Boot using XP loader."
date: 2009-01-07
forum: Installation &amp; Upgrades
---

### Post by teddeman on 2009-01-07
I have scoured the threads and not found the answer I am looking for.  I have a new PC with two SATA hard drives.  I have 64 bit XP on the first drive.  I would like to install Ub8.10 on the beginning of the second drive.  Both 320gb drive are broken up into two equal sized partitions (4 total).  

Last night I loaded the live CD, got to the partition manager, blew away the first partition on the second drive and created a ext3 partition for Ub8.10 and a 5 gig swap.  Through the advanced install options, I pointed the boot loader to install on sda2 (second drive).  

I need to know what line I need to add to the Windows boot loader to point to the UB8.10 loader.

---

### Post by caljohnsmith on 2009-01-07
If you can change your BIOS to boot the Ubuntu drive, then you could install Grub to its MBR (Master Boot Record) to make it bootable. That is usually an easier solution than adding Grub to your Windows boot loader, but it's up to you. In order to get a clearer picture of your setup though, how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it.

---

### Post by teddeman on 2009-01-07
> **caljohnsmith said:**
> If you can change your BIOS to boot the Ubuntu drive, then you could install Grub to its MBR (Master Boot Record) to make it bootable. That is usually an easier solution than adding Grub to your Windows boot loader, but it's up to you. In order to get a clearer picture of your setup though, how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it.

here it is:

```
============================= Boot Info Summary: ==============================

 => Drive sdc does not have a valid partition table.
 => Drive sdd does not have a valid partition table.
 => Drive sde does not have a valid partition table.
 => Drive sdf does not have a valid partition table.
 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of /dev/sdb2 
                       and looks at sector 2261055 of the same hard drive for 
                       the stage2 file and on partition #2 for 
                       /boot/grub/menu.lst .
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdb3: _________________________________________________________________________

    File system:       Extended Partition

sdb5: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4246839c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   312560639   156280288+   7  HPFS/NTFS
/dev/sda2       312560640   625137344   156288352+   7  HPFS/NTFS

sfdisk -V /dev/sda:

partition 2: start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5955326f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1       312576705   625137344   156280320    7  HPFS/NTFS
/dev/sdb2   *          63   302728859   151364398+  83  Linux
/dev/sdb3       302728860   312576704     4923922+   5  Extended
/dev/sdb5       302728923   312576704     4923891   82  Linux swap / Solaris

Partition table entries are not in disk order

sfdisk -V /dev/sdb:

partition 1: start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/sdb: OK

Drive sdc: _____________________________________________________________________

fdisk -lu /dev/sdc:

sfdisk -V /dev/sdc:

/dev/sdc: No medium found

sfdisk: cannot open /dev/sdc for reading

Drive sdd: _____________________________________________________________________

fdisk -lu /dev/sdd:

sfdisk -V /dev/sdd:

/dev/sdd: No medium found

sfdisk: cannot open /dev/sdd for reading

Drive sde: _____________________________________________________________________

fdisk -lu /dev/sde:

sfdisk -V /dev/sde:

/dev/sde: No medium found

sfdisk: cannot open /dev/sde for reading

Drive sdf: _____________________________________________________________________

fdisk -lu /dev/sdf:

sfdisk -V /dev/sdf:

/dev/sdf: No medium found

sfdisk: cannot open /dev/sdf for reading

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="90200D34200D22B8" TYPE="ntfs" 
/dev/sda2: UUID="FEA0ABBDA0AB7B33" LABEL="New Volume" TYPE="ntfs" 
/dev/sdb1: UUID="96789FAE789F8B9D" LABEL="New Volume" TYPE="ntfs" 
/dev/sdb2: UUID="97c41e98-32f8-4fc8-b7dd-4f83b6003aea" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="d4bdf4a4-6791-42e7-94d8-8c49129a8c30" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Professional x64 Edition" /noexecute=optin /fastdetect

multi(0)disk(0)rdisk(0)partition(1)\bootsect.lnx="UBUNTU 8.10"
=========================== sdb2/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=97c41e98-32f8-4fc8-b7dd-4f83b6003aea ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=97c41e98-32f8-4fc8-b7dd-4f83b6003aea

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		97c41e98-32f8-4fc8-b7dd-4f83b6003aea
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=97c41e98-32f8-4fc8-b7dd-4f83b6003aea ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		97c41e98-32f8-4fc8-b7dd-4f83b6003aea
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=97c41e98-32f8-4fc8-b7dd-4f83b6003aea ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		97c41e98-32f8-4fc8-b7dd-4f83b6003aea
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
chainloader	+1


=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=97c41e98-32f8-4fc8-b7dd-4f83b6003aea /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=d4bdf4a4-6791-42e7-94d8-8c49129a8c30 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sdb2/boot: ==================================

total 12812
drwxr-xr-x  3 root root    4096 2009-01-07 01:17 .

drwxr-xr-x 20 root root    4096 2009-01-07 01:17 ..
-rw-r--r--  1 root root  503560 2008-10-24 07:55 abi-2.6.27-7-generic
-rw-r--r--  1 root root   85316 2008-10-24 07:55 config-2.6.27-7-generic
drwxr-xr-x  2 root root    4096 2009-01-07 01:17 grub
-rw-r--r--  1 root root 8649299 2009-01-07 01:17 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r--  1 root root 1352144 2008-10-24 07:55 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1130 2008-10-24 07:57 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2339712 2008-10-24 07:55 vmlinuz-2.6.27-7-generic

=============================== sdb2/boot/grub: ===============================

total 216
drwxr-xr-x 2 root root   4096 2009-01-07 01:17 .
drwxr-xr-x 3 root root   4096 2009-01-07 01:17 ..
-rw-r--r-- 1 root root    197 2009-01-07 01:17 default
-rw-r--r-- 1 root root     30 2009-01-07 01:17 device.map
-rw-r--r-- 1 root root   8108 2009-01-07 01:17 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-01-07 01:17 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-01-07 01:17 installed-version
-rw-r--r-- 1 root root   8712 2009-01-07 01:17 jfs_stage1_5
-rw-r--r-- 1 root root   4604 2009-01-07 01:17 menu.lst
-rw-r--r-- 1 root root   7352 2009-01-07 01:17 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-01-07 01:17 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-07 01:17 stage1
-rw-r--r-- 1 root root 121460 2009-01-07 01:17 stage2
-rw-r--r-- 1 root root   9556 2009-01-07 01:17 xfs_stage1_5

=============================== StdErr Messages: ===============================

/dev/sdc: No medium found

sfdisk: cannot open /dev/sdc for reading
/dev/sdd: No medium found

sfdisk: cannot open /dev/sdd for reading
/dev/sde: No medium found

sfdisk: cannot open /dev/sde for reading
/dev/sdf: No medium found

sfdisk: cannot open /dev/sdf for reading
```

Thanks for your help.

Ted

---

### Post by caljohnsmith on 2009-01-07
OK, to install Grub to the MBR of your Ubuntu drive, you can do:
```
sudo grub
grub> root (hd1,1)
grub> setup (hd1)
grub> quit
```
And then if you set your BIOS to boot the Ubuntu drive, you should be able to boot into Ubuntu if all goes well. Once you get into Ubuntu, how about opening your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And at the end of that file add:
```
title       Windows XP
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
And then you should be able to boot Windows XP from your Grub menu. Let me know how it goes or if you run into problems.

---

### Post by teddeman on 2009-01-07
Took care of step 1.  Is there a way to continue to use the windows loader and point it to the grub as a second option?

---

### Post by caljohnsmith on 2009-01-07
If you want to use the Windows boot loader, how about downloading and using "[bootpart]("http://www.winimage.com/bootpart.htm")" within Windows. It's easier to use bootpart rather than manually copy your Grub boot sector and add reference to it in Windows boot.ini file, because bootpart automates the whole process. Let me know how that goes or if you run into problems.

---

### Post by teddeman on 2009-01-08
> **caljohnsmith said:**
> If you want to use the Windows boot loader, how about downloading and using "[bootpart]("http://www.winimage.com/bootpart.htm")" within Windows. It's easier to use bootpart rather than manually copy your Grub boot sector and add reference to it in Windows boot.ini file, because bootpart automates the whole process. Let me know how that goes or if you run into problems.

Did not like bootpart.  I had another tutorial that mentioned the following statement:"sudo dd if=/dev/sdb of=/bootsect.lnx bs=512 count=1"  I entered this in a terminal window, copied the file back to the sda (windows partition), and added the following to the boot.ini file "c:\bootsect.lnx "Ubuntu 8.10""  When I rebooted and selected U 8.10, the screen went black and "GRUB" appeared in the upper left corner.  The computer did nothing else.  I must have been close?

---

### Post by caljohnsmith on 2009-01-08
> **teddeman said:**
> Did not like bootpart.  I had another tutorial that mentioned the following statement:"sudo dd if=/dev/sdb of=/bootsect.lnx bs=512 count=1"  I entered this in a terminal window, copied the file back to the sda (windows partition), and added the following to the boot.ini file "c:\bootsect.lnx "Ubuntu 8.10""  When I rebooted and selected U 8.10, the screen went black and "GRUB" appeared in the upper left corner.  The computer did nothing else.  I must have been close?
That's actually why I suggested using bootpart, because bootpart is smart enough to modify the Grub boot sector when you try to boot Grub from a drive other than the drive Windows is on. In other words, copying the Grub boot sector with dd and adding it manually to the boot.ini file as you did normally only works if Grub is on the same drive as Windows; but fortunately, if install Grub to the boot sector of the linux partition in a special way first, then you should be able to use that method without any problems. So to do that, how about trying:
```
sudo grub
grub> device (hd1) /dev/sdb
grub> device (hd0) /dev/sdb
grub> root (hd1,1)
grub> setup (hd0,1)
grub> quit
```
And please post the output of the above commands prior to doing the "quit". After that, simply copy the Grub boot sector to your Windows partition similar to what you did before:
```
sudo mount /dev/sda1 /mnt
sudo dd if=/dev/sdb2 of=/mnt/bootsect.lnx bs=512 count=1
```
Note you should use "sdb2" rather than "sdb" above to copy the boot sector of the Ubuntu sdb2 partition, rather than the sdb MBR. And if you still have the line in your boot.ini file for the bootsect.lnx, then hopefully you will then be able to boot Ubuntu from your Windows boot menu. Let me know how it goes or if you run into problems.

---

### Post by teddeman on 2009-01-08
Step 1 Output:

```
teddeman@Athlon8400U:~$ sudo grub
[sudo] password for teddeman: 
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> device (hd1) /dev/sdb
device (hd1) /dev/sdb
grub> device (hd0) /dev/sdb
device (hd0) /dev/sdb
grub> root (hd1,1)
root (hd1,1)
grub> setup (hd0,1)
setup (hd0,1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,1)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd1,1)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 d (hd0,1) /boot/grub/stage2 p /boot/grub/menu.lst "... succeeded
Done.
grub> 
```

Step 2 completed, rebooting now.

Success!!!  You are the man!  Now I just need to think about adding Windows 7 (on its way from MS Technet as I type) to the second half of my SDB drive.  I want to test it for mom who hates vista (doesn't everyone?) on her new laptop.  I think I am going to be able to sell the wife on 8.10 (as this is installed on her new computer!).

Thanks for all your help.  

Will installing the 218 updates that are waiting going to screw up the boot process?  would a kernel upgrade screw it up?

---

### Post by caljohnsmith on 2009-01-08
> **teddeman said:**
> 
Will installing the 218 updates that are waiting going to screw up the boot process?  would a kernel upgrade screw it up?
Well, I can't say for sure, but I think you should be fine about all the updates. If you have any problems though, there's always help waiting in the forums. Cheers and have fun with all your OSes. :)

---

