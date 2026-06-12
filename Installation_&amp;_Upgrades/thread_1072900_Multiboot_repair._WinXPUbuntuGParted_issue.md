---
title: "Multiboot repair. WinXP/Ubuntu/GParted issue"
date: 2009-02-17
forum: Installation &amp; Upgrades
---

### Post by Mylorharbour on 2009-02-17
**[Solved]**


I followed Herman's multiboot/Grub partition route a while ago to set up a test machine booting WinXP and several variants of Ubuntu. All worked well until I needed to re-install WinXP. As I knew I'd lose the MBR I backed it up as Herman suggests, just the first 466 bytes. I then re-installed XP into it's original partition and restored the MBR after checking all was well with XP.

Now on boot up I get Grub Error 15. I ran the boot_info_script which I think shows all is well but strangely I can't boot any Ubuntu partition from Super Grub Disk, although I do get as far as a splash screen on the Kubuntu partition. SGD will boot XP just fine. More bad news......using a Hardy LiveCD and firing up GParted I find it can't see any partitions on sda. All it sees is 234Gb unallocated. All operating systems are on sda.

I'm thinking I've screwed the partition table somehow but, if so, how can the boot_info_script and Super Grub Disk see the partitions? At least if GParted could see the partitions I could delete them and start again.

Could there be a quick fix for this or will I need to delete the partitions using the XP installation disk and rebuild the setup?

---

### Post by Mylorharbour on 2009-02-18
*Apologies for cross-posting this but in error I posted it in the Absolute Beginner Talk Forum. As you will se it's by no means a beginners post.*


I followed Herman's multiboot/Grub partition route a while ago to set up a test machine booting WinXP and several variants of Ubuntu. All worked well until I needed to re-install WinXP. As I knew I'd lose the MBR I backed it up as Herman suggests, just the first 466 bytes. I then re-installed XP into it's original partition and restored the MBR after checking all was well with XP.

Now on boot up I get Grub Error 15. I ran the boot_info_script which I think shows all is well but strangely I can't boot any Ubuntu partition from Super Grub Disk, although I do get as far as a splash screen on the Kubuntu partition. SGD will boot XP just fine. More bad news......using a Hardy LiveCD and firing up GParted I find it can't see any partitions on sda. All it sees is 234Gb unallocated. All operating systems are on sda.

I'm thinking I've screwed the partition table somehow but, if so, how can the boot_info_script and Super Grub Disk see the partitions? At least if GParted could see the partitions I could delete them and start again.

Could there be a quick fix for this or will I need to delete the partitions using the XP installation disk and rebuild the setup?

---

### Post by Herman on 2009-02-18
It sounds like Windows has corrupted your partition table somehow.
My suggestion is to use [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") to rebuild your partition table.

You can install TestDisk temporarily in your Ubuntu Live CD or you can use Ubuntu Rescue Remix or Parted Magic or System Rescue CD, I think any of those would include TestDisk.

Regards, Herman :)

---

### Post by caljohnsmith on 2009-02-18
Can you post the output of the Boot Info Script so we can see exactly what the results are? It may be that you won't have to use testdisk to recover your partition table if the problem is a simple issue of overlapping partitions or something like that; although testdisk could certainly work to fix problems like that, it can take a while to do a complete scan, and correcting simple problems with the partition table can usually be done more efficiently with sfdisk or other tools. It's worth mentioning that I've seen in the forums how sometimes a person's partition table becomes corrupt when they reinstall Windows (as Herman all ready mentioned), so it seems the Windows partitioner sometimes does not get along well with drives that use Linux CHS geometry or have Linux partitions (or maybe it is some other issue).

---

### Post by overdrank on 2009-02-18
Threads merged :)

---

### Post by Mylorharbour on 2009-02-18
It may be helpful to know that I can use the Super Grub Disk to boot Windows. Windows Disk Management can see all the partitions. What you may find odd though is that the HD with the operating systems on is Disk 1 and the 2nd HD is above it labelled Disk 0.There are only files on the 2nd HD.

boot_info_script (RESULTS.txt) is attached as requested. Partition 6 is the dedicated GRUB partition.

---

### Post by Mylorharbour on 2009-02-18
2nd attempt due to attachment failure.


```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc
 => No known boot loader is installed in the MBR of /dev/sdd

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

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /etc/fstab

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda9: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda10: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 7.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda11: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda12: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /boot/grub/menu.lst

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdd2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdd3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdd4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0007f86f

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   123,073,964   123,073,902   7 HPFS/NTFS
/dev/sda2         123,073,965   488,392,064   365,318,100   5 Extended
/dev/sda5         123,074,091   355,229,279   232,155,189  83 Linux
/dev/sda6         355,229,343   375,969,194    20,739,852  83 Linux
/dev/sda7         375,969,258   396,773,369    20,804,112  83 Linux
/dev/sda8         396,773,433   417,368,699    20,595,267  83 Linux
/dev/sda9         417,368,763   438,156,809    20,788,047  83 Linux
/dev/sda10        438,156,873   458,977,049    20,820,177  83 Linux
/dev/sda11        458,977,113   479,652,704    20,675,592  83 Linux
/dev/sda12        479,652,768   480,359,564       706,797  83 Linux
/dev/sda3         480,359,565   488,392,064     8,032,500  82 Linux swap / Solaris

/dev/sda2 overlaps with /dev/sda3

Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00010bde

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   976,768,064   976,768,002   5 Extended
/dev/sdb5                 126   410,235,839   410,235,714  83 Linux
/dev/sdb6         410,235,903   976,768,064   566,532,162   7 HPFS/NTFS


Drive sdc: _____________________________________________________________________

Disk /dev/sdc: 4235 MB, 4235984896 bytes
2 heads, 63 sectors/track, 65661 cylinders, total 8273408 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0002ff07

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63     8,273,407     8,273,345   b W95 FAT32

/dev/sdc1 ends after the last cylinder of /dev/sdc

Drive sdd: _____________________________________________________________________

Disk /dev/sdd: 4204 MB, 4204789760 bytes
130 heads, 62 sectors/track, 1018 cylinders, total 8212480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6f20736b

Partition  Boot         Start           End          Size  Id System

/dev/sdd1     ?   778,135,908 1,919,645,538 1,141,509,631  72 Unknown
/dev/sdd2     ?   168,689,522 2,104,717,761 1,936,028,240  65 Novell Netware 386
/dev/sdd3     ? 1,869,881,465 3,805,909,656 1,936,028,192  79 Unknown
/dev/sdd4     ? 2,885,681,152 2,885,736,650        55,499   d Unknown

/dev/sdd1 ends after the last sector of /dev/sdd
/dev/sdd1 overlaps with /dev/sdd2
/dev/sdd1 overlaps with /dev/sdd3
/dev/sdd2 ends after the last sector of /dev/sdd
/dev/sdd2 overlaps with /dev/sdd3
/dev/sdd3 ends after the last sector of /dev/sdd
/dev/sdd3 overlaps with /dev/sdd4
/dev/sdd4 ends after the last sector of /dev/sdd

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="52EC0B3EEC0B1BBB" TYPE="ntfs" 
/dev/sda3: UUID="4020e4b3-acfa-4617-89bd-8cfef03eb51e" TYPE="swap" 
/dev/sda5: LABEL="Home" UUID="3ec93643-a772-46e3-819d-8ba4c963ecb1" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: LABEL="Spare" UUID="7396e5a9-8d29-47b1-8f4b-074ed43177a2" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="60640d03-c41a-42df-97cb-40771a9f3ce7" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda8: LABEL="Hardy" UUID="600a31e9-eece-4204-9e18-eb98c5f475c9" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda9: LABEL="Kubuntu" UUID="8a3de09c-581d-4be1-b194-54e8feaf7e1f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda10: LABEL="Gutsy_sda13" UUID="4383047f-4b5e-4445-b139-f82ebcb71917" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda11: LABEL="Studio_sda12" UUID="db15b278-9763-4601-96be-46890552ecdc" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda12: LABEL="GRUB" UUID="cd905205-263b-4f9d-ad48-6371d81d1cfc" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="6a4614bc-e70d-4ba1-b41e-5da0855e89d5" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb6: UUID="7526EC4A5412B28E" LABEL="Intrenal 2 NTFS" TYPE="ntfs" 
/dev/sdc1: LABEL="USB DRIVE T" UUID="38A2-FBE9" TYPE="vfat" 
/dev/loop0: TYPE="squashfs" 
/dev/loop1: UUID="881cf4f6-9d9b-45e1-9409-2f3db0cd553e" TYPE="ext3" 
/dev/sdd: LABEL="KINGSTON" UUID="E815-92C5" TYPE="vfat" 

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
/dev/sdc1 on /cdrom type vfat (rw,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdd on /media/KINGSTON type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)

================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=60640d03-c41a-42df-97cb-40771a9f3ce7 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda9
UUID=3ec93643-a772-46e3-819d-8ba4c963ecb1 /home           ext3    relatime        0       2
# /dev/sda5
UUID=4020e4b3-acfa-4617-89bd-8cfef03eb51e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


 193.0GB: boot/initrd.img-2.6.27-7-generic
 193.0GB: boot/initrd.img-2.6.27-9-generic
 193.0GB: boot/vmlinuz-2.6.27-7-generic
 193.0GB: boot/vmlinuz-2.6.27-9-generic
 193.0GB: initrd.img
 193.0GB: initrd.img.old
 193.0GB: vmlinuz
 193.0GB: vmlinuz.old

=========================== sda8/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=600a31e9-eece-4204-9e18-eb98c5f475c9 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,9)

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

title		Ubuntu Hardy 8.04, kernel 2.6.24-16-generic
root		(hd0,9)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=600a31e9-eece-4204-9e18-eb98c5f475c9 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,9)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=600a31e9-eece-4204-9e18-eb98c5f475c9 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,9)
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


=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda10
UUID=600a31e9-eece-4204-9e18-eb98c5f475c9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda9
UUID=3ec93643-a772-46e3-819d-8ba4c963ecb1 /home           ext3    relatime        0       2
# /dev/sda5
UUID=4020e4b3-acfa-4617-89bd-8cfef03eb51e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#/dev/sdb5: Video Workspace on second internal HD 1st partition
/dev/sdb5 /media/video_workspace ext3 auto,user,exec,rw,sync 0 3
#/dev/sdb6: NTFS shared area for backups on second internal HD 2nd partition
/dev/sdb5 /media/ntfs ntfs auto,user,exec,rw,sync 0 4

=================== sda8: Location of files loaded by Grub: ===================


 206.0GB: boot/grub/menu.lst
 206.0GB: boot/grub/stage2
 206.0GB: boot/initrd.img-2.6.24-16-generic
 206.0GB: boot/initrd.img-2.6.24-16-generic.bak
 206.0GB: boot/initrd.img-2.6.24-19-generic
 206.0GB: boot/initrd.img-2.6.24-19-generic.bak
 206.1GB: boot/initrd.img-2.6.24-21-generic
 205.9GB: boot/initrd.img-2.6.24-21-generic.bak
 206.1GB: boot/initrd.img-2.6.24-22-generic
 206.0GB: boot/initrd.img-2.6.24-22-generic.bak
 206.0GB: boot/initrd.img-2.6.24-23-generic
 205.9GB: boot/initrd.img-2.6.24-23-generic.bak
 206.0GB: boot/vmlinuz-2.6.24-16-generic
 206.0GB: boot/vmlinuz-2.6.24-19-generic
 206.0GB: boot/vmlinuz-2.6.24-21-generic
 206.0GB: boot/vmlinuz-2.6.24-22-generic
 206.0GB: boot/vmlinuz-2.6.24-23-generic
 206.0GB: initrd.img
 206.0GB: initrd.img.old
 206.0GB: vmlinuz
 206.0GB: vmlinuz.old

=========================== sda9/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=8a3de09c-581d-4be1-b194-54e8feaf7e1f ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,10)

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
root		(hd0,10)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=8a3de09c-581d-4be1-b194-54e8feaf7e1f ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,10)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=8a3de09c-581d-4be1-b194-54e8feaf7e1f ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,10)
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


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda10.
title		Ubuntu Hardy 8.04, kernel 2.6.24-16-generic (on /dev/sda10)
root		(hd0,9)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=600a31e9-eece-4204-9e18-eb98c5f475c9 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda10.
title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode) (on /dev/sda10)
root		(hd0,9)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=600a31e9-eece-4204-9e18-eb98c5f475c9 ro single 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda10.
title		Ubuntu 8.04, memtest86+ (on /dev/sda10)
root		(hd0,9)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sda9/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda11
UUID=8a3de09c-581d-4be1-b194-54e8feaf7e1f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda9
UUID=3ec93643-a772-46e3-819d-8ba4c963ecb1 /home           ext3    relatime        0       2
# /dev/sda5
UUID=4020e4b3-acfa-4617-89bd-8cfef03eb51e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda9: Location of files loaded by Grub: ===================


 219.9GB: boot/grub/menu.lst
 219.8GB: boot/grub/stage2
 219.9GB: boot/initrd.img-2.6.24-16-generic
 219.9GB: boot/initrd.img-2.6.24-16-generic.bak
 219.9GB: boot/vmlinuz-2.6.24-16-generic
 219.9GB: initrd.img
 219.9GB: vmlinuz

========================== sda10/boot/grub/menu.lst: ==========================

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
# kopt=root=UUID=4383047f-4b5e-4445-b139-f82ebcb71917 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,12)

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

title		Ubuntu 7.10, kernel 2.6.22-15-generic
root		(hd0,12)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=4383047f-4b5e-4445-b139-f82ebcb71917 ro quiet splash
initrd		/boot/initrd.img-2.6.22-15-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode)
root		(hd0,12)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=4383047f-4b5e-4445-b139-f82ebcb71917 ro single
initrd		/boot/initrd.img-2.6.22-15-generic

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,12)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=4383047f-4b5e-4445-b139-f82ebcb71917 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,12)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=4383047f-4b5e-4445-b139-f82ebcb71917 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,12)
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


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda10.
title		Ubuntu Hardy 8.04, kernel 2.6.24-16-generic (on /dev/sda10)
root		(hd0,9)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=600a31e9-eece-4204-9e18-eb98c5f475c9 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda10.
title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode) (on /dev/sda10)
root		(hd0,9)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=600a31e9-eece-4204-9e18-eb98c5f475c9 ro single 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda10.
title		Ubuntu 8.04, memtest86+ (on /dev/sda10)
root		(hd0,9)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda11.
title		Ubuntu 8.04, kernel 2.6.24-16-generic (on /dev/sda11)
root		(hd0,10)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=8a3de09c-581d-4be1-b194-54e8feaf7e1f ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda11.
title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode) (on /dev/sda11)
root		(hd0,10)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=8a3de09c-581d-4be1-b194-54e8feaf7e1f ro single 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda11.
title		Ubuntu 8.04, memtest86+ (on /dev/sda11)
root		(hd0,10)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda12.
title		Ubuntu 8.04, kernel 2.6.24-16-generic (on /dev/sda12)
root		(hd0,11)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=db15b278-9763-4601-96be-46890552ecdc ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda12.
title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode) (on /dev/sda12)
root		(hd0,11)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=db15b278-9763-4601-96be-46890552ecdc ro single 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda12.
title		Ubuntu 8.04, memtest86+ (on /dev/sda12)
root		(hd0,11)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sda10/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda13
UUID=4383047f-4b5e-4445-b139-f82ebcb71917 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda9
UUID=3ec93643-a772-46e3-819d-8ba4c963ecb1 /home           ext3    defaults        0       2
# /dev/sda1
UUID=560440FA0440DE9D /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda10
UUID=600a31e9-eece-4204-9e18-eb98c5f475c9 /media/sda10    ext3    defaults        0       2
# /dev/sda11
UUID=8a3de09c-581d-4be1-b194-54e8feaf7e1f /media/sda11    ext3    defaults        0       2
# /dev/sda12
UUID=db15b278-9763-4601-96be-46890552ecdc /media/sda12    ext3    defaults        0       2
# /dev/sda6
UUID=cd905205-263b-4f9d-ad48-6371d81d1cfc /media/sda6     ext3    defaults        0       2
# /dev/sda7
UUID=10bbf32d-5b88-410c-a740-4fb6957bdc92 /media/sda7     ext3    defaults        0       2
# /dev/sda8
UUID=7396e5a9-8d29-47b1-8f4b-074ed43177a2 /media/sda8     ext3    defaults        0       2
# /dev/sdb5
UUID=6a4614bc-e70d-4ba1-b41e-5da0855e89d5 /media/sdb5     ext3    defaults        0       2
# /dev/sdb6
UUID=7526EC4A5412B28E /media/sdb6     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=4020e4b3-acfa-4617-89bd-8cfef03eb51e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

=================== sda10: Location of files loaded by Grub: ===================


 225.9GB: boot/grub/menu.lst
 225.9GB: boot/grub/stage2
 225.9GB: boot/initrd.img-2.6.22-14-generic
 225.9GB: boot/initrd.img-2.6.22-14-generic.bak
 225.8GB: boot/initrd.img-2.6.22-15-generic
 225.8GB: boot/initrd.img-2.6.22-15-generic.bak
 225.9GB: boot/vmlinuz-2.6.22-14-generic
 225.9GB: boot/vmlinuz-2.6.22-15-generic
 225.8GB: initrd.img
 225.9GB: initrd.img.old
 225.9GB: vmlinuz
 225.9GB: vmlinuz.old

========================== sda11/boot/grub/menu.lst: ==========================

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
# kopt=root=UUID=db15b278-9763-4601-96be-46890552ecdc ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,11)

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

title		Ubuntu 8.04.2, kernel 2.6.24-23-rt
root		(hd0,11)
kernel		/boot/vmlinuz-2.6.24-23-rt root=UUID=db15b278-9763-4601-96be-46890552ecdc ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-rt
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-rt (recovery mode)
root		(hd0,11)
kernel		/boot/vmlinuz-2.6.24-23-rt root=UUID=db15b278-9763-4601-96be-46890552ecdc ro single
initrd		/boot/initrd.img-2.6.24-23-rt

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,11)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=db15b278-9763-4601-96be-46890552ecdc ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,11)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=db15b278-9763-4601-96be-46890552ecdc ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, kernel 2.6.24-19-rt
root		(hd0,11)
kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=db15b278-9763-4601-96be-46890552ecdc ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-rt
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-19-rt (recovery mode)
root		(hd0,11)
kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=db15b278-9763-4601-96be-46890552ecdc ro single
initrd		/boot/initrd.img-2.6.24-19-rt

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic
root		(hd0,11)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=db15b278-9763-4601-96be-46890552ecdc ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,11)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=db15b278-9763-4601-96be-46890552ecdc ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.2, kernel 2.6.24-16-generic
root		(hd0,11)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=db15b278-9763-4601-96be-46890552ecdc ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,11)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=db15b278-9763-4601-96be-46890552ecdc ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,11)
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


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda10.
title		Ubuntu Hardy 8.04, kernel 2.6.24-16-generic (on /dev/sda10)
root		(hd0,9)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=600a31e9-eece-4204-9e18-eb98c5f475c9 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda10.
title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode) (on /dev/sda10)
root		(hd0,9)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=600a31e9-eece-4204-9e18-eb98c5f475c9 ro single 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda10.
title		Ubuntu 8.04, memtest86+ (on /dev/sda10)
root		(hd0,9)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda11.
title		Ubuntu 8.04, kernel 2.6.24-16-generic (on /dev/sda11)
root		(hd0,10)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=8a3de09c-581d-4be1-b194-54e8feaf7e1f ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda11.
title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode) (on /dev/sda11)
root		(hd0,10)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=8a3de09c-581d-4be1-b194-54e8feaf7e1f ro single 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda11.
title		Ubuntu 8.04, memtest86+ (on /dev/sda11)
root		(hd0,10)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sda11/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda12
UUID=db15b278-9763-4601-96be-46890552ecdc /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda9
UUID=3ec93643-a772-46e3-819d-8ba4c963ecb1 /home           ext3    relatime        0       2
# /dev/sda5
UUID=4020e4b3-acfa-4617-89bd-8cfef03eb51e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda11: Location of files loaded by Grub: ===================


 240.8GB: boot/grub/menu.lst
 240.8GB: boot/grub/stage2
 240.6GB: boot/initrd.img-2.6.24-16-generic
 240.6GB: boot/initrd.img-2.6.24-16-generic.bak
 240.7GB: boot/initrd.img-2.6.24-19-generic
 240.7GB: boot/initrd.img-2.6.24-19-generic.bak
 240.7GB: boot/initrd.img-2.6.24-19-rt
 240.7GB: boot/initrd.img-2.6.24-19-rt.bak
 240.7GB: boot/initrd.img-2.6.24-23-generic
 240.7GB: boot/initrd.img-2.6.24-23-generic.bak
 240.6GB: boot/initrd.img-2.6.24-23-rt
 240.7GB: boot/initrd.img-2.6.24-23-rt.bak
 240.7GB: boot/vmlinuz-2.6.24-16-generic
 240.7GB: boot/vmlinuz-2.6.24-19-generic
 240.7GB: boot/vmlinuz-2.6.24-19-rt
 240.7GB: boot/vmlinuz-2.6.24-23-generic
 240.7GB: boot/vmlinuz-2.6.24-23-rt
 240.6GB: initrd.img
 240.7GB: initrd.img.old
 240.7GB: vmlinuz
 240.7GB: vmlinuz.old

========================== sda12/boot/grub/menu.lst: ==========================

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
# kopt=root=UUID=4383047f-4b5e-4445-b139-f82ebcb71917 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,12)

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

title		GRUB Partition Menu - Ubuntu Hardy Heron 8.04 in sda10
root		(hd0,9)
kernel		/vmlinuz root=/dev/sda10 ro quiet splash
initrd		/initrd.img
boot

title		Ubuntu Studio Intrepid Ibex 8.10 in sda7
root		(hd0,6)
kernel		/vmlinuz root=/dev/sda7 ro quiet splash
initrd		/initrd.img
boot

title		Ubuntu Studio Hardy Heron 8.04 in sda12
root		(hd0,11)
kernel		/vmlinuz root=/dev/sda12 ro quiet splash
initrd		/initrd.img
boot

title		Ubuntu Gutsy Gibbon 7.10 in sda13
root		(hd0,12)
kernel		/vmlinuz root=/dev/sda13 ro quiet splash
initrd		/initrd.img
boot

title		Kubuntu Hardy Heron 8.04 in sda11
root		(hd0,10)
kernel		/vmlinuz root=/dev/sda11 ro quiet splash
initrd		/initrd.img
boot

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,12)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=4383047f-4b5e-4445-b139-f82ebcb71917 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,12)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=4383047f-4b5e-4445-b139-f82ebcb71917 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,12)
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


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda10.
title		Ubuntu Hardy 8.04, kernel 2.6.24-16-generic (on /dev/sda10)
root		(hd0,9)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=600a31e9-eece-4204-9e18-eb98c5f475c9 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda10.
title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode) (on /dev/sda10)
root		(hd0,9)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=600a31e9-eece-4204-9e18-eb98c5f475c9 ro single 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda10.
title		Ubuntu 8.04, memtest86+ (on /dev/sda10)
root		(hd0,9)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda11.
title		Ubuntu 8.04, kernel 2.6.24-16-generic (on /dev/sda11)
root		(hd0,10)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=8a3de09c-581d-4be1-b194-54e8feaf7e1f ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda11.
title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode) (on /dev/sda11)
root		(hd0,10)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=8a3de09c-581d-4be1-b194-54e8feaf7e1f ro single 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda11.
title		Ubuntu 8.04, memtest86+ (on /dev/sda11)
root		(hd0,10)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda12.
title		Ubuntu 8.04, kernel 2.6.24-16-generic (on /dev/sda12)
root		(hd0,11)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=db15b278-9763-4601-96be-46890552ecdc ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda12.
title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode) (on /dev/sda12)
root		(hd0,11)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=db15b278-9763-4601-96be-46890552ecdc ro single 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda12.
title		Ubuntu 8.04, memtest86+ (on /dev/sda12)
root		(hd0,11)
kernel		/boot/memtest86+.bin  
savedefault
boot


=================== sda12: Location of files loaded by Grub: ===================


 245.9GB: boot/grub/menu.lst
 245.9GB: boot/grub/stage2

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdd

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 26 00  |.X.MSDOS5.0...&.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 00 00 00  |........?.......|
00000020  00 50 7d 00 45 1f 00 00  00 00 00 00 02 00 00 00  |.P}.E...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 c5 92 15 e8 4e  4f 20 4e 41 4d 45 20 20  |..)....NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 08  |{......|.N..V@..|
00000070  cd 13 73 05 b9 ff ff 8a  f1 66 0f b6 c6 40 66 0f  |..s......f...@f.|
00000080  b6 d1 80 e2 3f f7 e2 86  cd c0 ed 06 41 66 0f b7  |....?.......Af..|
00000090  c9 66 f7 e1 66 89 46 f8  83 7e 16 00 75 38 83 7e  |.f..f.F..~..u8.~|
000000a0  2a 00 77 32 66 8b 46 1c  66 83 c0 0c bb 00 80 b9  |*.w2f.F.f.......|
000000b0  01 00 e8 2b 00 e9 48 03  a0 fa 7d b4 7d 8b f0 ac  |...+..H...}.}...|
000000c0  84 c0 74 17 3c ff 74 09  b4 0e bb 07 00 cd 10 eb  |..t.<.t.........|
000000d0  ee a0 fb 7d eb e5 a0 f9  7d eb e0 98 cd 16 cd 19  |...}....}.......|
000000e0  66 60 66 3b 46 f8 0f 82  4a 00 66 6a 00 66 50 06  |f`f;F...J.fj.fP.|
000000f0  53 66 68 10 00 01 00 80  7e 02 00 0f 85 20 00 b4  |Sfh.....~.... ..|
00000100  41 bb aa 55 8a 56 40 cd  13 0f 82 1c 00 81 fb 55  |A..U.V@........U|
00000110  aa 0f 85 14 00 f6 c1 01  0f 84 0d 00 fe 46 02 b4  |.............F..|
00000120  42 8a 56 40 8b f4 cd 13  b0 f9 66 58 66 58 66 58  |B.V@......fXfXfX|
00000130  66 58 eb 2a 66 33 d2 66  0f b7 4e 18 66 f7 f1 fe  |fX.*f3.f..N.f...|
00000140  c2 8a ca 66 8b d0 66 c1  ea 10 f7 76 1a 86 d6 8a  |...f..f....v....|
00000150  56 40 8a e8 c0 e4 06 0a  cc b8 01 02 cd 13 66 61  |V@............fa|
00000160  0f 82 54 ff 81 c3 00 02  66 40 49 0f 85 71 ff c3  |..T.....f@I..q..|
00000170  4e 54 4c 44 52 20 20 20  20 20 20 00 00 00 00 00  |NTLDR      .....|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 52 65  |..............Re|
000001b0  6d 6f 76 65 20 64 69 73  6b 73 20 6f 72 20 6f 74  |move disks or ot|
000001c0  68 65 72 20 6d 65 64 69  61 2e ff 0d 0a 44 69 73  |her media....Dis|
000001d0  6b 20 65 72 72 6f 72 ff  0d 0a 50 72 65 73 73 20  |k error...Press |
000001e0  61 6e 79 20 6b 65 79 20  74 6f 20 72 65 73 74 61  |any key to resta|
000001f0  72 74 0d 0a 00 00 00 00  00 ac cb d8 00 00 55 aa  |rt............U.|
00000200

Unknown BootLoader  on sdb6

00000000  eb 5b 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.[.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 ff b3 73 18  |........?.....s.|
00000020  00 00 00 00 80 00 80 00  41 98 c4 21 00 00 00 00  |........A..!....|
00000030  04 00 00 00 00 00 00 00  84 49 1c 02 00 00 00 00  |.........I......|
00000040  f6 00 00 00 01 00 00 00  8e b2 12 54 4a ec 26 75  |...........TJ.&u|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 fa 33 c0  |..............3.|
00000060  8e d0 bc 00 7c fb b8 c0  07 8e d8 c7 06 54 00 00  |....|........T..|
00000070  00 c7 06 56 00 00 00 c7  06 5b 00 10 00 b8 00 0d  |...V.....[......|
00000080  8e c0 2b db e8 07 00 68  00 0d 68 66 02 cb 50 53  |..+....h..hf..PS|
00000090  51 52 06 66 a1 54 00 66  03 06 1c 00 66 33 d2 66  |QR.f.T.f....f3.f|
000000a0  0f b7 0e 18 00 66 f7 f1  fe c2 88 16 5a 00 66 8b  |.....f......Z.f.|
000000b0  d0 66 c1 ea 10 f7 36 1a  00 88 16 25 00 a3 58 00  |.f....6....%..X.|
000000c0  a1 18 00 2a 06 5a 00 40  3b 06 5b 00 76 03 a1 5b  |...*.Z.@;.[.v..[|
000000d0  00 50 b4 02 8b 16 58 00  b1 06 d2 e6 0a 36 5a 00  |.P....X......6Z.|
000000e0  8b ca 86 e9 8a 36 25 00  b2 80 cd 13 58 72 2a 01  |.....6%.....Xr*.|
000000f0  06 54 00 83 16 56 00 00  29 06 5b 00 76 0b c1 e0  |.T...V..).[.v...|
00000100  05 8c c2 03 d0 8e c2 eb  8a 07 5a 59 5b 58 c3 be  |..........ZY[X..|
00000110  59 01 eb 08 be e3 01 eb  03 be 39 01 e8 09 00 be  |Y.........9.....|
00000120  ad 01 e8 03 00 fb eb fe  ac 3c 00 74 09 b4 0e bb  |.........<.t....|
00000130  07 00 cd 10 eb f2 c3 1d  00 41 20 64 69 73 6b 20  |.........A disk |
00000140  72 65 61 64 20 65 72 72  6f 72 20 6f 63 63 75 72  |read error occur|
00000150  72 65 64 2e 0d 0a 00 29  00 41 20 6b 65 72 6e 65  |red....).A kerne|
00000160  6c 20 66 69 6c 65 20 69  73 20 6d 69 73 73 69 6e  |l file is missin|
00000170  67 20 66 72 6f 6d 20 74  68 65 20 64 69 73 6b 2e  |g from the disk.|
00000180  0d 0a 00 25 00 41 20 6b  65 72 6e 65 6c 20 66 69  |...%.A kernel fi|
00000190  6c 65 20 69 73 20 74 6f  6f 20 64 69 73 63 6f 6e  |le is too discon|
000001a0  74 69 67 75 6f 75 73 2e  0d 0a 00 33 00 49 6e 73  |tiguous....3.Ins|
000001b0  65 72 74 20 61 20 73 79  73 74 65 6d 20 64 69 73  |ert a system dis|
000001c0  6b 65 74 74 65 20 61 6e  64 20 72 65 73 74 61 72  |kette and restar|
000001d0  74 0d 0a 74 68 65 20 73  79 73 74 65 6d 2e 0d 0a  |t..the system...|
000001e0  00 17 00 5c 4e 54 4c 44  52 20 69 73 20 63 6f 6d  |...\NTLDR is com|
000001f0  70 72 65 73 73 65 64 2e  0d 0a 00 00 00 00 55 aa  |pressed.......U.|
00000200

Unknown BootLoader  on sdd1


Unknown BootLoader  on sdd2


Unknown BootLoader  on sdd3


Unknown BootLoader  on sdd4



=============================== StdErr Messages: ===============================

hexdump: /dev/sdd1: No such file or directory
hexdump: /dev/sdd1: No such file or directory
/home/ubuntu/Desktop/boot_info_script024.sh: line 1043: [: =: unary operator expected
hexdump: /dev/sdd2: No such file or directory
hexdump: /dev/sdd2: No such file or directory
/home/ubuntu/Desktop/boot_info_script024.sh: line 1043: [: =: unary operator expected
hexdump: /dev/sdd3: No such file or directory
hexdump: /dev/sdd3: No such file or directory
/home/ubuntu/Desktop/boot_info_script024.sh: line 1043: [: =: unary operator expected
hexdump: /dev/sdd4: No such file or directory
hexdump: /dev/sdd4: No such file or directory
/home/ubuntu/Desktop/boot_info_script024.sh: line 1043: [: =: unary operator expected
```

---

### Post by caljohnsmith on 2009-02-18
> **Mylorharbour said:**
> ```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0007f86f

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   123,073,964   123,073,902   7 HPFS/NTFS
[COLOR="Red"]/dev/sda2         123,073,965   488,392,064[/COLOR]   365,318,100   5 Extended
/dev/sda5         123,074,091   355,229,279   232,155,189  83 Linux
/dev/sda6         355,229,343   375,969,194    20,739,852  83 Linux
/dev/sda7         375,969,258   396,773,369    20,804,112  83 Linux
/dev/sda8         396,773,433   417,368,699    20,595,267  83 Linux
/dev/sda9         417,368,763   438,156,809    20,788,047  83 Linux
/dev/sda10        438,156,873   458,977,049    20,820,177  83 Linux
/dev/sda11        458,977,113   479,652,704    20,675,592  83 Linux
/dev/sda12        479,652,768   480,359,564       706,797  83 Linux
[COLOR="Red"]/dev/sda3         480,359,565   488,392,064[/COLOR]     8,032,500  82 Linux swap / Solaris
[COLOR="Red"]
/dev/sda2 overlaps with /dev/sda3[/COLOR]

```
As shown highlighted in red, the problem is that your sda3 primary swap partition is inside of your sda2 extended partition; therefore sda3 should either be a logical partition, or the boundaries of your sda2 extended partition should be changed so it doesn't include the sda3 partition. But according to the fstab files in all your distros, it looks like the sda3 swap partition is supposed to be logical partition sda5. So to correct the problem, how about downloading the attached "partition_table.txt" file to your Ubuntu desktop, and then do:
```
sudo sfdisk --no-reread -f /dev/sda  < ~/Desktop/partition_table.txt
```
And please post the output. Next reboot to your Live CD, and please post the output of:
```
sudo fdisk -lu
sudo parted /dev/sda print
```
Also, your other linux partitions will now be in the same order as they are physically on the drive, so we will need to tweak the menu.lst for whichever distro you want to be in charge of Grub on start up. Please let me know and we can work from there.

---

### Post by Mylorharbour on 2009-02-18
Interesting point that.

Strange thing is I don't have an sda3 but boot_info_script seems to have misinterpreted some partitions. Is that possible? Swap is sda5 or at least it used to be.

sda9 is/was my /home partition. The script says it's Hardy

I have a screenshot of sda as it was prior to the XP re-installation, see attachment. Very little should have changed since then but it does appear I installed Intrepid into one of the spare partitions some months ago but I don't remember which one.

Will you need to edit your attachment before we go any further?

---

### Post by caljohnsmith on 2009-02-18
> **Mylorharbour said:**
> 
Strange thing is I don't have an sda3 but boot_info_script seems to have misinterpreted the partition. Is that possible? Swap is sda5.

That's actually the whole point, your XP install changed your partition table so that your previous sda5 swap partition is now sda3 instead. If you are still doubtful, how about doing:
```
sudo fdisk -lu
sudo parted /dev/sda print
```
So if I'm not mistaken, the first command will show you sda3, and it will be type "82" or swap. The second command will give you an error I think, probably saying that the HDD has overlapping partitions. So is that true? That would also be why gparted doesn't show any partitions on your sda drive right now--the partition table is corrupt as I tried to explain in my previous post. I am only trying to help, so if you would rather correct the partition table yourself with testdisk or some other tool, those are definitely other alternatives. It's up to you.

---

### Post by Mylorharbour on 2009-02-18
Sorry. No criticism intended. I just like to make an attempt at understanding what goes wrong and what is done to fix it. Just call me an advanced newbie.....................probably the worst kind eh?

So sda5 has become sda3 and the others have probably been re-assigned too!

Ok

sudo fdisk -lu
```
ubuntu@ubuntu:~$ sudo fdisk -lu
omitting empty partition (5)

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0007f86f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   123073964    61536951    7  HPFS/NTFS
/dev/sda2       123073965   488392064   182659050    5  Extended
/dev/sda3       480359565   488392064     4016250   82  Linux swap / Solaris
/dev/sda5       123074091   355229279   116077594+  83  Linux
/dev/sda6       355229343   375969194    10369926   83  Linux
/dev/sda7       375969258   396773369    10402056   83  Linux
/dev/sda8       396773433   417368699    10297633+  83  Linux
/dev/sda9       417368763   438156809    10394023+  83  Linux
/dev/sda10      438156873   458977049    10410088+  83  Linux
/dev/sda11      458977113   479652704    10337796   83  Linux
/dev/sda12      479652768   480359564      353398+  83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00010bde

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   976768064   488384001    5  Extended
/dev/sdb5             126   410235839   205117857   83  Linux
/dev/sdb6       410235903   976768064   283266081    7  HPFS/NTFS

Disk /dev/sdc: 4235 MB, 4235984896 bytes
2 heads, 63 sectors/track, 65661 cylinders, total 8273408 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0002ff07

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63     8273407     4136672+   b  W95 FAT32

Disk /dev/sdd: 4204 MB, 4204789760 bytes
130 heads, 62 sectors/track, 1018 cylinders, total 8212480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   ?   778135908  1919645538   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(96542, 119, 11)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(238169, 54, 51)
Partition 1 does not end on cylinder boundary.
/dev/sdd2   ?   168689522  2104717761   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(20929, 28, 47)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(261131, 30, 42)
Partition 2 does not end on cylinder boundary.
/dev/sdd3   ?  1869881465  3805909656   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(231995, 28, 30)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(472197, 29, 39)
Partition 3 does not end on cylinder boundary.
/dev/sdd4   ?  2885681152  2885736650       27749+   d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(358024, 124, 25)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(358031, 109, 33)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order
ubuntu@ubuntu:~$ 

```

sudo parted /dev/sda print
```
ubuntu@ubuntu:~$ sudo parted /dev/sda print
Error: Can't have overlapping partitions.                                 
ubuntu@ubuntu:~$ 

```

I see what you mean. Will it be ok to use your partition attachment as it is? I'll need to continue with this tomorrow. It's well past midnight here in the UK. 

Thanks very much for your help so far.

---

### Post by caljohnsmith on 2009-02-18
> **Mylorharbour said:**
> 
I see what you mean. Will it be ok to use your partition attachment as it is? I'll need to continue with this tomorrow. It's well past midnight here in the UK. 

Thanks very much for your help so far.
Sure, you should be able to use the partition table from my previous post. Let me know how it goes when you have the chance to do it.

---

### Post by Mylorharbour on 2009-02-19
Ok, this is the output of *sudo sfdisk --no-reread -f /dev/sda  < ~/Desktop/partition_table.txt*


```
ubuntu@ubuntu:~$ sudo sfdisk --no-reread -f /dev/sda  < ~/Desktop/partition_table.txt

Disk /dev/sda: 30401 cylinders, 255 heads, 63 sectors/track
Old situation:
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+   7660    7661-  61536951    7  HPFS/NTFS
/dev/sda2       7661   30400   22740  182659050    5  Extended
		start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/sda3      29901   30400     500    4016250   82  Linux swap / Solaris
		start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/sda4          0       -       0          0    0  Empty
/dev/sda5       7661+  22111   14451- 116077594+  83  Linux
		start: (c,h,s) expected (1023,254,63) found (1023,2,1)
/dev/sda6      22112+  23402    1291-  10369926   83  Linux
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda7      23403+  24697    1295-  10402056   83  Linux
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda8      24698+  25979    1282-  10297633+  83  Linux
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda9      25980+  27273    1294-  10394023+  83  Linux
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda10     27274+  28569    1296-  10410088+  83  Linux
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda11     28570+  29856    1287-  10337796   83  Linux
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda12     29857+  29900      44-    353398+  83  Linux
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)
New situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *        63 123073964  123073902   7  HPFS/NTFS
/dev/sda2     123073965 488392064  365318100   5  Extended
/dev/sda3             0         -          0   0  Empty
/dev/sda4             0         -          0   0  Empty
/dev/sda5     480359565 488392064    8032500  82  Linux swap / Solaris
/dev/sda6     123074091 355229279  232155189  83  Linux
/dev/sda7     355229343 375969194   20739852  83  Linux
/dev/sda8     375969258 396773369   20804112  83  Linux
/dev/sda9     396773433 417368699   20595267  83  Linux
/dev/sda10    417368763 438156809   20788047  83  Linux
/dev/sda11    438156873 458977049   20820177  83  Linux
/dev/sda12    458977113 479652704   20675592  83  Linux
/dev/sda13    479652768 480359564     706797  83  Linux
Successfully wrote the new partition table

Re-reading the partition table ...
BLKRRPART: Device or resource busy
The command to re-read the partition table failed
Reboot your system now, before using mkfs

If you created or changed a DOS partition, /dev/foo7, say, then use dd(1)
to zero the first 512 bytes:  dd if=/dev/zero of=/dev/foo7 bs=512 count=1
(See fdisk(8).)
ubuntu@ubuntu:~$ 
```

I'll now reboot the LiveCD and post again

Cheers

---

### Post by Mylorharbour on 2009-02-19
Output of sudo fdisk -lu

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0007f86f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   123073964    61536951    7  HPFS/NTFS
/dev/sda2       123073965   488392064   182659050    5  Extended
/dev/sda5       480359565   488392064     4016250   82  Linux swap / Solaris
/dev/sda6       123074091   355229279   116077594+  83  Linux
/dev/sda7       355229343   375969194    10369926   83  Linux
/dev/sda8       375969258   396773369    10402056   83  Linux
/dev/sda9       396773433   417368699    10297633+  83  Linux
/dev/sda10      417368763   438156809    10394023+  83  Linux
/dev/sda11      438156873   458977049    10410088+  83  Linux
/dev/sda12      458977113   479652704    10337796   83  Linux
/dev/sda13      479652768   480359564      353398+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00010bde

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   976768064   488384001    5  Extended
/dev/sdb5             126   410235839   205117857   83  Linux
/dev/sdb6       410235903   976768064   283266081    7  HPFS/NTFS

Disk /dev/sdc: 4235 MB, 4235984896 bytes
2 heads, 63 sectors/track, 65661 cylinders, total 8273408 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0002ff07

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63     8273407     4136672+   b  W95 FAT32
ubuntu@ubuntu:~$ 
```

Output of sudo parted /dev/sda print

```
ubuntu@ubuntu:~$ sudo parted /dev/sda print
Model: ATA ST3250820AS (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  63.0GB  63.0GB  primary   ntfs         boot 
 2      63.0GB  250GB   187GB   extended                    
 6      63.0GB  182GB   119GB   logical   ext3              
 7      182GB   192GB   10.6GB  logical   ext3              
 8      192GB   203GB   10.7GB  logical   ext3              
 9      203GB   214GB   10.5GB  logical   ext3              
10      214GB   224GB   10.6GB  logical   ext3              
11      224GB   235GB   10.7GB  logical   ext3              
12      235GB   246GB   10.6GB  logical   ext3              
13      246GB   246GB   362MB   logical   ext3              
 5      246GB   250GB   4113MB  logical   linux-swap        

ubuntu@ubuntu:~$ 
```

---

### Post by caljohnsmith on 2009-02-19
It looks like your partition table is OK now, so hopefully that won't be a problem any more. I was looking over more carefully the previous boot info script results in post #7, and it looks like you have a dedicated Grub partition, is that true? Before we corrected your partition table, it was on sda12, and now it is on sda13. So is it safe to assume you want to use that to boot all your distros? If so, how about doing the following:
```

sudo grub
grub> root (hd0,12)
grub> setup (hd0)
grub> quit
sudo mount /dev/sda13 /mnt && gksudo gedit /mnt/boot/grub/menu.lst
```
And change the (hdX,Y) and sdaX references as shown highlighted in blue (you can just copy/paste it if you want into your menu.lst):
```
title		GRUB Partition Menu - Ubuntu Hardy Heron 8.04 in [COLOR="Blue"]sda9[/COLOR]
root		[COLOR="Blue"](hd0,8)[/COLOR]
kernel		/vmlinuz root=/dev/[COLOR="Blue"]sda9[/COLOR] ro quiet splash
initrd		/initrd.img
boot

title		Ubuntu Studio Intrepid Ibex 8.10 in sda7
root		(hd0,6)
kernel		/vmlinuz root=/dev/sda7 ro quiet splash
initrd		/initrd.img
boot

title		Ubuntu Studio Hardy Heron 8.04 in sda12
root		(hd0,11)
kernel		/vmlinuz root=/dev/sda12 ro quiet splash
initrd		/initrd.img
boot

title		Ubuntu Gutsy Gibbon 7.10 in [COLOR="Blue"]sda11[/COLOR]
root		[COLOR="Blue"](hd0,10)[/COLOR]
kernel		/vmlinuz root=/dev/[COLOR="Blue"]sda11[/COLOR] ro quiet splash
initrd		/initrd.img
boot

title		Kubuntu Hardy Heron 8.04 in [COLOR="Blue"]sda10[/COLOR]
root		[COLOR="Blue"](hd0,9)[/COLOR]
kernel		/vmlinuz root=/dev/[COLOR="Blue"]sda10[/COLOR] ro quiet splash
initrd		/initrd.img
boot

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		[COLOR="Blue"](hd0,10)[/COLOR]
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=4383047f-4b5e-4445-b139-f82ebcb71917 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		[COLOR="Blue"](hd0,10)[/COLOR]
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=4383047f-4b5e-4445-b139-f82ebcb71917 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		[COLOR="Blue"](hd0,10)[/COLOR]
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


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda10.
title		Ubuntu Hardy 8.04, kernel 2.6.24-16-generic (on /dev/[COLOR="Blue"]sda9[/COLOR])
root		[COLOR="Blue"](hd0,8)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=600a31e9-eece-4204-9e18-eb98c5f475c9 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/[COLOR="Blue"]sda9[/COLOR].
title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode) (on /dev/sda10)
root		[COLOR="Blue"](hd0,8)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=600a31e9-eece-4204-9e18-eb98c5f475c9 ro single 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda10.
title		Ubuntu 8.04, memtest86+ (on /dev/sda9)
root		[COLOR="Blue"](hd0,8)[/COLOR]
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda11.
title		Ubuntu 8.04, kernel 2.6.24-16-generic (on /dev/[COLOR="Blue"]sda9[/COLOR])
root		[COLOR="Blue"](hd0,8)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=8a3de09c-581d-4be1-b194-54e8feaf7e1f ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda11.
title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode) (on /dev/[COLOR="Blue"]sda9[/COLOR])
root		[COLOR="Blue"](hd0,8)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=8a3de09c-581d-4be1-b194-54e8feaf7e1f ro single 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda11.
title		Ubuntu 8.04, memtest86+ (on /dev/[COLOR="Blue"]sda9[/COLOR])
root		[COLOR="Blue"](hd0,8)[/COLOR]
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda12.
title		Ubuntu 8.04, kernel 2.6.24-16-generic (on /dev/sda12
root		(hd0,11)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=db15b278-9763-4601-96be-46890552ecdc ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda12.
title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode) (on /dev/sda12)
root		(hd0,11)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=db15b278-9763-4601-96be-46890552ecdc ro single 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda12.
title		Ubuntu 8.04, memtest86+ (on /dev/sda12)
root		(hd0,11)
kernel		/boot/memtest86+.bin  
savedefault
boot

```
Let me know how that goes or if you run into problems.

---

### Post by Mylorharbour on 2009-02-19
THANK YOU!!

You are a STAR!!

All's ok now would you believe. That's saved me an awful lot of time rebuilding my setup. Thanks again. Shame there's no eBay style feedback on here....:D

---

### Post by caljohnsmith on 2009-02-19
You're certainly welcome, and I'm glad it all worked OK; cheers and enjoy your multi-boot setup. :)

---

