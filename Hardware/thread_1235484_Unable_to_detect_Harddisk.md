---
title: "Unable to detect Harddisk"
date: 2009-08-09
forum: Hardware
---

### Post by jadhav333 on 2009-08-09
Till Yesterday.. I had my system properly installed and fully working.. I did a normal shutdown.. 

Today I am unable to detect the boot hard disk :O

I have 2 harddisks.. 
Boot Hardisk is 500Gb Seagate IDE
Other Harddisk is 1TB Seagate  Sata

The Bios shows presence of both harddisks..  
But Ubuntu is unable to boot.. 
  [COLOR="Blue"] ** EDIT **[/COLOR]
The bios doesnot correctly show the hard disk.. [COLOR="Red"]Earlier its name was ST3500.... Now it is incorrectly shown as SV3702630c.[/COLOR]

Does it mean that somehow the HD controller/soemthing else has got corrupted.. **How can I recover this Harddisk**
  [COLOR="Blue"] ** Edit **[/COLOR]

The System rescue CD / Ubuntu live CD does not detect the boot hard disk.. 

I have tried removing and reconnecting the data/power cable connections as well.. 

It should probably not be a motherboard/IDE port issue as the DVDrom connected to the same data cable functions fine.. 
[B]
Assistance needed![/B]

---

### Post by IcarusR on 2009-08-09
Have you tried putting the drive in another machine & see if it will then boot from it ??

---

### Post by jadhav333 on 2009-08-10
I have only one machine.. :(
[B]
anyways new updates..[/B]

The hard disk got detected after rechecking cables & rebooting the m/c a couple of times..

The data is still secure and accessible from ubuntu live cd.. 
But the system doesnot boot.. 

I tried updating the grub using this ([http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)) method.. the method was successful.. although.. **on reboot it only displays the text 'grub' and a flashing  cursor.. **

I tried reinstalling the ubuntu os again.. .. everthing else is fine.. no errors.. reboot didnot work.. 

now I am currently on live cd and posting this message..
[B]
some thing has gone wrong with the mbr or grub or soemthing like that.. any suggestions.. please..[/B]

---

### Post by jadhav333 on 2009-08-11
Here is my **fdisk -l **listing:

---

### Post by jadhav333 on 2009-08-11
Here is a listing of my **Boot Info** based on the following link:
**[http://ubuntuforums.org/showpost.php?p=6725571&postcount=3](http://ubuntuforums.org/showpost.php?p=6725571&postcount=3)**

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
   [COLOR="Red"] Boot sector type:  -
    Boot sector info:  [/COLOR]
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    [COLOR="Red"]Boot sector type:  -
    Boot sector info:[/COLOR]  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0004b3bf

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   153,597,464   153,597,402  83 Linux
/dev/sda2         153,597,465   163,830,869    10,233,405  82 Linux swap / Solaris
/dev/sda3         163,830,870 1,048,434,029   884,603,160  83 Linux
/dev/sda4       1,048,434,030 1,953,520,064   905,086,035  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0008005b

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   146,480,669   146,480,607  83 Linux
/dev/sdb2         146,480,670   156,248,189     9,767,520  82 Linux swap / Solaris
/dev/sdb3         156,248,190   976,768,064   820,519,875  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="7010fde3-dcbb-4bf3-b389-66355854bfc8" TYPE="ext3" 
/dev/sda2: UUID="abb90cdd-59fe-48db-92a2-84bdceef3a51" TYPE="swap" 
/dev/sda3: LABEL="Disk 01" UUID="acdc3159-ac8b-4826-88d1-2d2c54470165" TYPE="ext3" 
/dev/sda4: LABEL="Disk 02" UUID="13d35536-a2f5-4ca0-9317-e04e5bb35c37" TYPE="ext3" 
/dev/sdb1: UUID="cf9c2a8d-1f50-48f1-8083-b1cc23b6f338" TYPE="ext3" 
/dev/sdb2: UUID="dd7730f4-639e-4cc2-be1d-9dceafdf1212" TYPE="swap" 
/dev/sdb3: UUID="9646e3d9-0540-434a-a538-77401dcf9948" TYPE="ext3" 

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
/dev/sdb3 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sdb1 on /media/disk-1 type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sda1 on /media/disk-2 type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sda3 on /media/Disk 01 type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sda4 on /media/Disk 02 type ext3 (rw,nosuid,nodev,uhelper=hal)


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
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=cf9c2a8d-1f50-48f1-8083-b1cc23b6f338 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=cf9c2a8d-1f50-48f1-8083-b1cc23b6f338

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
uuid		cf9c2a8d-1f50-48f1-8083-b1cc23b6f338
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=cf9c2a8d-1f50-48f1-8083-b1cc23b6f338 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		cf9c2a8d-1f50-48f1-8083-b1cc23b6f338
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=cf9c2a8d-1f50-48f1-8083-b1cc23b6f338 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		cf9c2a8d-1f50-48f1-8083-b1cc23b6f338
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=cf9c2a8d-1f50-48f1-8083-b1cc23b6f338 /               ext3    relatime,errors=remount-ro 0       1
# /media/disk-sda3 was on /dev/sda3 during installation
UUID=acdc3159-ac8b-4826-88d1-2d2c54470165 /media/disk-sda3 ext3    relatime        0       2
# /media/disk-sda4 was on /dev/sda4 during installation
UUID=13d35536-a2f5-4ca0-9317-e04e5bb35c37 /media/disk-sda4 ext3    relatime        0       2
# /media/disk-sdb3 was on /dev/sdb3 during installation
UUID=9646e3d9-0540-434a-a538-77401dcf9948 /media/disk-sdb3 ext3    relatime        0       2
# swap was on /dev/sda2 during installation
UUID=abb90cdd-59fe-48db-92a2-84bdceef3a51 none            swap    sw              0       0
# swap was on /dev/sdb2 during installation
UUID=dd7730f4-639e-4cc2-be1d-9dceafdf1212 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


   6.7GB: boot/grub/menu.lst
   6.7GB: boot/grub/stage2
   6.7GB: boot/initrd.img-2.6.28-11-generic
   6.7GB: boot/vmlinuz-2.6.28-11-generic
   6.7GB: initrd.img
   6.7GB: vmlinuz

---

### Post by jadhav333 on 2009-08-11
something is wrong for sure.. what do you think the **boot info **reveal about the state of the grub.. I have highlighted some text in [COLOR="Red"]red[/COLOR].. is that a point of concern..

---

### Post by jadhav333 on 2009-08-12
somebody.. :(

---

### Post by jadhav333 on 2009-08-15
ISSUE RESOLVED

I downloaded Hiren's BootCD.. Recommended for a comprehensive collection of system diagnostic, testing, recovery, tools.. [http://www.hirensbootcd.net/](http://www.hirensbootcd.net/)

I used seagate seatools to test physical integrity of my drive.. it passed the test..

Then I did a Erase Track 0.. Important to backup all data before this operation, as it is a data destructive tool.

Then I re-installed Ubuntu from Live CD.. Voila I am back online..

---

