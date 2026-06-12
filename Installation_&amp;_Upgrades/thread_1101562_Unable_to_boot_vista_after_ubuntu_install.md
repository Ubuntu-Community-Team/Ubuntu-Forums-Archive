---
title: "Unable to boot vista after ubuntu install"
date: 2009-03-20
forum: Installation &amp; Upgrades
---

### Post by harunahi on 2009-03-20
Hi, 

I have installed Ubuntu as a dual boot system with Vista.

However, now when I try to boot to Vista the system hangs at 'Starting...' after selecting Vista from Grub.

I tried repairing using the Vista DVD but that has made no difference. Ubuntu boots fine and I have access to the Vista partition from there, but I can't boot into Vista.

Can anyone advise what the problem might be?

Thanks!

---

### Post by meierfra. on 2009-03-20
In order to get a clearer picture of your setup, I suggest to boot into  Ubuntu  and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by harunahi on 2009-03-20
Thank you very much for your reply!

As requested:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 2048. But according to the info from fdisk, 
                       sda1 starts at sector 63.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

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
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa1f4d1db

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   614,405,924   614,405,862   7 HPFS/NTFS
/dev/sda2         614,405,925   976,768,064   362,362,140   5 Extended
/dev/sda5         614,405,988   633,940,964    19,534,977  82 Linux swap / Solaris
/dev/sda6         633,941,028   976,768,064   342,827,037  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="52540AC3540AA9B5" TYPE="ntfs" 
/dev/sda5: UUID="da4f3004-c1d8-49fb-8d4b-4d9d8919024c" TYPE="swap" 
/dev/sda6: UUID="901c0ea0-e7b6-4d3b-b820-3ebe19c46dcf" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
/dev/sda1 on /windows type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jon/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jon)


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
# kopt=root=UUID=901c0ea0-e7b6-4d3b-b820-3ebe19c46dcf ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=901c0ea0-e7b6-4d3b-b820-3ebe19c46dcf

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
uuid		901c0ea0-e7b6-4d3b-b820-3ebe19c46dcf
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=901c0ea0-e7b6-4d3b-b820-3ebe19c46dcf ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		901c0ea0-e7b6-4d3b-b820-3ebe19c46dcf
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=901c0ea0-e7b6-4d3b-b820-3ebe19c46dcf ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		901c0ea0-e7b6-4d3b-b820-3ebe19c46dcf
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=901c0ea0-e7b6-4d3b-b820-3ebe19c46dcf ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		901c0ea0-e7b6-4d3b-b820-3ebe19c46dcf
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=901c0ea0-e7b6-4d3b-b820-3ebe19c46dcf ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		901c0ea0-e7b6-4d3b-b820-3ebe19c46dcf
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


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=901c0ea0-e7b6-4d3b-b820-3ebe19c46dcf /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=52540AC3540AA9B5 /windows        ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=da4f3004-c1d8-49fb-8d4b-4d9d8919024c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 432.3GB: boot/grub/menu.lst
 432.3GB: boot/grub/stage2
 432.4GB: boot/initrd.img-2.6.27-11-generic
 432.4GB: boot/initrd.img-2.6.27-7-generic
 432.4GB: boot/vmlinuz-2.6.27-11-generic
 432.4GB: boot/vmlinuz-2.6.27-7-generic
 432.4GB: initrd.img
 432.4GB: initrd.img.old
 432.4GB: vmlinuz
 432.4GB: vmlinuz.old
```

---

### Post by meierfra. on 2009-03-20
>  Boot sector info:  According to the info in the boot sector, sda1 starts  at sector 2048. But according to the info from fdisk, sda1 starts at sector 63.


Your Windows boot sector needs some fixing:

 Download the [testdisk-6.10.linux26.tar.bz2 package](http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2) to your desktop, and then do:

```


cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static /dev/sda

```

Choose "proceed" on the first screen, then
"intel"
"advanced",
Select the Windows partition (although it should be selected already) and choose
"boot"
"RebuildBS"
"Write"  

Then press "q" a few times to quit  testdisk, reboot and see whether you can boot into Vista.
 (If it does not give you an option to "write", it means that the original and rebuild boot sector are identical, and  testdisk RebuildBS won't be able to solve your problem)


This should take care of your "starting up" problem.  But I suspect that you will be greeted by a blue screen of death when you try to boot  Vista.  If this is the case, check out this link:

[http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/)

---

### Post by harunahi on 2009-03-20
Fantastic!

Worked a treat and didn't even get the blue screen of death!

Greatly appreciated. Thank you very much indeed!

---

### Post by meierfra. on 2009-03-20
> Worked a treat and didn't even get the blue screen of death!

Great. Have fun with Ubuntu and Vista.

---

