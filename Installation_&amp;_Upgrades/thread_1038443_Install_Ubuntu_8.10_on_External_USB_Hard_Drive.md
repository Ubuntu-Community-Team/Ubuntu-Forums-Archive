---
title: "Install Ubuntu 8.10 on External USB Hard Drive"
date: 2009-01-12
forum: Installation &amp; Upgrades
---

### Post by russet_wolf on 2009-01-12
Hello, I'm completely new to Ubuntu and Linux all together, but I was browsing around and saw a few old threads on installing Ubuntu to an external USB Hard Drive. Upon trying, all looked smooth, but on restart I got no GRUB loader and went straight to Windows. Looking into my G: drive, it was empty. I tried again, installing "inside Windows" this time, and upon restart was directed straight to Windows again. I checked the drive and there were files present, but none of the files were useable, except the uninstall.

Some help please? My external drive is a WD MyPassport Essential, but I reformatted it so it has no data on it. I'm using a Ubuntu 8.10 disk, I don't know if it's a "live" disk or something else; in fact I don't even know what that term means. Any help would be much appreciated. =D

---

### Post by briandu on 2009-01-12
Ok a live CD will boot up on the CD only - however ur BIOS must be set to boot from the CD not the HD.

When booting from CD u will have and enviro to play in - no damage to ur existing system.

Look in enviro there is an install option. Use that and target ur external drive.

It will sort out the GRUB for u but you may find u cannot find Windows if u remove the ext HD so then you need to reinstall grub on the boot sector.

however do the first part first then come back.

Cheers

---

### Post by russet_wolf on 2009-01-12
I don't seem to be able to "target" anything. The installer just goes automatically to my internal drive (if I have nothing plugged in) or to my external drive if it is plugged in. I really have no choice on the matter. The first time I went through, I followed the same procedure and it did not work. However, I had formatted my internal hard drive in Windows and this time I formatted it in the demo on the live CD. Hopefully it will work. It's at 88% right now...

---

### Post by Pumalite on 2009-01-12
For your perusal:
[http://ubuntuforums.org/showthread.php?t=789528&highlight=Herman](http://ubuntuforums.org/showthread.php?t=789528&highlight=Herman)

---

### Post by russet_wolf on 2009-01-12
Okay, it seems to be working from the external hard drive, but when i unplug it, just as you said, it tries to boot the Grub loader and says "Error 21". I would like to be able to use my computer (Windows) without having the external drive plugged in, and to be able to boot Ubuntu from my external drive (with all my files, etc.) on other computers without installing anything on the nes host computer. Any suggestions?

---

### Post by Pumalite on 2009-01-12
Read the link I gave you. All the instructions are there.

---

### Post by caljohnsmith on 2009-01-12
Hi russet_wolf, In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by russet_wolf on 2009-01-13
Alrighty, here's my boot script:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  Geometry: 240 Heads and 63 sectors per Track. No 
                       errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks 
                       /ubuntu/disks/boot/ /ubuntu/disks/boot/grub 
                       /ubuntu/disks/boot/grub

sdb1: _________________________________________________________________________

    File system:       ext2
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
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdb6: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x01e801e7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   156280319    78140128+   7  HPFS/NTFS

sfdisk -V /dev/sda:

partition 1: end: (c,h,s) expected (1023,254,63) found (1023,239,63)
/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63     7791524     3895731   83  Linux
/dev/sdb2         7791525   488392064   240300270    5  Extended
/dev/sdb5         7791588   482721119   237464766   83  Linux
/dev/sdb6       482721183   488392064     2835441   82  Linux swap / Solaris

sfdisk -V /dev/sdb:

Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
/dev/sdb: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="7E9C747A9C742EB1" TYPE="ntfs" 
/dev/sdb1: LABEL="Swift" UUID="d46a55b1-2a5f-4534-8614-4eef61de3000" TYPE="ext2" 
/dev/sdb5: UUID="94349197-f891-421b-878e-5f734c25d63e" TYPE="ext3" 
/dev/sdb6: UUID="ee38e34a-89c9-48cc-8bbb-78b3d9b442b5" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sdb5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/russet/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=russet)
/dev/sdb1 on /media/Swift type ext2 (rw,nosuid,nodev,uhelper=hal)
/dev/sda1 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

================================ sda1/boot.ini: ================================

[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

c:\wubildr.mbr="Ubuntu"


============================== sda1/ubuntu/disks: ==============================

total 4
drwxrwxrwx 1 root root    0 2009-01-12 22:02 .
drwxrwxrwx 1 root root 4096 2009-01-12 22:02 ..
drwxrwxrwx 1 root root    0 2009-01-12 22:02 boot
drwxrwxrwx 1 root root    0 2009-01-12 22:02 shared

=========================== sda1/ubuntu/disks/boot/: ===========================

total 0
drwxrwxrwx 1 root root 0 2009-01-12 22:02 .
drwxrwxrwx 1 root root 0 2009-01-12 22:02 ..
drwxrwxrwx 1 root root 0 2009-01-12 22:02 grub

========================= sda1/ubuntu/disks/boot/grub: =========================

total 0
drwxrwxrwx 1 root root 0 2009-01-12 22:02 .
drwxrwxrwx 1 root root 0 2009-01-12 22:02 ..

========================= sda1/ubuntu/disks/boot/grub: =========================

total 0
drwxrwxrwx 1 root root 0 2009-01-12 22:02 .
drwxrwxrwx 1 root root 0 2009-01-12 22:02 ..

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
# kopt=root=UUID=94349197-f891-421b-878e-5f734c25d63e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=94349197-f891-421b-878e-5f734c25d63e

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
uuid		94349197-f891-421b-878e-5f734c25d63e
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=94349197-f891-421b-878e-5f734c25d63e ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		94349197-f891-421b-878e-5f734c25d63e
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=94349197-f891-421b-878e-5f734c25d63e ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		94349197-f891-421b-878e-5f734c25d63e
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=94349197-f891-421b-878e-5f734c25d63e ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		94349197-f891-421b-878e-5f734c25d63e
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=94349197-f891-421b-878e-5f734c25d63e ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		94349197-f891-421b-878e-5f734c25d63e
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb5
UUID=94349197-f891-421b-878e-5f734c25d63e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb6
UUID=ee38e34a-89c9-48cc-8bbb-78b3d9b442b5 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sdb5/boot: ==================================

total 23764
drwxr-xr-x  3 root root    4096 2009-01-13 20:17 .
drwxr-xr-x 20 root root    4096 2009-01-13 20:15 ..
-rw-r--r--  1 root root  507665 2008-11-04 16:00 abi-2.6.27-7-generic
-rw-r--r--  1 root root  507665 2008-11-20 18:46 abi-2.6.27-9-generic
-rw-r--r--  1 root root   91364 2008-11-04 16:00 config-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-11-20 18:46 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2009-01-13 20:15 grub
-rw-r--r--  1 root root 8180822 2009-01-13 20:15 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8180619 2009-01-13 20:17 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 16:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-11-04 16:00 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1029585 2008-11-20 18:46 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1073 2008-11-04 16:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-11-20 18:48 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2244464 2008-11-04 16:00 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2244304 2008-11-20 18:46 vmlinuz-2.6.27-9-generic

=============================== sdb5/boot/grub: ===============================

total 224
drwxr-xr-x 2 root root   4096 2009-01-13 20:15 .
drwxr-xr-x 3 root root   4096 2009-01-13 20:17 ..
-rw-r--r-- 1 root root    197 2009-01-12 20:14 default
-rw-r--r-- 1 root root     30 2009-01-12 20:14 device.map
-rw-r--r-- 1 root root   8108 2009-01-12 20:14 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-01-12 20:14 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-01-12 20:14 installed-version
-rw-r--r-- 1 root root   8712 2009-01-12 20:14 jfs_stage1_5
-rw-r--r-- 1 root root   5103 2009-01-13 20:15 menu.lst
-rw-r--r-- 1 root root   5019 2009-01-13 20:15 menu.lst~
-rw-r--r-- 1 root root   7352 2009-01-12 20:14 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-01-12 20:14 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-12 20:14 stage1
-rw-r--r-- 1 root root 121460 2009-01-12 20:14 stage2
-rw-r--r-- 1 root root   9556 2009-01-12 20:14 xfs_stage1_5

=============================== StdErr Messages: ===============================

No errors were reported.
```

---

### Post by caljohnsmith on 2009-01-13
Can you set your BIOS to boot the 250 GB Ubuntu drive? If so, how about following these steps from your Live CD (the Ubuntu install CD):
```
sudo apt-get install lilo
sudo lilo -M  /dev/sda mbr
```
That will restore a Windows MBR to your Windows drive so that you can boot straight into Windows when you boot the Windows drive. Next, to install Grub to your Ubuntu drive, try:
```
sudo grub
grub> root (hd1,0)
grub> makeactive
grub> root (hd1,4)
grub> setup (hd1)
grub> quit

```
Next, how about we modify your Grub's menu.lst so you can boot Windows from your Ubuntu drive if you want to:
```
sudo mount /dev/sdb5 /mnt
gksudo gedit /mnt/boot/grub/menu.lst
```
And change the Windows entry at the bottom to:
```
title       Windows XP 
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
And lastly, it doesn't look like you have your Ubuntu Wubi install any more (the Ubuntu install inside of Windows), so it would be good to remove the Ubuntu entry from your Windows boot loader:
```
sudo umount /mnt
sudo mount /dev/sda1 /mnt
gksudo gedit /mnt/boot.ini
```
And delete the last line in your boot.ini file as highlighted in red below:
```
[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
[COLOR="Red"]c:\wubildr.mbr="Ubuntu"[/COLOR]
```
And finally, reboot, set your BIOS to boot the Ubuntu drive, and you should be able to boot either Ubuntu or Windows from the Grub menu if all goes well. Also, if you disconnect the Ubuntu drive, you should be able to boot straight into Windows. Let me know how it goes or if you run into problems. :)

---

### Post by russet_wolf on 2009-01-15
Alright, I tried following your instructions from the Live CD, but I could only get through the first two lines. I ended up reinstalling Ubuntu, and from my external drive carried out your instructions. It looks like it all worked, except that I can't seem to set my BIOS to boot from  the external drive. The three USB options I have are USB-FDD, USB-CDROM, and USB-ZIP. I have tried setting it to each in turn, but none seem to work. Is there anything I can do?

---

### Post by caljohnsmith on 2009-01-15
How about running the Boot Info Script again as per post #7 so I can get an idea of what your new setup is.

---

### Post by russet_wolf on 2009-01-16
Actually, I found an [All-in-one boot floppy]("http://rescup.winbuilder.net/bootdisk/") that lets me boot from my external hard drive. Whenever I want to boot from a computer that won't boot from USB automatically, like my desktop, all I have to do is insert that and choose (hd1).

Thank you though for all your help, I would be lost without it!!

---

### Post by caljohnsmith on 2009-01-17
Glad to hear you found a successful workaround; cheers and enjoy your new Ubuntu install. :)

---

### Post by russet_wolf on 2009-01-17
Thanks, I'm loving it already!

---

