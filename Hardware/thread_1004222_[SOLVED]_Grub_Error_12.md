---
title: "[SOLVED] Grub Error 12"
date: 2008-12-07
forum: Hardware
---

### Post by nerdpride on 2008-12-07
Hello. Because of a cooling problem with my beloved Toshiba Satellite A75, I have had to completely redo my hard drive. I have Ubuntu on 48 GB partition, 2 GB of Swap space, and 50 GB of Windows XP. When I boot up GRUB comes up normally, however, when I select XP it gives Error 12. I hve read a few similar post spread thinly across the internet, but nothing there has fixed by problem.

Here is my partition table:

```
Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd8c3d8c3

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5932    47648758+  83  Linux
/dev/hda2           11919       12161     1951897+  82  Linux swap / Solaris
/dev/hda3            5933       11914    48050415    5  Extended
/dev/hda5            5933       11914    48050383+  83  Linux

Partition table entries are not in disk order
```

I have attached menu.lst

---

### Post by caljohnsmith on 2008-12-07
Your fdisk output only shows linux partitions, no NTFS/FAT partitions which Windows would need to be installed on. Since you just recently reinstalled, I would suggest reinstalling again, but first set up a primary NTFS partition for Windows (I wouldn't recommend trying to put Windows on a logical partition, although with enough hassle it can be done), and then also set up the rest of your Linux partitions, which can be primary or logical (it doesn't matter). If you boot your Live CD and go to System > Admin > Partition Editor, you can use that to set up your partitions. How about trying that and let me know how it goes, or let me know if you run into problems.

---

### Post by nerdpride on 2008-12-15
Well I can't reinstallwindows since i created that patition from an image (using partimage). I have already installed GParted. And I am fine at managing patitions i just can't figure out what is wrong. Below is an image from GPartted:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=96538&stc=1&d=1229395379[/IMG]

Does any body have any idea what is wrong? It way above me.

---

### Post by nerdpride on 2008-12-15
Okay that picture is terrible. Here is the table from the more "Copy & Paste" friendly text-based Parted:

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  48.8GB  48.8GB  primary   ext2         boot 
 3      48.8GB  98.0GB  49.2GB  extended                    
 5      48.8GB  98.0GB  49.2GB  logical   ntfs              
 2      98.0GB  100GB   1999MB  primary   linux-swap

---

### Post by caljohnsmith on 2008-12-15
So is Windows supposed to be on sda5? Because that is the only NTFS partition you listed. In order to get a clearer picture of your setup, how about downloading the attached "boot_info7.sh.txt" file to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo sh ~/Desktop/boot_info7.sh.txt
```
That will create a "BootInfo.txt" file on your desktop; please copy/paste the contents of that file to your next post, or you can attach the file itself to your post. That will help clarify your setup and what your problem might be.

---

### Post by nerdpride on 2008-12-15
Now i see what you are saying. What is a logical partition and how can i move all the data from that partition to a normal partition. And I have finally included a good copy of my partition table. I have some music, software, and file that could not be cheaply replaced if replaced at all. Thank you to anyone kind enough to waste their time on an, I am  sure, stupid problem.


[Partition Table]("http://ubuntuforums.org/attachment.php?attachmentid=96541&stc=1&d=1229396737")

---

### Post by nerdpride on 2008-12-15
You guys are fast. Thanks a ton. her is the file:

```
Grub is installed in the MBR of /dev/sda and looks on the same drive in partition #1 for its boot files.

sda1 :ext2:BS: None:OS Linux: /boot/grub/menu.lst /boot /boot/grub 

sda2 :swap:BS: None:OS : 

sda3 ::BS: None:OS : 

sda5 :ntfs:BS: XP:OS : /boot.ini /ntldr /NTDETECT.COM 


Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd8c3d8c3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    95297579    47648758+  83  Linux
/dev/sda2       191462670   195366464     1951897+  82  Linux swap / Solaris
/dev/sda3        95297580   191398409    48050415    5  Extended
/dev/sda5        95297643   191398409    48050383+  83  Linux

Partition table entries are not in disk order
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 95297517, Id=83, bootable
/dev/sda2 : start=191462670, size=  3903795, Id=82
/dev/sda3 : start= 95297580, size= 96100830, Id= 5
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start= 95297643, size= 96100767, Id=83

sda1/boot/grub/menu.lst

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
# kopt=root=UUID=0cb33649-5267-4e8f-9478-45c1b82a14e2 ro

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=0cb33649-5267-4e8f-9478-45c1b82a14e2 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=0cb33649-5267-4e8f-9478-45c1b82a14e2 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0cb33649-5267-4e8f-9478-45c1b82a14e2 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0cb33649-5267-4e8f-9478-45c1b82a14e2 ro  single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda5
title		Microsoft Windows XP Home Edition
root		(hd0,4)
savedefault
makeactive
chainloader	+1


sda1/boot

total 29984
drwxr-xr-x  3 root root    4096 2008-12-07 10:32 .
drwxr-xr-x 21 root root    4096 2008-12-07 10:31 ..
-rw-r--r--  1 root root  422607 2008-04-10 12:51 abi-2.6.24-16-generic
-rw-r--r--  1 root root  507665 2008-11-20 18:46 abi-2.6.27-9-generic
-rw-r--r--  1 root root   79964 2008-04-10 12:51 config-2.6.24-16-generic
-rw-r--r--  1 root root   91364 2008-11-20 18:46 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2008-12-07 10:31 grub
-rw-r--r--  1 root root 7831567 2008-12-06 13:40 initrd.img-2.6.24-16-generic
-rw-r--r--  1 root root 7349268 2008-04-22 14:00 initrd.img-2.6.24-16-generic.bak
-rw-r--r--  1 root root 8104103 2008-12-07 10:32 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 16:11 memtest86+.bin
-rw-r--r--  1 root root  899892 2008-04-10 12:51 System.map-2.6.24-16-generic
-rw-r--r--  1 root root 1029585 2008-11-20 18:46 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1073 2008-11-20 18:48 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 1904248 2008-04-10 12:51 vmlinuz-2.6.24-16-generic
-rw-r--r--  1 root root 2244304 2008-11-20 18:46 vmlinuz-2.6.27-9-generic

sda1/boot/grub

total 212
drwxr-xr-x 2 root root   4096 2008-12-07 10:31 .
drwxr-xr-x 3 root root   4096 2008-12-07 10:32 ..
-rw-r--r-- 1 root root    197 2008-12-06 13:40 default
-rw-r--r-- 1 root root     15 2008-12-06 13:40 device.map
-rw-r--r-- 1 root root   8056 2008-12-06 13:40 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2008-12-06 13:40 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-06 13:40 installed-version
-rw-r--r-- 1 root root   8608 2008-12-06 13:40 jfs_stage1_5
-rw-r--r-- 1 root root   4935 2008-12-07 10:31 menu.lst
-rw-r--r-- 1 root root   4914 2008-12-07 10:31 menu.lst~
-rw-r--r-- 1 root root   7324 2008-12-06 13:40 minix_stage1_5
-rw-r--r-- 1 root root   9632 2008-12-06 13:40 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-06 13:40 stage1
-rw-r--r-- 1 root root 108356 2008-12-06 13:40 stage2
-rw-r--r-- 1 root root   9276 2008-12-06 13:40 xfs_stage1_5

sda5/boot.ini

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


StdErr Messages 

ls: cannot access /dev/hd?: No such file or directory
ls: cannot access /dev/hd??*: No such file or directory
/dev/sda2 looks like swapspace - not mounted
mount: you must specify the filesystem type
umount: sda2: not mounted
mount: you must specify the filesystem type
/dev/sda3: unknown volume type
umount: sda3: not mounted
```

---

### Post by caljohnsmith on 2008-12-15
Something isn't quite right, because fdisk lists sda5 is type "83" which is a linux file system, and yet "vol_id" reported it as NTFS. How about doing the following:
```
sudo fdisk -l
sudo sfdisk -c /dev/sda 5 7
sudo fdisk -l
sudo mount /dev/sda5 /mnt
ls -l /mnt
```
And please post the output of all the above commands.

---

### Post by nerdpride on 2008-12-15
Here you go:
```
pete@pete-linux:~$ sudo fdisk -l
[sudo] password for pete: 

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd8c3d8c3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5932    47648758+  83  Linux
/dev/sda2           11919       12161     1951897+  82  Linux swap / Solaris
/dev/sda3            5933       11914    48050415    5  Extended
/dev/sda5            5933       11914    48050383+  83  Linux

Partition table entries are not in disk order
pete@pete-linux:~$ sudo sfdisk -c /dev/sda 5 7
Done

pete@pete-linux:~$ sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd8c3d8c3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5932    47648758+  83  Linux
/dev/sda2           11919       12161     1951897+  82  Linux swap / Solaris
/dev/sda3            5933       11914    48050415    5  Extended
/dev/sda5            5933       11914    48050383+   7  HPFS/NTFS

Partition table entries are not in disk order
pete@pete-linux:~$ sudo mount /dev/sda5 /mnt
pete@pete-linux:~$ ls -l /mnt
total 2095485
drwxrwxrwx 1 root root       4096 2008-08-01 15:40 AtherosMB51.temp
drwxrwxrwx 1 root root       4096 2008-08-04 16:13 Audio.temp
-rwxrwxrwx 1 root root          0 2008-07-31 21:33 AUTOEXEC.BAT
-rwxrwxrwx 1 root root        211 2008-07-31 21:27 boot.ini
-rwxrwxrwx 1 root root          0 2008-07-31 21:33 CONFIG.SYS
drwxrwxrwx 1 root root       4096 2008-08-23 11:11 Dev-Cpp
drwxrwxrwx 1 root root       4096 2008-11-26 23:55 Display.temp
drwxrwxrwx 1 root root       4096 2008-08-01 15:37 Documents and Settings
-rwxrwxrwx 1 root root          0 2008-07-31 21:33 IO.SYS
-rwxrwxrwx 1 root root          0 2008-07-31 21:33 MSDOS.SYS
-rwxrwxrwx 1 root root      47564 2006-02-28 07:00 NTDETECT.COM
-rwxrwxrwx 1 root root     250032 2006-02-28 07:00 ntldr
-rwxrwxrwx 1 root root 2145386496 2008-12-02 12:51 pagefile.sys
drwxrwxrwx 1 root root      24576 2008-11-27 22:31 Program Files
drwxrwxrwx 1 root root          0 2008-07-31 22:45 RECYCLER
drwxrwxrwx 1 root root       4096 2008-07-31 21:36 System Volume Information
drwxrwxrwx 1 root root          0 2008-10-30 21:18 temp
drwxrwxrwx 1 root root       8192 2008-11-27 22:30 TouchPad.temp
drwxrwxrwx 1 root root          0 2008-11-26 23:54 tpadenable.temp
drwxrwxrwx 1 root root      28672 2008-11-29 00:14 WINDOWS
pete@pete-linux:~$ 

```

---

### Post by caljohnsmith on 2008-12-16
OK, that's great, it looks so far like your XP sda5 partition is fine; probably what happened when you copied XP into sda5 is that partimage didn't change the file system byte in the partition table to 0x07 or NTFS, and instead left it as 0x83 or Linux. But now that problem is fixed, so the next steps would be:
```
sudo mount /dev/sda5 /mnt
gksudo gedit /mnt/boot.ini
```
Then change your boot.ini file to use "partition(3)":
```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)[COLOR="Blue"]partition(3)[/COLOR]\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)[COLOR="Blue"]partition(3)[/COLOR]\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

```
Save, and next please post the output of:
```
sudo hexdump -s 28 -n 4 -e '"%d\n"' /dev/sda5
```
And lastly, you'll need to change your menu.lst to boot Windows correctly:
```
gksudo gedit /boot/grub/menu.lst
```
And change your current Windows entry at the bottom of the file to:
```
title		Microsoft Windows XP Home Edition
rootnoverify    (hd0,4)
chainloader	+1
```
Then reboot, try Windows XP from the Grub menu, and let me know exactly what happens. It might be that you will have to repair the Windows boot sector, but first let me know how far you get when booting Windows so we will know if that is necessary.

---

### Post by nerdpride on 2008-12-17
Okay i am about to try to boot. Here is the input and output of what you posted (including stupid mistakes).

```
pete@pete-linux:~$ sudo mount dev/sda5 /mnt
[sudo] password for pete: 
mount: special device dev/sda5 does not exist
pete@pete-linux:~$ sudo mount /dev/sda5 /mnt
pete@pete-linux:~$ gksudo gedit /mnt/boot.ini
pete@pete-linux:~$ sudo hexdump -s -28 -n 4 -e '"%d/n"' /dev/sda5
hexdump: -28: bad skip value
pete@pete-linux:~$ sudo hexdump -s 28 -n 4 -e '"%d/n"' /dev/sda5
63/npete@pete-linux:~$ gksudo gedit /boot/grub/menu.lst

```

---

### Post by nerdpride on 2008-12-17
I tried to boot. All it did was say:

Starting Up...

_


for a good 3 1/2 minutes at which point i assumed there was an error and forced a shutdown.

---

### Post by caljohnsmith on 2008-12-17
OK, according to that hexdump output, the embedded sector info in your XP boot sector shows the XP partition starts at sector 63, when really your XP partition starts at sector 95297643. Fortunately "testdisk" can usually fix that problem, so to use testdisk, first make sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "no log", choose the correct HDD and "proceed", choose "intel", choose "advanced", select the Windows sda5 partition, choose "boot", then choose "Rebuild BS"; if testdisk gives you a warning that the "sectors are not identical", then choose "write". After you are done doing the "rebuild BS" in testdisk, reboot and let me know exactly what happens when you try to boot Windows from Grub.

---

### Post by nerdpride on 2008-12-17
That worked great great. Thanks. Speaking of thanks here is you 1,082nd.

---

### Post by caljohnsmith on 2008-12-17
Glad that did the trick; cheers and have fun with Windows and Ubuntu. :)

---

