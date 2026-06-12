---
title: "Grub cannot find Vista partition"
date: 2009-02-07
forum: Installation &amp; Upgrades
---

### Post by swatsbiz on 2009-02-07
Hi,

I have a multi-hdd, multi partitioned setup, and I can't seem to get Grub to add the Vista install into the boot menu.

I have run the boot info script, and here's the output from that:

> ============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on boot drive #3 in 
    partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdc5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

sdc6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd109d73d

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    84,293,054    84,292,992   7 HPFS/NTFS
/dev/sda2          84,293,055   312,576,704   228,283,650   f W95 Ext d (LBA)
/dev/sda5          84,293,118   312,576,704   228,283,587   7 HPFS/NTFS


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4c984c97

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    81,915,434    81,915,372   7 HPFS/NTFS
/dev/sdb2          81,915,435   230,275,709   148,360,275   f W95 Ext d (LBA)
/dev/sdb5          81,915,498   163,830,869    81,915,372   7 HPFS/NTFS
/dev/sdb6         163,830,933   227,255,489    63,424,557   7 HPFS/NTFS
/dev/sdb7         227,255,553   230,275,709     3,020,157  82 Linux swap / Solaris
/dev/sdb3         230,275,710   312,576,704    82,300,995  83 Linux


Drive sdc: _____________________________________________________________________

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9c309c30

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    39,070,079    39,070,017   7 HPFS/NTFS
/dev/sdc2          39,070,080   234,420,479   195,350,400   f W95 Ext d (LBA)
/dev/sdc5    *     39,070,143   117,210,239    78,140,097   7 HPFS/NTFS
/dev/sdc6         117,210,303   234,420,479   117,210,177  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="6E90F35790F323ED" LABEL="Music Drive" TYPE="ntfs" 
/dev/sda5: UUID="E0941B6F941B4784" LABEL="largest of" TYPE="ntfs" 
/dev/sdb1: UUID="1CD47505D474E306" LABEL="XP Play" TYPE="ntfs" 
/dev/sdb3: UUID="2ff6adfa-faa5-46ce-85fd-12d584847136" TYPE="ext3" 
/dev/sdb5: UUID="8C0C8E570C8E3BE8" LABEL="40gb Fast 1" TYPE="ntfs" 
/dev/sdb6: UUID="44A0FF46A0FF3D4C" LABEL="71Gb Fast" TYPE="ntfs" 
/dev/sdb7: UUID="af1429af-e611-4b29-b272-74990fbe9499" TYPE="swap" 
/dev/sdc1: UUID="01C82974019BEC00" LABEL="Old Program" TYPE="ntfs" 
/dev/sdc5: UUID="7CD8EBDDD8EB9424" LABEL="SATA Windows" TYPE="ntfs" 
/dev/sdc6: UUID="bb6aa41b-26e5-47d9-bb6a-a5a0504da6ce" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sdb3 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
/dev/sdc6 on /home type ext3 (rw,relatime)
/dev/sdb5 on /media/40gb_Fast_1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb6 on /media/71Gb_Fast type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1 on /media/Music_Drive type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc1 on /media/Old_Program type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc5 on /media/SATA_Windows type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /media/XP_Play type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5 on /media/largest_of type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/david/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=david)

=========================== sdb3/boot/grub/menu.lst: ===========================

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
color cyan/blue white/blue

#A splash image for the menu
splashimage=/boot/grub/splashimages/29962-grubuntu.xpm.gz

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=2ff6adfa-faa5-46ce-85fd-12d584847136 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=2ff6adfa-faa5-46ce-85fd-12d584847136

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
# defoptions=quiet vga=792 splash

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
# howmany=2

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		2ff6adfa-faa5-46ce-85fd-12d584847136
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=2ff6adfa-faa5-46ce-85fd-12d584847136 ro quiet vga=792 splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		2ff6adfa-faa5-46ce-85fd-12d584847136
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=2ff6adfa-faa5-46ce-85fd-12d584847136 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		2ff6adfa-faa5-46ce-85fd-12d584847136
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=2ff6adfa-faa5-46ce-85fd-12d584847136 ro quiet vga=792 splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		2ff6adfa-faa5-46ce-85fd-12d584847136
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=2ff6adfa-faa5-46ce-85fd-12d584847136 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, memtest86+
uuid		2ff6adfa-faa5-46ce-85fd-12d584847136
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Windows NT/2000/XP (loader)
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista Ultimate (loader)
root		(hd0,1)
savedefault
makeactive
map		(hd1) (hd0)
map		(hd0) (hd1)
chainloader	+1


=============================== sdb3/etc/fstab: ===============================


proc /proc proc defaults 0 0
UUID=2ff6adfa-faa5-46ce-85fd-12d584847136 / ext3 relatime,errors=remount-ro 0 1
UUID=bb6aa41b-26e5-47d9-bb6a-a5a0504da6ce /home ext3 relatime 0 2
UUID=8C0C8E570C8E3BE8 /media/40gb_Fast_1 ntfs-3g defaults,locale=en_GB.UTF-8,force 0 0
UUID=44A0FF46A0FF3D4C /media/71Gb_Fast ntfs-3g defaults,locale=en_GB.UTF-8,force 0 0
UUID=6E90F35790F323ED /media/Music_Drive ntfs-3g defaults,locale=en_GB.UTF-8,force 0 0
UUID=01C82974019BEC00 /media/Old_Program ntfs-3g defaults,locale=en_GB.UTF-8,force 0 0
UUID=7CD8EBDDD8EB9424 /media/SATA_Windows ntfs-3g defaults,locale=en_GB.UTF-8,force 0 0
UUID=1CD47505D474E306 /media/XP_Play ntfs-3g defaults,locale=en_GB.UTF-8,force 0 0
UUID=E0941B6F941B4784 /media/largest_of ntfs-3g defaults,locale=en_GB.UTF-8,force 0 0
UUID=af1429af-e611-4b29-b272-74990fbe9499 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

//AITKENS_HOME/mss-14588    /mnt/Maxtor Church        cifs    guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

=================== sdb3: Location of files loaded by Grub: ===================


 124.6GB: boot/grub/menu.lst
 124.6GB: boot/grub/stage2
 124.6GB: boot/initrd.img-2.6.27-11-generic
 124.7GB: boot/initrd.img-2.6.27-7-generic
 124.6GB: boot/initrd.img-2.6.27-9-generic
 124.7GB: boot/vmlinuz-2.6.27-11-generic
 124.7GB: boot/vmlinuz-2.6.27-7-generic
 124.7GB: boot/vmlinuz-2.6.27-9-generic
 124.6GB: initrd.img
 124.6GB: initrd.img.old
 124.7GB: vmlinuz
 124.7GB: vmlinuz.old

================================ sdc1/boot.ini: ================================

[boot loader]

timeout=3

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows Work" /fastdetect /noexecute=optin /numproc=2

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional Work" 


=======Devices which don't seem to have a corresponding hard drive==============

 sdd .
 sde .


how should be Grub be setup for allowing Vista to boot?

many thanks
David

---

### Post by caljohnsmith on 2009-02-07
Do you know which HDD you are booting on start up? You have Grub installed to the MBR of both your sda and sdc drives, so it is ambiguous which drive you are booting. Also, it looks like Vista is on sdb1, yet Vista's boot files are on sda1. If you are booting the sda drive on start up, if you are lucky the following Vista entry might work:
```
title Windows Vista
root (hd0,0)
chainloader +1
```
If that doesn't work, then I would recommend following [meierfra's tutorial]("http://ubuntuforums.org/showpost.php?p=5726832") for how to restore Vista's boot files to its sdb1 partition, and then you can boot Vista from sdb1. Also, can you change your BIOS to boot the sdb drive on start up? If so, that would help simplify things, because you could install Grub to the MBR of sdb, and then your drives will be independent of each other when it comes to booting. If you want help with that let me know. Otherwise, if you have trouble with the tutorial, it's probably best to post to that thread since meierfra is much more qualified than I am to help you with it. Good luck and let me know how it goes.

---

### Post by swatsbiz on 2009-02-08
How simple was that solution, thank you very much!

---

