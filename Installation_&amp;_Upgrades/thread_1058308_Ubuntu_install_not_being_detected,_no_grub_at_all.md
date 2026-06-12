---
title: "Ubuntu install not being detected, no grub at all"
date: 2009-02-02
forum: Installation &amp; Upgrades
---

### Post by j.biddy on 2009-02-02
I've been running Ubuntu 8.04 (now 8.10) on my laptop for some time quite successfully. I recently decided to install it on my Desktop (dual-boot with XP). The installation itself went over without a hitch, however when the system is restarted or turned on no grub appears and the system immediately boots XP. I've tried using the Live CD and installing grub and that doesn't seem to be doing the job either. XP and Ubuntu are installed on different physical drives, though as I understand it that should not be a problem.

System specs:
Athlon XP 2500+ (OC to 2.0 Ghz, 200x10)
Abit NF7-S v2.0 (nForce2 Ultra 400)
1.0 GB DDR
Radeon X850 
Maxtor 80GB IDE (XP Partion)
WD 120 GB SATA
WD 160 GB IDE (30 GB Ubuntu partition, swap, 120 GB FAT32 partition)
Seagate 200 GB IDE

---

### Post by Crafty Kisses on 2009-02-02
You said you had Ubuntu installed on a different drive, so what you should do is from the BIOS, switch the boot order of your HD's, and make the one Ubuntu's on the primary.

---

### Post by j.biddy on 2009-02-02
Changed first boot to HDD3 and still no dice. I guess I'll try reinstalling grub again.

---

### Post by j.biddy on 2009-02-02
I reinstalled grub to hdd3 and still no luck.

---

### Post by caljohnsmith on 2009-02-02
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by j.biddy on 2009-02-02
Here it is:
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #4 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Grub0.97 is installed in the MBR of /dev/sdd and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdc1 has 
                       390719487 sectors, but according to the info from 
                       fdisk, it has 390721905 sectors.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdd2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x13ce13cd

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   234,436,544   234,436,482   7 HPFS/NTFS


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 80.0 GB, 80054059008 bytes
255 heads, 63 sectors/track, 9732 cylinders, total 156355584 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0c2c8fce

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   156,344,579   156,344,517   7 HPFS/NTFS


Drive sdc: _____________________________________________________________________

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
16 heads, 63 sectors/track, 387621 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf08964c0

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   390,721,967   390,721,905  42 SFS


Drive sdd: _____________________________________________________________________

Disk /dev/sdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0942cd58

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63    51,568,649    51,568,587  83 Linux
/dev/sdd2          51,568,650   312,576,704   261,008,055   5 Extended
/dev/sdd5          51,568,713    56,709,449     5,140,737  82 Linux swap / Solaris
/dev/sdd6          56,709,513   312,576,704   255,867,192   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="54E8C835E8C81760" LABEL="Shoties" TYPE="ntfs" 
/dev/sdb1: UUID="DC7090BB70909DB8" TYPE="ntfs" 
/dev/sdc1: UUID="80C8613EC8613416" LABEL="Da" TYPE="ntfs" 
/dev/sdd1: UUID="93d51bce-1cbe-4aab-943d-8ebb8f2f231d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdd5: UUID="0ee6d54f-e154-4c18-abae-6d2cbd8d2932" TYPE="swap" 
/dev/sdd6: UUID="F070-62CC" TYPE="vfat" 
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

default=multi(0)disk(0)rdisk(2)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(2)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


================================ sdb1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer


=========================== sdd1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=93d51bce-1cbe-4aab-943d-8ebb8f2f231d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=93d51bce-1cbe-4aab-943d-8ebb8f2f231d

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
uuid		93d51bce-1cbe-4aab-943d-8ebb8f2f231d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=93d51bce-1cbe-4aab-943d-8ebb8f2f231d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		93d51bce-1cbe-4aab-943d-8ebb8f2f231d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=93d51bce-1cbe-4aab-943d-8ebb8f2f231d ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		93d51bce-1cbe-4aab-943d-8ebb8f2f231d
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
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


=============================== sdd1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdd1
UUID=93d51bce-1cbe-4aab-943d-8ebb8f2f231d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdd6
UUID=F070-62CC  /windows        vfat    utf8,umask=007,gid=46 0       1
# /dev/sdd5
UUID=0ee6d54f-e154-4c18-abae-6d2cbd8d2932 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdd1: Location of files loaded by Grub: ===================


    .7GB: boot/grub/menu.lst
    .7GB: boot/grub/stage2
    .5GB: boot/initrd.img-2.6.27-7-generic
    .5GB: boot/vmlinuz-2.6.27-7-generic
    .5GB: initrd.img
    .5GB: vmlinuz

```

---

### Post by caljohnsmith on 2009-02-02
J.biddy, it looks like you have Grub correctly installed to the MBR (Master Boot Record) of your Ubuntu sdd drive, so can you change your BIOS to boot the Ubuntu drive on start up? If so, I think that should solve your problem.

---

### Post by j.biddy on 2009-02-03
I guess I misread which HDD the Ubuntu install was on. Changed HDD2 to boot first and everything works fine now, thanks all who helped me out!

---

