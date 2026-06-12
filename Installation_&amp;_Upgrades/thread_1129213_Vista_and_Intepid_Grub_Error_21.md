---
title: "Vista and Intepid Grub Error 21?"
date: 2009-04-18
forum: Installation &amp; Upgrades
---

### Post by Makoglider on 2009-04-18
Hello, I am completely new to Ubuntu.

I have Vista installed on my Internal HDD, and last night I tried to install Intrepid 8.10 on my external Western Digital My Book 1tb.

The installation ran smoothly, but when I restarted, it gave me Grub 1.5 Error 21.

I can only boot into a live cd of Intrepid now, what should I do?

---

### Post by meierfra. on 2009-04-18
You probably just have to reinstall grub. 
But in order to get a clearer picture of your setup, I suggest to boot  from the Ubuntu LiveCD and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post,  highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it.

Are your bios set to boot from the USB drive or from the internal drive?

---

### Post by Makoglider on 2009-04-18
> **meierfra. said:**
> Are your bios set to boot from the USB drive or from the internal drive?

I believe they are set to load the internal drive.

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Grub0.97 is installed in the MBR of /dev/sdh and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdh1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdh2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdh3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1549f232

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 1,226,594,879 1,226,594,817   7 HPFS/NTFS
/dev/sda2       1,226,594,880 1,250,258,624    23,663,745   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2013 MB, 2013265920 bytes
255 heads, 63 sectors/track, 244 cylinders, total 3932160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0d0c0b0a

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     3,919,859     3,919,797   6 FAT16


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 2013 MB, 2013265920 bytes
255 heads, 63 sectors/track, 244 cylinders, total 3932160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0d0c0b0a

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63     3,919,859     3,919,797   6 FAT16


Drive: sdh ___________________ _____________________________________________________

Disk /dev/sdh: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe8900690

Partition  Boot         Start           End          Size  Id System

/dev/sdh1                  63 1,743,804,864 1,743,804,802   7 HPFS/NTFS
/dev/sdh2    *  1,743,807,555 1,846,221,929   102,414,375  83 Linux
/dev/sdh3       1,948,636,305 1,953,520,064     4,883,760  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="ACE67792E6775C10" LABEL="HP" TYPE="ntfs" 
/dev/sda2: UUID="949CA48C9CA46A86" LABEL="FACTORY_IMAGE" TYPE="ntfs" 
/dev/sdb1: SEC_TYPE="msdos" LABEL="FILES" UUID="8015-71CD" TYPE="vfat" 
/dev/sdc1: SEC_TYPE="msdos" UUID="6C14-945F" TYPE="vfat" 
/dev/sdh1: UUID="2620B4BB20B49373" LABEL="Backup/ETC" TYPE="ntfs" 
/dev/sdh2: UUID="8a20df1b-f9f4-484f-9fe4-a5954d9f9d4d" TYPE="ext3" 
/dev/sdh3: UUID="978a3d20-8627-40a5-9b2f-4dc2c945ac53" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 
/dev/loop1: UUID="76e7f052-8701-4b84-b445-41bfcba057d3" TYPE="ext3" 

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
/dev/sdf1 on /cdrom type vfat (rw,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdg1 on /media/Backup_ETC type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdg2 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdg2 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/fuse on /home/ubuntu/.gvfs type fuse (rw,nosuid,nodev,user=ubuntu)
/dev/sdh2 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sdh1 on /media/Backup_ETC type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /media/FILES type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)


=========================== sdh2/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=8a20df1b-f9f4-484f-9fe4-a5954d9f9d4d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=8a20df1b-f9f4-484f-9fe4-a5954d9f9d4d

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
uuid		8a20df1b-f9f4-484f-9fe4-a5954d9f9d4d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8a20df1b-f9f4-484f-9fe4-a5954d9f9d4d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		8a20df1b-f9f4-484f-9fe4-a5954d9f9d4d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8a20df1b-f9f4-484f-9fe4-a5954d9f9d4d ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		8a20df1b-f9f4-484f-9fe4-a5954d9f9d4d
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


=============================== sdh2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=8a20df1b-f9f4-484f-9fe4-a5954d9f9d4d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb3
UUID=978a3d20-8627-40a5-9b2f-4dc2c945ac53 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdh2: Location of files loaded by Grub: ===================


 916.9GB: boot/grub/menu.lst
 917.0GB: boot/grub/stage2
 917.1GB: boot/initrd.img-2.6.27-7-generic
 917.1GB: boot/vmlinuz-2.6.27-7-generic
 917.1GB: initrd.img
 917.1GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg 

```

---

### Post by meierfra. on 2009-04-18
Set your bios to boot from  your Ubuntu drive (the external Western Digital). Then you should be able to boot into Ubuntu. 
(You will have to edit menu.lst, so that you can  boot into Vista. But  we'll worry about that later. )

---

### Post by Makoglider on 2009-04-18
I set the WD hard Drive boot, but I'm still getting Grub error 21.

---

### Post by meierfra. on 2009-04-18
Sounds like a problem with your bios.   Here are a couple of links where people solved grub error 21 by changing settings in the bios:

[http://lists.gnu.org/archive/html/bug-grub/2003-02/msg00082.html](http://lists.gnu.org/archive/html/bug-grub/2003-02/msg00082.html)

[http://ubuntuforums.org/showthread.php?t=1091349#7](http://ubuntuforums.org/showthread.php?t=1091349#7)

[http://ubuntuforums.org/showthread.php?t=517772#13](http://ubuntuforums.org/showthread.php?t=517772#13)

You might also see whether the Super Grub Disk lets you boot into Ubuntu:
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by Makoglider on 2009-04-18
> [http://lists.gnu.org/archive/html/bug-grub/2003-02/msg00082.html](http://lists.gnu.org/archive/html/bug-grub/2003-02/msg00082.html)

Not sure what he means here.

> [http://ubuntuforums.org/showthread.php?t=1091349#7](http://ubuntuforums.org/showthread.php?t=1091349#7)
[http://ubuntuforums.org/showthread.php?t=517772#13](http://ubuntuforums.org/showthread.php?t=517772#13)

Tried this, still getting Grub Error 21.

> [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

When I boot into the Ubuntu partition on the My Book, it gives me Grub Error 17. When I boot into Vista, I get Grub error 21.

---

### Post by meierfra. on 2009-04-18
> 
[QUOTE][http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
When I boot into the Ubuntu partition on the My Book, it gives me Grub Error 17. When I boot into Vista, I get Grub error 21. 
[/QUOTE]
Is this what happened when you tried to Ubuntu and Vista with SuperGrub?

Which methods did you use?

Try this. Boot from the SuperGrub disk. At the first screen press "c". Then type  

geometry (hd0)
geometry (hd1)
geometry (hd2)
geometry (hd3)
geometry (hd4)


This should  list the partitions on each of your hard drives. Are all your hard drives detected?

Press "esc" to get back to the first  screen. Choose

Choose Language and No Help
English SuperGrub Disk
Support
Show Hard Disk's  Partition Layouts.

Does this show your Ubuntu partition?

---

