---
title: "Configure Grub after a Wubi installation"
date: 2009-02-18
forum: Installation &amp; Upgrades
---

### Post by MastroLindo on 2009-02-18
Hello all, 

firstly, since this is my first post here, hello to all the community :)

I write here because I am having an issue configuring grub. Normally I don't have a lot of problems with normal installations, but on this machine I have installed ubuntu with wubi from a windows partition, and now the boot is becoming a little complicated and so to understand it better maybe I can have some help here :)

My issue is that right now windows is the default OS selected by grub, while I would like to have ubuntu instead. I tried to change the file /boot/grub/menu.lst switching the default from 0 to 1 (ubuntu is the second item I see in the list) but it didn't work since windows is still selected as default. I think that probably that is because of wubi and the fact that ubuntu is not on a proper partition, right? Anyway I searched a bit and even if I couldn't find my answer, I found out a script that can give nice boot information for me and maybe for the people here to understand my problem, so I will post its output.
Thanks in advance for any help, it is very appreciated :D


```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63. The info in boot sector on the starting 
                       sector of the MFT is wrong. The info in the boot 
                       sector on the starting sector of the MFT Mirror is 
                       wrong.
    Operating System:  
    Boot files/dirs:   /ubuntu/disks/boot/grub/menu.lst 
                       /ubuntu/winboot/menu.lst /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa236a236

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    40,960,079    40,960,017   7 HPFS/NTFS
/dev/sda2          40,960,080   156,295,439   115,335,360   f W95 Ext d (LBA)
/dev/sda5          40,960,143   156,295,439   115,335,297   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="80A02713A0270F6A" LABEL="system" TYPE="ntfs" 
/dev/sda5: UUID="56D828E1D828C15B" LABEL="DATA" TYPE="ntfs" 
/dev/loop0: UUID="24db7c21-d42c-45e6-a2ef-dcdd1c359f7d" TYPE="ext3" 

=============================== "mount" output: ===============================

/host/ubuntu/disks/root.disk on / type ext3 (rw,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/sda5 on /host type fuseblk (rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096)
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
/host/ubuntu/disks/boot on /boot type none (rw,bind)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(1)\WINNT

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

c:\wubildr.mbr="Ubuntu"


==================== sda5/ubuntu/disks/boot/grub/menu.lst: ====================

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
default		1

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
# kopt=root=UUID=56D828E1D828C15B loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio

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
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=56D828E1D828C15B loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=56D828E1D828C15B loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
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
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
chainloader	+1


======================== sda5/ubuntu/winboot/menu.lst: ========================

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

=================== sda5: Location of files loaded by Grub: ===================


  24.5GB: ubuntu/disks/boot/grub/menu.lst
  24.6GB: ubuntu/disks/boot/initrd.img-2.6.27-7-generic
  24.5GB: ubuntu/disks/boot/vmlinuz-2.6.27-7-generic
=========================== Unknown MBRs/Boot Sectors/etc =======================

MFT Sector of sda5

00000000  46 49 4c 45 30 00 03 00  69 fc 68 07 00 00 00 00  |FILE0...i.h.....|
00000010  01 00 01 00 38 00 01 00  98 01 00 00 00 04 00 00  |....8...........|
00000020  00 00 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |................|
00000030  61 00 00 00 00 00 00 00  10 00 00 00 60 00 00 00  |a...........`...|
00000040  00 00 18 00 00 00 00 00  48 00 00 00 18 00 00 00  |........H.......|
00000050  10 fb 36 27 b6 4e c8 01  10 fb 36 27 b6 4e c8 01  |..6'.N....6'.N..|
*
00000070  06 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 00 00 00 00 01 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  30 00 00 00 68 00 00 00  |........0...h...|
000000a0  00 00 18 00 00 00 03 00  4a 00 00 00 18 00 01 00  |........J.......|
000000b0  05 00 00 00 00 00 05 00  10 fb 36 27 b6 4e c8 01  |..........6'.N..|
000000c0  10 fb 36 27 b6 4e c8 01  10 fb 36 27 b6 4e c8 01  |..6'.N....6'.N..|
000000d0  10 fb 36 27 b6 4e c8 01  00 40 00 00 00 00 00 00  |..6'.N...@......|
000000e0  00 40 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |.@..............|
000000f0  04 03 24 00 4d 00 46 00  54 00 00 00 00 00 00 00  |..$.M.F.T.......|
00000100  80 00 00 00 48 00 00 00  01 00 40 00 00 00 01 00  |....H.....@.....|
00000110  00 00 00 00 00 00 00 00  af 03 00 00 00 00 00 00  |................|
00000120  40 00 00 00 00 00 00 00  00 00 3b 00 00 00 00 00  |@.........;.....|
00000130  00 00 3b 00 00 00 00 00  00 00 3b 00 00 00 00 00  |..;.......;.....|
00000140  32 b0 03 00 00 0c 00 00  b0 00 00 00 48 00 00 00  |2...........H...|
00000150  01 00 40 00 00 00 05 00  00 00 00 00 00 00 00 00  |..@.............|
00000160  00 00 00 00 00 00 00 00  40 00 00 00 00 00 00 00  |........@.......|
00000170  00 10 00 00 00 00 00 00  d8 01 00 00 00 00 00 00  |................|
00000180  d8 01 00 00 00 00 00 00  31 01 82 7f 27 00 00 00  |........1...'...|
00000190  ff ff ff ff 00 00 00 00  00 80 00 00 00 00 00 00  |................|
000001a0  00 80 00 00 00 00 00 00  31 08 00 00 0c 00 01 00  |........1.......|
000001b0  b0 00 00 00 48 00 00 00  01 00 40 00 00 00 05 00  |....H.....@.....|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001d0  40 00 00 00 00 00 00 00  00 10 00 00 00 00 00 00  |@...............|
000001e0  08 00 00 00 00 00 00 00  08 00 00 00 00 00 00 00  |................|
000001f0  31 01 ff ff 0b 00 00 00  ff ff ff ff 00 00 61 00  |1.............a.|
00000200

```

---

### Post by MastroLindo on 2009-02-18
if that helps, i found out that changing default from 0 to 1 altered not the main grub menu, but a submenu.

in practice when i boot I have two options: the first one (default) windows, the second ubuntu


when I choose ubuntu I have 10seconds to press esc to see more options. If i do i can see the traditional grub menu, with ubuntu on top, it-s recovery mode and/or other kernels just under, and at the end windows.

Altering the menu.lst parameters affects this second menu. I need instead to change the first one (and make it choose the ubuntu voice instead of the windows one)

---

### Post by caljohnsmith on 2009-02-18
The "main" boot menu that you see on start up is actually the Windows boot manager, not Grub. Therefore, if you want to make Ubuntu the default in that menu, you need to modify the Windows boot menu, specifically the Windows boot.ini file. You can do that from your Wubi Ubuntu install by doing the following:
```
gksudo gedit /host/boot.ini
```
And change the "default" line in your boot.ini as follows:
```
[boot loader]
timeout=30
[COLOR="Blue"]default=C:\wubildr.mbr[/COLOR]
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP" /fastdetect /NoExecute=OptIn
C:\wubildr.mbr="Ubuntu"
```
After you are done, it is really important to run the following "unix2dos" command on the file:
```
sudo apt-get install tofrodos
unix2dos /host/boot.ini
```
That will ensure that your boot.ini files retains its Windows-style line endings (carriage return + line feed), because Linux text editors just use a single line feed for line endings. Anyway, after doing the above changes, reboot, and let me know how it goes.

---

### Post by MastroLindo on 2009-02-18
perfect now it works perfectly thanks :)

after finding out that the problem was in the boot.ini the modify to do was trivial... (but I would not have known about unix2dos :D )

Thanks!

---

### Post by caljohnsmith on 2009-02-18
Glad to hear that worked OK; cheers and enjoy Ubuntu and Windows. :)

---

