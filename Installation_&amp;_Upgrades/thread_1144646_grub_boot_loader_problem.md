---
title: "grub boot loader problem"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by gangesh7 on 2009-04-30
hi!

i would like to know- how to re install grub bootloader (by live cd )as it is creating problems and i am not able to boot the system. i have windows xp and mint 5.0

---

### Post by meierfra. on 2009-05-01
> I would like to know- how to re install grub bootloader (by live cd )
See

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)


[B]If you need additional help:
[/B]
Describe  your problem in more detail. 
Do you get any error messaages?
Boot from the Ubuntu LiveCD and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post,  highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by gangesh7 on 2009-05-05
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 5 Elyssa
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xed19ed19

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    62,910,539    62,910,477   7 HPFS/NTFS
/dev/sda2          62,910,540   243,111,644   180,201,105   f W95 Ext d (LBA)
/dev/sda5          62,910,603   125,821,079    62,910,477   7 HPFS/NTFS
/dev/sda6         125,821,143   223,480,214    97,659,072  83 Linux
/dev/sda7         223,480,278   227,480,399     4,000,122  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="946C7EB86C7E9528" TYPE="ntfs" 
/dev/sda5: UUID="3694C30E94C2D013" TYPE="ntfs" 
/dev/sda6: UUID="2ff79fa7-cf9e-45d4-b629-765a2cda8381" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="05bc5d5f-7e55-4903-9b7b-68dbaa4fc9e8" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.17-10-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.17-10-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.17-10-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/mint/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mint)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda6/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

gfxmenu=/etc/grub/message.elyssa

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/sda6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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
##      altoptions=(recovery mode) single
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

title		Linux Mint, kernel 2.6.24-16-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sda6 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic

title		Linux Mint, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sda6 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Linux Mint, kernel memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
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
UUID=2ff79fa7-cf9e-45d4-b629-765a2cda8381 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=05bc5d5f-7e55-4903-9b7b-68dbaa4fc9e8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


  88.1GB: boot/grub/menu.lst
  88.1GB: boot/grub/stage2
  88.0GB: boot/initrd.img-2.6.24-16-generic
  88.1GB: boot/initrd.img-2.6.24-16-generic.bak
  88.1GB: boot/vmlinuz-2.6.24-16-generic
  88.0GB: initrd.img
  88.1GB: vmlinuz```

```

---

### Post by flatwombat on 2009-05-05
This may or may not be involved, but I'm booting 8 distros from grub (PCLOS is on the mbr) and all but 9.04 had booted properly with configfile entries: 

(example)

title Linux whatever
configfile (hd1,3)/boot/grub/menu.lst

However, Ubuntu 9.04 was the only entry that has ever failed by this method.  Turns out that Ubuntu 9.04 does not identify the root partition in it's menu entry and grub is completely lost trying to find it.  The simple solution is to mount Ubuntu from another distro, etc., and add a line such as "root=(hd0,4)".  

So, if XP and Mint are booting properly, give that a try before reinstalling grub.

---

### Post by meierfra. on 2009-05-05
The boot_info_script did not detect any problems. Grub seems to be configured correctly.  So if you would like some help you really need to describe your  situation in more detail.

What exactly happens when you try to boot?
Are you able to boot into XP?
Are you able to boot into Linux Mint?
Did you just install Linux Mint?
Did you just install Windows XP?
Do you get any error messaages?
Does the Grub menu appear?

---

### Post by gangesh7 on 2009-05-06
as u have asked me about the problem in detail, i m just answering the way you have asked and hope to get a quick response as i m facing severe problems.

regards```

```

What exactly happens when you try to boot?=boot loader menu doesn't appear
Are you able to boot into XP?=no
Are you able to boot into Linux Mint?=no
Did you just install Linux Mint?=1 month ago
Did you just install Windows XP?=no
Do you get any error messaages?=now i m getting error 18
Does the Grub menu appear?=no```

```

---

