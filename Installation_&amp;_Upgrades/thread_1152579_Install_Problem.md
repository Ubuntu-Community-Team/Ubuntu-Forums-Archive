---
title: "Install Problem"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by larryboz on 2009-05-07
Installed 9.04 onto a Vista machine. Now when I reboot it just goes to Vista with no option to boot into Ubuntu. I have a raid o drives with a seperate 650gb drive that I installed 9.04 onto. Any thoughts would greatly be appreciated
 
Thanks
 
Larry

---

### Post by lindsay7 on 2009-05-08
read this

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by larryboz on 2009-05-08
OK Read that and now Kubuntu loads up in grub but now don't get the option to boot vista now.  Total opposite of what was happening last night.  Need some more help.

Larry

---

### Post by kay-man on 2009-05-08
Please download this and place it on your Desktop in Ubuntu:

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

I'll have you run it, so that we can gather more information about your hard drive setup and boot process to troubleshoot the problem more clearly.

After you download it to the Desktop, right-click it and click Properties, then click the Permissions tab and check the box at the bottom of the window that 'allows executing'.

Then click the Applications menu at the top right of your screen, followed by the Accessories menu and then click Terminal. A black window will come up, in it type the following commands, ending each line with a press of the Enter key:

```
cd ~/Desktop
sudo ./boot*.sh
```

Please remember that in Linux, everything is case sensitive. Therefore, a lowercase 'd' is different than an uppercase 'D'. Also, you will be prompted for the password you gave when you installed Ubuntu whenever you use the 'sudo' command. The 'sudo' command escalates privileges and in this case is needed to properly view the hard drives and boot process.

After you have done this, it should place a Results.txt file on your desktop. Double-click that file and select Edit->Copy. Then return here and start a new reply message. In this message, click the # sign at the top of the message editor box and this will give you CODE tags; click between these tags ({code]here[/code}) and paste the contents that you copied from the Results.txt file.

---

### Post by larryboz on 2009-05-08
```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #3 in 
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No known boot loader is installed in the MBR of /dev/sdb
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Windows Vista
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x27dc8c40

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   960,668,014   960,667,952   7 HPFS/NTFS
/dev/sda2         960,669,696   976,787,455    16,117,760  12 Compaq diagnostics

/dev/sda1 ends after the last sector of /dev/sda
/dev/sda2 ends after the last sector of /dev/sda

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd735c9bc

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found
/dev/sdb1     ? 4,053,569,202 7,436,398,700 3,382,829,499  34 Unknown
/dev/sdb2     ? 1,186,486,553 4,085,294,531 2,898,807,979  1c Hidden W95 FAT32 (LBA)
/dev/sdb3     ? 1,674,220,351 5,089,900,730 3,415,680,380  27 Hidden HPFS/NTFS
/dev/sdb4     ?   815,596,674 3,508,668,419 2,693,071,746  f9 Unknown

/dev/sdb1 ends after the last sector of /dev/sdb
/dev/sdb1 overlaps with /dev/sdb2
/dev/sdb1 overlaps with /dev/sdb3
/dev/sdb2 ends after the last sector of /dev/sdb
/dev/sdb2 overlaps with /dev/sdb3
/dev/sdb2 overlaps with /dev/sdb4
/dev/sdb3 ends after the last sector of /dev/sdb
/dev/sdb3 overlaps with /dev/sdb4
/dev/sdb4 ends after the last sector of /dev/sdb

Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x913867d9

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          2,048 1,096,312,823 1,096,310,776   7 HPFS/NTFS
/dev/sdc2       1,096,323,795 1,250,258,624   153,934,830   5 Extended
/dev/sdc5       1,096,323,858 1,243,896,884   147,573,027  83 Linux
/dev/sdc6       1,243,896,948 1,250,258,624     6,361,677  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sdc1: UUID="04ECAAB7ECAAA302" LABEL="New Volume" TYPE="ntfs" 
/dev/sdc5: UUID="a1461b88-01c9-4eb5-bc3d-fe5f574c07a4" TYPE="ext3" 
/dev/sdc6: UUID="98e56332-6c39-4147-b625-6ed139699f9b" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sdc5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)


=========================== sdc5/boot/grub/menu.lst: ===========================

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
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=a1461b88-01c9-4eb5-bc3d-fe5f574c07a4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a1461b88-01c9-4eb5-bc3d-fe5f574c07a4

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		a1461b88-01c9-4eb5-bc3d-fe5f574c07a4
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=a1461b88-01c9-4eb5-bc3d-fe5f574c07a4 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		a1461b88-01c9-4eb5-bc3d-fe5f574c07a4
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=a1461b88-01c9-4eb5-bc3d-fe5f574c07a4 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		a1461b88-01c9-4eb5-bc3d-fe5f574c07a4
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdc5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc5 during installation
UUID=a1461b88-01c9-4eb5-bc3d-fe5f574c07a4 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdc6 during installation
UUID=98e56332-6c39-4147-b625-6ed139699f9b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdc5: Location of files loaded by Grub: ===================


 587.2GB: boot/grub/menu.lst
 587.3GB: boot/grub/stage2
 587.2GB: boot/initrd.img-2.6.28-11-generic
 587.2GB: boot/vmlinuz-2.6.28-11-generic
 587.2GB: initrd.img
 587.2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdb

00000000  da 3f f6 59 a1 fe 4a f4  81 96 a0 30 1f 06 03 55  |.?.Y..J....0...U|
00000010  1d 23 04 18 30 16 80 14  6f e8 4e 3f 97 b9 34 ab  |.#..0...o.N?..4.|
00000020  4b 86 8f bc 9c ea ac 3b  41 43 c6 d0 30 44 06 03  |K......;AC..0D..|
00000030  55 1d 1f 04 3d 30 3b 30  39 a0 37 a0 35 86 33 68  |U...=0;09.7.5.3h|
00000040  74 74 70 3a 2f 2f 63 72  6c 2e 6d 69 63 72 6f 73  |ttp://crl.micros|
00000050  6f 66 74 2e 63 6f 6d 2f  70 6b 69 2f 63 72 6c 2f  |oft.com/pki/crl/|
00000060  70 72 6f 64 75 63 74 73  2f 74 73 70 63 61 2e 63  |products/tspca.c|
00000070  72 6c 30 48 06 08 2b 06  01 05 05 07 01 01 04 3c  |rl0H..+........<|
00000080  30 3a 30 38 06 08 2b 06  01 05 05 07 30 02 86 2c  |0:08..+.....0..,|
00000090  68 74 74 70 3a 2f 2f 77  77 77 2e 6d 69 63 72 6f  |http://www.micro|
000000a0  73 6f 66 74 2e 63 6f 6d  2f 70 6b 69 2f 63 65 72  |soft.com/pki/cer|
000000b0  74 73 2f 74 73 70 63 61  2e 63 72 74 30 13 06 03  |ts/tspca.crt0...|
000000c0  55 1d 25 04 0c 30 0a 06  08 2b 06 01 05 05 07 03  |U.%..0...+......|
000000d0  08 30 0e 06 03 55 1d 0f  01 01 ff 04 04 03 02 06  |.0...U..........|
000000e0  c0 30 0d 06 09 2a 86 48  86 f7 0d 01 01 05 05 00  |.0...*.H........|
000000f0  03 82 01 01 00 25 9c 6f  87 39 2d 1a 88 b1 02 03  |.....%.o.9-.....|
00000100  3e bb f2 48 6c ea 3c 0d  0e ae ee e6 07 95 0e 62  |>..Hl.<........b|
00000110  ba 47 27 8f d3 0d aa 68  22 1f 29 fa cf fc be da  |.G'....h".).....|
00000120  ed a4 2f a8 f2 72 94 0e  74 27 b3 f4 ac 8c 00 45  |../..r..t'.....E|
00000130  c8 4d 9c 5e 01 04 de 8f  5b c9 e5 56 2a 9e e6 93  |.M.^....[..V*...|
00000140  3d f1 dd 01 21 c7 06 c1  e2 41 59 32 71 fd 58 16  |=...!....AY2q.X.|
00000150  21 b3 f3 1a e4 06 ab 5b  00 68 19 77 7c f8 f7 b7  |!......[.h.w|...|
00000160  bb a7 22 c9 54 2b 88 d2  88 9c cf 2c d0 3a 5f 3a  |..".T+.....,.:_:|
00000170  08 7c 15 61 f5 02 28 15  9f 39 6d c6 6a 2f f8 30  |.|.a..(..9m.j/.0|
00000180  78 ae 59 e4 ec 6a f8 b5  94 56 96 35 f7 c3 38 0c  |x.Y..j...V.5..8.|
00000190  3c 82 19 40 ce 80 8a 28  6a 02 59 1f 40 6c 0b c2  |<..@...(j.Y.@l..|
000001a0  ef b0 3f 35 7a eb a5 79  6a 8b d1 0a 22 e6 60 f8  |..?5z..yj...".`.|
000001b0  0b 10 12 ac 21 60 14 ad  bc c9 35 d7 bf fd 98 d7  |....!`....5.....|
000001c0  5a 01 34 05 7a 66 b2 8e  9c f1 bb e1 a1 c9 76 f0  |Z.4.zf........v.|
000001d0  f5 b2 1c 4c 4d 40 19 59  b8 46 ab 4c c8 ac 4c 94  |...LM@.Y.F.L..L.|
000001e0  42 e3 27 ae f9 53 3f 93  ca 63 7c 25 97 cb 97 c4  |B.'..S?..c|%....|
000001f0  36 9e f9 ae a0 30 82 04  9d 30 82 03 85 a0 03 02  |6....0...0......|
00000200

Unknown BootLoader  on sda2


Unknown BootLoader  on sdb1


Unknown BootLoader  on sdb2


Unknown BootLoader  on sdb3


Unknown BootLoader  on sdb4



=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg 
=============================== StdErr Messages: ===============================

hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb2: No such file or directory
hexdump: /dev/sdb2: No such file or directory
hexdump: /dev/sdb3: No such file or directory
hexdump: /dev/sdb3: No such file or directory
hexdump: /dev/sdb4: No such file or directory
hexdump: /dev/sdb4: No such file or directory

```

---

### Post by lindsay7 on 2009-05-08
I think this will work if not delete it from your grub menu and see if some one else has an answer.

type this in the terminal "sudo gedit /boot/grub/menu.lst"

paste this at the end of the file then save it.  Do not change anything else.


title		Windows Vista (loader)
rootnoverify	(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1



I think I have the numbering correct, if not you can delete it.

---

### Post by larryboz on 2009-05-08
Well that got me a little further as Vista now shows up in GRUB but when I select Vista it goes to next screen and says BOOTMGR missing.  Again I would like to thank all you guys for the help so far.

Larry

---

### Post by lindsay7 on 2009-05-08
I looked at your info again. Windows may be on (hd0,0) so go back to the grub menu and and change the line

rootnoverify (hd2,0)  change it to read (hd0,0) and let me know if that works.

Type this in the terminal "sudo gedit /boot/grub/menu.lst"

paste this at the end of the file then save it. Do not change anything else. Save and exit and reboot.




If that does not work here is some other things to try,

Go to this site and try this, you can cut and past. Let me know if this works.

[http://geniushackers.com/blog/2008/0...buntu-live-cd/](http://geniushackers.com/blog/2008/0...buntu-live-cd/)

Your windows is located on (hd2 or partition sdc), or it could be (hd0 or partition sda) I am not sure which one you need to use so you may need to try both.

If you can not get that to work, if you have your Vista disk or a vista recovery disk, Here is the info for that,

here is the vista info

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

You can download recovery disks here

[http://neosmart.net/blog/2008/window...disc-download/](http://neosmart.net/blog/2008/window...disc-download/)


The windos command would be bootrec.exe /fixBoot


When you add the windows mbr it may mess up your grub so you may need to do this

Type "sudo grub"
type "find /boot/grub/stage2" this should give something like (hd2,0) fill in what you get
type "root (hd2,0)" or what ever you need
type "setup (hd0)
type "quit"

---

