---
title: "Dual Booting XP and 9.04"
date: 2009-07-06
forum: Installation &amp; Upgrades
---

### Post by pageone on 2009-07-06
[SIZE=3]I sure could use some help getting this to work.  I have tried a number of different combinations, all to no avail.  Ubuntu boots just fine.  

Here is results of fdisk -l[/SIZE]

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00033726

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15298   122881153+  fd  Linux raid autodetect
/dev/sda2           15299       30596   122881185   fd  Linux raid autodetect
/dev/sda3           30597       45894   122881185   fd  Linux raid autodetect
/dev/sda4           45895       60801   119740477+  fd  Linux raid autodetect

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00033726

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       15298   122881153+  fd  Linux raid autodetect
/dev/sdb2           15299       30596   122881185   fd  Linux raid autodetect
/dev/sdb3           30597       45894   122881185   fd  Linux raid autodetect
/dev/sdb4           45895       60801   119740477+  fd  Linux raid autodetect

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ad3bc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        4462    35840983+   7  HPFS/NTFS
/dev/sdc2            4463        4468       48195   83  Linux
/dev/sdc3            4469        8292    30716280   83  Linux
/dev/sdc4            8293       38913   245963182+   5  Extended
/dev/sdc5            8293       10843    20490844+  82  Linux swap / Solaris
/dev/sdc6           11864       24866   104446566    b  W95 FAT32
/dev/sdc7           24867       38913   112832496    b  W95 FAT32

[SIZE=3]The drives sda and sdb are a RAID setup for data only (SATA drives).  Therefore, I am booting from sdc (a PATA drive).
[/SIZE]
[SIZE=3]Here is a copy of my menu.lst.  The only change I made was the timeout time.[/SIZE]

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
timeout        30

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
# kopt=root=UUID=cc751e5b-a063-4d73-a58b-a3e40f366345 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=52884e7c-c458-457d-b56f-ae5bd27704b6

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
uuid        52884e7c-c458-457d-b56f-ae5bd27704b6
kernel        /vmlinuz-2.6.28-11-generic root=UUID=cc751e5b-a063-4d73-a58b-a3e40f366345 ro quiet splash 
initrd        /initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        52884e7c-c458-457d-b56f-ae5bd27704b6
kernel        /vmlinuz-2.6.28-11-generic root=UUID=cc751e5b-a063-4d73-a58b-a3e40f366345 ro  single
initrd        /initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        52884e7c-c458-457d-b56f-ae5bd27704b6
kernel        /memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title        Microsoft Windows XP Professional
rootnoverify    (hd2,0)
savedefault
makeactive
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader    +1

[SIZE=3]I installed Ubuntu first, and then Win XP[/SIZE].[SIZE=3]  Win XP booted fine.  From there I reloaded the MBR from grub.   Now Win XP won't load.
 [/SIZE]
[SIZE=3]Any help you can give me is greatly appreciated.[/SIZE]

---

### Post by ronparent on 2009-07-06
With what grub instructions did you rewrite the mbr? Which is the first disk in your bios boot order? What does the grub command **find /boot/grub/stage1 **output? The answers could be useful to figure out what is not working right.

---

### Post by pageone on 2009-07-07
I ran the following sequence.  Before I ran this, Win XP booted just fine (no sign of Unbuntu).  Afterwards, Ubuntu ran fine but Win XP won't boot.

sudo grub
find /grub/stage1
(hd2,1)
root (hd2,1)
setup (hd2)
quit

---

### Post by ronparent on 2009-07-07
Since it runs, boot from your ubuntu install. Open a terminal and run sudo grub. Then run the find command like above and post what your output is. I can't tell for sure from your prior posting but I suspect xp is actually located on (hd0).

---

### Post by pageone on 2009-07-07
grub> find /grub/stage1
 (hd2,1)

grub>

---

### Post by presence1960 on 2009-07-08
posting so I can be subscribed to this thread.

---

### Post by pageone on 2009-07-08
As you requested in another thread, here is the results of 

sudo bash ~/Desktop/boot_info_script*.sh


```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #3 in 
    partition #2 for /grub/stage2 and /grub/menu.lst.
 => Grub is installed in the MBR of /dev/sdb and looks on boot drive #-127 in 
    partition #1 for /.
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #2 for /grub/stage2 and /grub/menu.lst.
 => No boot loader? is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda2 starts at sector 245762370.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda3 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda3 starts at sector 491524740.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda4 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda4 starts at sector 737287110.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb2 starts at sector 245762370.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb3 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb3 starts at sector 491524740.
    Operating System:  
    Boot files/dirs:   

sdb4: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb4 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb4 starts at sector 737287110.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sdc3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdc6 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc6 starts at sector 190579158.
    Operating System:  
    Boot files/dirs:   

sdc7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdc7 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc7 starts at sector 399472353.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00033726

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   245,762,369   245,762,307  fd Linux raid autodetect
/dev/sda2         245,762,370   491,524,739   245,762,370  fd Linux raid autodetect
/dev/sda3         491,524,740   737,287,109   245,762,370  fd Linux raid autodetect
/dev/sda4         737,287,110   976,768,064   239,480,955  fd Linux raid autodetect


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00033726

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   245,762,369   245,762,307  fd Linux raid autodetect
/dev/sdb2         245,762,370   491,524,739   245,762,370  fd Linux raid autodetect
/dev/sdb3         491,524,740   737,287,109   245,762,370  fd Linux raid autodetect
/dev/sdb4         737,287,110   976,768,064   239,480,955  fd Linux raid autodetect


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000ad3bc

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    71,682,029    71,681,967   7 HPFS/NTFS
/dev/sdc2          71,682,030    71,778,419        96,390  83 Linux
/dev/sdc3          71,778,420   133,210,979    61,432,560  83 Linux
/dev/sdc4         133,210,980   625,137,344   491,926,365   5 Extended
/dev/sdc5         133,211,106   174,192,794    40,981,689  82 Linux swap / Solaris
/dev/sdc6         190,579,158   399,472,289   208,893,132   b W95 FAT32
/dev/sdc7         399,472,353   625,137,344   225,664,992   b W95 FAT32


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 4005 MB, 4005560320 bytes
16 heads, 32 sectors/track, 15280 cylinders, total 7823360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf567f569

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             32     7,823,359     7,823,328   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="RAID11" UUID="8290-712A" TYPE="vfat" 
/dev/sda2: LABEL="RAID12" UUID="77BC-ED31" TYPE="vfat" 
/dev/sda3: LABEL="RAID13" UUID="77D4-5915" TYPE="vfat" 
/dev/sda4: LABEL="RAID14" UUID="77ED-8205" TYPE="vfat" 
/dev/sdb1: LABEL="RAID11" UUID="8290-712A" TYPE="vfat" 
/dev/sdb2: LABEL="RAID12" UUID="77BC-ED31" TYPE="vfat" 
/dev/sdb3: LABEL="RAID13" UUID="77D4-5915" TYPE="vfat" 
/dev/sdb4: LABEL="RAID14" UUID="77ED-8205" TYPE="vfat" 
/dev/sdc1: UUID="9298D7A398D783DF" TYPE="ntfs" 
/dev/sdc2: UUID="52884e7c-c458-457d-b56f-ae5bd27704b6" TYPE="ext3" 
/dev/sdc3: UUID="cc751e5b-a063-4d73-a58b-a3e40f366345" TYPE="ext3" 
/dev/sdc5: UUID="cf127dde-3686-4c36-87d8-3d24098c1856" TYPE="swap" 
/dev/sdc6: LABEL="DATA-1" UUID="C9F8-9E88" TYPE="vfat" 
/dev/sdc7: LABEL="DATA-2" UUID="CA18-6375" TYPE="vfat" 
/dev/sdd1: LABEL="KINGSTON" UUID="AC61-EF6E" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sdc3 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-13-generic/volatile type tmpfs (rw,mode=755)
/dev/sdc2 on /boot type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/wrocket/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=wrocket)
/dev/sdd1 on /media/KINGSTON type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)


=================== sda4: Location of files loaded by Grub: ===================


 456.9GB: initrd-2.6.23.15-137.fc8.img
 456.9GB: vmlinuz-2.6.23.15-137.fc8

=================== sdb4: Location of files loaded by Grub: ===================


 456.9GB: initrd-2.6.23.15-137.fc8.img
 456.9GB: vmlinuz-2.6.23.15-137.fc8

================================ sdc1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

============================= sdc2/grub/menu.lst: =============================

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
timeout        30

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
# kopt=root=UUID=cc751e5b-a063-4d73-a58b-a3e40f366345 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=52884e7c-c458-457d-b56f-ae5bd27704b6

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

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        52884e7c-c458-457d-b56f-ae5bd27704b6
kernel        /vmlinuz-2.6.28-13-generic root=UUID=cc751e5b-a063-4d73-a58b-a3e40f366345 ro quiet splash 
initrd        /initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        52884e7c-c458-457d-b56f-ae5bd27704b6
kernel        /vmlinuz-2.6.28-13-generic root=UUID=cc751e5b-a063-4d73-a58b-a3e40f366345 ro  single
initrd        /initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        52884e7c-c458-457d-b56f-ae5bd27704b6
kernel        /vmlinuz-2.6.28-11-generic root=UUID=cc751e5b-a063-4d73-a58b-a3e40f366345 ro quiet splash 
initrd        /initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        52884e7c-c458-457d-b56f-ae5bd27704b6
kernel        /vmlinuz-2.6.28-11-generic root=UUID=cc751e5b-a063-4d73-a58b-a3e40f366345 ro  single
initrd        /initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        52884e7c-c458-457d-b56f-ae5bd27704b6
kernel        /memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title        Microsoft Windows XP Professional
rootnoverify    (hd2,0)
savedefault
makeactive
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader    +1


=================== sdc2: Location of files loaded by Grub: ===================


  36.7GB: grub/menu.lst
  36.7GB: grub/stage2
  36.7GB: initrd.img-2.6.28-11-generic
  36.7GB: initrd.img-2.6.28-13-generic
  36.7GB: vmlinuz-2.6.28-11-generic
  36.7GB: vmlinuz-2.6.28-13-generic

=========================== sdc3/boot/grub/menu.lst: ===========================

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
timeout        30

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
# kopt=root=UUID=cc751e5b-a063-4d73-a58b-a3e40f366345 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=52884e7c-c458-457d-b56f-ae5bd27704b6

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

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        52884e7c-c458-457d-b56f-ae5bd27704b6
kernel        /vmlinuz-2.6.28-13-generic root=UUID=cc751e5b-a063-4d73-a58b-a3e40f366345 ro quiet splash 
initrd        /initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        52884e7c-c458-457d-b56f-ae5bd27704b6
kernel        /vmlinuz-2.6.28-13-generic root=UUID=cc751e5b-a063-4d73-a58b-a3e40f366345 ro  single
initrd        /initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        52884e7c-c458-457d-b56f-ae5bd27704b6
kernel        /vmlinuz-2.6.28-11-generic root=UUID=cc751e5b-a063-4d73-a58b-a3e40f366345 ro quiet splash 
initrd        /initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        52884e7c-c458-457d-b56f-ae5bd27704b6
kernel        /vmlinuz-2.6.28-11-generic root=UUID=cc751e5b-a063-4d73-a58b-a3e40f366345 ro  single
initrd        /initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        52884e7c-c458-457d-b56f-ae5bd27704b6
kernel        /memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title        Microsoft Windows XP Professional
rootnoverify    (hd2,0)
savedefault
makeactive
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader    +1


=============================== sdc3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc3 during installation
UUID=cc751e5b-a063-4d73-a58b-a3e40f366345 /               ext3    relatime,errors=remount-ro 0       1
# /boot was on /dev/sdc2 during installation
UUID=52884e7c-c458-457d-b56f-ae5bd27704b6 /boot           ext3    relatime        0       2
# swap was on /dev/sdc5 during installation
UUID=cf127dde-3686-4c36-87d8-3d24098c1856 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc3: Location of files loaded by Grub: ===================


  36.7GB: boot/grub/menu.lst
  36.7GB: boot/grub/stage2
  36.7GB: boot/initrd.img-2.6.28-11-generic
  36.7GB: boot/initrd.img-2.6.28-13-generic
  36.7GB: boot/vmlinuz-2.6.28-11-generic
  36.7GB: boot/vmlinuz-2.6.28-13-generic
  36.7GB: initrd.img
  36.7GB: initrd.img.old
  36.7GB: vmlinuz
  36.7GB: vmlinuz.old
```I really appreciate the help

---

### Post by DawieS on 2009-07-08
I had a similar problem last week when repairing XP. After the repair, although Windows was in the same partition as before, it installed the boot.ini file (and other boot files) in another data partition on the same hard drive. In addition, it seemed to me that it has reversed the direction of counting the partitions on the hard drive (0,1,2,3 became 3,2,1,0 in the MBR).

Try changing the partition number in the boot menu file at the bottom:

Example:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title Microsoft Windows XP Professional
rootnoverify (hd2,0)                <-----------------try  (hd2,1) or (hd2,2) or (hd2,3) etc.
savedefault
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1

---

### Post by pageone on 2009-07-08
ok, i tried 
(hd2,1)
(hd2,2)
(hd2,3)
(hd2,4)
(hd2,5)
(hd2,6)

and they all gave the same error, "no such partition exists"

---

### Post by presence1960 on 2009-07-08
I am not versed in raid arrays, but since you boot off your sdc disk (320 GB) Go into BIOS  and make sure your 320 GB disk is set as first boot in the HDD boot order. Then boot into Ubuntu and edit your Windows entry in menu.lst to this:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
chainloader    +1

```

The reason being Ubuntu (fdisk) and BIOS read the order of drives differently. Since your 320 GB drive is booting first it is actually (hd0) and your windows partition is (hd0,0). You no longer need your map lines because windows is on the first drive that boots. if it were on a drive that is second or third boot in BIOS then you would need the map lines. I am going by what you say that your raid array is strictly for storage and the 320 GB disk is for OSs.

I also run Sabayon 4.2 and in the installer it has an option to change the HDD order to match the BIOS. You can move each HDD up or down to match BIOS boot order. Maybe one day Ubuntu will have the same option.

Sorry about the delay, tonight is Tae Kwon Do night.

---

### Post by ronparent on 2009-07-08
Good advise. Also since you are using a raid bios, the raid array as identified in your raid bios should be your boot 'disk'. Should work since a grub mbr is identifed in sdc (along with sda and sdb). Repeat, as boot drive sdc will now be (hd0). As if not confusing enough already, shuffling the bios boot order also shuffles the grub drive designations.

PS Your initiative to post the boot_info_script was very helpful.

---

### Post by pageone on 2009-07-09
yahoo!!!  It worked.

It is amazing to me that simply swapping the IDE CD-drive and the IDE HD can make that much difference.

Thanks all.

---

