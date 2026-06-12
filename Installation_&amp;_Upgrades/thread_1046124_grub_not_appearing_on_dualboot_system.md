---
title: "grub not appearing on dualboot system"
date: 2009-01-21
forum: Installation &amp; Upgrades
---

### Post by AvvY on 2009-01-21
I'm doing a fresh dualboot of winxp with ubuntu. I installed XP first, then created several partitions for my Ubuntu install

/ (logical)
/home (logical)
a shared fat32 partition (extended)
and a swap space (extended)

When I start the computer Grub isn't loading and so the computer is defaulting to Winxp.

I loaded up the live CD and ran the relevant commands to reinstall Grub to hd0 but after two attempts it still wont work.

Thanx for your help

---

### Post by caljohnsmith on 2009-01-21
Do you have more than one HDD? If so, that would probably explain your situation. In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your booting problem might be.

---

### Post by AvvY on 2009-01-21
Yes I do have multiple drives in this system. Here is the output requested:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #3 in 
    partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on boot drive #3 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd
 => Windows is installed in the MBR of /dev/sde

sda1: _________________________________________________________________________

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

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdc3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc4: _________________________________________________________________________

    File system:       Extended Partition

sdc5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc6: _________________________________________________________________________

    File system:       swap

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x05de05dd

/dev/sda1     *           63  390,716,864  390,716,802   7 HPFS/NTFS

Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7b747b74

/dev/sdb1     *           63  390,716,864  390,716,802   7 HPFS/NTFS

Drive sdc: _____________________________________________________________________

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x70407040

/dev/sdc1     *           63   10,233,404   10,233,342   7 HPFS/NTFS
/dev/sdc2         10,233,405   49,303,484   39,070,080  83 Linux
/dev/sdc3         49,303,485   98,125,019   48,821,535  83 Linux
/dev/sdc4         98,125,020  156,296,384   58,171,365   5 Extended
/dev/sdc5         98,125,083  117,660,059   19,534,977   b W95 FAT32
/dev/sdc6        117,660,123  156,296,384   38,636,262  82 Linux swap / Solaris

Drive sdd: _____________________________________________________________________

Disk /dev/sdd: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xadc5adc5

/dev/sdd1                 63  234,436,544  234,436,482   7 HPFS/NTFS

Drive sde: _____________________________________________________________________

Disk /dev/sde: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0abf66ef

/dev/sde1                 63  488,392,064  488,392,002   7 HPFS/NTFS

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="825834E15834D59F" LABEL="Data 2" TYPE="ntfs" 
/dev/sdb1: UUID="94B4E17BB4E1606A" LABEL="Data 1" TYPE="ntfs" 
/dev/sdc1: UUID="D0E4E6DCE4E6C436" TYPE="ntfs" 
/dev/sdc2: UUID="1815ac7f-80de-40ca-b9f9-ffd1e12f8770" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc3: UUID="eceec5f7-31ea-4900-b5d5-a9f67e2f068b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc5: UUID="377F-7FCF" TYPE="vfat" 
/dev/sdc6: UUID="b7c6bfed-ffc9-4e21-b500-18cbb9be586e" TYPE="swap" 
/dev/sdd1: UUID="988CAFDD8CAFB3E2" LABEL="Backup pre rebuild" TYPE="ntfs" 
/dev/sde1: UUID="B236921F3691E49F" LABEL="Media 1" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

================================ sdc1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sdc2/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=1815ac7f-80de-40ca-b9f9-ffd1e12f8770 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,1)

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
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=1815ac7f-80de-40ca-b9f9-ffd1e12f8770 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=1815ac7f-80de-40ca-b9f9-ffd1e12f8770 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd2,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1


=============================== sdc2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc2
UUID=1815ac7f-80de-40ca-b9f9-ffd1e12f8770 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc3
UUID=eceec5f7-31ea-4900-b5d5-a9f67e2f068b /home           ext3    relatime        0       2
# /dev/sdc6
UUID=b7c6bfed-ffc9-4e21-b500-18cbb9be586e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sdc2/boot: ==================================

total 11092
drwxr-xr-x  3 root root    4096 2009-01-21 20:31 .
drwxr-xr-x 21 root root    4096 2009-01-21 20:31 ..
-rw-r--r--  1 root root  422667 2008-06-18 18:11 abi-2.6.24-19-generic
-rw-r--r--  1 root root   80049 2008-06-18 18:11 config-2.6.24-19-generic
drwxr-xr-x  2 root root    4096 2009-01-21 20:31 grub
-rw-r--r--  1 root root 7872420 2009-01-21 20:31 initrd.img-2.6.24-19-generic
-rw-r--r--  1 root root  103204 2007-09-28 10:06 memtest86+.bin
-rw-r--r--  1 root root  905146 2008-06-18 18:11 System.map-2.6.24-19-generic
-rw-r--r--  1 root root 1920472 2008-06-18 18:11 vmlinuz-2.6.24-19-generic

=============================== sdc2/boot/grub: ===============================

total 204
drwxr-xr-x 2 root root   4096 2009-01-21 20:31 .
drwxr-xr-x 3 root root   4096 2009-01-21 20:31 ..
-rw-r--r-- 1 root root    197 2009-01-21 20:31 default
-rw-r--r-- 1 root root     75 2009-01-21 20:31 device.map
-rw-r--r-- 1 root root   8056 2009-01-21 20:31 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2009-01-21 20:31 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-01-21 20:31 installed-version
-rw-r--r-- 1 root root   8608 2009-01-21 20:31 jfs_stage1_5
-rw-r--r-- 1 root root   4616 2009-01-21 20:31 menu.lst
-rw-r--r-- 1 root root   7324 2009-01-21 20:31 minix_stage1_5
-rw-r--r-- 1 root root   9632 2009-01-21 20:31 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-21 20:31 stage1
-rw-r--r-- 1 root root 108356 2009-01-21 20:31 stage2
-rw-r--r-- 1 root root   9276 2009-01-21 20:31 xfs_stage1_5

=================== sdc2: Location  of files loaded by Grub: ===================


   9.0GB: boot/grub/menu.lst
   9.0GB: boot/grub/stage2
   8.7GB: boot/initrd.img-2.6.24-19-generic
   8.8GB: boot/vmlinuz-2.6.24-19-generic
   8.7GB: initrd.img
   8.8GB: vmlinuz

=========================== Unknown MBRs or Boot Sectors =======================

Unknown BootLoader  on sdc5

00000000  eb 58 90 4d 53 57 49 4e  34 2e 31 00 02 10 20 00  |.X.MSWIN4.1... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 1b 45 d9 05  |........?....E..|
00000020  81 14 2a 01 3e 25 00 00  00 00 00 00 02 00 00 00  |..*.>%..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 cf 7f 7f 37 4e  4f 20 4e 41 4d 45 20 20  |..)...7NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 0e 1f be 74 7e ac  |  FAT32   ...t~.|
00000060  22 c0 74 06 b4 0e cd 10  eb f5 b4 00 cd 16 b4 00  |".t.............|
00000070  cd 19 eb fe 54 68 69 73  20 70 61 72 74 69 74 69  |....This partiti|
00000080  6f 6e 20 64 6f 65 73 20  6e 6f 74 20 68 61 76 65  |on does not have|
00000090  20 61 6e 20 6f 70 65 72  61 74 69 6e 67 20 73 79  | an operating sy|
000000a0  73 74 65 6d 20 6c 6f 61  64 65 72 20 69 6e 73 74  |stem loader inst|
000000b0  61 6c 6c 65 64 20 6f 6e  20 69 74 2e 0a 0d 50 72  |alled on it...Pr|
000000c0  65 73 73 20 61 20 6b 65  79 20 74 6f 20 72 65 62  |ess a key to reb|
000000d0  6f 6f 74 2e 2e 2e 00 66  61 74 00 00 00 00 00 00  |oot....fat......|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

No errors were reported.
```

The drive I am using that has Win/Lin installed is /dev/sdc where sdc1 is Windows and sdc2 is Ubuntu.

Thanx for your help!

---

### Post by caljohnsmith on 2009-01-21
OK, it looks like what happened is when you installed Grub, the default is that Grub gets installed to the MBR (Master Boot Record) of the sda drive, because usually that is the drive most people boot on start up. In your case though, you are obviously booting the sdc Windows/Ubuntu drive since you said you are still booting straight into Windows. To fix the problem, how about doing:
```
sudo grub
grub> root (hd2,1)
grub> setup (hd2)
grub> quit
```
Next you'll need to modify your Grub's menu.lst:
```
sudo mount /dev/sdc2 /mnt
gksudo gedit /mnt/boot/grub/menu.lst 
```
And change all the Ubuntu entries to use (hd0,1) instead of (hd2,1), similar to:
```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		[COLOR="Blue"](hd0,1)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=1815ac7f-80de-40ca-b9f9-ffd1e12f8770 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
```
Also change the "# groot" line to use (hd0,1):
```
# groot=[COLOR="Blue"](hd0,1)
[/COLOR]
```
Next change your Windows entry to:
```
title		Microsoft Windows XP Professional
root		(hd0,0)
chainloader	+1
```
Save, reboot, and if all goes well you should be able to boot into Ubuntu or Windows. Let me know how it goes or if you run into problems.

---

### Post by AvvY on 2009-01-21
Thank you! Everything worked perfectly. I changed all the lines as suggested and now grub loads, and now I'm finally into Ubuntu (updating everything as we speak).

Thank you so much for your assistance!

---

### Post by caljohnsmith on 2009-01-21
Glad that worked OK; cheer and have fun with Windows and Ubuntu. :)

---

