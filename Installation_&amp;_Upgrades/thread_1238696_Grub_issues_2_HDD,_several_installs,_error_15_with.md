---
title: "Grub issues: 2 HDD, several installs, error 15 with boot partition ...  Help!!!"
date: 2009-08-12
forum: Installation &amp; Upgrades
---

### Post by nucleus_607 on 2009-08-12
Greetings,
    I've been trying to install Ubuntu Server for days now.  All other versions of Ubuntu have been installed without a hitch however when installing Server, I keep getting Error 15 from Grub.  My last attempt at install, I installed a separate Ext 2 Boot Partition on an 80 GB drive dedicated to Ubuntu Server as well as a 1.5 GB SWAP partition with the remaining drive space for Server itself.   I then copied the /boot/ DIR from the Server install into the Ext 2 boot partition and adjusted my previous menu.lst file to reflect the change in kernal and init locations.  In all of my configurations, I keep getting sync errors from init at best.  Is this due to not editing the server partitions fstab file?  can i direct the root of the kernels UUID to point to an init on another partion; more specifically: can I set the root partition to the Boot Partition and the kernel's root in the menu.lst file to point to the actual Server partions init* file?
      Below is the output  RESULTS.txt of the boot_info_script which I came across sifting through the forums.  Hopefully this will help wioth diagnosing the boot issues....it's been days and a half-dozen re-installs and still no luck!

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders, total 120103200 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x205d205d

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    31,503,464    31,503,402   7 HPFS/NTFS
/dev/sda2          31,503,465    87,763,094    56,259,630  83 Linux
/dev/sda3          87,763,095   120,101,939    32,338,845   f W95 Ext d (LBA)
/dev/sda5         114,961,140   120,101,939     5,140,800  82 Linux swap / Solaris
/dev/sda6          87,763,221   113,708,069    25,944,849  83 Linux
/dev/sda7         113,708,133   114,945,074     1,236,942  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9b259b25

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63     1,028,159     1,028,097  83 Linux
/dev/sdb2           1,028,160    80,292,869    79,264,710   5 Extended
/dev/sdb5           1,028,223    77,304,779    76,276,557  83 Linux
/dev/sdb6          77,304,843    80,292,869     2,988,027  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 4009 MB, 4009754624 bytes
255 heads, 63 sectors/track, 487 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0161a511

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63     7,831,551     7,831,489   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="3C100BED100BAD48" TYPE="ntfs" 
/dev/sda2: UUID="c0e780ea-73c3-47fd-b1d0-662e6989a76b" TYPE="ext3" 
/dev/sda5: UUID="2172bb1d-0fe9-4202-b612-826d189d2622" TYPE="swap" 
/dev/sda6: UUID="b9a902f2-ba38-401b-9e0e-03c283d987e1" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="7770be42-0ca6-4b6a-9955-1d8e39a997b0" TYPE="swap" 
/dev/sdb1: LABEL="BootPartition" UUID="6dde215c-1c67-4f78-b882-1c58f760f723" TYPE="ext2" 
/dev/sdb5: UUID="a7251ac2-213b-49bb-8afd-11f46f68c44a" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb6: UUID="9ce37448-b50a-4eaf-943b-ac0571594ceb" TYPE="swap" 
/dev/sdc1: LABEL="PDL" UUID="9070-B3AD" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-14-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/nucleus/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=nucleus)
/dev/sdc1 on /media/PDL type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)


=========================== sda2/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=b835f8c3-66e1-4a80-bbb9-093b57321d7e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b835f8c3-66e1-4a80-bbb9-093b57321d7e

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

title        Ubuntu 9.04, kernel 2.6.28-11-server
uuid        Hqhbk2-11X2-G2y5-WiN1-Z8U6-QoJr-I9xfNp
kernel        /boot/vmlinuz-2.6.28-11-server root=UUID=Hqhbk2-11X2-G2y5-WiN1-Z8U6-QoJr-I9xfNp ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-server
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-server (recovery mode)
uuid        Hqhbk2-11X2-G2y5-WiN1-Z8U6-QoJr-I9xfNp
kernel        /boot/vmlinuz-2.6.28-11-server root=UUID=Hqhbk2-11X2-G2y5-WiN1-Z8U6-QoJr-I9xfNp ro  single
initrd        /boot/initrd.img-2.6.28-11-server

title        Ubuntu 9.04, memtest86+
uuid        Hqhbk2-11X2-G2y5-WiN1-Z8U6-QoJr-I9xfNp
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows NT/2000/XP
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title        Ubuntu 9.04, kernel 2.6.28-14-generic (on /dev/sda2)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=c0e780ea-73c3-47fd-b1d0-662e6989a76b ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title        Kubuntu 9.04, kernel 2.6.28-14-generic (on /dev/sda2)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=b9a902f2-ba38-401b-9e0e-03c283d987e1 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode) (on /dev/sda2)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=c0e780ea-73c3-47fd-b1d0-662e6989a76b ro single 
initrd        /boot/initrd.img-2.6.28-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda2)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=c0e780ea-73c3-47fd-b1d0-662e6989a76b ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda2)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=c0e780ea-73c3-47fd-b1d0-662e6989a76b ro single 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title        Ubuntu 9.04, memtest86+ (on /dev/sda2)
root        (hd0,1)
kernel        /boot/memtest86+.bin  
savedefault
boot





=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=c0e780ea-73c3-47fd-b1d0-662e6989a76b /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=2172bb1d-0fe9-4202-b612-826d189d2622 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


  25.0GB: boot/grub/menu.lst
  25.0GB: boot/grub/stage2
  25.0GB: boot/initrd.img-2.6.28-11-generic
  25.1GB: boot/initrd.img-2.6.28-14-generic
  25.0GB: boot/vmlinuz-2.6.28-11-generic
  25.1GB: boot/vmlinuz-2.6.28-14-generic
  25.1GB: initrd.img
  25.0GB: initrd.img.old
  25.1GB: vmlinuz
  25.0GB: vmlinuz.old

=========================== sda6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=b9a902f2-ba38-401b-9e0e-03c283d987e1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b9a902f2-ba38-401b-9e0e-03c283d987e1

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

title        Kubuntu 9.04, kernel 2.6.28-11-generic
uuid        b9a902f2-ba38-401b-9e0e-03c283d987e1
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=b9a902f2-ba38-401b-9e0e-03c283d987e1 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        c0e780ea-73c3-47fd-b1d0-662e6989a76b
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=c0e780ea-73c3-47fd-b1d0-662e6989a76b ro  quiet splash
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, Server
root        (hd1,0)
kernel        /vmlinuz-2.6.28-11-server root=6dde215c-1c67-4f78-b882-1c58f760f723 ro quiet splash
initrd        /initrd.img-2.6.28-11-server

title        Ubuntu 9.04, Server Alt
root        (hd1,0)
kernel        /vmlinuz-2.6.28-11-server root=a7251ac2-213b-49bb-8afd-11f46f68c44a ro quiet splash
initrd        /initrd.img-2.6.28-11-server


title        Ubuntu 9.04, Server Alt3
root        (hd1,0)
kernel        /vmlinuz-2.6.28-11-server root=a7251ac2-213b-49bb-8afd-11f46f68c44a ro quiet splash
initrd        /boot/initrd.img-2.6.28-11-server

title        Ubuntu 9.04, Server Alt2
root        (hd1,4)
kernel        /boot/vmlinuz-2.6.28-11-server root=a7251ac2-213b-49bb-8afd-11f46f68c44a ro quiet splash
initrd        /boot/initrd.img-2.6.28-11-server root=a7251ac2-213b-49bb-8afd-11f46f68c44a

title        Ubuntu 9.04, memtest86+
uuid        c0e780ea-73c3-47fd-b1d0-662e6989a76b
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows XP Professional
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1



=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=b9a902f2-ba38-401b-9e0e-03c283d987e1 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=7770be42-0ca6-4b6a-9955-1d8e39a997b0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


  56.5GB: boot/grub/menu.lst
  56.5GB: boot/grub/stage2
  56.4GB: boot/initrd.img-2.6.28-11-generic
  56.4GB: boot/vmlinuz-2.6.28-11-generic
  56.4GB: initrd.img
  56.4GB: vmlinuz

============================= sdb1/grub/menu.lst: =============================

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
# kopt=root=UUID=a7251ac2-213b-49bb-8afd-11f46f68c44a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a7251ac2-213b-49bb-8afd-11f46f68c44a

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

title        Ubuntu 9.04, kernel 2.6.28-11-server
uuid        a7251ac2-213b-49bb-8afd-11f46f68c44a
kernel        /boot/vmlinuz-2.6.28-11-server root=UUID=a7251ac2-213b-49bb-8afd-11f46f68c44a ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-server

title        Ubuntu 9.04, kernel 2.6.28-11-server (recovery mode)
uuid        a7251ac2-213b-49bb-8afd-11f46f68c44a
kernel        /boot/vmlinuz-2.6.28-11-server root=UUID=a7251ac2-213b-49bb-8afd-11f46f68c44a ro  single
initrd        /boot/initrd.img-2.6.28-11-server

title        Ubuntu 9.04, memtest86+
uuid        a7251ac2-213b-49bb-8afd-11f46f68c44a
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title        Ubuntu 9.04, memtest86+ (on /dev/sda2)
root        
kernel        /boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Kubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda6)
root        
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=b9a902f2-ba38-401b-9e0e-03c283d987e1 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu 9.04, memtest86+ (on /dev/sda6)
root        
kernel        /boot/memtest86+.bin  
savedefault
boot


=================== sdb1: Location of files loaded by Grub: ===================


    .2GB: grub/menu.lst
    .0GB: initrd.img-2.6.28-11-server
    .0GB: vmlinuz-2.6.28-11-server

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
# kopt=root=UUID=a7251ac2-213b-49bb-8afd-11f46f68c44a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a7251ac2-213b-49bb-8afd-11f46f68c44a

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

title        Ubuntu 9.04, kernel 2.6.28-11-server
uuid        a7251ac2-213b-49bb-8afd-11f46f68c44a
kernel        /boot/vmlinuz-2.6.28-11-server root=UUID=a7251ac2-213b-49bb-8afd-11f46f68c44a ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-server

title        Ubuntu 9.04, kernel 2.6.28-11-server (recovery mode)
uuid        a7251ac2-213b-49bb-8afd-11f46f68c44a
kernel        /boot/vmlinuz-2.6.28-11-server root=UUID=a7251ac2-213b-49bb-8afd-11f46f68c44a ro  single
initrd        /boot/initrd.img-2.6.28-11-server

title        Ubuntu 9.04, memtest86+
uuid        a7251ac2-213b-49bb-8afd-11f46f68c44a
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title        Ubuntu 9.04, memtest86+ (on /dev/sda2)
root        
kernel        /boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Kubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda6)
root        
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=b9a902f2-ba38-401b-9e0e-03c283d987e1 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu 9.04, memtest86+ (on /dev/sda6)
root        
kernel        /boot/memtest86+.bin  
savedefault
boot


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=a7251ac2-213b-49bb-8afd-11f46f68c44a /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=9ce37448-b50a-4eaf-943b-ac0571594ceb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


   4.8GB: boot/grub/menu.lst
   4.9GB: boot/initrd.img-2.6.28-11-server
   4.8GB: boot/vmlinuz-2.6.28-11-server
   4.9GB: initrd.img
   4.8GB: vmlinuz
```

---

### Post by oldfred on 2009-08-12
This page has some of the best explanations of Grub errors and how to resolve them.
[http://members.iinet.net.au/~herman546/p15.html#15]("http://members.iinet.net.au/%7Eherman546/p15.html#15")

One of your menu.lst has a UUID that does not exist? Was this before you changed partitions? Any changes will renumber UUIDs and force you to manually change many entries in your menu.lst
uuid        Hqhbk2-11X2-G2y5-WiN1-Z8U6-QoJr-I9xfNp

I think you need to check which drive your BIOS is booting from and reinstall GRUB into that MBR so it can point to the correct boot partition.

---

