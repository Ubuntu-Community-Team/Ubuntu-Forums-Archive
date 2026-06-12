---
title: "[SOLVED] Triple Boot Challenge"
date: 2009-01-12
forum: Installation &amp; Upgrades
---

### Post by radamo on 2009-01-12
Up until Saturday, I had a great setup for dual boot with Grub as my boot manager. 
Vista is on the first partition of drive 1.
Ubuntu is on the first partition of drive 2. 

Saturday I installed the Windows 7 Beta.  I put it on the first partition of the third drive and I guess my Vista Boot Loader added the Windows 7 option to the Boot Manager. 

I didn't realize I had a problem until I reloaded Grub and added the selection for Windows 7.  If I select the Windows 7 option from Grub I get Bootmgr is missing message.  When I select Vista from grub it loads the Window Boot Manager which shows a choice between Windows 7 or Vista. 

I would like it to boot Vista straight up and I think I can change that by deleting the Windows 7 option using msconfig. What I am struggling with is how to get a bootmgr installed to drive 3 so that when I select the Windows 7 option from Grub it loads properly. I tried using the Windows Vista install CD repair options but they seem to just keep looking at drive 1 where Vista is.  I even changed the bios boot order and that didn't help.  I really don't want to open the machine and disconnect drives 1 and 2 but that may be the only way. 

Does anyone know another way to tackle this?


Thanks for any assistance.
RA

---

### Post by caljohnsmith on 2009-01-12
In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your Windows booting problem might be.

---

### Post by radamo on 2009-01-12
> **caljohnsmith said:**
> In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your Windows booting problem might be.

Okay, I will do this tonight (I am not at my machine currently). Thanks for your offer of assistance. 
RA

---

### Post by maybeway36 on 2009-01-12
This has been part of the Wwindows dual-boot process ever since the 90s. When a new version of Windows is installed alongside the old one, the new one will put its bootloader on the old one's partition. It can get annoying when you want to boot them directly from GRUB.

---

### Post by radamo on 2009-01-12
> **maybeway36 said:**
> This has been part of the Wwindows dual-boot process ever since the 90s. When a new version of Windows is installed alongside the old one, the new one will put its bootloader on the old one's partition. It can get annoying when you want to boot them directly from GRUB.

Yup, just windows trying to "help"... and in the process not giving you any options to set things the way you actually want to.
RA

---

### Post by radamo on 2009-01-12
> **caljohnsmith said:**
> In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your Windows booting problem might be.

Here are the contents of my RESULTS.txt:
```
============================= Boot Info Summary: ==============================

 => Drive sde does not have a valid partition table.
 => Drive sdf does not have a valid partition table.
 => Drive sdg does not have a valid partition table.
 => Drive sdh does not have a valid partition table.
 => Drive sdi does not have a valid partition table.
 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       Extended Partition

sdb5: _________________________________________________________________________

    File system:       swap

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  Geometry: Heads and sectors per Track. According to 
                       the info in the boot sector, sdd1 starts at sector 63. 
                       But according to the info from fdisk, sdd1 starts at 
                       sector . The info in boot sector on the starting 
                       sector of the MFT is wrong. The info in the boot 
                       sector on the starting sector of the MFT Mirror is 
                       wrong.
    Mounting failed:
mount: special device /dev/sdd1 does not exist

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x22633f63

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    71682047    35840000    7  HPFS/NTFS
/dev/sda2        71682048   976771063   452544508    7  HPFS/NTFS

sfdisk -V /dev/sda:

Warning: partition 2 extends past end of disk

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x22633f6e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048    40962047    20480000   83  Linux
/dev/sdb2        40962048   972602672   465820312+   7  HPFS/NTFS
/dev/sdb3       972607230   976768064     2080417+   5  Extended
/dev/sdb5       972607293   976768064     2080386   82  Linux swap / Solaris

sfdisk -V /dev/sdb:

Warning: partition 1 does not end at a cylinder boundary

Drive sdc: _____________________________________________________________________

fdisk -lu /dev/sdc:

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6fc26fc2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048   312578047   156288000    7  HPFS/NTFS

sfdisk -V /dev/sdc:

Warning: partition 1 extends past end of disk

Drive sdd: _____________________________________________________________________

fdisk -lu /dev/sdd:

sfdisk -V /dev/sdd:

/dev/sdd: No such file or directory

sfdisk: cannot open /dev/sdd for reading

Drive sde: _____________________________________________________________________

fdisk -lu /dev/sde:

sfdisk -V /dev/sde:

/dev/sde: No medium found

sfdisk: cannot open /dev/sde for reading

Drive sdf: _____________________________________________________________________

fdisk -lu /dev/sdf:

sfdisk -V /dev/sdf:

/dev/sdf: No medium found

sfdisk: cannot open /dev/sdf for reading

Drive sdg: _____________________________________________________________________

fdisk -lu /dev/sdg:

sfdisk -V /dev/sdg:

/dev/sdg: No medium found

sfdisk: cannot open /dev/sdg for reading

Drive sdh: _____________________________________________________________________

fdisk -lu /dev/sdh:

sfdisk -V /dev/sdh:

/dev/sdh: No medium found

sfdisk: cannot open /dev/sdh for reading

Drive sdi: _____________________________________________________________________

fdisk -lu /dev/sdi:

sfdisk -V /dev/sdi:

/dev/sdi: No medium found

sfdisk: cannot open /dev/sdi for reading

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="9EEC5B7DEC5B4F21" LABEL="Vistaboot" TYPE="ntfs" 
/dev/sda2: UUID="8CB477BDB477A7FA" LABEL="Apps1" TYPE="ntfs" 
/dev/sdb1: UUID="db7f2c00-3634-4e22-9e50-2c620873016e" TYPE="ext3" 
/dev/sdb2: UUID="F4A8C4C2A8C48498" LABEL="Apps2" TYPE="ntfs" 
/dev/sdb5: UUID="f9020e36-1475-4930-b0bd-7e767e1caa91" TYPE="swap" 
/dev/sdc1: UUID="86DAB55FDAB54C65" LABEL="Win7Beta" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
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
/dev/sda1 on /media/sda1 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda2 on /media/sda2 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb2 on /media/sdb2 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/radamo/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=radamo)

================================== sda1/Boot: ==================================

total 608
drwxrwx--- 1 root plugdev   4096 2009-01-10 16:44 .
drwxrwx--- 1 root plugdev  12288 2009-01-12 11:34 ..
-rwxrwx--- 1 root plugdev  32768 2009-01-12 19:13 BCD
-rwxrwx--- 1 root plugdev  29696 2009-01-11 11:49 BCD.LOG
-rwxrwx--- 2 root plugdev      0 2007-12-22 12:01 BCD.LOG1
-rwxrwx--- 2 root plugdev      0 2007-12-22 12:01 BCD.LOG2
-rwxrwx--- 1 root plugdev  65536 2009-01-10 16:44 bootstat.dat
drwxrwx--- 1 root plugdev      0 2009-01-10 16:44 cs-CZ
drwxrwx--- 1 root plugdev      0 2009-01-10 16:44 da-DK
drwxrwx--- 1 root plugdev      0 2009-01-10 16:44 de-DE
drwxrwx--- 1 root plugdev      0 2009-01-10 16:44 el-GR
drwxrwx--- 1 root plugdev      0 2009-01-10 16:44 en-US
drwxrwx--- 1 root plugdev      0 2009-01-10 16:44 es-ES
drwxrwx--- 1 root plugdev      0 2009-01-10 16:44 fi-FI
drwxrwx--- 1 root plugdev      0 2009-01-10 16:44 Fonts
drwxrwx--- 1 root plugdev      0 2009-01-10 16:44 fr-FR
drwxrwx--- 1 root plugdev      0 2009-01-10 16:44 hu-HU
drwxrwx--- 1 root plugdev      0 2009-01-10 16:44 it-IT
drwxrwx--- 1 root plugdev      0 2009-01-10 16:44 ja-JP
drwxrwx--- 1 root plugdev      0 2009-01-10 16:44 ko-KR
-rwxrwx--- 1 root plugdev 473864 2008-12-13 02:01 memtest.exe
drwxrwx--- 1 root plugdev      0 2009-01-10 16:44 nb-NO
drwxrwx--- 1 root plugdev      0 2009-01-10 16:44 nl-NL
drwxrwx--- 1 root plugdev      0 2009-01-10 16:44 pl-PL
drwxrwx--- 1 root plugdev      0 2009-01-10 16:44 pt-BR
drwxrwx--- 1 root plugdev      0 2009-01-10 16:44 pt-PT
drwxrwx--- 1 root plugdev      0 2009-01-10 16:44 ru-RU
drwxrwx--- 1 root plugdev      0 2009-01-10 16:44 sv-SE
drwxrwx--- 1 root plugdev      0 2009-01-10 16:44 tr-TR
drwxrwx--- 1 root plugdev      0 2009-01-10 16:44 zh-CN
drwxrwx--- 1 root plugdev      0 2009-01-10 16:44 zh-HK
drwxrwx--- 1 root plugdev      0 2009-01-10 16:44 zh-TW

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
default		4

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
# kopt=root=UUID=db7f2c00-3634-4e22-9e50-2c620873016e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=db7f2c00-3634-4e22-9e50-2c620873016e ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=db7f2c00-3634-4e22-9e50-2c620873016e ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, memtest86+
root		(hd1,0)
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

title		Windows 7 Beta (loader)
root		(hd2,0)
savedefault
makeactive
chainloader	+1

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=db7f2c00-3634-4e22-9e50-2c620873016e /               ext3    errors=remount-ro,relatime 0       1
# /dev/sda1
UUID=9EEC5B7DEC5B4F21 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=8CB477BDB477A7FA /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb2
UUID=F4A8C4C2A8C48498 /media/sdb2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdc1
UUID=208A63908A6360F0 /media/sdc1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdc2
UUID=12C27A2EC27A1667 /media/sdc2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdc3
UUID=42088DB7088DAB0D /media/sdc3     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb5
UUID=f9020e36-1475-4930-b0bd-7e767e1caa91 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sdb1/boot: ==================================

total 12768
drwxr-xr-x  3 root   root      4096 2008-12-25 11:11 .
drwxr-xr-x 22 radamo radamo    4096 2008-12-25 11:11 ..
-rw-r--r--  1 root   root    503560 2008-11-20 18:30 abi-2.6.27-9-generic
-rw-r--r--  1 root   root     85316 2008-11-20 18:30 config-2.6.27-9-generic
drwxr-xr-x  2 root   root      4096 2009-01-10 15:30 grub
-rw-r--r--  1 root   root   8603222 2008-12-19 23:18 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root   root    124152 2008-09-11 16:11 memtest86+.bin
-rw-r--r--  1 root   root   1352144 2008-11-20 18:30 System.map-2.6.27-9-generic
-rw-r--r--  1 root   root      1130 2008-11-20 18:32 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root   root   2339712 2008-11-20 18:30 vmlinuz-2.6.27-9-generic

=============================== sdb1/boot/grub: ===============================

total 220
drwxr-xr-x 2 root root   4096 2009-01-10 15:30 .
drwxr-xr-x 3 root root   4096 2008-12-25 11:11 ..
-rw-r--r-- 1 root root    197 2008-03-21 09:08 default
-rw-r--r-- 1 root root     60 2008-03-21 09:08 device.map
-rw-r--r-- 1 root root   8040 2008-03-21 09:08 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2008-03-21 09:08 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-03-21 09:08 installed-version
-rw-r--r-- 1 root root   8608 2008-03-21 09:08 jfs_stage1_5
-rw-r--r-- 1 root root   4586 2009-01-10 15:30 menu.lst
-rw-r--r-- 1 root root   4503 2008-12-25 11:11 menu.lst~
-rw-r--r-- 1 root root   4640 2008-03-26 23:03 menu.lst_backup
-rw-r--r-- 1 root root   7324 2008-03-21 09:08 minix_stage1_5
-rw-r--r-- 1 root root   9632 2008-03-21 09:08 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-03-21 09:08 stage1
-rw-r--r-- 1 root root 108340 2008-03-21 09:08 stage2
-rw-r--r-- 1 root root   9276 2008-03-21 09:08 xfs_stage1_5

=========================== Unknown MBRs or Boot Sectors =======================

MFT Sector of /dev/sdd1


=============================== StdErr Messages: ===============================

/dev/sde: No medium found

sfdisk: cannot open /dev/sde for reading
/dev/sdf: No medium found

sfdisk: cannot open /dev/sdf for reading
/dev/sdg: No medium found

sfdisk: cannot open /dev/sdg for reading
/dev/sdh: No medium found

sfdisk: cannot open /dev/sdh for reading
/dev/sdi: No medium found

sfdisk: cannot open /dev/sdi for reading
hexdump: /dev/sdd1: No such device or address
/dev/sdd1: No such file or directory

sfdisk: cannot open /dev/sdd1 for reading
hexdump: /dev/sdd1: No such file or directory
hexdump: /dev/sdd1: No such file or directory
hexdump: /dev/sdd1: No such file or directory
hexdump: /dev/sdd1: No such file or directory
hexdump: /dev/sdd1: No such file or directory
```

sda1 = Vista with bootmgr
sdb1 = Ubuntu with grub
sdc1 = Windows 7 without bootmgr

Can I just copy bootmgr and /boot from sda1 to sdc1 so that it is in both places?

Thanks for any help you can offer,
RA

---

### Post by caljohnsmith on 2009-01-12
OK, so your Windows 7 has a Vista boot sector, so it tries to boot "bootmgr" on start up. But do you know if Windows 7 uses the same bootmgr that Vista uses? I don't know anything about Windows 7 yet as far as it's booting process goes. Does the Windows 7 install CD have a command line or "recovery console"? I think you will at least need that if you want to get Windows 7 booting separate from Vista. If the Win 7 CD has a command line, please let me know if the following commands return anything:
```
help bootrec
help bcdedit
bootrec /?
bcdedit /?

```

---

### Post by radamo on 2009-01-12
> **caljohnsmith said:**
> OK, so your Windows 7 has a Vista boot sector, so it tries to boot "bootmgr" on start up. But do you know if Windows 7 uses the same bootmgr that Vista uses? I don't know anything about Windows 7 yet as far as it's booting process goes. Does the Windows 7 install CD have a command line or "recovery console"? I think you will at least need that if you want to get Windows 7 booting separate from Vista. If the Win 7 CD has a command line, please let me know if the following commands return anything:
```
help bootrec
help bcdedit
bootrec /?
bcdedit /?

```

Yes it does have a command line.  I tried the recovery console options yesterday and they came back saying there were no errors found.  The Windows 7 install saw Vista and used the Vista Bootmgr to add the new environment.  Windows 7 seems VERY similar to Vista in structure.
RA

---

### Post by caljohnsmith on 2009-01-12
OK, it sounds like maybe we can get Win 7 booting separate from Vista since the Win 7 CD does have a command line, so how about doing:
```
sudo mount /dev/sdc1 /mnt
sudo cp -r /media/sda1/bootmgr /media/sda1/Boot /mnt
```
Next open up your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And then at the bottom, replace your current Windows 7 entry with the following:
```

title       Windows 7
rootnoverify     (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1
```
Next boot your Windows 7 Install CD, go to the command line, and do:
```
diskpart
```
At the diskpart prompt do:
```
list volume
exit
```
That should give you the drive letters of all the partitions, so find the drive letter for the Win 7 partition and use it as follows:
```
bcdedit /store C:\boot\bcd /set {default} osdevice boot
bcdedit /store C:\boot\bcd /set {default} device boot
bcdedit /store C:\boot\bcd /set {bootmgr} device boot
bcdedit /store C:\boot\bcd /set {memdiag} device boot
```
But replace "C" above with the Win 7 drive letter if it is different. Reboot, and let me know exactly what happens when you try Windows 7 from your Grub menu. We can work from there.

---

### Post by radamo on 2009-01-13
caljohnsmith,
Thanks so much for all of your assistance.  Got it all working.  After your changes I just had to delete the non-default entries in the Vista and Windows 7 Bootmgr's.  

I really appreciate all of your assistance. 

Best regards,
Rich

---

### Post by caljohnsmith on 2009-01-13
Glad to hear you got it working, but just for my own education, did you run the bcdedit commands on your Win 7 partition? If so, did you still get extra entries in the Win 7 boot manager when you booted Win 7 from Grub?

---

### Post by radamo on 2009-01-13
> **caljohnsmith said:**
> Glad to hear you got it working, but just for my own education, did you run the bcdedit commands on your Win 7 partition? If so, did you still get extra entries in the Win 7 boot manager when you booted Win 7 from Grub?

Yes, I did run the bcdedit commands in the windows 7 partition.  It gave me a mirror image to what showed on the Vista partition... only with Windows 7 as the default.  That is what I was referring to in my post.  

Once I finished and rebooted I had to remove with Vista line from the Windows 7 bootmgr menu and then the Windows 7 choice from the Vista bootmgr menu.  I used msconfig for that chore.  

Not sure where you learned the bcdedits... I poked around using google for a while and could find nothing helpful...  You really saved me some sweat... 

RA

---

