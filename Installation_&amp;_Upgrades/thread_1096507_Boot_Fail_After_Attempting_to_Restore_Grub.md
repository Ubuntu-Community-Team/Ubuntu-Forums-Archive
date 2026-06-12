---
title: "Boot Fail After Attempting to Restore Grub"
date: 2009-03-15
forum: Installation &amp; Upgrades
---

### Post by lemonshark10 on 2009-03-15
Hi I'm not exactly a noob but i'm relativly new at this so here goes. About 3 days ago i had a 100% functional triple boot between Windows vista, Windows 7, and Ubuntu 8.10. I decided to try Arch linux and install it in the partition previously occupied by windows 7.  got through the install but decided not to let Arch put in its own boot loader, i figured i would just edit themenu.lst to allow me to oot into arch using ubuntu. But i could not forthe life of me get grub to boot arch. But then i remembered that When i installed ubuntu it auto detected my windows install and created a grub entry for it, so i thought why couldn't it do that for Arch too. Then i found this link [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

and it said:
> The GUI Way: Using the Alternate/Install CD and Overwriting the Windows bootloader

   1. Boot your computer with the Ubuntu CD
   2. Go through the installation process until you reach "[!!!] Disk Partition"
   3. Select Manual Partition
   4. Mount your appropriate linux partions:
          * /
          * /boot
          * swap
          * ... 
   5.

      DO NOT FORMAT THEM.
   6. Finish the manual partition
   7. Say "Yes" when it asks you to save the changes
   8. It will give you errors saying that "the system couldn't install ....." after that
   9. Ignore them, keep select "continue" until you get back to the Ubuntu installation menu
  10. Jump to "Install Grub ...."
  11. Once it is finished, just restart your computer 

I tried that got to step 8 and clicked continue, then it asked me to type in my name and username and password and such so i just filled the fields to make it happy. Then i got to step 7 out of 7 of the install and it  gave a list of changes that were going to be made, however none of theminvolved overwritting or anything and i thought it was safe so i clicked continue. it popped open a box saying deleting previous files or something to that affect but was frozen. so i quit that and rebooted thinking it did nothing. However when grub tried to boot into ubuntu i got this: 
> Boot from (hd0,4) ext3 ad56c485-e6dc-48fa-b6a7-50cc1fd2c58e
Starting up ...
Loading, please wait...
mount: mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg.


BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

I tried booting into safe mode and with other kernals but i got the same message. I booted a live cd and my home directory is intact.
i would REALLY like to be able to boot back into Ubuntu. i could back up my data and do a fresh install but that would be a last resort. Thank you in advance for the help

With much thanks,
Lemonshark10

---

### Post by meierfra. on 2009-03-15
In order to get a clearer picture of your setup, I suggest to boot from your Ubuntu Live CD (the Ubuntu install CD) and download the Boot Info Script to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by lemonshark10 on 2009-03-15
Ok Here is the result.txt file

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 sda1 ntfs-3g force 0 0
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 sda1 ntfs-3g force 0 0

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda2': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda2 sda2 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda2 sda2 ntfs-3g force 0 0
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda2': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda2 sda2 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda2 sda2 ntfs-3g force 0 0

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  [H[2J Arch Linux () ()
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd16a2c15

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2    *      3,084,480    87,425,729    84,341,250   7 HPFS/NTFS
/dev/sda3          87,425,730   390,716,864   303,291,135   5 Extended
/dev/sda5          87,425,793   329,155,784   241,729,992  83 Linux
/dev/sda6         378,314,748   390,716,864    12,402,117  82 Linux swap / Solaris
/dev/sda7         329,155,848   378,314,684    49,158,837   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="881865A118658ECE" LABEL="TOSHIBA SYSTEM VOLUME" TYPE="ntfs" 
/dev/sda2: UUID="DE8A95E68A95BB89" LABEL="SQ004680V03" TYPE="ntfs" 
/dev/sda5: UUID="ad56c485-e6dc-48fa-b6a7-50cc1fd2c58e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="641634f5-3b82-4495-ab25-bd6074fffeb0" 
/dev/sda7: UUID="770bf718-ad2f-441c-adf2-c375fa53a558" SEC_TYPE="ext2" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


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
# kopt=root=UUID=ad56c485-e6dc-48fa-b6a7-50cc1fd2c58e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ad56c485-e6dc-48fa-b6a7-50cc1fd2c58e

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		ad56c485-e6dc-48fa-b6a7-50cc1fd2c58e
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=ad56c485-e6dc-48fa-b6a7-50cc1fd2c58e ro quiet splash
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		ad56c485-e6dc-48fa-b6a7-50cc1fd2c58e
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=ad56c485-e6dc-48fa-b6a7-50cc1fd2c58e ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		ad56c485-e6dc-48fa-b6a7-50cc1fd2c58e
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=ad56c485-e6dc-48fa-b6a7-50cc1fd2c58e ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		ad56c485-e6dc-48fa-b6a7-50cc1fd2c58e
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=ad56c485-e6dc-48fa-b6a7-50cc1fd2c58e ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		ad56c485-e6dc-48fa-b6a7-50cc1fd2c58e
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ad56c485-e6dc-48fa-b6a7-50cc1fd2c58e ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		ad56c485-e6dc-48fa-b6a7-50cc1fd2c58e
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ad56c485-e6dc-48fa-b6a7-50cc1fd2c58e ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		ad56c485-e6dc-48fa-b6a7-50cc1fd2c58e
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

title		Arch Linux
uuid		770bf718-ad2f-441c-adf2-c375fa53a558
kernel		/boot/vmlinuz26 root=UUID=770bf718-ad2f-441c-adf2-c375fa53a558 ro
initrd		/boot/kernel26.img


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/local/sbin/update-grub using templates
# from /usr/local/etc/grub.d and settings from /usr/local/etc/default/grub
#

### BEGIN /usr/local/etc/grub.d/00_header ###
set default=0
set timeout=5
set root=(hd0,5)
terminal console
### END /usr/local/etc/grub.d/00_header ###

### BEGIN /usr/local/etc/grub.d/10_hurd ###
### END /usr/local/etc/grub.d/10_hurd ###

### BEGIN /usr/local/etc/grub.d/10_linux ###
menuentry "GNU/Linux, linux 2.6.27-9-generic" {
	linux	(hd0,5)/boot/vmlinuz-2.6.27-9-generic root=/dev/sda5 ro 
	initrd	(hd0,5)/boot/initrd.img-2.6.27-9-generic
}
menuentry "GNU/Linux, linux 2.6.27-9-generic (single-user mode)" {
	linux	(hd0,5)/boot/vmlinuz-2.6.27-9-generic root=/dev/sda5 ro single 
	initrd	(hd0,5)/boot/initrd.img-2.6.27-9-generic
}
menuentry "GNU/Linux, linux 2.6.27-7-generic" {
	linux	(hd0,5)/boot/vmlinuz-2.6.27-7-generic root=/dev/sda5 ro 
	initrd	(hd0,5)/boot/initrd.img-2.6.27-7-generic
}
menuentry "GNU/Linux, linux 2.6.27-7-generic (single-user mode)" {
	linux	(hd0,5)/boot/vmlinuz-2.6.27-7-generic root=/dev/sda5 ro single 
	initrd	(hd0,5)/boot/initrd.img-2.6.27-7-generic
}
menuentry "GNU/Linux, linux 2.6.27-11-generic" {
	linux	(hd0,5)/boot/vmlinuz-2.6.27-11-generic root=/dev/sda5 ro 
	initrd	(hd0,5)/boot/initrd.img-2.6.27-11-generic
}
menuentry "GNU/Linux, linux 2.6.27-11-generic (single-user mode)" {
	linux	(hd0,5)/boot/vmlinuz-2.6.27-11-generic root=/dev/sda5 ro single 
	initrd	(hd0,5)/boot/initrd.img-2.6.27-11-generic
}
### END /usr/local/etc/grub.d/10_linux ###

=================== sda5: Location of files loaded by Grub: ===================


 145.9GB: boot/grub/grub.cfg
 145.9GB: boot/grub/menu.lst
 145.8GB: boot/grub/stage2
 145.4GB: boot/initrd.img-2.6.27-11-generic
 145.4GB: boot/initrd.img-2.6.27-7-generic
 145.5GB: boot/initrd.img-2.6.27-9-generic
 145.5GB: boot/vmlinuz-2.6.27-11-generic
 145.5GB: boot/vmlinuz-2.6.27-7-generic
 145.5GB: boot/vmlinuz-2.6.27-9-generic
 145.4GB: initrd.img
 145.5GB: initrd.img.old
 145.5GB: vmlinuz
 145.5GB: vmlinuz.old

=========================== sda7/boot/grub/menu.lst: ===========================

# Config file for GRUB - The GNU GRand Unified Bootloader
# /boot/grub/menu.lst

# DEVICE NAME CONVERSIONS 
#
#  Linux           Grub
# -------------------------
#  /dev/fd0        (fd0)
#  /dev/sda        (hd0)
#  /dev/sdb2       (hd1,1)
#  /dev/sda3       (hd0,2)
#

#  FRAMEBUFFER RESOLUTION SETTINGS
#     +-------------------------------------------------+
#          | 640x480    800x600    1024x768   1280x1024
#      ----+--------------------------------------------
#      256 | 0x301=769  0x303=771  0x305=773   0x307=775
#      32K | 0x310=784  0x313=787  0x316=790   0x319=793
#      64K | 0x311=785  0x314=788  0x317=791   0x31A=794
#      16M | 0x312=786  0x315=789  0x318=792   0x31B=795
#     +-------------------------------------------------+
#  for more details and different resolutions see
#  http://wiki.archlinux.org/index.php/GRUB#Framebuffer_Resolution 

# general configuration:
timeout   5
default   0
color light-blue/black light-cyan/blue

# boot sections follow
# each is implicitly numbered from 0 in the order of appearance below
#
# TIP: If you want a 1024x768 framebuffer, add "vga=773" to your kernel line.
#
#-*

# (0) Arch Linux
title  Arch Linux  [/boot/vmlinuz26]
root   (hd0,0)
kernel /vmlinuz26 root=/dev/sda3 ro
initrd /kernel26.img

# (1) Windows
#title Windows
#rootnoverify (hd0,0)
#makeactive
#chainloader +1

=============================== sda7/etc/fstab: ===============================

# 
# /etc/fstab: static file system information
#
# <file system>        <dir>         <type>    <options>          <dump> <pass>
none                   /dev/pts      devpts    defaults            0      0
none                   /dev/shm      tmpfs     defaults            0      0

#/dev/cdrom             /media/cd   auto    ro,user,noauto,unhide   0      0
#/dev/dvd               /media/dvd  auto    ro,user,noauto,unhide   0      0
#/dev/fd0               /media/fl   auto    user,noauto             0      0

UUID=641634f5-3b82-4495-ab25-bd6074fffeb0 swap swap defaults 0 0
UUID=770bf718-ad2f-441c-adf2-c375fa53a558 / ext3 defaults,noatime 0 1

=================== sda7: Location of files loaded by Grub: ===================


 184.1GB: boot/grub/menu.lst
 183.9GB: boot/vmlinuz26

```

thank you again for the help

---

### Post by meierfra. on 2009-03-15
> it popped open a box saying deleting previous files 

Well, it seems that various files from your Ubuntu partition got deleted. 

From RESULT.txt. I know that /etc/fstab and /etc/issue are missing. And the error message you got, seems to indicate that lots of  other files are missing.

Could you post the output of 

```
sudo mount /dev/sda5 /mnt
ls /mnt
ls /mnt/etc
```
 
do see what else might be missing.

---

### Post by lemonshark10 on 2009-03-15
Well here is the result for ls /mnt:
```
boot
cdrom
home
initrd.img
initrd.img.old
lost+found
media
mnt
opt
root
srv
sys
tmp
usr
var
vmlinuz
vmlinuz.old

```

but /mnt/etc doesn't exist so ls just gave me an error

---

### Post by meierfra. on 2009-03-15
/etc, /bin, /dev, /lib, and /proc are missing.

You might be able to use photorec to recover those directories. But I believe backing up your data and reinstalling is the easiest solution. 
You might consider creating a separate /home or /data partition.

---

### Post by lemonshark10 on 2009-03-15
Ok i will most likely back up and reinstall thank you for your help again

---

