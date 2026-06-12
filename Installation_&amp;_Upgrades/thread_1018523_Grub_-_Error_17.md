---
title: "Grub - Error 17"
date: 2008-12-22
forum: Installation &amp; Upgrades
---

### Post by NeilCollins on 2008-12-22
Hi

Wondered if anyone could help with a grub problem I'm having

Have set up my machine to dual boot vista (pre-installed) and ubuntu.  Installed ubuntu fine and was able to access, then installed EasyBCD and restored the Vista bootloader.  Ever since, whenever I try and access Ubuntu, I receive an 'error 17' - have had a look around at various similar problems, but as far as I can see everything looks OK.

blkid output

/dev/sda1: UUID="B2DC4475DC44363F" TYPE="ntfs" 
/dev/sda2: UUID="4C824F0A824EF84A" TYPE="ntfs" 
/dev/sda5: UUID="0680f694-9c53-48dc-a626-05af2d2f5676" TYPE="swap" 
/dev/sda6: UUID="8f08cda7-594e-4147-85fd-674405310caa" SEC_TYPE="ext2" TYPE="ext3" 
/dev/loop0: TYPE="squashfs"

fdisk output

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x07e4c5ac

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       27855   223743996    7  HPFS/NTFS
/dev/sda2           30405       60801   244158464    7  HPFS/NTFS
/dev/sda3           27856       30404    20474842+   5  Extended
/dev/sda5           27856       28098     1951866   82  Linux swap / Solaris
/dev/sda6           28099       30404    18522913+  83  Linux

Partition table entries are not in disk order

menu.lst entries

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		8f08cda7-594e-4147-85fd-674405310caa
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8f08cda7-594e-4147-85fd-674405310caa ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

fstab entries

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=8f08cda7-594e-4147-85fd-674405310caa /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=0680f694-9c53-48dc-a626-05af2d2f5676 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

can anyone shed some light?

just about to try an edited menu.lst with the following entry


title		Ubuntu 8.10, kernel 2.6.27-7-generic-2
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sda6 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

---

### Post by caljohnsmith on 2008-12-22
How exactly are you booting Ubuntu from Vista? Are you using NeoGrub with EasyBCD, or did you add the Grub boot sector to Vista using EasyBCD? In order to get a clearer picture of your setup, how about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and what your problem might be.

---

### Post by NeilCollins on 2008-12-22
Thanks for the reply

In answer to your first question, I have tried both options via EasyBCD - using NeoGrub and pasting in the lines from menu.lst, and also just adding grub.  I've tried to change c:\nst\menu.lst from within windows, but the changes aren't being reflected when I boot and choose the NeoGrub option.  Have also tried editing \boot\grub\menu.lst in linux, but again the changes haven't been reflected.  I noticed each time a backup(?) hidden file menu.lst~ has been created, which essentially represents the original version (i.e. what I'm seeing when I boot) - is this just default behaviour, or is this the reason I'm having problems?

Output of RESULTS.txt:

Windows is installed in the MBR of /dev/sda

sda1:
    File system:  ntfs
    Boot sector  type:  Vista
    Boot sector  info:  According to the info in the boot sector, sda1 starts at sector 2048.
    Operating System: Vista
    Boot files/directories present:  /menu.lst /bootmgr /Boot /NST

sda2:
    File system:  ntfs
    Boot sector  type:  Vista
    Boot sector  info:  According to the info in the boot sector, sda2 starts at sector 488450048.
    Operating System: 
    Boot files/directories present: 

sda3:
    File system:  Extended Partition

sda5:
    File system:  swap

sda6:
    File system:  ext3
    Boot sector  type:  No Boot Loader
    Boot sector  info:  
    Operating System: Ubuntu 8.10 \n \l
    Boot files/directories present:  /boot/grub/menu.lst /etc/fstab /boot /boot/grub


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x07e4c5ac

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   447490039   223743996    7  HPFS/NTFS
/dev/sda2       488450048   976766975   244158464    7  HPFS/NTFS
/dev/sda3       447490575   488440259    20474842+   5  Extended
/dev/sda5       447490638   451394369     1951866   82  Linux swap / Solaris
/dev/sda6       451394433   488440259    18522913+  83  Linux

Partition table entries are not in disk order

Warning: partition 1 does not end at a cylinder boundary

/dev/sda1: UUID="B2DC4475DC44363F" TYPE="ntfs" 
/dev/sda2: UUID="4C824F0A824EF84A" TYPE="ntfs" 
/dev/sda5: UUID="0680f694-9c53-48dc-a626-05af2d2f5676" TYPE="swap" 
/dev/sda6: UUID="8f08cda7-594e-4147-85fd-674405310caa" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 

sda1/menu.lst

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
# kopt=root=UUID=8f08cda7-594e-4147-85fd-674405310caa ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=8f08cda7-594e-4147-85fd-674405310caa

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
uuid		8f08cda7-594e-4147-85fd-674405310caa
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8f08cda7-594e-4147-85fd-674405310caa ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		8f08cda7-594e-4147-85fd-674405310caa
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8f08cda7-594e-4147-85fd-674405310caa ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		8f08cda7-594e-4147-85fd-674405310caa
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


sda1/Boot

total 796
drwxrwxrwx 1 root root   4096 2008-06-15 19:09 .
drwxrwxrwx 1 root root  40960 2008-12-22 14:30 ..
-rwxrwxrwx 1 root root  32768 2008-12-22 14:41 BCD
-rwxrwxrwx 1 root root 262144 2008-12-22 14:41 BCD.LOG
-rwxrwxrwx 2 root root      0 2008-01-13 05:15 BCD.LOG1
-rwxrwxrwx 2 root root      0 2008-01-13 05:15 BCD.LOG2
-rwxrwxrwx 1 root root  65536 2008-01-13 05:15 bootstat.dat
drwxrwxrwx 1 root root      0 2008-06-15 19:09 cs-CZ
drwxrwxrwx 1 root root      0 2008-06-15 19:09 da-DK
drwxrwxrwx 1 root root      0 2008-06-15 19:09 de-DE
drwxrwxrwx 1 root root      0 2008-06-15 19:09 el-GR
drwxrwxrwx 1 root root      0 2008-06-15 19:09 en-US
drwxrwxrwx 1 root root      0 2008-06-15 19:09 es-ES
drwxrwxrwx 1 root root      0 2008-06-15 19:09 fi-FI
drwxrwxrwx 1 root root      0 2008-06-15 19:09 Fonts
drwxrwxrwx 1 root root      0 2008-06-15 19:09 fr-FR
drwxrwxrwx 1 root root      0 2008-06-15 19:09 hu-HU
drwxrwxrwx 1 root root      0 2008-06-15 19:09 it-IT
drwxrwxrwx 1 root root      0 2008-06-15 19:09 ja-JP
drwxrwxrwx 1 root root      0 2008-06-15 19:09 ko-KR
-rwxrwxrwx 1 root root 406584 2008-01-19 07:43 memtest.exe
drwxrwxrwx 1 root root      0 2008-06-15 19:09 nb-NO
drwxrwxrwx 1 root root      0 2008-06-15 19:09 nl-NL
drwxrwxrwx 1 root root      0 2008-06-15 19:09 pl-PL
drwxrwxrwx 1 root root      0 2008-06-15 19:09 pt-BR
drwxrwxrwx 1 root root      0 2008-06-15 19:09 pt-PT
drwxrwxrwx 1 root root      0 2008-06-15 19:09 ru-RU
drwxrwxrwx 1 root root      0 2008-06-15 19:09 sv-SE
drwxrwxrwx 1 root root      0 2008-06-15 19:09 tr-TR
drwxrwxrwx 1 root root      0 2008-06-15 19:09 zh-CN
drwxrwxrwx 1 root root      0 2008-06-15 19:09 zh-HK
drwxrwxrwx 1 root root      0 2008-06-15 19:09 zh-TW

sda1/NST

total 49
drwxrwxrwx 1 root root     0 2008-12-22 14:30 .
drwxrwxrwx 1 root root 40960 2008-12-22 14:30 ..
-rwxrwxrwx 1 root root   516 2008-12-22 14:32 menu.lst
-rwxrwxrwx 1 root root  8192 2008-04-08 17:50 NeoGrub.mbr

sda6/boot/grub/menu.lst

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
# kopt=root=UUID=8f08cda7-594e-4147-85fd-674405310caa ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=8f08cda7-594e-4147-85fd-674405310caa

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic-Neil
uuid		8f08cda7-594e-4147-85fd-674405310caa
kernel		(hd0,5)/boot/vmlinuz-2.6.27-7-generic root=/dev/sda6 ro quiet splash 
initrd		(hd0,5)/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		8f08cda7-594e-4147-85fd-674405310caa
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8f08cda7-594e-4147-85fd-674405310caa ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		8f08cda7-594e-4147-85fd-674405310caa
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8f08cda7-594e-4147-85fd-674405310caa ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		8f08cda7-594e-4147-85fd-674405310caa
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


sda6/etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=8f08cda7-594e-4147-85fd-674405310caa /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=0680f694-9c53-48dc-a626-05af2d2f5676 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

sda6/boot

total 11932
drwxr-xr-x  3 root root    4096 2008-12-20 20:31 .
drwxr-xr-x 20 root root    4096 2008-12-20 20:31 ..
-rw-r--r--  1 root root  507665 2008-10-24 08:29 abi-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-10-24 08:29 config-2.6.27-7-generic
drwxr-xr-x  2 root root    4096 2008-12-22 12:51 grub
-rw-r--r--  1 root root 8159390 2008-12-20 20:31 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-10-24 08:29 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-10-24 08:31 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2244272 2008-10-24 08:29 vmlinuz-2.6.27-7-generic

sda6/boot/grub

total 248
drwxr-xr-x 2 root root   4096 2008-12-22 12:51 .
drwxr-xr-x 3 root root   4096 2008-12-20 20:31 ..
-rw-r--r-- 1 root root    197 2008-12-20 20:31 default
-rw-r--r-- 1 root root     15 2008-12-20 20:31 device.map
-rw-r--r-- 1 root root   8108 2008-12-20 20:31 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-20 20:31 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-20 20:31 installed-version
-rw-r--r-- 1 root root   8712 2008-12-20 20:31 jfs_stage1_5
-rw-r--r-- 1 root root   4619 2008-12-22 12:49 menu2.lst~
-rw-r--r-- 1 root root   4863 2008-12-22 12:48 menu2.lst~~
-rw-r--r-- 1 root root   4845 2008-12-21 15:50 menu.lst
-rw-r--r-- 1 root root   4802 2008-12-22 12:51 menu.lst~
-rw-r--r-- 1 root root   4619 2008-12-20 20:31 menu.lst~~
-rw-r--r-- 1 root root   7352 2008-12-20 20:31 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-20 20:31 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-20 20:31 stage1
-rw-r--r-- 1 root root 121460 2008-12-20 20:31 stage2
-rw-r--r-- 1 root root   9556 2008-12-20 20:31 xfs_stage1_5

StdErr Messages

---

### Post by caljohnsmith on 2008-12-22
> **NeilCollins said:**
> Thanks for the reply

In answer to your first question, I have tried both options via EasyBCD - using NeoGrub and pasting in the lines from menu.lst, and also just adding grub.  I've tried to change c:\nst\menu.lst from within windows, but the changes aren't being reflected when I boot and choose the NeoGrub option.  Have also tried editing \boot\grub\menu.lst in linux, but again the changes haven't been reflected.  I noticed each time a backup(?) hidden file menu.lst~ has been created, which essentially represents the original version (i.e. what I'm seeing when I boot) - is this just default behaviour, or is this the reason I'm having problems?

Whenever you edit a text file in Linux, the text editor will usually create a backup of the file you are editing with the tilde ~ at the end of the file name, so that's actually normal. I think the easiest solution for your problem would be to use the EasyBCD option to add the Grub boot sector, but I think the reason why it didn't work for you yet is because you still need to install Grub to the Ubuntu partition boot sector. How about doing the following from the Live CD:
```
sudo grub
grub> root (hd0,5)
grub> setup (hd0,5)
grub> quit
```
And please post the output of the above commands. After that, try adding the sda6 partition Grub boot sector to the Vista boot menu with EasyBCD; here is a tutorial of how to do that:

[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

How about giving that a shot and let me know how it goes. :)

---

### Post by NeilCollins on 2008-12-22
Step 1 results below - about to boot into Vista to try step 2

grub> root (hd0,5)      

grub> setup (hd0,5)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,5)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,5)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd0,5) /boot/grub/stage2 p /boot/grub/menu
.lst "... succeeded
Done.

---

### Post by NeilCollins on 2008-12-22
Success!

That seemed to do the trick.

I wasn't aware I needed to manually add grub to the boot sector, as it was bringing up a menu, and I had previously been able to enter Ubuntu without any problem.

All's well that ends well.

Cheers for the help :)

---

### Post by caljohnsmith on 2008-12-22
Great to hear that worked OK. Cheers and have fun with Vista and Ubuntu. :)

---

