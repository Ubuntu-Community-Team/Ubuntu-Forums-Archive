---
title: "Boot Error"
date: 2009-01-31
forum: Installation &amp; Upgrades
---

### Post by sunnny on 2009-01-31
Hi All

I am new to ubuntu.
I have installed Ubuntu 8.10 yesterday and installation was successfully completed. when i tried to boot from the hard disk i got this error:-

[B]Reboot and Select proper Boot device
or Insert Boot Media in selected Boot device and press a key[/B]

I have checked in bios, it is showing the harddisk as a primary master.

Please Suggest

Thanks for help

---

### Post by dstew on 2009-01-31
Are you sure your BIOS was set to boot the hard drive? A hard drive can be designated as a primary master, but you still need to tell the BIOs to boot it.

---

### Post by caljohnsmith on 2009-01-31
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by sunnny on 2009-02-01
yes i am sure that i am booting from the right hard disk....

Thanks caljohnsmith i will try what you have suggested me and will post the reslut as soon as posible..

---

### Post by sunnny on 2009-02-10
Sorry for the late reply 
here is the content of the result file

```


============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders, total 78242976 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcdfab0e8

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     4,883,759     4,883,697  82 Linux swap / Solaris
/dev/sda2           4,883,760    78,236,549    73,352,790   5 Extended
/dev/sda5           4,883,823    78,236,549    73,352,727  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: TYPE="swap" UUID="3583354d-b7f1-42e0-aace-75a6bdeac8f2" 
/dev/sda5: UUID="6f9f2555-bac3-4313-8d2d-c6e1be937e71" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd1 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda5 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)

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
# kopt=root=UUID=6f9f2555-bac3-4313-8d2d-c6e1be937e71 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=6f9f2555-bac3-4313-8d2d-c6e1be937e71

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
uuid		6f9f2555-bac3-4313-8d2d-c6e1be937e71
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=6f9f2555-bac3-4313-8d2d-c6e1be937e71 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		6f9f2555-bac3-4313-8d2d-c6e1be937e71
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=6f9f2555-bac3-4313-8d2d-c6e1be937e71 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		6f9f2555-bac3-4313-8d2d-c6e1be937e71
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=6f9f2555-bac3-4313-8d2d-c6e1be937e71 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=3583354d-b7f1-42e0-aace-75a6bdeac8f2 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  35.3GB: boot/grub/menu.lst
  35.5GB: boot/grub/stage2
  35.4GB: boot/initrd.img-2.6.27-7-generic
  35.4GB: boot/vmlinuz-2.6.27-7-generic
  35.4GB: initrd.img
  35.4GB: vmlinuz

```

---

### Post by caljohnsmith on 2009-02-10
It looks like your Grub is configured just fine, and I don't see anything else about your HDD setup that would prevent you from booting. Therefore I think it must be a BIOS issue of some sort. Have you checked your BIOS boot order to make sure your HDD is listed there as dstew mentioned? I would try setting your HDD as first to boot before any of your other drives to see if that is the issue. Good luck and let us know how it goes.

---

### Post by sunnny on 2009-02-14
Hi
I have checked bios setting there is nothing wrong with it.
harddisk is set as a master and also in the boot order.

---

### Post by caljohnsmith on 2009-02-14
Have you checked the jumper settings on that HDD? Is the HDD jumpered for "master"? Also, what HDD-related BIOS settings do you have available? Look for settings like "auto-detect", LBA, CHS, RAID, AHCI/HCI/EHCI vs. IDE, IDE-emulation, legacy IDE, native IDE, ACPI, DMA, etc. and please let me know what you find.

---

### Post by sunnny on 2009-02-19
Thanks for the gr8 help...
but there is some problem with my harddisk i guess ...;)

---

### Post by andywragg on 2009-02-19
I too am having the exact error as you. I have essentially blown away my Windows 2003 server OS and replaced it with Ubuntu 8.10. Had to completely remove all NTFS partitions first and turn off my SATA Raid controller (2 x 80GB SATA drives attached for file storage) in BIOS. All I have left now is my 40GB ATA drive which was the boot/system disk for windows, which is where I have installed Ubuntu 8.10. Installation seems fine (plenty of HDD activity) then nothing after the reboot. I thought these free distributions were supposed to be the mutts nuts. I think I'll go back to billyware.

---

### Post by andywragg on 2009-02-19
OK 
It seems that Server doesnt like my hardware or there is a bug in the code, but desktop goes on just fine. 
I removed the Ubuntu server Partition using my favourite magic tools disk and then installed the desktop version. No problems what so ever. No changes to BIOS required, it just works.

AOpen/Via ak77-KT600 with VT8237 Southbridge chipset
Athlon XP
2GB RAM
1 x 40GB ATA disk for OS
2 x 80GB SATA disks for files

---

