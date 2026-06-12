---
title: "[SOLVED] Grub Error 13: Same hard drive, separate partitions"
date: 2008-12-19
forum: Installation &amp; Upgrades
---

### Post by airjaw on 2008-12-19
Hi guys, wondering if you could help with this problem my computer developed.

I've had dual-boot XP and Ubuntu for a while now, everything worked fine. For some reason, within the past few weeks, Grub cannot boot into Windows XP.

Error 13: Invalid or Unsupported Executable format.

I did some research and here are results for fdisk -l and menu.lst:

had to do sudo fdisk -l (note: fdisk -l did not work)
[B]fdisk - l
[/B]
> Cannot open /dev/sda
Cannot Open /dev/sdb

**sudo fdisk -l**
> Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x08000000                     

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       14267       14594     2620416    c  W95 FAT32 (LBA)
/dev/sda2            2551       13172    85321215   83  Linux          
/dev/sda3           14161       14593     3478072+   5  Extended       
/dev/sda4           13173       14160     7936110   83  Linux
/dev/sda5           14448       14593     1172713+  82  Linux swap / Solaris
/dev/sda6           14161       14447     2305264+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xad6ce434

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24321   195358401   83  Linux



**menu.lst**
> ## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		339bab9c-9a2a-438f-a7d2-72516e5144b6
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=339bab9c-9a2a-438f-a7d2-72516e5144b6 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		339bab9c-9a2a-438f-a7d2-72516e5144b6
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=339bab9c-9a2a-438f-a7d2-72516e5144b6 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		339bab9c-9a2a-438f-a7d2-72516e5144b6
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=339bab9c-9a2a-438f-a7d2-72516e5144b6 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		339bab9c-9a2a-438f-a7d2-72516e5144b6
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=339bab9c-9a2a-438f-a7d2-72516e5144b6 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		339bab9c-9a2a-438f-a7d2-72516e5144b6
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



I'm pretty sure /dev/sda3 is my Windows Drive.. but not sure how whether booting to hd0,0 is right. I'm not sure what could have rewritten my menu.lst file as it was working before.. Maybe NTFS configuration tool which I installed recently?

Also, this is on the same laptop harddrive, just partitioned out into separate drives.

Any help or perspective is appreciated! I really can't afford to mess up my Ubuntu environment right now.
Thank you.

---

### Post by upchucky on 2008-12-19
get advanced supergrub to fix mbr

may need live cd such as knoppix to edit boot files to set the partitions and boot stages right

---

### Post by 73ckn797 on 2008-12-19
> **airjaw said:**
> Hi guys, wondering if you could help with this problem my computer developed.

I've had dual-boot XP and Ubuntu for a while now, everything worked fine. For some reason, within the past few weeks, Grub cannot boot into Windows XP.

Error 13: Invalid or Unsupported Executable format.

I did some research and here are results for fdisk -l and menu.lst:

had to do sudo fdisk -l (note: fdisk -l did not work)
[B]fdisk - l
[/B]


**sudo fdisk -l**


**menu.lst**


I'm pretty sure /dev/sda3 is my Windows Drive.. but not sure how whether booting to hd0,0 is right. I'm not sure what could have rewritten my menu.lst file as it was working before.. Maybe NTFS configuration tool which I installed recently?

Also, this is on the same laptop harddrive, just partitioned out into separate drives.

Any help or perspective is appreciated! I really can't afford to mess up my Ubuntu environment right now.
Thank you.


Try editing (hd0,0) to (hd0,2) and see what happens. You can first try this from the grub menu by highlighting the XP selection and pressing "e". Then highlight the (hd0,0) line and pressing "e" again. Then change to (hd0,2). You then can press "b" to boot the change.

---

### Post by caljohnsmith on 2008-12-19
How about opening a terminal (Applications > Acceossories > Terminal), and please post the output of:
```
sudo mkdir /mnt/sda1 /mnt/sda2
sudo mount /dev/sda1 /mnt/sda1
sudo mount /dev/sda2 /mnt/sda2
ls -l /mnt/sda1 /mnt/sda2
```
And we can work from there if you want.

---

### Post by 73ckn797 on 2008-12-19
> **caljohnsmith said:**
> How about opening a terminal (Applications > Acceossories > Terminal), and please post the output of:
```
sudo mkdir /mnt/sda1 /mnt/sda2
sudo mount /dev/sda1 /mnt/sda1
sudo mount /dev/sda2 /mnt/sda2
ls -l /mnt/sda1 /mnt/sda2
```And we can work from there if you want.

caljohnsmith will fix you up for sure.

---

### Post by airjaw on 2008-12-19
> **73ckn797 said:**
> Try editing (hd0,0) to (hd0,2) and see what happens. You can first try this from the grub menu by highlighting the XP selection and pressing "e". Then highlight the (hd0,0) line and pressing "e" again. Then change to (hd0,2). You then can press "b" to boot the change.

Thanks for advice.  Tried that,
got 
hd0,2
> Error 12: Invalid device requested

linux boots to hd0, 3

sudo mount /dev/sda1 /mnt/sda1
> mount: you must specify the filesystem type

sudo mkdir /mnt/sda3
sudo mount -t Extended /dev/sda3 /mnt/sda3
> mount: unknown filesystem type 'Extended'
sudo mount -t ntfs /dev/sda3 /mnt/sda3
> Failed to mount '/dev/sda3': Invalid argument
The device '/dev/sda3' doesn't have a valid NTFS.

I should also add that I have never been able to access my Windows NTFS drive from within Ubuntu. For some reason it never shows up.

---

### Post by caljohnsmith on 2008-12-19
OK, please post the output of:
```
sudo blkid
sudo mount -t vfat -o force /dev/sda1 /mnt/sda1
sudo mount /dev/sda2 /mnt/sda2
ls -l /mnt/sda1 /mnt/sda2
```

---

### Post by airjaw on 2008-12-19
**sudo blkid**
> /dev/sda2: UUID="652f78cc-09d3-4f4e-b861-6b7d1cbc69ab" TYPE="ext3"
/dev/sda4: UUID="339bab9c-9a2a-438f-a7d2-72516e5144b6" TYPE="ext3"
/dev/sda5: TYPE="swap" UUID="315badc5-b892-4cad-b994-500b4daa9929"
/dev/sda6: TYPE="swap" UUID="c7080b1b-92c8-4237-9505-08519ff3a851"
/dev/sdb1: LABEL="Backup" UUID="345587f1-8eef-42d2-9648-d6047f6fc5bc" SEC_TYPE="ext2" TYPE="ext3"


**sudo mount -t vfat -o force /dev/sda1 /mnt/sda1**
> mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


**sudo mount /dev/sda2 /mnt/sda2**
Seemed to have worked.

**ls -l /mnt/sda1 /mnt/sda2**
> /mnt/sda1:
total 0

/mnt/sda2:
total 20
drwxr-xr-x 57 airjaw airjaw  4096 2008-12-19 15:16 airjaw
drwx------  2 root   root   16384 2008-11-18 14:47 lost+found


---

### Post by caljohnsmith on 2008-12-19
When was the last time you were able to boot successfully into Windows, and what have you done on your computer since then? You don't have any NTFS/FAT partitions, which is what Windows would use. Your sda1 partition is labeled as FAT in the partition table, but blkid says the file system is ext2. Also, sda1 is only 2.6 GB, so that's not enough to hold Windows. I thought that maybe your sda2 partition could possibly have Windows, because I figured there might be a mistake in the partition table about it being labeled as a linux file system. But blkid says sda2 is ext3, and also sda2 doesn't have your Windows installation; the directory listing only showed "airjaw" and "lost+found" folders. Were you previously able to boot Windows from your Grub menu, and have you made any changes to your Grub's menu.lst since then? 

In order to get a clearer picture of your setup, how about doing:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "boot_info_results.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup.

---

### Post by airjaw on 2008-12-19
Thanks for all the continued help..

I last booted into windows several weeks ago.
I can't think of anything that I have done to mess anything up.
All I've done since then is install software and Ubuntu updates.

here is the rundown of my devices:

sda1 : not sure what this is
sda2 : my /home partition, 86GB
sda3 : pretty sure this is my windows partition, 35GB
sda4 : linux partition, /
sda5,6: swap partitions
sdb : my external hard drive, ext3


> Grub is installed in the MBR of /dev/sda and looks on the same drive in partition #4 for its boot files.
No known boot loader is installed in the MBR of /dev/sdb

sda1:
    File system:  Extended Partition

sda2:
    File system:  ext3
    Boot sector  type:  Unknown
    Boot sector  info:  
    Operating System: 
    Boot files/directories present: 

sda3:
    File system:  Extended Partition

sda4:
    File system:  ext3
    Boot sector  type:  Unknown
    Boot sector  info:  
    Operating System: Linux
    Boot files/directories present:  /boot/grub/menu.lst /boot /boot/grub

sda5:
    File system:  swap

sda6:
    File system:  swap

sdb1:
    File system:  ext3
    Boot sector  type:  Unknown
    Boot sector  info:  
    Operating System: 
    Boot files/directories present: 


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x08000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *   229197824   234438655     2620416    c  W95 FAT32 (LBA)
/dev/sda2        40965750   211608179    85321215   83  Linux
/dev/sda3       227480400   234436544     3478072+   5  Extended
/dev/sda4       211608180   227480399     7936110   83  Linux
/dev/sda5       232091118   234436544     1172713+  82  Linux swap / Solaris
/dev/sda6       227480526   232091054     2305264+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xad6ce434

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   390716864   195358401   83  Linux
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=229197824, size=  5240832, Id= c, bootable
/dev/sda2 : start= 40965750, size=170642430, Id=83
/dev/sda3 : start=227480400, size=  6956145, Id= 5
/dev/sda4 : start=211608180, size= 15872220, Id=83
/dev/sda5 : start=232091118, size=  2345427, Id=82
/dev/sda6 : start=227480526, size=  4610529, Id=82
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=       63, size=390716802, Id=83
/dev/sdb2 : start=        0, size=        0, Id= 0
/dev/sdb3 : start=        0, size=        0, Id= 0
/dev/sdb4 : start=        0, size=        0, Id= 0

sda4/boot/grub/menu.lst

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
# kopt=root=UUID=339bab9c-9a2a-438f-a7d2-72516e5144b6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=339bab9c-9a2a-438f-a7d2-72516e5144b6

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		339bab9c-9a2a-438f-a7d2-72516e5144b6
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=339bab9c-9a2a-438f-a7d2-72516e5144b6 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		339bab9c-9a2a-438f-a7d2-72516e5144b6
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=339bab9c-9a2a-438f-a7d2-72516e5144b6 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		339bab9c-9a2a-438f-a7d2-72516e5144b6
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=339bab9c-9a2a-438f-a7d2-72516e5144b6 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		339bab9c-9a2a-438f-a7d2-72516e5144b6
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=339bab9c-9a2a-438f-a7d2-72516e5144b6 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		339bab9c-9a2a-438f-a7d2-72516e5144b6
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


sda4/boot

total 23764
drwxr-xr-x  3 root root    4096 2008-12-16 17:43 .
drwxr-xr-x 21 root root    4096 2008-12-05 14:57 ..
-rw-r--r--  1 root root  507665 2008-11-04 16:00 abi-2.6.27-7-generic
-rw-r--r--  1 root root  507665 2008-11-20 18:46 abi-2.6.27-9-generic
-rw-r--r--  1 root root   91364 2008-11-04 16:00 config-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-11-20 18:46 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2008-11-29 14:06 grub
-rw-r--r--  1 root root 8182593 2008-11-26 18:21 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8182884 2008-12-16 17:43 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 16:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-11-04 16:00 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1029585 2008-11-20 18:46 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1073 2008-11-04 16:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-11-20 18:48 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2244464 2008-11-04 16:00 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2244304 2008-11-20 18:46 vmlinuz-2.6.27-9-generic

sda4/boot/grub

total 224
drwxr-xr-x 2 root root   4096 2008-11-29 14:06 .
drwxr-xr-x 3 root root   4096 2008-12-16 17:43 ..
-rw-r--r-- 1 root root    197 2008-11-18 17:07 default
-rw-r--r-- 1 root root     30 2008-11-18 17:07 device.map
-rw-r--r-- 1 root root   8108 2008-11-18 17:07 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-11-18 17:07 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-11-18 17:07 installed-version
-rw-r--r-- 1 root root   8712 2008-11-18 17:07 jfs_stage1_5
-rw-r--r-- 1 root root   5103 2008-11-29 14:06 menu.lst
-rw-r--r-- 1 root root   4621 2008-11-29 14:06 menu.lst~
-rw-r--r-- 1 root root   7352 2008-11-18 17:07 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-11-18 17:07 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-11-18 17:07 stage1
-rw-r--r-- 1 root root 121460 2008-11-18 17:07 stage2
-rw-r--r-- 1 root root   9556 2008-11-18 17:07 xfs_stage1_5

StdErr Messages 

Unknown MBR on /dev/sdb

00000000  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  00 00 00 00 00 00 00 00  34 e4 6c ad 00 00 00 01  |........4.l.....|
000001c0  01 00 83 fe ff ff 3f 00  00 00 82 dd 49 17 00 00  |......?.....I...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


---

### Post by caljohnsmith on 2008-12-19
Your Windows can't be on sda3 because that is an "extended" partition, meaning that it is merely a conceptual container for your logical partitions. :) Since your Ubuntu install is obviously on sda4, and since sda2 is just your personal documents, that only leaves sda1 as a possible partition for Windows. Yet as I mentioned earlier, sda1 is only 2.6 GB which to my knowledge is not big enough to hold Windows. Did you do any kind of partition changes recently? But I see there is a huge ~21 GB chunk of unused space on your HDD right now, so I suspect your Windows partition may have been deleted. 

In order to find out if the Windows partition was deleted, you can use "testdisk" to scan your HDD for lost/deleted partitions. How about first making sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
**If you are using Version 6.8:**
After starting testdisk with the above command, choose "no log", select HDD and "Proceed", "Intel", "Analyze", "Proceed", "N" to skip the search for Vista partitions, hit enter to continue, and select "Search!" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results.
[B]
If you are using Version 6.9:[/B]
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", "quick search", "N" to skip the search for Vista partitions, hit enter to continue, and select "Deeper Search" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results.

---

### Post by airjaw on 2008-12-20
[HTML]
Disk /dev/sda - 120 GB / 111 GiB - CHS 14594 255 63
Partition               Start        End    Size in sectors
* HPFS - NTFS              0   1  1  2549 254 63   40965687 
P Linux                 2550   0  1 13171 254 63  170642430 
P Linux                13172   0  1 14159 254 63   15872220 
L Linux Swap           14160   2  1 14446 254 63    4610529 
L Linux Swap           14447   1  1 14592 254 63    2345427[/HTML]

[HTML]
Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0   1  1  2549 254 63   40965687
 2 P Linux                 2550   0  1 13171 254 63  170642430
 3 P Linux                13172   0  1 14159 254 63   15872220
 4 E extended LBA         14160   0  1 14593 254 63    6972210
 5 L Linux Swap           14160   2  1 14446 254 63    4610529
 6 L Linux Swap           14447   1  1 14592 254 63    2345427[/HTML]

[HTML]Current partition structure:
     Partition                  Start        End    Size in sectors

Invalid FAT boot sector
 1 * FAT32 LBA            14266 230 45 14593  33 32    5240832
 1 * FAT32 LBA            14266 230 45 14593  33 32    5240832
 2 P Linux                 2550   0  1 13171 254 63  170642430
 3 E extended             14160   0  1 14592 254 63    6956145
 4 P Linux                13172   0  1 14159 254 63   15872220
Space conflict between the following two partitions
 3 E extended             14160   0  1 14592 254 63    6956145
 1 * FAT32 LBA            14266 230 45 14593  33 32    5240832
 5 L Linux Swap           14447   1  1 14592 254 63    2345427
   X extended             14160   0  2 14446 254 63    4610654
 6 L Linux Swap           14160   2  1 14446 254 63    4610529[/HTML]


[HTML]The harddisk (120 GB / 111 GiB) seems too small! (< 120 GB / 112 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partitions can't be recovered:
     Partition               Start        End    Size in sectors
  Linux                13661   1  1 14649   0 59   15872216
  Linux                13662   2  1 14650   1 59   15872216[/HTML]


I've run it a few times because I am never sure where the results are.  The above is what I keep getting.

---

### Post by caljohnsmith on 2008-12-20
> **airjaw said:**
> ```
Current partition structure:
Partition Start End Size in sectors

Invalid FAT boot sector
1 * FAT32 LBA 14266 230 45 14593 33 32 5240832
1 * FAT32 LBA 14266 230 45 14593 33 32 5240832
2 P Linux 2550 0 1 13171 254 63 170642430
3 E extended 14160 0 1 14592 254 63 6956145
4 P Linux 13172 0 1 14159 254 63 15872220
[COLOR="Red"]Space conflict between the following two partitions[/COLOR]
3 E extended 14160 0 1 14592 254 63 6956145
1 * FAT32 LBA 14266 230 45 14593 33 32 5240832
5 L Linux Swap 14447 1 1 14592 254 63 2345427
X extended 14160 0 2 14446 254 63 4610654
6 L Linux Swap 14160 2 1 14446 254 63 4610529 
```
It definitely looks like something happened with the partitions on your HDD, because as you can see from the above error, your partition table is corrupt at this point. sda1 is a primary partition, and yet it is inside of the sda3 extended partition, so sda1 should be a logical partition instead. But the above output is not the results of the "deep search"; the deep search should take a while to run. Which version of testdisk are you using? Please follow my previous instructions in order to do the deep search, and post the results when that is finished.

---

### Post by airjaw on 2008-12-20
> **caljohnsmith said:**
> It definitely looks like something happened with the partitions on your HDD, because as you can see from the above error, your partition table is corrupt at this point. sda1 is a primary partition, and yet it is inside of the sda3 extended partition, so sda1 should be a logical partition instead. But the above output is not the results of the "deep search"; the deep search should take a while to run. Which version of testdisk are you using? Please follow my previous instructions in order to do the deep search, and post the results when that is finished.

Sorry, I think I'm doing it correctly but never get any "substantial" test results.

This is the deep search in action:
[HTML]Disk /dev/sda - 120 GB / 111 GiB - CHS 14594 255 63
Analyse cylinder  5741/14593: 39%


  HPFS - NTFS              0   1  1  2549 254 49   40965673
  HPFS - NTFS              0   1 15  2549 254 63   40965673
  Linux                 2550   0  1 13171 254 57  170642424
  Linux                 2550   0  1 13171 254 57  170642424


  Stop[/HTML]

Thanks for your continued help.  How does this kind of thing happen?
I suppose I could reinstall WinXP again but we'd have to make sure the partition is working right?

edit:: same result as before.. says the partitions can't be recovered.

---

### Post by caljohnsmith on 2008-12-20
It's actually perfectly normal for testdisk to claim that one or more of the partitions can't be recovered, but doesn't testdisk say something about "continue" and give you the deep search results? We need the deep search results in order to proceed.

---

### Post by airjaw on 2008-12-20
It does say "continue" at the bottom.
After I press ENTER i get this screen:
[HTML]Disk /dev/sda - 120 GB / 111 GiB - CHS 14594 255 63
     Partition               Start        End    Size in sectors
D HPFS - NTFS              0   1  1  2549 254 63   40965687
D HPFS - NTFS              0   1 15  2549 254 63   40965673
D Linux                 2550   0  1 13171 254 63  170642430
D Linux                11188   0  1 14446 254 63   52355835
D Linux                13172   0  1 14159 254 63   15872220
D Linux Swap           14160   2  1 14446 254 63    4610529
L Linux Swap           14447   1  1 14592 254 63    2345427[/HTML]

It allows me to move the cursor up and down to highlight the different drives.  Usually I just press ENTER here again and it takes me back to the main screen. I must be missing a step.

---

### Post by caljohnsmith on 2008-12-20
> **airjaw said:**
> ```
Disk /dev/sda - 120 GB / 111 GiB - CHS 14594 255 63
     Partition               Start        End    Size in sectors
[COLOR="blue"]D or *[/COLOR] HPFS - NTFS              0   1  1  2549 254 63   40965687
[COLOR="blue"]D or *[/COLOR] HPFS - NTFS              0   1 15  2549 254 63   40965673
[COLOR="Red"]P[/COLOR] Linux                 2550   0  1 13171 254 63  170642430
[COLOR="Red"]D[/COLOR] Linux                11188   0  1 14446 254 63   52355835
[COLOR="Red"]L[/COLOR] Linux                13172   0  1 14159 254 63   15872220
[COLOR="Red"]L[/COLOR] Linux Swap           14160   2  1 14446 254 63    4610529
[COLOR="Red"]L[/COLOR] Linux Swap           14447   1  1 14592 254 63    2345427
```
OK, great, you finally have the deep search results above. As you probably have all ready noticed, you can use the up/down arrow keys to select each partition and then move the right/left arrow keys to change the partition from "*", "P", "L", and "D". 

Select each of the first two NTFS partitions above, press "P" to get a directory listing, and for whichever of those two NTFS partitions shows your Windows root directory, mark that partition as "*" and the other partition as "D". Next mark the remaining partitions as I have highlighted in red above, but for the two linux partitions that are marked "L", use "P" to make sure you can see their directories. If you can, make one final check that everything is marked as shown above (except you choose the correct NTFS partition), press enter to proceed, and then you can choose to write the new partition table to your HDD. After that reboot, and first see if you can boot into Ubuntu. If you can, please post:
```
sudo fdisk -lu
```
And also try booting into Windows from your Grub menu. Let me know how it goes.

---

### Post by airjaw on 2008-12-20
First NTFS partition has my windows files on it
Second NTFS partition :
[HTML]Can't open filesystem. Filesystem seems damaged.
[/HTML]
Third Linux partition:  my home directory
Fourth linux partition: No file found, filesystem seems damaged
5th Linux: my root / filesystem
6th, 7th: swap 

[HTML]
* HPFS - NTFS              0   1  1  2549 254 63   40965687
D HPFS - NTFS              0   1 15  2549 254 63   40965673
D Linux                 2550   0  1 13171 254 63  170642430
D Linux                11188   0  1 14446 254 63   52355835
D Linux                13172   0  1 14159 254 63   15872220
D Linux Swap           14160   2  1 14446 254 63    4610529
L Linux Swap           14447   1  1 14592 254 63    2345427[/HTML]

What do P and D mean? Should my 5th partition (15872220) be P?

---

### Post by caljohnsmith on 2008-12-20
> **airjaw said:**
> 
What do P and D mean? Should my 5th partition (15872220) be P?
"P" means primary partition, "D" means you want it deleted, and "L" means logical partition. Try marking all the partitions as given in my previous post, but mark the first NTFS partition as "*" since that is your Windows partition. If for some reason you can't mark the 5th linux partition as "L", mark it as "P" instead. Same with the 3rd linux partition: if you can't mark it as "P", then choose "L".

---

### Post by airjaw on 2008-12-20
Thanks!
this is what I did:
[HTML]Disk /dev/sda - 120 GB / 111 GiB - CHS 14594 255 63
     Partition               Start        End    Size in sectors
* HPFS - NTFS              0   1  1  2549 254 63   40965687
D HPFS - NTFS              0   1 15  2549 254 63   40965673
P Linux                 2550   0  1 13171 254 63  170642430
D Linux                11188   0  1 14446 254 63   52355835
P Linux                13172   0  1 14159 254 63   15872220
L Linux Swap           14160   2  1 14446 254 63    4610529
L Linux Swap           14447   1  1 14592 254 63    2345427

[/HTML]

the 5th one wouldn't mark as L so I put P, third one was OK with P.

I'll be back as I reboot

[HTML]     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0   1  1  2549 254 63   40965687
 2 P Linux                 2550   0  1 13171 254 63  170642430
 3 P Linux                13172   0  1 14159 254 63   15872220
 4 E extended LBA         14160   0  1 14593 254 63    6972210
 5 L Linux Swap           14160   2  1 14446 254 63    4610529
 6 L Linux Swap           14447   1  1 14592 254 63    2345427


[  Quit  ]  [ Write  ]
                       Write partition structure to disk[/HTML]


Edit::
Grub Loading stage1.5.

GRUB loading, please wait...
Error 17

edit2:: 
I made a SuperGrub CD and booted to it. SuperGrub will boot windows but Ubuntu doesn't work.

---

### Post by caljohnsmith on 2008-12-20
OK, how about booting your Live CD and do:
```
sudo grub
grub> find /boot/grub/stage1
```
The command above should return your main Ubuntu partition in the form of (hdX,Y) where X and Y are numbers, for example (hd0,2), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Please post the output of all the above commands, reboot, and let me know what happens on start up.

---

### Post by airjaw on 2008-12-20
[HTML]grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,2)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.
[/HTML]


edit: rebooting.. grub starts up! and I'm able to boot into both Ubuntu and Windows.
Do you mind giving me a (brief) explanation of what just happened? I'd like to have some context so maybe I could do more next time.. (or the long version if its not too much trouble)
Thanks so much for your help!

---

### Post by caljohnsmith on 2008-12-20
> **airjaw said:**
> 
edit: rebooting.. grub starts up! and I'm able to boot into both Ubuntu and Windows.
Do you mind giving me a (brief) explanation of what just happened? I'd like to have some context so maybe I could do more next time.. (or the long version if its not too much trouble)
Thanks so much for your help!
That's great news both Ubuntu and Windows are booting OK. Truthfully I have no idea what happened that your Windows partition was accidentally deleted--only you might have some clues about that. Did you use a partition editor recently? 

Anyway, the main clue about your problem was that you had about 21 GB of unused space at the beginning of your drive. That almost never happens--if a drive has unused space it is usually at the end of the drive. Also I didn't notice at first but your partition table was corrupt, and that along with the fact that you couldn't even mount sda1 led me to believe that your partition table had been changed. So fortunately testdisk came to the rescue and found your original partitions. Anyway, cheers and have fun with Windows and Ubuntu. :)

---

### Post by airjaw on 2008-12-21
Yea weird.. i'm not sure how that happened. I didn't do any strange things recently. oh well.. thanks again.

---

