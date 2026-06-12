---
title: "dual boot Vista &amp; Ubuntu,wont start VIsta need Help!"
date: 2009-10-07
forum: Installation &amp; Upgrades
---

### Post by livlizard on 2009-10-07
this is my first time i using linux..before,i use vista,i wanna create dual boot but i cant start vista after install ubuntu 9.04..every time i choose "Window Vista (Loader)" in booting menu:
starting up
grub stage2...

and go back to booting menu again

need help pliss :(

this is my boot_script result

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda2 and 
                       looks at sector 7225407 on boot drive #2 for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

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

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfe8a98b0

Partition  Boot         Start           End          Size  Id System

/dev/sda1              16,065   163,830,869   163,814,805   f W95 Ext d (LBA)
/dev/sda5              16,128   102,414,374   102,398,247   7 HPFS/NTFS
/dev/sda6         102,414,438   163,830,869    61,416,432   7 HPFS/NTFS
/dev/sda2    *    163,842,048   471,042,047   307,200,000   7 HPFS/NTFS
/dev/sda3         471,042,048   976,771,071   505,729,024   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4ebc4ebb

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    40,965,749    40,965,687  83 Linux
/dev/sdb2          40,965,750   312,560,639   271,594,890   f W95 Ext d (LBA)
/dev/sdb5          40,965,813    61,448,624    20,482,812   7 HPFS/NTFS
/dev/sdb6          61,448,688   163,846,934   102,398,247   7 HPFS/NTFS
/dev/sdb7         163,846,998   245,762,369    81,915,372   7 HPFS/NTFS
/dev/sdb8         245,762,433   312,560,639    66,798,207   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda3: UUID="1A96F38F96F36A21" LABEL="Document" TYPE="ntfs" 
/dev/sda5: UUID="FC58BD2858BCE316" LABEL="Vista" TYPE="ntfs" 
/dev/sda6: UUID="DAB85BD2B85BABAF" LABEL="XP" TYPE="ntfs" 
/dev/sdb1: UUID="d6678e0b-e4f5-4524-b21b-dc17145c53d4" TYPE="ext2" 
/dev/sdb5: UUID="FAA4FF74A4FF322D" LABEL="Software" TYPE="ntfs" 
/dev/sdb6: UUID="D42C03772C035440" LABEL="Document" TYPE="ntfs" 
/dev/sdb7: UUID="1C640DE5640DC28E" LABEL="Games" TYPE="ntfs" 
/dev/sdb8: UUID="E670164F701626B9" LABEL="Back Up" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sdb1 on / type ext2 (rw,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/akbar/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=akbar)
/dev/sdb6 on /media/Document type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda3 on /media/Document_ type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


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
# kopt=root=UUID=d6678e0b-e4f5-4524-b21b-dc17145c53d4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d6678e0b-e4f5-4524-b21b-dc17145c53d4

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        d6678e0b-e4f5-4524-b21b-dc17145c53d4
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=d6678e0b-e4f5-4524-b21b-dc17145c53d4 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        d6678e0b-e4f5-4524-b21b-dc17145c53d4
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=d6678e0b-e4f5-4524-b21b-dc17145c53d4 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        d6678e0b-e4f5-4524-b21b-dc17145c53d4
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista
root    (hd0,0)
savedefault
makeactive
chainloader    +1


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
UUID=d6678e0b-e4f5-4524-b21b-dc17145c53d4 /               ext2    errors=remount-ro 0       1
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


   3.6GB: boot/grub/menu.lst
   3.6GB: boot/grub/stage2
   3.6GB: boot/initrd.img-2.6.28-11-generic
   3.6GB: boot/vmlinuz-2.6.28-11-generic
   3.6GB: initrd.img
   3.6GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  98 ff ff ff 6e 6b 20 10  8e c1 41 35 7d fe c6 01  |....nk ...A5}...|
00000010  00 00 00 00 90 a8 07 00  00 00 00 00 00 00 00 00  |................|
00000020  ff ff ff ff ff ff ff ff  01 00 00 00 e8 92 11 00  |................|
00000030  58 bb 00 00 ff ff ff ff  00 00 00 00 00 00 00 00  |X...............|
00000040  12 00 00 00 4e 00 00 00  d5 06 00 00 15 00 00 00  |....N...........|
00000050  50 43 49 23 56 45 4e 5f  38 30 38 36 26 44 45 56  |PCI#VEN_8086&DEV|
00000060  5f 37 31 32 32 00 00 00  d8 ff ff ff 76 6b 09 00  |_7122.......vk..|
00000070  4e 00 00 00 90 92 11 00  01 00 00 00 01 00 00 00  |N...............|
00000080  43 6c 61 73 73 47 55 49  44 00 00 00 00 00 00 00  |ClassGUID.......|
00000090  a8 ff ff ff 7b 00 34 00  44 00 33 00 36 00 45 00  |....{.4.D.3.6.E.|
000000a0  39 00 37 00 44 00 2d 00  45 00 33 00 32 00 35 00  |9.7.D.-.E.3.2.5.|
000000b0  2d 00 31 00 31 00 43 00  45 00 2d 00 42 00 46 00  |-.1.1.C.E.-.B.F.|
000000c0  43 00 31 00 2d 00 30 00  38 00 30 00 30 00 32 00  |C.1.-.0.8.0.0.2.|
000000d0  42 00 45 00 31 00 30 00  33 00 31 00 38 00 7d 00  |B.E.1.0.3.1.8.}.|
000000e0  00 00 00 00 00 00 00 00  f8 ff ff ff 68 92 11 00  |............h...|
000000f0  98 ff ff ff 6e 6b 20 10  8e c1 41 35 7d fe c6 01  |....nk ...A5}...|
00000100  00 00 00 00 90 a8 07 00  00 00 00 00 00 00 00 00  |................|
00000110  ff ff ff ff ff ff ff ff  01 00 00 00 d8 93 11 00  |................|
00000120  58 bb 00 00 ff ff ff ff  00 00 00 00 00 00 00 00  |X...............|
00000130  12 00 00 00 4e 00 00 00  d6 06 00 00 15 00 00 00  |....N...........|
00000140  50 43 49 23 56 45 4e 5f  38 30 38 36 26 44 45 56  |PCI#VEN_8086&DEV|
00000150  5f 37 31 32 34 00 00 00  d8 ff ff ff 76 6b 09 00  |_7124.......vk..|
00000160  4e 00 00 00 80 93 11 00  01 00 00 00 01 00 00 00  |N...............|
00000170  43 6c 61 73 73 47 55 49  44 00 00 00 00 00 00 00  |ClassGUID.......|
00000180  a8 ff ff ff 7b 00 34 00  44 00 33 00 36 00 45 00  |....{.4.D.3.6.E.|
00000190  39 00 37 00 44 00 2d 00  45 00 33 00 32 00 35 00  |9.7.D.-.E.3.2.5.|
000001a0  2d 00 31 00 31 00 43 00  45 00 2d 00 42 00 46 00  |-.1.1.C.E.-.B.F.|
000001b0  43 00 31 00 2d 00 30 00  38 00 30 00 30 00 00 01  |C.1.-.0.8.0.0...|
000001c0  01 01 07 fe ff ff 3f 00  00 00 27 79 1a 06 00 fe  |......?...'y....|
000001d0  ff ff 05 fe ff ff 66 79  1a 06 2f 24 a9 03 00 00  |......fy../$....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by zvacet on 2009-10-08
In terminal type 

```
gksudo gedit /boot/grub/menu.lst
```
 
and replace

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title Windows Vista
root (hd0,0)
savedefault
makeactive
chainloader +1

with 

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda5
title Windows Vista
root (hd0,4)
savedefault
makeactive
chainloader +1

---

### Post by livlizard on 2009-10-09
> **zvacet said:**
> In terminal type 

```
gksudo gedit /boot/grub/menu.lst
```
 
and replace

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title Windows Vista
root (hd0,0)
savedefault
makeactive
chainloader +1

with 

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda5
title Windows Vista
root (hd0,4)
savedefault
makeactive
chainloader +1

it doesn't work,but i fix my boot loader with window vista cd(startup repair)
now i wanna reinstall ubuntu

anyway,thanks for the help :)

---

### Post by Bartender on 2009-10-09
Unless you're absolutely sure the install CD is good, i'd suggest downloading a fresh copy or burning another CD.  Use good quality CD-R, burn it slow.

---

