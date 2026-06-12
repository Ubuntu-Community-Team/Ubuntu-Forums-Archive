---
title: "New HD in XB3000 docking station giving GRUB error 22"
date: 2009-01-20
forum: Hardware
---

### Post by FreewareFan on 2009-01-20
Hello all.  I have an HP DV9000 running Ubuntu 8.10 64bit.  I have the laptop attached to an HP XB3000 docking station, and all systems work fine, and I daily use GRUB to select from 3 OS's on my internal hard drives.

The issue I'm now having is that the docking station has the ability to run another hard drive, which is seen as a USB drive by 8.10 Ubuntu.  I installed the new HD, and here's what happens.  With the 300gb hd powered on before boot, the GRUB gives this error:

GRUB loading stage1.5

GRUB loading, please wait...

Error 22


At that point, GRUB just hangs, and I have to do a hard power-off.  If I remove power from the 300gb hd, GRUB will once again boot up normally, no problems.

I have used Gparted to partition the hd as an ext3 primary partition, and then used Storage Device Manager to make a mount point, and then mounted the hd.  After that, I set the permissions by opening a terminal and using:

sudo chown -R m /media/dockbase
sudo chgrp -R m /media/dockbase


Of course, /media/dockbase is where I chose to mount the drive.

So, all that to say this:  I do not know what to do now to get rid of the GRUB error 22 on boot.  For me to use the drive at all, I have to disconnect power, boot up, reconnect power, then use Storage Device Manager to mount the drive.  I can't mount the drive from Places, because it says I do not have permissions.  I thought that was what chown and chgrp was for??

Anyone have any suggestions as to what I can try next?  Thanks much for any ideas!

fwf

---

### Post by caljohnsmith on 2009-01-20
In order to troubleshoot your Grub problem, I think it would help to get a clearer picture of your setup, so how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your booting problem might be.

---

### Post by FreewareFan on 2009-01-20
Very well.  The drive I'm having trouble with is /dev/sdc.  The output of the bash file is this:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => HP/Gateway is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot

sda2: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda6: _________________________________________________________________________

    File system:       swap

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       Extended Partition

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdb6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xecb45ac0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   114065391    57031672    7  HPFS/NTFS
/dev/sda2       114077565   195366464    40644450    5  Extended
/dev/sda5       114077628   127732814     6827593+  83  Linux
/dev/sda6       127732878   131636609     1951866   82  Linux swap / Solaris
/dev/sda7       131636673   195366464    31864896   83  Linux

sfdisk -V /dev/sda:

Warning: partition 1 does not end at a cylinder boundary

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa602a602

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   255995774   127997856   83  Linux
/dev/sdb2       255995775   337911209    40957717+  83  Linux
/dev/sdb3       337911210   488392064    75240427+   5  Extended
/dev/sdb5       337911273   353542454     7815591   83  Linux
/dev/sdb6       353542518   488392064    67424773+  83  Linux

sfdisk -V /dev/sdb:

Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
/dev/sdb: OK

Drive sdc: _____________________________________________________________________

fdisk -lu /dev/sdc:

Disk /dev/sdc: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4d49ff75

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   586067264   293033601   83  Linux

sfdisk -V /dev/sdc:

Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
/dev/sdc: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="84941D37941D2CE4" TYPE="ntfs" 
/dev/sda5: UUID="06befa94-0845-4643-a3d7-4e8e04f12ee1" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="75a2350f-3b4b-4d1d-a756-254cfdd6c4a5" TYPE="swap" 
/dev/sda7: UUID="169a4723-26b4-4dd1-acab-be7d48b09c3e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: LABEL="data1" UUID="920f489e-df18-48bc-bdf0-13c59e669e4d" TYPE="ext3" 
/dev/sdb2: LABEL="data2" UUID="8af8eab3-46c8-4f4f-bb5f-65d3ace0f6fd" TYPE="ext3" 
/dev/sdb5: UUID="c7739160-7623-4255-8c23-1df757a3e1fb" TYPE="ext3" 
/dev/sdb6: UUID="095c5d26-4883-415d-a31e-f5310ca614c7" TYPE="ext3" 
/dev/sdc1: LABEL="dockbase" UUID="fc69917f-7ba3-4356-89be-7fe1b4c63c8e" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sdb5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
/dev/sdb6 on /home type ext3 (rw,relatime)
/dev/sdb1 on /media/data1 type ext3 (rw)
/dev/sdb2 on /media/data2 type ext3 (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/m/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=m)
/dev/sdc1 on /media/dockbase type ext3 (rw)

================================== sda1/Boot: ==================================

total 524
drwxrwxrwx 1 root root   4096 2008-12-25 23:41 .
drwxrwxrwx 1 root root   8192 2009-01-16 15:38 ..
-rwxrwxrwx 1 root root  24576 2009-01-16 21:38 BCD
-rwxrwxrwx 1 root root  21504 2009-01-16 21:27 BCD.LOG
-rwxrwxrwx 2 root root      0 2008-12-25 23:41 BCD.LOG1
-rwxrwxrwx 2 root root      0 2008-12-25 23:41 BCD.LOG2
-rwxrwxrwx 1 root root  65536 2008-12-25 23:41 bootstat.dat
drwxrwxrwx 1 root root      0 2008-12-25 23:41 cs-CZ
drwxrwxrwx 1 root root      0 2008-12-25 23:41 da-DK
drwxrwxrwx 1 root root      0 2008-12-25 23:41 de-DE
drwxrwxrwx 1 root root      0 2008-12-25 23:41 el-GR
drwxrwxrwx 1 root root      0 2008-12-25 23:41 en-US
drwxrwxrwx 1 root root      0 2008-12-25 23:41 es-ES
drwxrwxrwx 1 root root      0 2008-12-25 23:41 fi-FI
drwxrwxrwx 1 root root      0 2008-12-25 23:41 Fonts
drwxrwxrwx 1 root root      0 2008-12-25 23:41 fr-FR
drwxrwxrwx 1 root root      0 2008-12-25 23:41 hu-HU
drwxrwxrwx 1 root root      0 2008-12-25 23:41 it-IT
drwxrwxrwx 1 root root      0 2008-12-25 23:41 ja-JP
drwxrwxrwx 1 root root      0 2008-12-25 23:41 ko-KR
-rwxrwxrwx 1 root root 406584 2008-01-20 20:21 memtest.exe
drwxrwxrwx 1 root root      0 2008-12-25 23:41 nb-NO
drwxrwxrwx 1 root root      0 2008-12-25 23:41 nl-NL
drwxrwxrwx 1 root root      0 2008-12-25 23:41 pl-PL
drwxrwxrwx 1 root root      0 2008-12-25 23:41 pt-BR
drwxrwxrwx 1 root root      0 2008-12-25 23:41 pt-PT
drwxrwxrwx 1 root root      0 2008-12-25 23:41 ru-RU
drwxrwxrwx 1 root root      0 2008-12-25 23:41 sv-SE
drwxrwxrwx 1 root root      0 2008-12-25 23:41 tr-TR
drwxrwxrwx 1 root root      0 2008-12-25 23:41 zh-CN
drwxrwxrwx 1 root root      0 2008-12-25 23:41 zh-HK
drwxrwxrwx 1 root root      0 2008-12-25 23:41 zh-TW

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
# kopt=root=UUID=06befa94-0845-4643-a3d7-4e8e04f12ee1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=06befa94-0845-4643-a3d7-4e8e04f12ee1

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		06befa94-0845-4643-a3d7-4e8e04f12ee1
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=06befa94-0845-4643-a3d7-4e8e04f12ee1 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		06befa94-0845-4643-a3d7-4e8e04f12ee1
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=06befa94-0845-4643-a3d7-4e8e04f12ee1 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		06befa94-0845-4643-a3d7-4e8e04f12ee1
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=06befa94-0845-4643-a3d7-4e8e04f12ee1 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		06befa94-0845-4643-a3d7-4e8e04f12ee1
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=06befa94-0845-4643-a3d7-4e8e04f12ee1 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		06befa94-0845-4643-a3d7-4e8e04f12ee1
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


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc             proc         defaults                    0  0  
# /dev/sda5
UUID=06befa94-0845-4643-a3d7-4e8e04f12ee1  /                 ext3         relatime,errors=remount-ro  0  1  
# /dev/sda7
UUID=169a4723-26b4-4dd1-acab-be7d48b09c3e  /home             ext3         relatime                    0  2  
# /dev/sda6
UUID=75a2350f-3b4b-4d1d-a756-254cfdd6c4a5  none              swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0     udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/sdb1                                  /media/data1      ext3         defaults                    0  0  
/dev/sdb2                                  /media/data2      ext3         defaults                    0  0  
/dev/sdb5                                  /media/64bitroot  ext3         defaults                    0  0  
/dev/sdb6                                  /media/64bithome  ext3         defaults                    0  0  

================================== sda5/boot: ==================================

total 23796
drwxr-xr-x  3 root root    4096 2009-01-06 09:27 .
drwxr-xr-x 20 root root    4096 2009-01-06 09:25 ..
-rw-r--r--  1 root root  507665 2008-11-04 15:00 abi-2.6.27-7-generic
-rw-r--r--  1 root root  507665 2008-11-20 17:46 abi-2.6.27-9-generic
-rw-r--r--  1 root root   91364 2008-11-04 15:00 config-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-11-20 17:46 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2009-01-06 09:25 grub
-rw-r--r--  1 root root 8199999 2009-01-06 09:25 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8199986 2009-01-06 09:27 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 15:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-11-04 15:00 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1029585 2008-11-20 17:46 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1073 2008-11-04 15:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-11-20 17:48 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2244464 2008-11-04 15:00 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2244304 2008-11-20 17:46 vmlinuz-2.6.27-9-generic

=============================== sda5/boot/grub: ===============================

total 224
drwxr-xr-x 2 root root   4096 2009-01-06 09:25 .
drwxr-xr-x 3 root root   4096 2009-01-06 09:27 ..
-rw-r--r-- 1 root root    197 2009-01-06 08:21 default
-rw-r--r-- 1 root root     15 2009-01-06 08:21 device.map
-rw-r--r-- 1 root root   8108 2009-01-06 08:21 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-01-06 08:21 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-01-06 08:21 installed-version
-rw-r--r-- 1 root root   8712 2009-01-06 08:21 jfs_stage1_5
-rw-r--r-- 1 root root   5101 2009-01-06 09:25 menu.lst
-rw-r--r-- 1 root root   5017 2009-01-06 09:25 menu.lst~
-rw-r--r-- 1 root root   7352 2009-01-06 08:21 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-01-06 08:21 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-06 08:21 stage1
-rw-r--r-- 1 root root 121460 2009-01-06 08:21 stage2
-rw-r--r-- 1 root root   9556 2009-01-06 08:21 xfs_stage1_5

=========================== sdb5/boot/grub/menu.lst: ===========================

#color black/black black/black

#A splash image for the menu
splashimage=/boot/grub/splashimages/grub_face.xpm.gz
default 0
timeout		5

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
# kopt=root=UUID=c7739160-7623-4255-8c23-1df757a3e1fb ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=c7739160-7623-4255-8c23-1df757a3e1fb

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
# defoptions=quiet vga=769 splash

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

title Ubuntu 8.10 64bit
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=c7739160-7623-4255-8c23-1df757a3e1fb ro quiet splash
initrd /boot/initrd.img-2.6.27-9-generic

title Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=c7739160-7623-4255-8c23-1df757a3e1fb ro  single
initrd /boot/initrd.img-2.6.27-9-generic

title Ubuntu 8.10, kernel 2.6.27-7-generic
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=c7739160-7623-4255-8c23-1df757a3e1fb ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=c7739160-7623-4255-8c23-1df757a3e1fb ro  single
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, memtest86+
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

title Other operating systems:
root

title Windows Vista/Longhorn (loader)
root (hd0,0)
chainloader +1
savedefault
makeactive

title Ubuntu 8.10 32bit (on /dev/sda5)
root (hd0,4)
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=06befa94-0845-4643-a3d7-4e8e04f12ee1 ro quiet splash
initrd /boot/initrd.img-2.6.27-9-generic
savedefault

title Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode) (on /dev/sda5)
root (hd0,4)
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=06befa94-0845-4643-a3d7-4e8e04f12ee1 ro single
initrd /boot/initrd.img-2.6.27-9-generic
savedefault

title Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sda5)
root (hd0,4)
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=06befa94-0845-4643-a3d7-4e8e04f12ee1 ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic
savedefault

title Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda5)
root (hd0,4)
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=06befa94-0845-4643-a3d7-4e8e04f12ee1 ro single
initrd /boot/initrd.img-2.6.27-7-generic
savedefault

title Ubuntu 8.10, memtest86+ (on /dev/sda5)
root (hd0,4)
kernel /boot/memtest86+.bin
savedefault


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc            proc         defaults                    0  0  
# /dev/sdb5
UUID=c7739160-7623-4255-8c23-1df757a3e1fb  /                ext3         relatime,errors=remount-ro  0  1  
# /dev/sdb6
UUID=095c5d26-4883-415d-a31e-f5310ca614c7  /home            ext3         relatime                    0  2  
# /dev/sda6
UUID=75a2350f-3b4b-4d1d-a756-254cfdd6c4a5  none             swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0    udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/sdb1                                  /media/data1     ext3         defaults                    0  0  
/dev/sdb2                                  /media/data2     ext3         defaults                    0  0  
/dev/sdc1                                  /media/dockbase  ext3         defaults                    0  0  

================================== sdb5/boot: ==================================

total 25516
drwxr-xr-x  3 root root    4096 2009-01-17 03:29 .
drwxr-xr-x 20 root root    4096 2009-01-10 15:06 ..
-rw-r--r--  1 root root  503560 2008-11-04 14:53 abi-2.6.27-7-generic
-rw-r--r--  1 root root  503560 2008-11-20 17:30 abi-2.6.27-9-generic
-rw-r--r--  1 root root   85316 2008-11-04 14:53 config-2.6.27-7-generic
-rw-r--r--  1 root root   85316 2008-11-20 17:30 config-2.6.27-9-generic
drwxr-xr-x  3 root root    4096 2009-01-17 03:33 grub
-rw-r--r--  1 root root 8666918 2009-01-17 03:29 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8667069 2009-01-17 03:29 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 15:11 memtest86+.bin
-rw-r--r--  1 root root 1352144 2008-11-04 14:53 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1352144 2008-11-20 17:30 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1130 2008-11-04 14:57 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1130 2008-11-20 17:32 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2339552 2008-11-04 14:53 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2339712 2008-11-20 17:30 vmlinuz-2.6.27-9-generic

=============================== sdb5/boot/grub: ===============================

total 244
drwxr-xr-x 3 root root   4096 2009-01-17 03:33 .
drwxr-xr-x 3 root root   4096 2009-01-17 03:29 ..
-rw-r--r-- 1 root root    197 2009-01-10 10:45 default
-rw-r--r-- 1 root root     30 2009-01-10 10:45 device.map
-rw-r--r-- 1 root root   8108 2009-01-10 10:45 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-01-10 10:45 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-01-10 10:45 installed-version
-rw-r--r-- 1 root root   8712 2009-01-10 10:45 jfs_stage1_5
-rw-r--r-- 1 root root   4365 2009-01-17 03:33 menu.lst
-rw-r--r-- 1 root root   4365 2009-01-17 03:33 menu.lst~
-rw-r--r-- 1 root root   6719 2009-01-14 18:56 menu.lst.backup
-rw-r--r-- 1 root root   6715 2009-01-14 19:37 menu.lst_original
-rw-r--r-- 1 root root   7352 2009-01-10 10:45 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-01-10 10:45 reiserfs_stage1_5
drwxr-xr-x 2 root m      4096 2009-01-15 20:05 splashimages
-rw-r--r-- 1 root root    512 2009-01-10 10:45 stage1
-rw-r--r-- 1 root root 121460 2009-01-10 10:45 stage2
-rw-r--r-- 1 root root   9556 2009-01-10 10:45 xfs_stage1_5

=============================== StdErr Messages: ===============================

No errors were reported.
```

---

### Post by caljohnsmith on 2009-01-20
OK, I think I see what the problem is; you have Grub installed to the MBR (Master Boot Record) of your sda drive, but it points to the 5th partition on the 2nd drive in your BIOS boot order, which is supposed to be your sdb drive obviously. What is probably happening is that when you turn on your sdc drive, your BIOS sees the sdc drive as the 2nd boot drive instead of the sdb drive, and your sdb drive would then be the 3rd boot drive. If that's the case, that would give you a Grub error 22, because a Grub error 22 is:
[QUOTE=Grub Manual]Error 22: No such partition
This error is returned if a partition is requested in the device part of a device- or full file name which isn't on the selected disk.[/QUOTE]
And your sdc drive does not have a 5th partition, so that's why a Grub error 22 would make sense. Your situation is one of the big problems with installing Grub to the MBR of a drive other than the drive that has Grub's boot files. You could try to make your sdb drive come before the sdc drive in the BIOS boot order, but I would recommend simply installing Grub to the MBR of your sdb drive, and then change your BIOS to boot the sdb drive before all the other drives. Then it doesn't matter if the other drives are connected or not, and it doesn't matter what order they are in the BIOS boot order; your drives will be independent of each other as far as booting is concerned. If that sounds like what you might want, how about doing:
```
sudo grub
grub> root (hd1,0)
grub> makeactive
grub> root (hd1,4)
grub> setup (hd1)
grub> quit
```
Then reboot, set your BIOS to boot the sdb drive, and you should at least get a Grub menu on start up (which is 90% of the battle). It looks like your sdb5 Ubuntu's menu.lst might need some tweaking though, at least to boot into your 64-bit Ubuntu, because the boot stanzas are missing a "uuid" or "root" line. But let me know how far you get and we can work from there.

---

### Post by FreewareFan on 2009-01-20
I believe I understand what you just told me.  However, there is a small problem..... my BIOS does not let me choose which internal drive boots first, and which boots second.  There is only one entry that covers the two of them, and that is labeled "Notebook Hard Drive" 

So, I do not think this strategy will work because of the limits of my BIOS.  And it will not let me disable booting from the "USB Hard Drive"  either, which is a shame, because that would probably be a work-around for the GRUB issue also...

Any other ideas?

---

