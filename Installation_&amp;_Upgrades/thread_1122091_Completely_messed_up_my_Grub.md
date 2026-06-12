---
title: "Completely messed up my Grub"
date: 2009-04-10
forum: Installation &amp; Upgrades
---

### Post by Mr dirt on 2009-04-10
I wanted to take some of the options out from Grub and ended up erasing something important. It gives me an error 11, and wont give me the option to boot into Ubuntu (Jaunty).> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x40df40de

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7649    61440561    7  HPFS/NTFS
/dev/sda2            7650        9729    16707600    5  Extended
/dev/sda5            7650        9729    16707568+  83  Linux

Disk /dev/sdc: 1031 MB, 1031798784 bytes
255 heads, 63 sectors/track, 125 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9a36bbaa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         125     1004031    b  W95 FAT32
ubuntu@ubuntu:~$ 





I also tried this from the live cd...

> This will restore grub if you already had grub installed but lost it to a windows install or some other occurence that erased/changed your MBR so that grub no longer appears at start up or it returns an error.

(This how to is written for Ubuntu but should work on other systems. The only thing to take note of, when you see "sudo" that will mean to you that the following command should be entered at a root terminal.)

Boot into the live Ubuntu cd. This can be the live installer cd or the older live session Ubuntu cds.

When you get to the desktop open a terminal and enter. (I am going to give you the commands and then I will explain them later)

Code:

sudo grub

This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands

Code:

find /boot/grub/stage1

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)

Code:

root (hd?,?)

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

Code:

setup (hd0)

Finally exit the grub shell
Code:

quit



There is nothing in the notepad in the menu lst page...

---

### Post by ivanvajar on 2009-04-10
There can't be anything since it's not menu.lst you need to boot from HDD. Did you type correct option in ***root (hd?,?)***? You need to enter values returned by ***find /boot/grub/stage1***.

---

### Post by Herman on 2009-04-10
> There is nothing in the notepad in the menu lst page... :) It's a common beginner's mistake to try to open the menu.lst in the live CD instead of in the hard disk partition. The live CD doesn't have a menu.lst file, so what you are probably actually doing is creating a new (empty) file and calling it 'menu.lst'.  :)

You are not the first and you won't be the last. 
The reason I know is because I tried it myself when I was new around here.

What you need to do is 'mount' your hard disk installed Ubuntu file system (in the partition), and then access the file through the 'mount point', (through the live CD's /media directory).

Here's a link that explains what I mean, 
[Rescue your Linux system with a Live CD]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD")[COLOR=#666666][COLOR=#000000] - includes commands for opening vital files.

Regards, Herman :)
[/COLOR][/COLOR]

---

### Post by lolol i r linux noob on 2009-04-10
I recked my grub so the delay was 0 so it loaded the default option straight away. my default was windows so a had to use the live cd to change it back.
Did you not make a backup of the menu.lst when u first edited it. if you did use ur live cd to restore the backup.

---

### Post by Mr dirt on 2009-04-10
I didnt make a backup and I really dont know how to edit the grub from within the live cd

---

### Post by Mr dirt on 2009-04-10
Ok I think I can edit the grub but I dont know what Ubuntu info I should put...cause I didnt back it up, how can I getthis resolved.

---

### Post by lolol i r linux noob on 2009-04-10
As my name suggest a dont no much about linux so i cant offer any further help.

---

### Post by Mr dirt on 2009-04-10
This is my sudo grub stuff so you guys can tell me what to write for lrst menu which I think I can edit without re>        [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> 

grub> find /boot/grub/stage1
 (hd0,4)

grub> root (hd0,4)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,4)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

grub> 

installing grub



this is my lrst menu contents > # menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=7d48d302-f0d0-4700-98a0-e967d414df40 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7d48d302-f0d0-4700-98a0-e967d414df40

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

title		Ubuntu


### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


As you can see I erased pretty much everything...lol

---

### Post by Mr dirt on 2009-04-10
I found a sample online and took a shot at it and while it changed grub (at least I can access it (thanks Herman) it said error 15 cant find file...> title Ubuntu, kernel 2.6.17-10-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root (hd0,4)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro single
initrd /boot/initrd.img-2.6.17-10-generic
boot

title Ubuntu, memtest86+
root (hd0,4)
kernel /boot/memtest86+.bin
quiet
boot


### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows vvXP
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


I just need to know what to write for root and kernal...

---

### Post by Mr dirt on 2009-04-10
I tried again and got error 17, if someone can help me get my grub info, I could enter it real quick.

---

### Post by Mr dirt on 2009-04-10
This is what gave me an errror 17 > 
## ## End Default Options ##
title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/sda5 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/sda5 ro single
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd0,1)
kernel		/boot/memtest86+.bin  
savedefault
boot
title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd0,1)
kernel		/boot/memtest86+.bin  
savedefault
boot

title Ubuntu, kernel 2.6.17-10-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro single
initrd /boot/initrd.img-2.6.17-10-generic
boot

title Ubuntu, memtest86+

somebody has to know how I can get my original grub info ,ie what I should type into terminal to find out which hd?sda? my ubuntu is on...

---

### Post by unutbu on 2009-04-10
When you boot from the LiveCD, do you have an internet connection? If so, please follow these instructions to run boot_info_script:
[http://ubuntuforums.org/showpost.php?p=6725571&postcount=3](http://ubuntuforums.org/showpost.php?p=6725571&postcount=3)

If not, boot from the LiveCD, open a terminal, and type
```

sudo mount /dev/sda5 /mnt
ls -l /mnt/boot
```
Then post the output from the above commands.

---

### Post by Mr dirt on 2009-04-10
> ============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu jaunty (development 
                       branch)
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x40df40de

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   122,881,184   122,881,122   7 HPFS/NTFS
/dev/sda2         122,881,185   156,296,384    33,415,200   5 Extended
/dev/sda5         122,881,248   156,296,384    33,415,137  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1031 MB, 1031798784 bytes
255 heads, 63 sectors/track, 125 cylinders, total 2015232 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9a36bbaa

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63     2,008,124     2,008,062   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="92B4AAB6B4AA9BEB" TYPE="ntfs" 
/dev/sda5: UUID="7d48d302-f0d0-4700-98a0-e967d414df40" TYPE="ext4" 
/dev/ramzswap0: TYPE="swap" 
/dev/sdc1: LABEL="JIMMY" UUID="ECEE-2D9D" TYPE="vfat" 

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
/dev/sdc1 on /media/JIMMY type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)
/dev/sda5 on /media/disk type ext4 (rw,nosuid,nodev,uhelper=hal)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


=========================== sda5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=7d48d302-f0d0-4700-98a0-e967d414df40 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7d48d302-f0d0-4700-98a0-e967d414df40

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
title		Ubuntu

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=7d48d302-f0d0-4700-98a0-e967d414df40 /               ext4    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  66.0GB: boot/grub/menu.lst
  64.6GB: boot/grub/stage2
  65.9GB: boot/initrd.img-2.6.28-11-generic
  65.5GB: boot/vmlinuz-2.6.28-11-generic
  65.9GB: initrd.img
  65.5GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb 


here are the results

---

### Post by Mr dirt on 2009-04-10
More results> ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~$ ls -l /mnt/boot
total 12964
-rw-r--r-- 1 root root  529118 2009-04-08 06:46 abi-2.6.28-11-generic
-rw-r--r-- 1 root root   96795 2009-04-08 06:46 config-2.6.28-11-generic
drwxr-xr-x 2 root root    4096 2009-04-10 22:48 grub
-rw-r--r-- 1 root root 7541045 2009-04-10 16:37 initrd.img-2.6.28-11-generic
-rw-r--r-- 1 root root  128796 2009-03-27 17:15 memtest86+.bin
-rw-r--r-- 1 root root 1456232 2009-04-08 06:46 System.map-2.6.28-11-generic
-rw-r--r-- 1 root root    1074 2009-04-08 06:48 vmcoreinfo-2.6.28-11-generic
-rw-r--r-- 1 root root 3501744 2009-04-08 06:46 vmlinuz-2.6.28-11-generic
ubuntu@ubuntu:~$ 





---

### Post by unutbu on 2009-04-10
Boot the LiveCD. Open a terminal. Type
```

sudo mount /dev/sda5 /mnt
gksu gedit /mnt/boot/grub/menu.lst
```

About 80% of the way down, change

```
## ## End Default Options ##
title Ubuntu
```

to

```
## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		7d48d302-f0d0-4700-98a0-e967d414df40
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7d48d302-f0d0-4700-98a0-e967d414df40 ro quiet 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		7d48d302-f0d0-4700-98a0-e967d414df40
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7d48d302-f0d0-4700-98a0-e967d414df40 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

```

Save and exit gedit.
Reboot and see if you can boot Jaunty.

---

### Post by Mr dirt on 2009-04-10
Thanks alot man but now I have a new problem the dam menu lst wont let me save to it, In the begining it did now it wont let me save to it.


Could not save the file /media/disk/boot/grub/menu.lst.


You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.


Maybe I was playing with it too much...lol

---

### Post by unutbu on 2009-04-10
Be sure you type these commands:
```

sudo mount /dev/sda5 /mnt
gksu gedit /mnt/boot/grub/menu.lst

```
This mounts your Linux partition at /mnt, not /media.

---

### Post by Mr dirt on 2009-04-10
It worked, your the man, thanks for everything dude.

---

### Post by Catiline on 2009-04-11
Thanks! this fixed by lost GRUB like a charm!

---

