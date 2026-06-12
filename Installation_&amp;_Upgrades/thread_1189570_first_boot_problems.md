---
title: "first boot problems"
date: 2009-06-16
forum: Installation &amp; Upgrades
---

### Post by kenglishj on 2009-06-16
i am installing ubuntu studio with all 4 extra features enabled. installation CD completed successfully, it next told me to reboot, which i did. here is where my problem comes in:
 
the first time i boot up the grub command line shows up. from here i told it to reboot because i did install it so that it would go to the graphic interface, not a command line
 
after rebooting, it goes into the graphic interface and checks installation. after this it says it is checking the partitions when a pop up shows saying:
"some of the partitions you created are too small. please make the following partitions at least this large (in bytes):
 
/ 2021574144
 
if you choose not to go back to the partitioner and increase the size of these partitions, the installation may fail"
 
**why is this error message coming up? why every other time does it go to grub command line?**
 
 

some background info: 
[LIST]
[*]i am dual booting
[*]i am booting off of an external hard drive, 2 partitions for Linux
[*]30 GB Linux-swap
[*]20 GB ext3: this partition i specified as the root drive in the install CD
[*]both partitions created and edited in gparted on the latest ubuntu live CD
[*]my local hard drive is GB allocated to windows PX. on gparted it shows i have 7 megs of unallocated space, but when going through the install, nothing showed up except for the main partition on this drive
[/LIST]any help is greatly appreciated :3

---

### Post by presence1960 on 2009-06-16
well first off 30 Gb for swap is way, way, way too much. Hopefully that is a typo. Let's see what you have. Boot off the Live CD, when the desktop loads download to your desktop Boot Info Script from here: [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
Open a terminal and run this command : ```
sudo bash ~/Desktop/boot_info_script*.sh
```
This will create a RESULTS.txt file on your desktop. Paste the contents of that file back here. Once pasted highlight all text and click # on the toolbar to place code tags around the text. This will show us more info about your setup.

**make sure your Ubuntu external drive is plugged in when you do this please.**

P.S. Swap should generally be 1 to 1.5 times your RAM. If you want to use suspend or hibernate you need at least as much swap as RAM.

---

### Post by kenglishj on 2009-06-17
ok here is the code. swap is 3, not 30 and i changed the unalocated space on the main drive into just another partition to see if that would do anything, nothing happened

```
============================= Boot Info Summary: ==============================

 => ThinkPad is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /BOOT.INI /ntldr /ntdetect.com /wubildr.mbr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/menu.lst /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/disks/root.disk

sdb2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcccdcccd

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    78,125,039    78,124,977   7 HPFS/NTFS
/dev/sda2          78,125,040    78,140,159        15,120   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5c74ae42

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   377,495,369   377,495,307   c W95 FAT32 (LBA)
/dev/sdb2         377,495,370   383,792,849     6,297,480  82 Linux swap / Solaris
/dev/sdb3    *    383,792,850   425,738,564    41,945,715  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="44FC2C88FC2C75F8" LABEL="Local Disk" TYPE="ntfs" 
/dev/sda2: UUID="3654549F1AACBF2B" TYPE="ntfs" 
/dev/sdb1: LABEL="TACI" UUID="EE4D-4942" TYPE="vfat" 
/dev/sdb2: UUID="c808e470-a03d-4075-a780-5b14a49b288a" TYPE="swap" 
/dev/sdb3: UUID="7d9adcfb-38c8-4ac2-91dd-57fdc3f91d68" SEC_TYPE="ext2" TYPE="ext3" 

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
/dev/sdb1 on /media/TACI type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)


================================ sda1/BOOT.INI: ================================

[boot loader] 
timeout=10 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\wubildr.mbr = "Ubuntu" 

======================== sdb1/ubuntu/winboot/menu.lst: ========================

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
    find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
    configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
    fallback 2
    find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
    configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
    fallback 3
    find --set-root --ignore-floppies /menu.lst
    configfile /menu.lst

title find /boot/grub/menu.lst
    fallback 4
    find --set-root --ignore-floppies /boot/grub/menu.lst
    configfile /boot/grub/menu.lst

title find /grub/menu.lst
    fallback 5
    find --set-root --ignore-floppies /grub/menu.lst
    configfile /grub/menu.lst

title commandline
    commandline

title reboot
    reboot

title halt
    halt

================================== sdb1 Wubi: ==================================

ubuntu/boot/root.disk was found, but could not be mounted

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=7d9adcfb-38c8-4ac2-91dd-57fdc3f91d68 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7d9adcfb-38c8-4ac2-91dd-57fdc3f91d68

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

title        Ubuntu 9.04, kernel 2.6.28-3-rt
uuid        7d9adcfb-38c8-4ac2-91dd-57fdc3f91d68
kernel        /boot/vmlinuz-2.6.28-3-rt root=UUID=7d9adcfb-38c8-4ac2-91dd-57fdc3f91d68 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-3-rt
quiet

title        Ubuntu 9.04, kernel 2.6.28-3-rt (recovery mode)
uuid        7d9adcfb-38c8-4ac2-91dd-57fdc3f91d68
kernel        /boot/vmlinuz-2.6.28-3-rt root=UUID=7d9adcfb-38c8-4ac2-91dd-57fdc3f91d68 ro  single
initrd        /boot/initrd.img-2.6.28-3-rt

title        Ubuntu 9.04, memtest86+
uuid        7d9adcfb-38c8-4ac2-91dd-57fdc3f91d68
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdb3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb3 during installation
UUID=7d9adcfb-38c8-4ac2-91dd-57fdc3f91d68 /               ext3    relatime,errors=remount-ro 0       1
/dev/sdb2       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb3: Location of files loaded by Grub: ===================


 214.7GB: boot/grub/menu.lst
 214.7GB: boot/grub/stage2
 214.8GB: boot/initrd.img-2.6.28-3-rt
 214.8GB: boot/vmlinuz-2.6.28-3-rt
 214.8GB: initrd.img
 214.8GB: vmlinuz
=============================== StdErr Messages: ===============================

mount: you must specify the filesystem type
umount: /tmp/BootInfo/Wubi: not mounted
umount: /tmp/BootInfo/Wubi: not mounted

```thanks

---

### Post by presence1960 on 2009-06-17
what is that first partition on your external drive? It says it has a wubu menu.lst on it & it can't be mounted. Did you try installing wubi as well? It looks like you did that as well as an install on a partition!

Try this first, boot into windows and uninstall wubi from Control Panel Add & Remove programs. It will say Ubuntu and uninstalls like any other Windows software. When that is completed then try booting up again and see what happens.

If you can't get it up in the worst case scenario you can format your external drive, make new partitions and try the install again. Here are some links to help you out:

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html) - for a free pdf Ubuntu pocketguide which has an excellent step by step on installing ubuntu.

I would suggest that you read and absorb as much as you can before undertaking an operation such as installing a new OS. You should have all your ducks in a row and basically understand what it is you are going to do before you attempt to do it.

---

### Post by kenglishj on 2009-06-17
the first partition is data i have for windows - files and things like that. does ubuntu need to boot from the first partition then?

i do not believe i did anything to install wubi, unless it tried to without telling me so.
.....actualy, its possible that i did... about a month ago i tried to install ubuntu inside windows. it got stuck at one spot for quite a while so i stopped it, im not sure if i ever deleted it. let me check, haha, stupid me

thanks for the help, i will try this out and see what happens :)

---

### Post by kenglishj on 2009-06-17
that was it, thanks for the help! :D

---

### Post by presence1960 on 2009-06-17
here's how i know you installed wubi- this is from the results you posted:

```
=============================== sda1/BOOT.INI:==============================

[boot loader] 
timeout=10 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\wubildr.mbr = "Ubuntu" 

```

---

### Post by presence1960 on 2009-06-17
> **kenglishj said:**
> that was it, thanks for the help! :D

Enjoy Ubuntu!

---

### Post by kenglishj on 2009-06-17
thanks :3

after i select ubuntu from the boot menu, every other time i boot up the grub comand line shows up... any idea on how to fix this or atleast what to type in so it continues to ubuntu?

---

