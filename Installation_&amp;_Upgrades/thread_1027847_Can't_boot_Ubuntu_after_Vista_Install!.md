---
title: "Can't boot Ubuntu after Vista Install!"
date: 2009-01-01
forum: Installation &amp; Upgrades
---

### Post by SeanKing on 2009-01-01
Hello

I've encountered a problem and I cant figure out a solution. I have searched through the forum and came across similar issues but need better help.

My issue is that I installed Ubuntu and hooked it up perfectly for the first time(im some what a newbie). I then decided to install Vista and now I cant boot into Ubuntu. My computer boots into Vista automatically. It doesn't give me the which OS to boot option.

After searching on the net I came across a tutorial on how to fix this issue. What i did was boot Ubuntu from the cd then :

grub> root (hd0,<press tab>
grub> root (hd0,0)
grub> setup (hd0)
grub> quit 

I then rebooted and I thought it fixed my issue but when i selected ubuntu as the OS it then said error 17 and some message about not able to mount............ Can anyone please help me? Thank!......

---

### Post by caljohnsmith on 2009-01-01
OK, how about on start up select the first Ubuntu entry in the Grub menu, press "e" to edit it, select the line that says "root (hdX,Y)" where X and Y are numbers, press "e" to edit it, change it to the (hdX,Y) that worked to install Grub in your previous commands, press return to save the change, then press "b" to boot. Based on the info you gave, I think that should be all it takes to boot Ubuntu. Note that the change is not permanent, so you'll need to modify your menu.lst to make it permanent.

So if it works, when you get into Ubuntu, just do:
```
gksudo gedit /boot/grub/menu.lst
```
And change the line that says "# groot=(hdX,Y)" to use the (hdX,Y) that worked to boot Ubuntu. Save, quit gedit, then run:
```
sudo update-grub
```
And you should be all set. Let me know how it goes or if you run into problems.

---

### Post by SeanKing on 2009-01-01
Awesome, your directions worked for me!! Thank you so much I really appreciate it. It was very easy to do. Just one quick question.......... after fallowing your directions i just notice it takes a little while for it to boot into ubuntu. normal?

---

### Post by caljohnsmith on 2009-01-01
> **SeanKing said:**
> Awesome, your directions worked for me!! Thank you so much I really appreciate it. It was very easy to do. Just one quick question.......... after fallowing your directions i just notice it takes a little while for it to boot into ubuntu. normal?
Glad to hear you booted into Ubuntu OK. But about your question, do you mean it seems to take a little while longer than normal to boot Ubuntu? I would have to know more about your setup, so how about doing:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

---

### Post by SeanKing on 2009-01-01
Here are the results of the command you told me to type :
```

============================= Boot Info Summary: ==============================

 => Grub is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for its boot files.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda2: _________________________________________________________________________

    File system:       swap

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda3 starts 
                       at sector 171399168.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda4 starts 
                       at sector 290908160.
    Operating System:  
    Boot files/dirs:   /bootmgr /BOOT

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x289638e7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1       147412440   167397299     9992430   83  Linux
/dev/sda2       167397300   171397484     2000092+  82  Linux swap / Solaris
/dev/sda3   *   171399168   290908159    59754496    7  HPFS/NTFS
/dev/sda4       290908160   312569855    10830848    7  HPFS/NTFS

sfdisk -V /dev/sda:

Warning: partition 3 does not start at a cylinder boundary

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="ec05f63c-9c6d-4df9-9753-1402e9eeddbb" TYPE="ext3" 
/dev/sda2: UUID="d818c6a4-81e3-41f9-ae49-2de26d9224d7" TYPE="swap" 
/dev/sda3: UUID="D41C605C1C603B9C" TYPE="ntfs" 
/dev/sda4: UUID="8C6A2DF76A2DDEA8" LABEL="HP_RECOVERY" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
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
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/sean/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=sean)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=sean)

=========================== sda1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=ec05f63c-9c6d-4df9-9753-1402e9eeddbb ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=ec05f63c-9c6d-4df9-9753-1402e9eeddbb ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=ec05f63c-9c6d-4df9-9753-1402e9eeddbb ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-4-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-4-generic root=UUID=ec05f63c-9c6d-4df9-9753-1402e9eeddbb ro quiet splash 
initrd		/boot/initrd.img-2.6.27-4-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-4-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-4-generic root=UUID=ec05f63c-9c6d-4df9-9753-1402e9eeddbb ro  single
initrd		/boot/initrd.img-2.6.27-4-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,0)
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


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=ec05f63c-9c6d-4df9-9753-1402e9eeddbb /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=d818c6a4-81e3-41f9-ae49-2de26d9224d7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sda1/boot: ==================================

total 23960
drwxr-xr-x  3 root root    4096 2008-12-27 18:04 .
drwxr-xr-x 20 root root    4096 2008-12-23 11:55 ..
-rw-r--r--  1 root root  504774 2008-09-23 23:15 abi-2.6.27-4-generic
-rw-r--r--  1 root root  507665 2008-11-20 18:46 abi-2.6.27-9-generic
-rw-r--r--  1 root root   95910 2008-09-23 23:15 config-2.6.27-4-generic
-rw-r--r--  1 root root   91364 2008-11-20 18:46 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2009-01-01 21:00 grub
-rw-r--r--  1 root root 8347726 2008-12-22 18:17 initrd.img-2.6.27-4-generic
-rw-r--r--  1 root root 8138327 2008-12-27 18:04 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 16:11 memtest86+.bin
-rw-r--r--  1 root root 1041452 2008-09-23 23:15 System.map-2.6.27-4-generic
-rw-r--r--  1 root root 1029585 2008-11-20 18:46 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1073 2008-09-23 23:17 vmcoreinfo-2.6.27-4-generic
-rw-r--r--  1 root root    1073 2008-11-20 18:48 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2305072 2008-12-22 18:16 vmlinuz-2.6.27-4-generic
-rw-r--r--  1 root root 2244304 2008-11-20 18:46 vmlinuz-2.6.27-9-generic

=============================== sda1/boot/grub: ===============================

total 224
drwxr-xr-x 2 root root   4096 2009-01-01 21:00 .
drwxr-xr-x 3 root root   4096 2008-12-27 18:04 ..
-rw-r--r-- 1 root root    197 2008-12-22 18:17 default
-rw-r--r-- 1 root root     15 2008-12-22 18:17 device.map
-rw-r--r-- 1 root root   8108 2008-12-22 18:17 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-22 18:17 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-22 18:17 installed-version
-rw-r--r-- 1 root root   8712 2008-12-22 18:17 jfs_stage1_5
-rw-r--r-- 1 root root   5111 2009-01-01 21:00 menu.lst
-rw-r--r-- 1 root root   5111 2009-01-01 21:00 menu.lst~
-rw-r--r-- 1 root root   7352 2008-12-22 18:17 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-22 18:17 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-22 18:17 stage1
-rw-r--r-- 1 root root 121500 2008-12-22 18:17 stage2
-rw-r--r-- 1 root root   9556 2008-12-22 18:17 xfs_stage1_5

================================== sda3/Boot: ==================================

total 524
drwxrwxrwx 1 root root   4096 2008-12-31 14:26 .
drwxrwxrwx 1 root root   8192 2008-12-31 20:10 ..
-rwxrwxrwx 1 root root  24576 2009-01-01 20:52 BCD
-rwxrwxrwx 1 root root  21504 2009-01-01 17:23 BCD.LOG
-rwxrwxrwx 2 root root      0 2008-12-31 14:26 BCD.LOG1
-rwxrwxrwx 2 root root      0 2008-12-31 14:26 BCD.LOG2
-rwxrwxrwx 1 root root  65536 2008-12-31 14:26 bootstat.dat
drwxrwxrwx 1 root root      0 2008-12-31 14:26 cs-CZ
drwxrwxrwx 1 root root      0 2008-12-31 14:26 da-DK
drwxrwxrwx 1 root root      0 2008-12-31 14:26 de-DE
drwxrwxrwx 1 root root      0 2008-12-31 14:26 el-GR
drwxrwxrwx 1 root root      0 2008-12-31 14:26 en-US
drwxrwxrwx 1 root root      0 2008-12-31 14:26 es-ES
drwxrwxrwx 1 root root      0 2008-12-31 14:26 fi-FI
drwxrwxrwx 1 root root      0 2008-12-31 14:26 Fonts
drwxrwxrwx 1 root root      0 2008-12-31 14:26 fr-FR
drwxrwxrwx 1 root root      0 2008-12-31 14:26 hu-HU
drwxrwxrwx 1 root root      0 2008-12-31 14:26 it-IT
drwxrwxrwx 1 root root      0 2008-12-31 14:26 ja-JP
drwxrwxrwx 1 root root      0 2008-12-31 14:26 ko-KR
-rwxrwxrwx 1 root root 406584 2008-01-20 21:21 memtest.exe
drwxrwxrwx 1 root root      0 2008-12-31 14:26 nb-NO
drwxrwxrwx 1 root root      0 2008-12-31 14:26 nl-NL
drwxrwxrwx 1 root root      0 2008-12-31 14:26 pl-PL
drwxrwxrwx 1 root root      0 2008-12-31 14:26 pt-BR
drwxrwxrwx 1 root root      0 2008-12-31 14:26 pt-PT
drwxrwxrwx 1 root root      0 2008-12-31 14:26 ru-RU
drwxrwxrwx 1 root root      0 2008-12-31 14:26 sv-SE
drwxrwxrwx 1 root root      0 2008-12-31 14:26 tr-TR
drwxrwxrwx 1 root root      0 2008-12-31 14:26 zh-CN
drwxrwxrwx 1 root root      0 2008-12-31 14:26 zh-HK
drwxrwxrwx 1 root root      0 2008-12-31 14:26 zh-TW

================================== sda4/BOOT: ==================================

total 7960
drwxrwxrwx 1 root root    8192 2008-12-23 06:32 .
drwxrwxrwx 1 root root   12288 2008-12-31 20:10 ..
-rwxrwxrwx 1 root root  262144 2008-12-23 06:32 BCD
-rwxrwxrwx 1 root root    9216 2008-12-23 06:32 BCD.LOG
-rwxrwxrwx 1 root root 3170304 2006-09-25 13:10 BOOT.SDI
-rwxrwxrwx 1 root root    1089 2008-03-26 12:08 Desktop.ini
-rwxrwxrwx 1 root root    8134 2002-09-10 12:14 Folder.htt
-rwxrwxrwx 2 root root  181898 2002-09-16 10:37 protect.chinese hong kong
-rwxrwxrwx 2 root root  181916 2002-09-16 10:37 protect.chinese simplified
-rwxrwxrwx 2 root root  181898 2002-09-16 10:37 protect.chinese traditional
-rwxrwxrwx 2 root root  181865 2006-04-27 12:19 protect.czech
-rwxrwxrwx 2 root root  181726 2005-11-03 10:21 protect.danish
-rwxrwxrwx 2 root root  181605 2002-09-10 09:56 protect.dutch
-rwxrwxrwx 1 root root  181651 2002-09-10 09:50 Protect.ed
-rwxrwxrwx 2 root root  181648 2004-11-22 10:28 protect.english
-rwxrwxrwx 2 root root  181673 2005-11-03 10:20 protect.finnish
-rwxrwxrwx 2 root root  181736 2005-11-03 10:19 protect.french
-rwxrwxrwx 2 root root  181669 2005-11-03 10:18 protect.german
-rwxrwxrwx 2 root root  182689 2005-11-23 10:56 protect.greek
-rwxrwxrwx 2 root root  182605 2006-01-23 04:18 protect.hebrew
-rwxrwxrwx 2 root root  181696 2007-08-28 10:58 protect.hungarian
-rwxrwxrwx 2 root root  181554 2005-11-03 10:17 protect.italian
-rwxrwxrwx 2 root root  182351 2007-06-19 11:22 protect.japanese
-rwxrwxrwx 2 root root  218295 2005-11-24 06:24 protect.korean
-rwxrwxrwx 2 root root  181578 2005-11-03 10:15 protect.norwegian
-rwxrwxrwx 2 root root  181789 2006-04-25 10:44 protect.polish
-rwxrwxrwx 2 root root  181624 2005-11-03 10:13 protect.portuguese
-rwxrwxrwx 2 root root  181882 2005-10-27 15:24 protect.portuguese brazilian
-rwxrwxrwx 2 root root  211936 2004-06-28 04:52 protect.russian
-rwxrwxrwx 2 root root  181586 2005-11-03 10:11 protect.spanish
-rwxrwxrwx 2 root root  181602 2002-09-10 10:15 protect.swedish
-rwxrwxrwx 2 root root  181783 2003-08-12 06:37 protect.turkish

=============================== StdErr Messages: ===============================

No errors were reported.
```

---

### Post by caljohnsmith on 2009-01-01
OK, thanks for posting that, it helps give me a much better picture of your setup. But according to everything the script shows, it looks like you have your menu.lst and fstab configured correctly, so nothing obvious really stands out. If you wanted to, you could go through the output of "dmesg" to see if you find any peculiar errors or anything, but it could take a lot of work to try and sort through all of dmesg's output; that's just one idea though. Anyway, cheers and Happy New Year. :)

---

### Post by SeanKing on 2009-01-01
Once again, Thanks so much............... Happy New year to you too!

---

