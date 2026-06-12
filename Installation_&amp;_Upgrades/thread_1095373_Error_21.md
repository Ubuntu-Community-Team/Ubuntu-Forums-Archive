---
title: "Error 21"
date: 2009-03-13
forum: Installation &amp; Upgrades
---

### Post by blindape on 2009-03-13
Hi,

I recently installed Ubuntu on my Acer Inspire laptop using the wubi installation and it worked great.  This morning I was installing Kubuntu onto a USB HD so I could take it with me on the go and use it with different computers.

However, after installation I re-started the computer and got the following error:

GRUB Loading Stage1.5


GRUB loading, please wait...
Error 21

I have been unable to start the computer form the USB HD or the internal HD.  I can however start it using the ubuntu live CD and I've checked my internal hard drive and everything seems to still be there for both windows vista and ubuntu.  It also looks like Kubuntu was installed on the external HD as well.  I need to be able to use windows for work on Tuesday, is there anything I can do to restore my previous start-up where I selected either to boot to Windows or to Ubuntu?

Regards,

John Curwood

---

### Post by bobmatino17 on 2009-03-13
this could be some help...
[http://ubuntuforums.org/showthread.php?t=1081550]("http://ubuntuforums.org/showthread.php?t=1081550")

---

### Post by kestrel1 on 2009-03-13
Sounds like grub got messed up. Have a look at this to restore grub:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
I know it says about restoring after wipes out grub, but it should still work

---

### Post by blindape on 2009-03-14
Thanks for such a quick response.  It's given me alot of research and for a while I was unsure where to start.  But reading the thread at:
[http://ubuntuforums.org/showthread.php?p=6665548](http://ubuntuforums.org/showthread.php?p=6665548)
It seemed similar to my challenge, so I started following the steps suggested with similar results:

sudo grub

grub> find /boot/grub/stage1

giving the error
Error 15: File not found

I then downloaded the file boot_info_script and ran it.  I was unable to attach the file due to an error on the web page so I have pasted the contents onto the end of this post.  Since my log file is quite different to the one in the other thread I decided not to carry on following its instructions, but to post my results too date here.

One thought that has crossed my mind.  The fact that Unubtu is a wubi install so it's installed inside windows, does this affect how grub is used?

by the way the Live CD I'm using is Ubuntu 8.10.

Once again thanks for your responses.

Regards,

John Curwood.

RESULTS.txt

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #3 in 
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /ntldr /ntdetect.com

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/disks/boot/grub/menu.lst 
                       /ubuntu/winboot/menu.lst /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/disks/root.disk

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5b0ed2a2

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    16,370,234    16,370,172  27 Hidden HPFS/NTFS
/dev/sda2    *     16,370,235    86,654,609    70,284,375   6 FAT16
/dev/sda3          86,654,610   156,296,384    69,641,775   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2087 MB, 2087714816 bytes
2 heads, 63 sectors/track, 32361 cylinders, total 4077568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0048d497

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32     4,077,567     4,077,536   6 FAT16

/dev/sdb1 ends after the last cylinder of /dev/sdb

blkid -c /dev/null: ____________________________________________________________

/dev/ramzswap0: TYPE="swap" 
/dev/sda1: UUID="AA0C919716D9B5D2" LABEL="PQSERVICE" TYPE="ntfs" 
/dev/sda2: UUID="C010996810996666" LABEL="ACER" TYPE="ntfs" 
/dev/sda3: UUID="68D823B3D8237F06" LABEL="DATA" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 
/dev/sdb1: SEC_TYPE="msdos" UUID="D4F2-1057" TYPE="vfat" 

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
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda3 on /media/DATA type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2 on /media/ACER type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)


==================== sda3/ubuntu/disks/boot/grub/menu.lst: ====================

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
# kopt=root=UUID=68D823B3D8237F06 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=68D823B3D8237F06 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=68D823B3D8237F06 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
chainloader	+1


======================== sda3/ubuntu/winboot/menu.lst: ========================

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
	find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
	configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
	fallback 2
	find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
	configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
	fallback 3
	find --set-root --ignore-floppies /menu.lst
	configfile /menu.lst

title find /boot/grub/menu.lst
	fallback 4
	find --set-root --ignore-floppies /boot/grub/menu.lst
	configfile /boot/grub/menu.lst

title find /grub/menu.lst
	fallback 5
	find --set-root --ignore-floppies /grub/menu.lst
	configfile /grub/menu.lst

title commandline
	commandline

title reboot
	reboot

title halt
	halt

=================== sda3: Location of files loaded by Grub: ===================


  71.7GB: ubuntu/disks/boot/grub/menu.lst
  71.7GB: ubuntu/disks/boot/initrd.img-2.6.27-7-generic
  62.0GB: ubuntu/disks/boot/vmlinuz-2.6.27-7-generic

---

### Post by meierfra. on 2009-03-14
It seems that the boot info script did not detect the Kubuntu hard drive.
Was the Kubuntu drive plugged in when  you run the boot info script? 
Or did you install Kubuntu to the 2GB drive /dev/sdb?

---

### Post by blindape on 2009-03-15
I'm not sure if the kubuntu hard-drive was plugged in or not when when I ran that script (i'll re-run with the hard-drive plugged in).  I also want to be able to boot to windows and Ubuntu when the USB hard drive is not plugged.

Cheers,

John.

---

### Post by blindape on 2009-03-15
OK,

Here is the RESULTS.txt file, and this time the USB hard drive was definitely plugged in.

I hope this helps.

Regards,

John Curwood

---

### Post by meierfra. on 2009-03-15
Yup, the Kubuntu drive was detected  this time.  To fix your problem, you need to install Grub to the MBR of the Kubuntu drive, and  install a Windows style MBR to the internal drive:

So boot from the Live CD and open a terminal.

Step 1)  Install Grub to the MBR of the Kubuntu drive:

```
sudo grub 
```

and at the "grub>" prompt.

```
 find /boot/grub/stage2 
```

This will return (hdX,4), where X is a number, probably (hd1,4)

Still at the "grub>" prompt:

```
root (hdX,4)
setup (hdX)
quit

```

(here X  needs to be replaced by the number you got from "/find /boot/grub/stage2")


Step 2)  Install a Windows Type MBR to the internal drive.

```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```


Reboot, with the bios set to boot from the Kubuntu drive.

---

### Post by blindape on 2009-03-15
Thankyou so much, everything is now booting up as it was before the install and I can now go to work on Tuesday.  I really appreciate the contributions of all those that have posted to this thread.

Regards,

John Curwood

---

### Post by meierfra. on 2009-03-15
> everything is now booting up as it was before the instal
Great. Are you also able to boot into Kubuntu?

One more thing.  I suggest to edit your Kubuntu menu.lst. Then you will be able to boot into Vista even if your external drive is plugged in, without having to change the boot order in the bios.

```
gksudo gedit /boot/grub/menu.lst
```


Change your  Vista item to

title		Windows Vista/Longhorn (loader)
root		(hd1,1)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader	+1



Also I'm a little confused about your partition /dev/sda1 (The first partition on the internal drive). The boot info script says that the partition has  a "Vista Operating System". On the other hand it contains some XP boot files (but "boot.ini" is missing).
Can you tell me what is on that partition? I'm the author of the boot info script and I'm trying to  figure out whether the script is malfunctioning or whether you just happen to have  weird partition.

---

