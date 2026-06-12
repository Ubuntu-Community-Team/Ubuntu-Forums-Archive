---
title: "LILO or GRUB?"
date: 2009-06-16
forum: Installation &amp; Upgrades
---

### Post by nodger on 2009-06-16
How do I find out if I'm using Lilo or Grub?

I'm using Ubuntu Jaunty (upgraded from 8) and I also have a virus-ridden Vista on my laptop which I want to replace with XP. I know that when I do this I won't be able to boot into Ubuntu until I get the disk (which I've no idea where is is)

So is there any program on XP I can use to overwrite the LILO (or GRUB) and have a dual-boot with XP and Ubuntu.

Sorry, I'm rubbish with these things

---

### Post by Sef on 2009-06-16
Ubuntu uses GRUB.  [Super GRUB Disk]("http://supergrubdisk.org") is what you need to restore GRUB after installing XP.

---

### Post by nodger on 2009-06-16
And this will solve all my problems?
Nice..
:popcorn:

---

### Post by Sef on 2009-06-16
> And this will solve all my problems?

Yes. It will.

---

### Post by Sef on 2009-06-16
> And this will solve all my problems?

Yes. It will.

>  So is there any program on XP I can use to overwrite the LILO (or GRUB) and have a dual-boot with XP and Ubuntu.

No, Windows only see windows oses.

---

### Post by Reymond on 2009-06-16
> **Sef said:**
> Ubuntu uses GRUB.  [Super GRUB Disk]("http://supergrubdisk.org") is what you need to restore GRUB after installing XP.
Sorry, but I'm having similar type of problem as 'nodger' has. If you kindly explain in a little more detailed way how to restore GRUB after installing XP , it'll be more helpful to me.

---

### Post by unutbu on 2009-06-16
Reymond, this should help: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by nodger on 2009-06-16
> **Sef said:**
> Yes. It will.



No, Windows only see windows oses.

I'm pretty sure I used a Windows program before that installed a boot menu for me. I can't remember the name of it though

---

### Post by Steven Edwards on 2009-06-23
> **Sef said:**
> Ubuntu uses GRUB.  [Super GRUB Disk]("http://supergrubdisk.org") is what you need to restore GRUB after installing XP. Can I use Super GRUB Disk to easily replace LILO with GRUB if I'm using LVM2?

---

### Post by unutbu on 2009-06-23
Super GRUB Disk can install GRUB, thus replacing any boot loader (e.g. LILO).

GRUB can not read LVM2. 
I don't think LILO can read LVM2 either -- though I'm not sure.

To boot an OS which is inside an LVM, you need a /boot partition which exists in a normal partition outside the LVM.

---

### Post by Steven Edwards on 2009-06-23
> **unutbu said:**
> Super GRUB Disk can install GRUB, thus replacing any boot loader (e.g. LILO).

GRUB can not read LVM2. 
I don't think LILO can read LVM2 either -- though I'm not sure. Thanks unutbu.

The upgrade to 2.6.28-13 caused my graphics to go bye-bye (Radeon HD 3450, supposed to be supported).  LILO is my bootloader and I'm trying to 1) see if the 2.6.28-11 kernel still exists and, if so, 2) change LILO's configuration to point to it.

KVPM (via the 9.04 LiveDVD) can see the volumes, but can't mount any of them.  (Nor can the command line equivalents.)

Can the Super GRUB disk help me there? :)

ETA: /dev/sda1 contains GRUB, but my computer always uses LILO.

---

### Post by irv on 2009-06-23
> **nodger said:**
> I'm pretty sure I used a Windows program before that installed a boot menu for me. I can't remember the name of it though

From the Windows install CD I ran a fix on the MBR. I don't remember what the command was, but you could google it. I remember after running it I could boot to the Grub menu and go into Windows or Ubuntu.
So you are right, it can be done.

---

### Post by unutbu on 2009-06-23
Steven Edwards,

I don't know enough about LILO to help you boot the 2.6.28-11 kernel using it.

Did you upgrade the kernel by installing the 
linux-image-2.6.28-13-generic package? If so, you should be okay, since this 
does not remove the linux-image-2.6.28-11-generic package. 
So the 2.6.28-11 kernel (and all the attendant /lib/modules/*) should still exist.

If you had been using GRUB, your GRUB boot menu would have allowed you to 
select the 2.6.28-11 kernel and boot from it if the *-13 kernel did not work.
On this basis, it seems perhaps moving to GRUB would be an improvement.

If you'd like to try booting with GRUB, please first run [boot_info_script]("http://ubuntuforums.org/showpost.php?p=6725571&postcount=3") and post the RESULTS.txt file here.

---

### Post by Steven Edwards on 2009-06-23
> **unutbu said:**
> Did you upgrade the kernel by installing the 
linux-image-2.6.28-13-generic package? I ran the updates that came via the Update Manager yesterday, which included 2.6.28-13.  I'm pretty sure it was -generic.

My RESULTS.txt, with the caveat that GRUB in /dev/sda1 was from an install a few weeks prior to the one I'm using now:

```
============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda
 => No known boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       lvm2pv
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'lvm2pv'

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       lvm2pv
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'lvm2pv'

sdd1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /BOOT.INI

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd6afe16e

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63       257,039       256,977  83 Linux
/dev/sda2             257,040 2,930,272,064 2,930,015,025   5 Extended
/dev/sda5             257,103 2,930,272,064 2,930,014,962  8e Linux LVM


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x076923f6

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   586,099,394   586,099,332   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x97be5b6a

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   976,768,064   976,768,002  8e Linux LVM


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 180.0 GB, 180045766656 bytes
255 heads, 63 sectors/track, 21889 cylinders, total 351651888 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf051f051

Partition  Boot         Start           End          Size  Id System

/dev/sdd1              16,065   351,646,784   351,630,720   f W95 Ext d (LBA)
/dev/sdd5              16,128   351,646,784   351,630,657   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="ba9a3955-0b9c-4660-9852-0f9f405d2f8e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="uZ1fiS-5Wo4-VNzC-gzs0-ekVz-Bepn-1MZe82" TYPE="lvm2pv" 
/dev/sdb1: UUID="C050E38D50E3888C" LABEL="300gb" TYPE="ntfs" 
/dev/sdc1: UUID="Lbh2zY-y9I8-P0Zz-517G-veEW-NiE4-CLBr2W" TYPE="lvm2pv" 
/dev/sdd5: UUID="3EEE-E8F1" TYPE="vfat" 
/dev/mapper/main-swap: UUID="888a898b-129f-440a-9d0d-f11b21b92c74" TYPE="swap" 
/dev/mapper/main-root: UUID="07ca8a50-ad66-4b64-96e0-6ca94705e8d3" TYPE="jfs" 
/dev/mapper/main-usr: UUID="daba50c9-46a4-44b4-9c35-cbe651bbb0ef" TYPE="jfs" 
/dev/mapper/main-var: UUID="b4d08a51-5dba-4de2-a81f-979bc6cccb03" TYPE="jfs" 
/dev/mapper/main-tmp: UUID="806817ff-cb8f-4a4f-892c-34c15c03983a" TYPE="jfs" 
/dev/mapper/main-home: UUID="f3a995d9-9b22-4646-8bc4-aff140fa2263" TYPE="jfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


============================= sda1/grub/menu.lst: =============================

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
# kopt=root=/dev/mapper/main-root ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ba9a3955-0b9c-4660-9852-0f9f405d2f8e

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
uuid		ba9a3955-0b9c-4660-9852-0f9f405d2f8e
kernel		/vmlinuz-2.6.27-11-generic root=/dev/mapper/main-root ro quiet splash noapic nolapic
initrd		/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		ba9a3955-0b9c-4660-9852-0f9f405d2f8e
kernel		/vmlinuz-2.6.27-11-generic root=/dev/mapper/main-root ro  single
initrd		/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		ba9a3955-0b9c-4660-9852-0f9f405d2f8e
kernel		/vmlinuz-2.6.27-7-generic root=/dev/mapper/main-root ro quiet splash irqpoll 
initrd		/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		ba9a3955-0b9c-4660-9852-0f9f405d2f8e
kernel		/vmlinuz-2.6.27-7-generic root=/dev/mapper/main-root ro  single
initrd		/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		ba9a3955-0b9c-4660-9852-0f9f405d2f8e
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title		Microsoft Windows XP Home Edition
root		(hd1,1)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


=================== sda1: Location of files loaded by Grub: ===================


    .0GB: grub/menu.lst
    .0GB: grub/stage2
    .0GB: initrd.img-2.6.27-11-generic
    .0GB: initrd.img-2.6.27-7-generic
    .0GB: vmlinuz-2.6.27-11-generic
    .0GB: vmlinuz-2.6.27-7-generic

================================ sdd5/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(3)\XP

[operating systems]

multi(0)disk(0)rdisk(0)partition(3)\XP="Microsoft Windows XP Professional Edition" /fastdetect

C:\="Microsoft Windows"

multi(0)disk(0)rdisk(0)partition(1)\="Microsoft Windows ME" /fastdetect

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows ME/0" /fastdetect

C:\bootsect.lnx="Gentoo Linux"


================================ sdd5/BOOT.INI: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(3)\XP

[operating systems]

multi(0)disk(0)rdisk(0)partition(3)\XP="Microsoft Windows XP Professional Edition" /fastdetect

C:\="Microsoft Windows"

multi(0)disk(0)rdisk(0)partition(1)\="Microsoft Windows ME" /fastdetect

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows ME/0" /fastdetect

C:\bootsect.lnx="Gentoo Linux"

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdb

00000000  90 e9 7d 01 fa 33 c0 8e  d0 8e c0 8e d8 bc 00 7c  |..}..3.........||
00000010  8b f4 fb bf 00 06 b9 00  01 f3 a5 bb 20 06 ff e3  |............ ...|
00000020  90 90 be 7d 07 81 3c aa  55 75 11 e8 58 00 73 0c  |...}..<.Uu..X.s.|
00000030  e8 65 00 72 07 e8 b1 00  72 3b eb 2c be 7d 07 c7  |.e.r....r;.,.}..|
00000040  04 00 00 ba 80 00 be be  07 b9 04 00 f6 04 80 75  |...............u|
00000050  07 83 c6 10 e2 f6 eb 1d  8a 74 01 8b 4c 02 bb 00  |.........t..L...|
00000060  7c b8 01 02 cd 13 72 0d  81 3e fe 7d 55 aa 75 05  ||.....r..>.}U.u.|
00000070  ea 00 7c 00 00 be 6a 07  ac 0a c0 74 fe bb 07 00  |..|...j....t....|
00000080  b4 0e cd 10 eb f2 bb 00  7e c6 07 13 c6 47 01 00  |........~....G..|
00000090  b2 80 b8 00 e0 cd 13 c3  bf 00 7e ba f0 01 b3 a0  |..........~.....|
000000a0  e8 84 00 72 0c b1 01 e8  48 00 72 05 e8 19 00 73  |...r....H.r....s|
000000b0  16 f6 c3 10 75 05 80 cb  10 eb e5 81 fa 70 01 74  |....u........p.t|
000000c0  05 ba 70 01 eb d8 f9 c3  81 bd fe 01 55 aa 75 17  |..p.........U.u.|
000000d0  8b 75 02 81 fe be 01 77  0e 03 f7 81 3c aa 55 75  |.u.....w....<.Uu|
000000e0  06 f6 44 02 01 75 01 f9  c3 bf 00 7c b1 0a e8 01  |..D..u.....|....|
000000f0  00 c3 52 57 83 c2 02 b0  01 ee 42 8a c1 ee 42 32  |..RW......B...B2|
00000100  c0 ee 42 ee 42 8a c3 ee  42 b0 20 ee e8 33 00 ec  |..B.B...B. ..3..|
00000110  24 fd 3c 58 75 0d 83 ea  07 b9 00 01 fa f3 6d fb  |$.<Xu.........m.|
00000120  f8 eb 01 f9 5f 5a c3 52  83 c2 07 ec a8 80 75 0f  |...._Z.R......u.|
00000130  4a 8a c3 ee 42 ec 24 d0  3c 50 75 03 f8 eb 01 f9  |J...B.$.<Pu.....|
00000140  5a c3 51 8b 0e 6c 04 83  c1 12 81 c2 ff 01 ec 8a  |Z.Q..l..........|
00000150  e0 80 e4 d8 80 fc 58 74  06 3b 0e 6c 04 75 ef 81  |......Xt.;.l.u..|
00000160  ea ff 01 b9 00 20 e2 fe  59 c3 0d 0a 45 72 72 6f  |..... ..Y...Erro|
00000170  72 20 4c 6f 61 64 69 6e  67 20 4f 53 00 aa 55 00  |r Loading OS..U.|
00000180  00 e9 80 fe 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  f6 23 69 07 00 00 00 01  |.........#i.....|
000001c0  01 00 07 fe ff ff 3f 00  00 00 84 2a ef 22 00 00  |......?....*."..|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
``` Thanks for taking the time to help.

Steven

---

### Post by lisati on 2009-06-23
> **nodger said:**
> I'm pretty sure I used a Windows program before that installed a boot menu for me. I can't remember the name of it though

The relevant Windows commands I know about include "fdisk /mbr", "fixmbr" and "fixboot", but they have a habit of messing with grub's abiility to take charge of the boot process. I think someone else has posted a link to a thread that deals with getting grub working again.

---

### Post by paul_be on 2009-06-23
> **nodger said:**
> I'm pretty sure I used a Windows program before that installed a boot menu for me. I can't remember the name of it though

You may have used a program like Acronis OS selector, but this is not a free program, restoring grub is the way to go:)

---

### Post by unutbu on 2009-06-23
Steven Edwards,

It doesn't look like you have a Jaunty kernel in sda1, so if you had previously been able to boot Jaunty, it means LILO (and you) are able to work deeper magic than I know about.

How did you set LILO up the first time? Did you install Jaunty from the LiveCD, then manually install LILO? If so, why not do it again? It seems to me that would be the least invasive way to fix things. 

I notice in the RESULTS.txt file this output from blkid:

```
/dev/mapper/main-swap: UUID="888a898b-129f-440a-9d0d-f11b21b92c74" TYPE="swap" 
/dev/mapper/main-root: UUID="07ca8a50-ad66-4b64-96e0-6ca94705e8d3" TYPE="jfs" 
/dev/mapper/main-usr: UUID="daba50c9-46a4-44b4-9c35-cbe651bbb0ef" TYPE="jfs" 
/dev/mapper/main-var: UUID="b4d08a51-5dba-4de2-a81f-979bc6cccb03" TYPE="jfs" 
/dev/mapper/main-tmp: UUID="806817ff-cb8f-4a4f-892c-34c15c03983a" TYPE="jfs" 
/dev/mapper/main-home: UUID="f3a995d9-9b22-4646-8bc4-aff140fa2263" TYPE="jfs" 
```

How about boot a Jaunty LiveDVD, open a terminal and type

```
sudo apt-get install lvm2 
sudo mount /dev/mapper/main-root /mnt
sudo mount /dev/mapper/main-home /mnt/home
sudo mount /dev/mapper/main-usr /mnt/usr
sudo mount /dev/mapper/main-var /mnt/var
sudo mount /dev/mapper/main-tmp /mnt/tmp

```
Does this mount your LVM2 root and home logical volumes at /mnt and /mnt/home?
Have you tried this already? 
What were the error messages, if any?

If there are error messages or this does not successfully mount the logical volumes,
stop and post back here with the terminal output. 

If you can successfully mount the logical volumes, I believe this would install
GRUB and allow you could boot:
```

sudo mkdir /tmp/boot
sudo mount /dev/sda1 /tmp/boot            # Mount sda1 at /tmp/boot
sudo rsync -a /mnt/boot/ /tmp/boot/       # Copy Jaunty kernels and initrd to sda1
sudo umount /tmp/boot
sudo mount /dev/sda1 /mnt/boot            # Mount sda1 at /mnt/boot

cd /mnt
sudo mount --bind {/,}proc
sudo mount  --bind {/,}sys
sudo mount  --bind {/,}dev
sudo chroot /mnt                          # Change root so you are "inside" Jaunty
grep -v rootfs /proc/mounts > /etc/mtab
apt-get install grub 
grub-install  --recheck /dev/sda          # Install GRUB to sda's MBR overwriting LILO
update-grub                               # Create a /boot/grub/menu.lst

```
If all this works, then you'll also want to update /etc/fstab to mount sda1 at /boot
and remove the old /boot dir from the main-root logical volume. But of course that can wait until after we succeed in booting Jaunty.

---

### Post by Steven Edwards on 2009-06-23
> **unutbu said:**
> Steven Edwards,

It doesn't look like you have a Jaunty kernel in sda1, so if you had previously been able to boot Jaunty, it means LILO (and you) are able to work deeper magic than I know about.

How did you set LILO up the first time? Did you install Jaunty from the LiveCD, then manually install LILO? If so, why not do it again? It seems to me that would be the least invasive way to fix things. Alrighty, so... the history:

I got a 1.5TB drive a few months back and tried to transfer my Windows XP install to from the original 80gb drive.  XP wouldn't boot from the new drive and Microsoft said they had no utilities to help, so I told them they lost a customer and installed Intrepid (with GRUB) on the machine, a Dell Dimension 8400.

The CPU fan went bad, so I decided to upgrade instead of replacing it and paying for it to be installed.  New computer arrived, so the drives from the Dell machine got transferred to the new one.  Intrepid was either quirky or wouldn't boot, so I reinstalled Intrepid on top of the old one.  I never (to my knowledge) voluntarily chose LILO, but the new install used it.

Jaunty was released, so I waited a few days and then ran [sudo apt-get dist-upgrade] to upgrade.  Everything's worked great since then (except for a change in MouseKeys that's mildly annoying), and then yesterday happened.

I haven't installed over the existing installation for two main reasons: 1) I learn nothing that way, and 2) aren't geeks [in training?] massochists when it comes to doing this stuff? :)

> How about boot a Jaunty LiveDVD, open a terminal and type

```
sudo apt-get install lvm2 
sudo mount /dev/mapper/main-root /mnt
sudo mount /dev/mapper/main-home /mnt/home
sudo mount /dev/mapper/main-usr /mnt/usr
sudo mount /dev/mapper/main-var /mnt/var
sudo mount /dev/mapper/main-tmp /mnt/tmp

```
Does this mount your LVM2 root and home logical volumes at /mnt and /mnt/home?
Have you tried this already? 
What were the error messages, if any? No, yes, and:

```
ubuntu@ubuntu:~$ sudo mount /dev/mapper/main-root /mnt
mount: wrong fs type, bad option, bad superblock on /dev/mapper/main-root,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ sudo mount /dev/mapper/main-home /mnt/home
mount: mount point /mnt/home does not exist
ubuntu@ubuntu:~$ sudo mount /dev/mapper/main-usr /mnt/usr
mount: mount point /mnt/usr does not exist
ubuntu@ubuntu:~$ sudo mount /dev/mapper/main-var /mnt/var
mount: mount point /mnt/var does not exist
ubuntu@ubuntu:~$ sudo mount /dev/mapper/main-tmp /mnt/tmp
mount: mount point /mnt/tmp does not exist
``` If /mnt/{home,usr,var,tmp} existed, they'd return the same error as the first mount attempt.

dmesg | tail:

```
[  197.652337] [drm] writeback test succeeded in 1 usecs
[  198.940191] eth0: no IPv6 routers present
[ 2826.579616] VFS: Can't find an ext2 filesystem on dev dm-1.
[ 2864.513893] JFS: nTxBlock = 8192, nTxLock = 65536
[ 3640.947793] kjournald starting.  Commit interval 5 seconds
[ 3640.948847] EXT3 FS on sda1, internal journal
[ 3640.948856] EXT3-fs: mounted filesystem with ordered data mode.
[ 8014.617236] kjournald starting.  Commit interval 5 seconds
[ 8014.617809] EXT3 FS on sda1, internal journal
[ 8014.617821] EXT3-fs: mounted filesystem with ordered data mode.
``` I can mount /dev/sda1, but it does me no good.  (Not that I'm aware of, anyway.)

This is my last post for the night, so I want to reiterate my appreciation for your help. :)

Steven

---

### Post by unutbu on 2009-06-23
Right. I forgot to use vgchange:
How about try
```

sudo vgchange -ay 
sudo mkdir /mnt/{home,usr,var,tmp}
sudo mount /dev/mapper/main-root /mnt
sudo mount /dev/mapper/main-home /mnt/home
sudo mount /dev/mapper/main-usr /mnt/usr
sudo mount /dev/mapper/main-var /mnt/var
sudo mount /dev/mapper/main-tmp /mnt/tmp
```

---

### Post by Steven Edwards on 2009-06-24
> **unutbu said:**
> Right. I forgot to use vgchange:
How about try Same errors, unfortunately:

```
ubuntu@ubuntu:~$ sudo vgchange -ay 
  6 logical volume(s) in volume group "main" now active
ubuntu@ubuntu:~$ sudo mkdir /mnt/{home,usr,var,tmp}
ubuntu@ubuntu:~$ sudo mount /dev/mapper/main-root /mnt
mount: wrong fs type, bad option, bad superblock on /dev/mapper/main-root,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ sudo mount /dev/mapper/main-home /mnt/home
mount: wrong fs type, bad option, bad superblock on /dev/mapper/main-home,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ sudo mount /dev/mapper/main-usr /mnt/usr
mount: wrong fs type, bad option, bad superblock on /dev/mapper/main-usr,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ sudo mount /dev/mapper/main-var /mnt/var
mount: wrong fs type, bad option, bad superblock on /dev/mapper/main-var,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ sudo mount /dev/mapper/main-tmp /mnt/tmp
mount: wrong fs type, bad option, bad superblock on /dev/mapper/main-tmp,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

---

### Post by Steven Edwards on 2009-06-24
> **Steven Edwards said:**
> Same errors, unfortunately: ...and the fix:

Before running mount, run fsck.jfs on each of /dev/mapper/main-{root,tmp,usr,var,home}.  Everything mounts now, so I'll be looking for what I can do now.

---

### Post by Steven Edwards on 2009-06-24
/mnt/etc/lilo.conf:

```
# Automatically added by lilo postinst script
large-memory

# /etc/lilo.conf - See: `lilo(8)' and `lilo.conf(5)',
# ---------------       `install-mbr(8)', `/usr/share/doc/lilo/',
#                       and `/usr/share/doc/mbr/'.

# +---------------------------------------------------------------+
# |                        !! Reminder !!                         |
# |                                                               |
# | Don't forget to run `lilo' after you make changes to this     |
# | conffile, `/boot/bootmess.txt' (if you have created it), or   |
# | install a new kernel.  The computer will most likely fail to  |
# | boot if a kernel-image post-install script or you don't       |
# | remember to run `lilo'.                                       |
# |                                                               |
# +---------------------------------------------------------------+

# Specifies the boot device.  This is where Lilo installs its boot
# block.  It can be either a partition, or the raw device, in which
# case it installs in the MBR, and will overwrite the current MBR.
#
boot=/dev/sda

# Specifies the device that should be mounted as root. (`/')
#
#root=/dev/mapper/main-root

# This option may be needed for some software RAID installs.
#
# raid-extra-boot=mbr-only

# Enable map compaction:
# Tries to merge read requests for adjacent sectors into a single
# read request. This drastically reduces load time and keeps the
# map smaller.  Using `compact' is especially recommended when
# booting from a floppy disk.  It is disabled here by default
# because it doesn't always work.
#
# compact

# Installs the specified file as the new boot sector
# You have the choice between: text, bmp, and menu
# Look in lilo.conf(5) manpage for details
#
#install=menu

# Specifies the location of the map file
#
map=/boot/map

# You can set a password here, and uncomment the `restricted' lines
# in the image definitions below to make it so that a password must
# be typed to boot anything but a default configuration.  If a
# command line is given, other than one specified by an `append'
# statement in `lilo.conf', the password will be required, but a
# standard default boot will not require one.
#
# This will, for instance, prevent anyone with access to the
# console from booting with something like `Linux init=/bin/sh',
# and thus becoming `root' without proper authorization.
#
# Note that if you really need this type of security, you will
# likely also want to use `install-mbr' to reconfigure the MBR
# program, as well as set up your BIOS to disallow booting from
# removable disk or CD-ROM, then put a password on getting into the
# BIOS configuration as well.  Please RTFM `install-mbr(8)'.
#
# password=tatercounter2000

# Specifies the number of deciseconds (0.1 seconds) LILO should
# wait before booting the first image.
#
delay=20

# You can put a customized boot message up if you like.  If you use
# `prompt', and this computer may need to reboot unattended, you
# must specify a `timeout', or it will sit there forever waiting
# for a keypress.  `single-key' goes with the `alias' lines in the
# `image' configurations below.  eg: You can press `1' to boot
# `Linux', `2' to boot `LinuxOLD', if you uncomment the `alias'.
#
# message=/boot/bootmess.txt
#	prompt
#	delay=100
#	timeout=100

# Specifies the VGA text mode at boot time. (normal, extended, ask, <mode>)
#
# vga=ask
# vga=9
#


# Kernel command line options that apply to all installed images go
# here.  See: The `boot-prompt-HOWTO' and `kernel-parameters.txt' in
# the Linux kernel `Documentation' directory.
#
# append=""
 
# If you used a serial console to install Ubuntu, this option should be
# enabled by default.
# serial=

#
# Boot up Linux by default.
#
default=Linux

image=/vmlinuz
	label=Linux
	read-only
#	restricted
#	alias=1
	append="root=/dev/mapper/main-root  "
	initrd=/initrd.img

image=/vmlinuz.old
	label=LinuxOLD
	read-only
	optional
#	restricted
#	alias=2
	append="root=/dev/mapper/main-root  "
	initrd=/initrd.img.old


# If you have another OS on this machine to boot, you can uncomment the
# following lines, changing the device name on the `other' line to
# where your other OS' partition is.
#
# other=/dev/hda4
#	label=HURD
#	restricted
#	alias=3
``` I changed the default= line from Linux to LinuxOLD (maps to boot/{initrd.img, vmlinuz}-2.6.28-11-generic), and that didn't fix my flgrx problem.

If I can get it to boot to a shell with the 2.6.28-11 kernel, I'll reinstall flgrx and see if that helps.

---

### Post by Steven Edwards on 2009-06-24
> **Steven Edwards said:**
> I changed the default= line from Linux to LinuxOLD (maps to boot/{initrd.img, vmlinuz}-2.6.28-11-generic), and that didn't fix my flgrx problem.

If I can get it to boot to a shell with the 2.6.28-11 kernel, I'll reinstall flgrx and see if that helps. I'm back! :D

When LILO appears on the screen, but before the ... appear, hit a key and you (if anyone else has this problem) can choose which kernel to boot from.

Boy is it good to have everything back to normal. :)

Thanks for your time and patience.  Your assistance was invaluable.

---

### Post by unutbu on 2009-06-25
Steven Edwards, fantastic. I'm glad you got this problem sorted.

You've shown me that LILO can boot LVM partitions! Thank you.

According to Jai yen's post, [http://www.debianhelp.org/node/9664](http://www.debianhelp.org/node/9664), 
GRUB can not directly boot LVM partitions... instead it needs a /boot which resides outside the LVM.

It's interesting to see that LILO can do something that GRUB can not.

---

### Post by brucewestfall on 2009-07-16
Maybe I've got everything wrong, but... I really hate GRUB.

I have used Linux since some early Redhat in the 90's and have installed additional redhats, fedora, suse, LOTS of Ubuntu versions - I have not used MS for over 3 years now.

I love Linux.  Lately, GRUB is the major thorn in my side.  I am now on about my 4th (separate) day of trying to fix a GRUB problem, with no real progress yet.

Yes, I have read and re-read the forums.  Thank goodness for the LiveCD!  It is the only thing that keeps my computer working.

I just completed my 3rd reinstall of Ubunutu 9.04 and GRUB is where the problem seems to be coming from.  It all started by suspending my computer - I knew it was buggy in the past, but tried it again.  That was about 8 days ago.

I always liked LILO.  Never had a problem with it.  Now with GRUB, I have had to reinstall multiple times to get my computer back.  I respect and admire the people working on GRUB - there is no way I can comprehend how to do what they do - but I am sick and tired of getting GRUB errors that kill my PC.

GRUB vs. LILO?

LILO.

---

### Post by brucewestfall on 2009-07-19
Sure enough, installing Lilo fixed my problems.

[http://www.bauer-power.net/2007/08/changing-from-grub-to-lilo-ubuntu-704.html](http://www.bauer-power.net/2007/08/changing-from-grub-to-lilo-ubuntu-704.html)

I am running 9.04, but the directions worked perfectly.

Now, I can use my computer.  I am finding other disturbing things with 9.04 that will likely cause me to go back to 8.10 - CTRL+ALT+BACKSPACE got disabled ( I fixed that ) Some files I try to install say 'file cannot be found' when it really is there.  Older .deb files are being reported as corrupted, and my SD card is no longer recognized at all.

But I sure love Lilo.

---

### Post by andrew.46 on 2009-08-18
Hi Steven,

> **Steven Edwards said:**
> When LILO appears on the screen, but before the ... appear, hit a key and you (if anyone else has this problem) can choose which kernel to boot from.

Mind you there is some flexibility in this by manipulating a few options. The following are my own lilo.conf settings in this regard:

```
# Wait until the timeout to boot (if commented out, boot the
# first entry immediately):
**[COLOR="Red"]prompt[/COLOR]**
# Timeout before the first entry boots.
# This is given in tenths of a second, so 600 for every minute:
**[COLOR="Red"]timeout = 1200[/COLOR]**
```

And of course this allows the use of arrow keys to select kernel/partition before the default option boots.

All the best,

Andrew

---

