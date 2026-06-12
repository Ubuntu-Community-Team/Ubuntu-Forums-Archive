---
title: "Windows does not start up"
date: 2009-09-30
forum: Installation &amp; Upgrades
---

### Post by Fastrack1988 on 2009-09-30
Installed ubuntu onto system have windows xp as boot partition but in the grub menu i choose windows xp and it goes to another page saying starting up and then nothink happens ive ran the boot info script as been trying to find problem on forum i am a begginer to linux so its probably a small problem 

heres the resultssda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbdcabdca

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   250,067,789   250,067,727   7 HPFS/NTFS
/dev/sda2         296,945,460   312,576,704    15,631,245  83 Linux
/dev/sda3         250,067,790   296,945,459    46,877,670   5 Extended
/dev/sda5         250,067,853   296,945,459    46,877,607  83 Linux

any replie be greatly appreciated
thanks

---

### Post by rreese6 on 2009-09-30
You said that you ran the boot info script, but there seems to be data missing in the output.

To help you with your problem, more information is needed.

1. Boot up with LiveCD. Once you are on the Desktop, got to this link and download:
```
[Download Boot Information Script]("http://sourceforge.net/projects/bootinfoscript/")
```
This Script will gather your current configuration and make a report.
This gives us a better idea of what your problem is and how to fix it.

2. Open up terminal and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will make a file called "Readme.txt" on your desktop.

3. Post the contents of that file here.

---

### Post by Fastrack1988 on 2009-10-01
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbdcabdca

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   250,067,789   250,067,727   7 HPFS/NTFS
/dev/sda2         296,945,460   312,576,704    15,631,245  83 Linux
/dev/sda3         250,067,790   296,945,459    46,877,670   5 Extended
/dev/sda5         250,067,853   296,945,459    46,877,607  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="DC6C26306C2605BC" TYPE="ntfs" 
/dev/sda2: UUID="fd7089cc-ee8e-4bb7-9cc5-d0c63e7d28f1" TYPE="ext2" 
/dev/sda5: UUID="532b79fd-65e3-441b-8379-fe56d1a17a17" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda2 on / type ext2 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
/dev/sda5 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/sean/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=sean)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sda2/boot/grub/menu.lst: ===========================

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=fd7089cc-ee8e-4bb7-9cc5-d0c63e7d28f1 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=fd7089cc-ee8e-4bb7-9cc5-d0c63e7d28f1 ro quiet splash
initrd        /boot/initrd.img-2.6.24-19-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=fd7089cc-ee8e-4bb7-9cc5-d0c63e7d28f1 ro single
initrd        /boot/initrd.img-2.6.24-19-generic

title        Ubuntu 8.04.1, memtest86+
root        (hd0,1)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1


=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=fd7089cc-ee8e-4bb7-9cc5-d0c63e7d28f1 /               ext2    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=532b79fd-65e3-441b-8379-fe56d1a17a17 /home           ext3    relatime        0       2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


 156.9GB: boot/grub/menu.lst
 156.9GB: boot/grub/stage2
 156.4GB: boot/initrd.img-2.6.24-19-generic
 156.4GB: boot/vmlinuz-2.6.24-19-generic
 156.4GB: initrd.img
 156.4GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  25 85 ed b7 e6 53 21 a5  8f c8 df be 6b e4 ce cb  |%....S!.....k...|
00000010  ad 7b c8 f7 3c 45 b2 8d  1c 62 36 f6 fe bf d3 26  |.{..<E...b6....&|
00000020  1b ab ca ed 2c 68 7e 3e  aa 45 43 67 00 46 5d 80  |....,h~>.ECg.F].|
00000030  a9 02 ca af 1a 4e 45 9b  6d dd 78 97 30 e8 07 0e  |.....NE.m.x.0...|
00000040  31 51 6c c3 b8 dc 31 8f  22 57 18 7c d5 30 25 76  |1Ql...1."W.|.0%v|
00000050  ca c9 a9 7b c0 54 1f 29  73 4b 4b c3 7d 25 e1 d2  |...{.T.)sKK.}%..|
00000060  e3 cf 5f 6e 14 08 f7 bf  81 b1 ee 69 fe d0 ee 17  |.._n.......i....|
00000070  67 7d 52 fb 03 93 ff ce  da 01 37 90 cb 73 a0 3e  |g}R.......7..s.>|
00000080  8b 32 82 26 eb 3d 86 03  2d fb 6f ce 3f 66 ab 3f  |.2.&.=..-.o.?f.?|
00000090  f3 f9 0d 06 f7 cb 69 07  91 17 1f bc e1 8e 91 6f  |......i........o|
000000a0  7a f4 25 2a 4d f2 ae ea  79 0d e9 cb 6d 46 f7 3d  |z.%*M...y...mF.=|
000000b0  fc db 8f 16 e8 2e c7 e0  e6 8a f3 b1 99 79 e0 8b  |.............y..|
000000c0  c3 a7 cd 35 32 c1 73 62  b7 2b 66 b7 88 45 be 9a  |...52.sb.+f..E..|
000000d0  1d 9b 99 02 0c 92 1e 28  9e 1f 0f 87 c3 e8 73 f0  |.......(......s.|
000000e0  f7 4f 0c 37 7f 9f b1 bf  79 c5 a3 05 ae 3a 89 35  |.O.7....y....:.5|
000000f0  fb 50 fd ac b6 a5 fb dd  7c 5f df b8 f7 c5 9b ad  |.P......|_......|
00000100  26 ff ef 43 87 97 f7 ee  28 11 fa 2e 1d ec 11 ee  |&..C....(.......|
00000110  66 d8 b8 62 f3 7a 6c 4e  7c 62 f2 ff 8f 0c a2 7e  |f..b.zlN|b.....~|
00000120  65 1b af b8 64 e9 3d 9d  ea 09 37 df 64 e4 b9 77  |e...d.=...7.d..w|
00000130  d6 89 e7 9b 11 e3 21 e1  5f 9f 4d 65 29 5d 96 a8  |......!._.Me)]..|
00000140  df b0 aa 41 ff 7c 54 99  71 58 39 ef a6 1c 17 79  |...A.|T.qX9....y|
00000150  f9 b0 f2 ec fc e8 11 18  d1 61 07 fd 4a 30 07 99  |.........a..J0..|
00000160  7e e6 0d ac a2 d0 eb 2f  36 8c 38 ab b9 d5 74 37  |~....../6.8...t7|
00000170  3b 2b dc e5 65 56 ea f2  d7 61 fa 6c 01 70 e0 ef  |;+..eV...a.l.p..|
00000180  ab 14 b5 5e 4a c0 aa e4  6f ac 28 4c 30 ea ef 59  |...^J...o.(L0..Y|
00000190  3b f1 9a 6e d3 f6 ce 12  bf 6f f9 7a 7c d2 27 e6  |;..n.....o.z|.'.|
000001a0  0c 8d 12 eb 90 1b f8 e7  cb 94 e9 1e df 61 ff 1a  |.............a..|
000001b0  f9 18 ea c9 43 b9 87 b1  bc 60 c0 8f 77 ae 69 3a  |....C....`..w.i:|
000001c0  12 9c 6a 37 de 8b 61 b1  22 4b fa c6 4f b7 7f e6  |..j7..a."K..O...|
000001d0  57 a2 67 cb 88 3f 3f 89  5a 22 17 e8 ee b3 be d5  |W.g..??.Z"......|
000001e0  b4 5b 0c eb 3d ff 71 23  1b 89 95 5f aa 46 6f d6  |.[..=.q#..._.Fo.|
000001f0  09 b6 4d c3 cb dc 48 0b  9f ad fc 7d 83 ba 47 cd  |..M...H....}..G.|
00000200

---

### Post by rreese6 on 2009-10-01
Thx.
It appears that Windows is on the first partition.
but the following is list in your boot.ini file:

```
[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOW S
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Micro soft Windows XP Professional" /noexecute=optin /fastdetect

```

the partition(1) is actually pointing to the second partition (Linux)

edit the boot.ini file to change "partition(1)" to "partition(0)"

```
[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(0)\WINDOW S
[operating systems]
multi(0)disk(0)rdisk(0)partition(0)\WINDOWS="Micro soft Windows XP Professional" /noexecute=optin /fastdetect

```

---

### Post by Fastrack1988 on 2009-10-01
done and still not working

---

### Post by rreese6 on 2009-10-01
Have you tried the windows recovery disk?

---

### Post by presence1960 on 2009-10-01
> **rreese6 said:**
> Have you tried the windows recovery disk?

+1.

Boot from the Windows XP install disk and follow the directions [here]("http://ubuntuforums.org/showthread.php?t=1014708") for XP.

Reboot and make sure you boot right into XP. Id so you are halfway there. Now you need to restore GRUB to MBR by doing this:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

Now you should be good to go.

---

### Post by rreese6 on 2009-10-01
> **presence1960 said:**
> +1.

Boot from the Windows XP install disk and follow the directions [here]("http://ubuntuforums.org/showthread.php?t=1014708") for XP.

>>SNIP<<

+1
Thanks presence1960, I always enjoy your Skill in helping others...
and causing me to remember things I've forgotten along the joyful trail of Linux.
Plus some really good new "tricks".

---

