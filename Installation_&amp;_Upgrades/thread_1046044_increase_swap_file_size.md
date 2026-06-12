---
title: "increase swap file size"
date: 2009-01-21
forum: Installation &amp; Upgrades
---

### Post by venkatesh_b87 on 2009-01-21
hi everybody, i am using vista home basic and now installed ubuntu8.04 lts desktop edition. i used the option "install inside windows" option availabe in the cd. i could use ubuntu successfully. the issue is i have tried to install oracle in it, which needs a swap file size of 1024 mb. my system says it has only 983 mb. so how should i increase the swap size so that i could install oracle in it.
actaully i have tried the following options,
[B]sudo dd if=/dev/zero of=/swapfile bs=1M count=1024
sudo mkswap /swapfile
sudo swapon /swapfile[/B]
but again the system says that i have only 983mb. 
please help me to increase the swap size and let me know how to check the size.
thanks ...

---

### Post by venkatesh_b87 on 2009-01-21
i kindly request someone to help me fixing the issue stated above... thanks......

---

### Post by caljohnsmith on 2009-01-21
I'm not sure exactly how Wubi handles doing swap space; it probably is different than a normal install, so that might be why you are running into problems. How about first posting:
```
free
cat /etc/fstab
sudo blkid -c /dev/null

```
And we can work from there if you want.

---

### Post by venkatesh_b87 on 2009-01-21
thanks for your reply......

root@hari-laptop:~# free
             total       used       free     shared    buffers   cached
Mem:       3106732    1030932    2075800          0     276820   485084
-/+ buffers/cache:     269028    2837704
Swap:       976552          0     976552
root@hari-laptop:~# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
root@hari-laptop:~# sudo blkid -c /dev/null
/dev/sda1: UUID="EA76DCA676DC74B3" TYPE="ntfs" 
/dev/sda2: UUID="24BE3FA0BE3F6986" LABEL="movies" TYPE="ntfs" 
/dev/sda4: UUID="2C88743C8874071C" LABEL="HP_RECOVERY" TYPE="ntfs" 
/dev/sda5: UUID="FC3056F63056B6FC" LABEL="files" TYPE="ntfs" 
/dev/sda6: UUID="4E5888915888798B" LABEL="data" TYPE="ntfs" 
/dev/sda7: UUID="30EECFCBEECF8814" LABEL="Ubuntu" TYPE="ntfs" 
/dev/loop0: UUID="4559af2b-db7c-4f87-b1bb-9845c6d0ba0b" TYPE="ext3" 
root@hari-laptop:~#

---

### Post by caljohnsmith on 2009-01-21
OK, it does look like Wubi handles swap a little differently. How about doing:
```
sudo mount /dev/sda7 /mnt
ls -l /mnt/ubuntu/disks/swap.disk
```
If that shows your swap.disk file, then proceed with:
```
sudo swapoff -a
sudo dd if=/dev/zero of=/mnt/ubuntu/disks/swap.disk bs=1M count=1024
sudo mkswap /mnt/ubuntu/disks/swap.disk
sudo swapon -a
free
```
And see if you have 1024 MB worth of swap space. If that doesn't work, try rebooting and then check the swap space again with "free". Also, please post the output of:
```
cat /etc/initramfs-tools/conf.d/resume
```
And we can go from there.

---

### Post by venkatesh_b87 on 2009-01-22
thanks john..
here is the console output:

root@hari-laptop:~# sudo mount /dev/sda7 /mnt
fuse: mount failed: Device or resource busy

root@hari-laptop:~# ls -l /mnt/ubuntu/disks/swap.disk
ls: cannot access /mnt/ubuntu/disks/swap.disk: No such file or directory

root@hari-laptop:~# cat /etc/initramfs-tools/conf.d/resume
cat: /etc/initramfs-tools/conf.d/resume: No such file or directory
root@hari-laptop:~# 
----------------------------------
i would like to mention that i have 3gb ram in my laptop. also the drive in which i have installed ubuntu from inside vista basic is 27gb, out of which i had used only 10gb.so how should i proceed now...?
thanks...

---

### Post by caljohnsmith on 2009-01-22
I think it would help to get a little clearer picture of your setup before we proceed, so how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what it will take to increase your swap.

---

### Post by avtolle on 2009-01-22
A few general observations on installing "under Windows" using Wubi. First, the installer asks how large a size is to be used for Ubuntu, and within that space both the / and swap partitions are created. Next, the virtual drive, for lack of a better term, is created within said space. 

From looking at the posting of the responses to the commands given, it looks like the drive was mounted, which makes sense if the OP was running the commands from his Ubuntu installation, and not from a live CD. 

What might be an option is to go to the Wubi subforum, look at the stickys, particularly the bottom one, and get to the FAQs, where there is a link to the Wubi site. I'd suggest that either he follow the procedure to increase the size of his Wubi install, or add another "virtual dirve", which might then be used for swap. I have a feeling (don't know, haven't tried it) that the traditional ways to increase the size of a partition on a Ububntu install to HDD won't work in this situation.

---

### Post by venkatesh_b87 on 2009-01-22
```
============================= Boot Info Summary: ==============================

 => HP/Gateway is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /wubildr.mbr /boot

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/disks/boot/grub/menu.lst 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks 
                       /ubuntu/disks/boot/ /ubuntu/disks/boot/grub 
                       /ubuntu/disks/boot/grub

sda3: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048. But according to the info from fdisk, 
                       sda5 starts at sector 205748224.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 2048. But according to the info from fdisk, 
                       sda6 starts at sector 237320192.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 2048. But according to the info from fdisk, 
                       sda7 starts at sector 268795904.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x57ad6c4e

/dev/sda1     *           63  149,123,071  149,123,009   7 HPFS/NTFS
/dev/sda2        149,123,072  205,746,175   56,623,104   7 HPFS/NTFS
/dev/sda3        205,746,176  291,481,599   85,735,424   f W95 Ext'd (LBA)
/dev/sda5        205,748,224  237,318,143   31,569,920   7 HPFS/NTFS
/dev/sda6        237,320,192  268,793,855   31,473,664   7 HPFS/NTFS
/dev/sda7        268,795,904  291,481,599   22,685,696   7 HPFS/NTFS
/dev/sda4        291,483,360  312,576,704   21,093,345   7 HPFS/NTFS

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="EA76DCA676DC74B3" TYPE="ntfs" 
/dev/sda2: UUID="24BE3FA0BE3F6986" LABEL="movies" TYPE="ntfs" 
/dev/sda4: UUID="2C88743C8874071C" LABEL="HP_RECOVERY" TYPE="ntfs" 
/dev/sda5: UUID="FC3056F63056B6FC" LABEL="files" TYPE="ntfs" 
/dev/sda6: UUID="4E5888915888798B" LABEL="data" TYPE="ntfs" 
/dev/sda7: UUID="30EECFCBEECF8814" LABEL="Ubuntu" TYPE="ntfs" 
/dev/loop0: UUID="4559af2b-db7c-4f87-b1bb-9845c6d0ba0b" TYPE="ext3" 

=============================== "mount" output: ===============================

/host/ubuntu/disks/root.disk on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
/host/ubuntu/disks/boot on /boot type none (rw,bind)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /root/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev)
/dev/sda7 on /media/Ubuntu type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)

================================== sda1/boot: ==================================

total 1008
drwxrwxrwx 1 root root   4096 2005-11-24 23:37 .
drwxrwxrwx 1 root root   8192 2009-01-22 19:32 ..
-rwxrwxrwx 1 root root  32768 2009-01-23 07:12 bcd
-rwxrwxrwx 1 root root 262144 2009-01-23 07:09 BCD.LOG
-rwxrwxrwx 2 root root 262144 2007-12-17 08:23 BCD.LOG1
-rwxrwxrwx 2 root root      0 2005-11-24 23:24 BCD.LOG2
-rwxrwxrwx 1 root root   1024 2006-09-18 17:57 bootfix.bin
-rwxrwxrwx 1 root root  65536 2005-11-24 23:24 bootstat.dat
drwxrwxrwx 1 root root      0 2005-11-24 23:24 cs-CZ
drwxrwxrwx 1 root root      0 2005-11-24 23:24 da-DK
drwxrwxrwx 1 root root      0 2005-11-24 23:24 de-DE
drwxrwxrwx 1 root root      0 2005-11-24 23:24 el-GR
drwxrwxrwx 1 root root      0 2005-11-24 23:24 en-US
drwxrwxrwx 1 root root      0 2005-11-24 23:24 es-ES
-rwxrwxrwx 1 root root   2048 2006-09-18 17:57 etfsboot.com
drwxrwxrwx 1 root root      0 2005-11-24 23:24 fi-FI
drwxrwxrwx 1 root root      0 2005-11-24 23:24 fonts
drwxrwxrwx 1 root root      0 2005-11-24 23:24 fr-FR
drwxrwxrwx 1 root root      0 2005-11-24 23:24 hu-HU
drwxrwxrwx 1 root root      0 2005-11-24 23:24 it-IT
drwxrwxrwx 1 root root      0 2005-11-24 23:24 ja-JP
drwxrwxrwx 1 root root      0 2005-11-24 23:24 ko-KR
-rwxrwxrwx 1 root root 386664 2006-11-02 15:21 memtest.exe
drwxrwxrwx 1 root root      0 2005-11-24 23:24 nb-NO
drwxrwxrwx 1 root root      0 2005-11-24 23:24 nl-NL
drwxrwxrwx 1 root root      0 2005-11-24 23:24 pl-PL
drwxrwxrwx 1 root root      0 2005-11-24 23:24 pt-BR
drwxrwxrwx 1 root root      0 2005-11-24 23:24 pt-PT
drwxrwxrwx 1 root root      0 2005-11-24 23:24 ru-RU
drwxrwxrwx 1 root root      0 2005-11-24 23:24 sv-SE
drwxrwxrwx 1 root root      0 2005-11-24 23:24 tr-TR
drwxrwxrwx 1 root root      0 2005-11-24 23:24 zh-CN
drwxrwxrwx 1 root root      0 2005-11-24 23:24 zh-HK
drwxrwxrwx 1 root root      0 2005-11-24 23:24 zh-TW

==================== sda2/ubuntu/disks/boot/grub/menu.lst: ====================

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
# kopt=root=UUID=24BE3FA0BE3F6986 loop=/ubuntu/disks/root.disk ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)/ubuntu/disks

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,1)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=24BE3FA0BE3F6986 loop=/ubuntu/disks/root.disk ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,1)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=24BE3FA0BE3F6986 loop=/ubuntu/disks/root.disk ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,1)/ubuntu/disks
kernel		/boot/memtest86+.bin

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
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title		Windows Vista/Longhorn (loader)
root		(hd0,3)
savedefault
chainloader	+1


============================== sda2/ubuntu/disks: ==============================

total 7812512
drwxrwxrwx 1 root root          0 2009-01-17 04:36 .
drwxrwxrwx 1 root root       4096 2009-01-17 04:26 ..
drwxrwxrwx 1 root root       4096 2009-01-17 15:45 boot
-rwxrwxrwx 2 root root 7000000000 2009-01-23 07:15 root.disk
drwxrwxrwx 1 root root          0 2009-01-17 04:26 shared
-rwxrwxrwx 2 root root 1000000000 2009-01-17 10:09 swap.disk

=========================== sda2/ubuntu/disks/boot/: ===========================

total 18228
drwxrwxrwx 1 root root    4096 2009-01-17 15:45 .
drwxrwxrwx 1 root root       0 2009-01-17 04:36 ..
-rwxrwxrwx 1 root root  422607 2008-04-10 22:21 abi-2.6.24-16-generic
-rwxrwxrwx 1 root root   79964 2008-04-10 22:21 config-2.6.24-16-generic
drwxrwxrwx 1 root root       0 2009-01-17 15:45 grub
-rwxrwxrwx 1 root root 7885620 2009-01-17 15:45 initrd.img-2.6.24-16-generic
-rwxrwxrwx 1 root root 7349268 2008-04-22 23:30 initrd.img-2.6.24-16-generic.bak
-rwxrwxrwx 1 root root  103204 2007-09-28 15:36 memtest86+.bin
-rwxrwxrwx 1 root root  899892 2008-04-10 22:21 System.map-2.6.24-16-generic
-rwxrwxrwx 1 root root 1904248 2008-04-10 22:21 vmlinuz-2.6.24-16-generic

========================= sda2/ubuntu/disks/boot/grub: =========================

total 21
drwxrwxrwx 1 root root    0 2009-01-17 15:45 .
drwxrwxrwx 1 root root 4096 2009-01-17 15:45 ..
-rwxrwxrwx 1 root root  191 2009-01-17 15:45 default
-rwxrwxrwx 1 root root   30 2009-01-17 15:45 device.map
-rwxrwxrwx 1 root root 4803 2009-01-17 15:45 menu.lst
-rwxrwxrwx 1 root root 4293 2009-01-17 15:45 menu.lst~

========================= sda2/ubuntu/disks/boot/grub: =========================

total 21
drwxrwxrwx 1 root root    0 2009-01-17 15:45 .
drwxrwxrwx 1 root root 4096 2009-01-17 15:45 ..
-rwxrwxrwx 1 root root  191 2009-01-17 15:45 default
-rwxrwxrwx 1 root root   30 2009-01-17 15:45 device.map
-rwxrwxrwx 1 root root 4803 2009-01-17 15:45 menu.lst
-rwxrwxrwx 1 root root 4293 2009-01-17 15:45 menu.lst~

=================== sda2: Location  of files loaded by Grub: ===================


  82.7GB: ubuntu/disks/boot/grub/menu.lst
  82.6GB: ubuntu/disks/boot/initrd.img-2.6.24-16-generic
  82.5GB: ubuntu/disks/boot/initrd.img-2.6.24-16-generic.bak
  82.5GB: ubuntu/disks/boot/vmlinuz-2.6.24-16-generic

================================== sda4/boot: ==================================

total 8708
drwxrwxrwx 1 root root   12288 2009-01-09 07:17 .
drwxrwxrwx 1 root root   12288 2009-01-18 13:55 ..
-rwxrwxrwx 1 root root   28672 2009-01-17 19:22 BCD
-rwxrwxrwx 1 root root  262144 2009-01-17 19:22 BCD.LOG
-rwxrwxrwx 2 root root  262144 2006-08-29 15:17 bcd.LOG1
-rwxrwxrwx 2 root root       0 2006-08-29 15:17 bcd.LOG2
-rwxrwxrwx 1 root root    1024 2006-07-06 13:46 BOOTFIX.BIN
-rwxrwxrwx 1 root root 3170304 2006-05-19 13:30 boot.sdi
-rwxrwxrwx 1 root root   87552 2006-11-02 06:00 BOOTSECT.EXE
-rwxrwxrwx 1 root root     891 2008-09-06 16:49 Desktop.ini
-rwxrwxrwx 1 root root    2048 2006-09-18 18:57 ETFSBOOT.COM
-rwxrwxrwx 1 root root    8134 2002-09-10 21:44 Folder.htt
drwxrwxrwx 1 root root       0 2008-08-13 20:14 FONTS
-rwxrwxrwx 1 root root  385024 2006-08-13 23:10 memtest.exe
-rwxrwxrwx 2 root root  181898 2002-09-16 20:07 protect.chinese hong kong
-rwxrwxrwx 2 root root  181916 2002-09-16 20:07 protect.chinese simplified
-rwxrwxrwx 2 root root  181898 2002-09-16 20:07 protect.chinese traditional
-rwxrwxrwx 2 root root  181865 2006-04-27 21:49 protect.czech
-rwxrwxrwx 2 root root  181726 2005-11-03 20:51 protect.danish
-rwxrwxrwx 2 root root  181605 2002-09-10 19:26 protect.dutch
-rwxrwxrwx 1 root root  181651 2002-09-10 19:20 Protect.ed
-rwxrwxrwx 2 root root  181648 2004-11-22 20:58 protect.english
-rwxrwxrwx 2 root root  181673 2005-11-03 20:50 protect.finnish
-rwxrwxrwx 2 root root  181736 2005-11-03 20:49 protect.french
-rwxrwxrwx 2 root root  181669 2005-11-03 20:48 protect.german
-rwxrwxrwx 2 root root  182689 2005-11-23 21:26 protect.greek
-rwxrwxrwx 2 root root  182605 2006-01-23 14:48 protect.hebrew
-rwxrwxrwx 2 root root  181696 2007-08-28 20:28 protect.hungarian
-rwxrwxrwx 2 root root  181554 2005-11-03 20:47 protect.italian
-rwxrwxrwx 2 root root  182566 2006-04-10 15:16 protect.japanese
-rwxrwxrwx 2 root root  218295 2005-11-24 16:54 protect.korean
-rwxrwxrwx 2 root root  181578 2005-11-03 20:45 protect.norwegian
-rwxrwxrwx 2 root root  181789 2006-04-25 20:14 protect.polish
-rwxrwxrwx 2 root root  181624 2005-11-03 20:43 protect.portuguese
-rwxrwxrwx 2 root root  181882 2005-10-28 00:54 protect.portuguese brazilian
-rwxrwxrwx 2 root root  211936 2004-06-28 14:22 protect.russian
-rwxrwxrwx 2 root root  181586 2005-11-03 20:41 protect.spanish
-rwxrwxrwx 2 root root  181602 2002-09-10 19:45 protect.swedish
-rwxrwxrwx 2 root root  181783 2003-08-12 16:07 protect.turkish

=============================== StdErr Messages: ===============================

No errors were reported.

```
thanks john..

---

### Post by caljohnsmith on 2009-01-22
OK, I see your swap file is actually in the sda2 partition and not sda7, so that was my mistake. How about trying the commands from post #5 again, but change "sda7" to "sda2" in the first mount command. Let me know how that goes.

---

### Post by venkatesh_b87 on 2009-01-23
```
root@hari-laptop:~# sudo mount /dev/sda2 /mnt
root@hari-laptop:~# ls -l /mnt/ubuntu/disks/swap.disk
-rwxrwxrwx 2 root root 1000000000 2009-01-17 10:09 /mnt/ubuntu/disks/swap.disk
root@hari-laptop:~# sudo swapoff -a
root@hari-laptop:~# sudo dd if=/dev/zero of=/mnt/ubuntu/disks/swap.disk bs=1M count=1024

1024+0 records in
1024+0 records out
1073741824 bytes (1.1 GB) copied, 41.4908 s, 25.9 MB/s
root@hari-laptop:~# 
root@hari-laptop:~# sudo mkswap /mnt/ubuntu/disks/swap.disk
Setting up swapspace version 1, size = 1073737 kB
no label, UUID=7ff2e904-dfcc-4b00-b50a-ec6f09db0100
root@hari-laptop:~# sudo swapon -a
root@hari-laptop:~# free
             total       used       free     shared    buffers     cached
Mem:       3106732    2641092     465640          0     778400    1562396
-/+ buffers/cache:     300296    2806436
Swap:      1048568          0    1048568
root@hari-laptop:~# 
```

---

### Post by caljohnsmith on 2009-01-23
Great, so it looks like you have 1024 MB worth of swap now. Have you tried rebooting?

---

### Post by venkatesh_b87 on 2009-01-23
thanks john.. you are great. i have sufficient swap area to install oracle, although i have some issues in its installation, oracle forums are guiding me.
thank you.

---

### Post by caljohnsmith on 2009-01-23
Glad to hear that worked OK. Good luck getting Oracle going. :)

---

### Post by Joebubba360 on 2009-12-04
@caljohnsmith 

I was able to use your method without a hitch. Thank you so much for the wonderful post!

Joe

---

