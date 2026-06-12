---
title: "Grub error 12 question"
date: 2009-02-19
forum: Installation &amp; Upgrades
---

### Post by timofthec on 2009-02-19
A quick question: -

I have windows XP installed on the Primary Hard Drive, which has two partitions: c: and d:

I then have ubuntu installed on a second (slave) hard drive, which also has two partitions: the main one and then the swap partition (sorry, don't know the correct terminology).

When recreating grub after a re-install of XP, what would I enter for X and Y in this string: -

```
grub> root (hdX,Y)
```

and also, does this string remain as: -

```
grub> setup (hd0)
```

Just trying to recreate the grub loader but getting an error 12 message and I believe I entered the wrong values.

The code comes from this guide - [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) - which I followed last night and I thought had worked.

---

### Post by frozie on 2009-02-19
The X and Y where is root.
after you find /boot/grub/stage1,
the root must be seen.that's the (hdx,y)

---

### Post by timofthec on 2009-02-19
> **frozie said:**
> The X and Y where is root.
after you find /boot/grub/stage1,
the root must be seen.that's the (hdx,y)

Sorry Frozie - don't understand what that means :confused:

I have attempted to recreate Grub again and when I run ```
find /boot/grub/stage1
``` I get (hd1,0).  I then do ```
root (hd1,0)
```

For ```
setup (hd0)
``` I have tried both (hd0) and (hd1) but I still get the same error message.

Looking at the windows stanza in /boot/grub/menu.lst, I have this: -
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

The root entry here is (hd0,0) - is that the problem?

---

### Post by caljohnsmith on 2009-02-19
I think it would help to get a clearer picture of your setup, so how about downloading the **Boot Info Script** to your Ubuntu desktop (can be a Live CD):

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post.

---

### Post by timofthec on 2009-02-19
hi cal, the results reads as follows :-

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63. The info in boot sector on the starting 
                       sector of the MFT is wrong. The info in the boot 
                       sector on the starting sector of the MFT Mirror is 
                       wrong.
    Operating System:  Windows XP
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe615f229

Partition  Boot         Start           End          Size  Id System

/dev/sda1              16,065   122,881,184   122,865,120   f W95 Ext d (LBA)
/dev/sda5              16,128   122,881,184   122,865,057   7 HPFS/NTFS
/dev/sda2    *    122,881,185   184,313,744    61,432,560   7 HPFS/NTFS


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9ffae1e4

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   112,358,609   112,358,547  83 Linux
/dev/sdb2         112,358,610   117,226,304     4,867,695   5 Extended
/dev/sdb5         112,358,673   117,226,304     4,867,632  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda2: UUID="166C63DA6C63B363" LABEL="Virtual" TYPE="ntfs" 
/dev/sda5: UUID="22B0BCF5B0BCD111" LABEL="Main" TYPE="ntfs" 
/dev/sdb1: UUID="3cb17080-8b44-4e3e-86ae-3c0c6a8216d6" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="cfdc4cd9-3297-47df-b65f-511284ac23c2" 

=============================== "mount" output: ===============================

/dev/sdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)


================================ sda2/boot.ini: ================================

[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

=========================== sdb1/boot/grub/menu.lst: ===========================

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		6

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=3cb17080-8b44-4e3e-86ae-3c0c6a8216d6 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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
# howmany=2

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

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=3cb17080-8b44-4e3e-86ae-3c0c6a8216d6 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=3cb17080-8b44-4e3e-86ae-3c0c6a8216d6 ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, kernel 2.6.24-22-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=3cb17080-8b44-4e3e-86ae-3c0c6a8216d6 ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-22-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=3cb17080-8b44-4e3e-86ae-3c0c6a8216d6 ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=3cb17080-8b44-4e3e-86ae-3c0c6a8216d6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=cfdc4cd9-3297-47df-b65f-511284ac23c2 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

=================== sdb1: Location of files loaded by Grub: ===================


  44.3GB: boot/grub/menu.lst
  44.3GB: boot/grub/stage2
  44.3GB: boot/initrd.img-2.6.20-17-generic
  44.3GB: boot/initrd.img-2.6.22-15-generic
  44.3GB: boot/initrd.img-2.6.22-15-generic.bak
  44.4GB: boot/initrd.img-2.6.24-19-generic
  44.3GB: boot/initrd.img-2.6.24-19-generic.bak
  44.4GB: boot/initrd.img-2.6.24-21-generic
  44.3GB: boot/initrd.img-2.6.24-21-generic.bak
  44.3GB: boot/initrd.img-2.6.24-22-generic
  44.3GB: boot/initrd.img-2.6.24-22-generic.bak
  44.3GB: boot/initrd.img-2.6.24-23-generic
  44.3GB: boot/initrd.img-2.6.24-23-generic.bak
  44.3GB: boot/vmlinuz-2.6.20-17-generic
  44.3GB: boot/vmlinuz-2.6.22-15-generic
  44.3GB: boot/vmlinuz-2.6.24-19-generic
  44.3GB: boot/vmlinuz-2.6.24-21-generic
  44.3GB: boot/vmlinuz-2.6.24-22-generic
  44.4GB: boot/vmlinuz-2.6.24-23-generic
  44.3GB: initrd.img
  44.3GB: initrd.img.old
  44.4GB: vmlinuz
  44.3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  53 00 65 00 63 00 75 00  72 00 69 00 74 00 79 00  |S.e.c.u.r.i.t.y.|
00000010  00 00 90 90 50 00 72 00  6f 00 78 00 79 00 00 00  |....P.r.o.x.y...|
00000020  41 00 75 00 74 00 6f 00  43 00 6f 00 6e 00 66 00  |A.u.t.o.C.o.n.f.|
00000030  69 00 67 00 00 00 90 90  43 00 6f 00 6e 00 6e 00  |i.g.....C.o.n.n.|
00000040  77 00 69 00 7a 00 20 00  41 00 64 00 6d 00 69 00  |w.i.z. .A.d.m.i.|
00000050  6e 00 20 00 4c 00 6f 00  63 00 6b 00 00 00 90 90  |n. .L.o.c.k.....|
00000060  43 00 6f 00 6e 00 6e 00  65 00 63 00 74 00 69 00  |C.o.n.n.e.c.t.i.|
00000070  6f 00 6e 00 20 00 53 00  65 00 74 00 74 00 69 00  |o.n. .S.e.t.t.i.|
00000080  6e 00 67 00 73 00 00 00  44 00 69 00 73 00 70 00  |n.g.s...D.i.s.p.|
00000090  6c 00 61 00 79 00 20 00  49 00 6e 00 6c 00 69 00  |l.a.y. .I.n.l.i.|
000000a0  6e 00 65 00 20 00 49 00  6d 00 61 00 67 00 65 00  |n.e. .I.m.a.g.e.|
000000b0  73 00 00 00 43 00 6f 00  64 00 65 00 42 00 61 00  |s...C.o.d.e.B.a.|
000000c0  73 00 65 00 53 00 65 00  61 00 72 00 63 00 68 00  |s.e.S.e.a.r.c.h.|
000000d0  50 00 61 00 74 00 68 00  00 00 90 90 46 00 6f 00  |P.a.t.h.....F.o.|
000000e0  72 00 63 00 65 00 43 00  6f 00 64 00 65 00 44 00  |r.c.e.C.o.d.e.D.|
000000f0  6f 00 77 00 6e 00 6c 00  6f 00 61 00 64 00 4c 00  |o.w.n.l.o.a.d.L.|
00000100  6f 00 67 00 00 00 90 90  41 00 75 00 74 00 6f 00  |o.g.....A.u.t.o.|
00000110  53 00 65 00 61 00 72 00  63 00 68 00 00 00 90 90  |S.e.a.r.c.h.....|
00000120  41 00 70 00 70 00 65 00  6e 00 64 00 20 00 43 00  |A.p.p.e.n.d. .C.|
00000130  6f 00 6d 00 70 00 6c 00  65 00 74 00 69 00 6f 00  |o.m.p.l.e.t.i.o.|
00000140  6e 00 00 00 55 00 73 00  65 00 20 00 41 00 75 00  |n...U.s.e. .A.u.|
00000150  74 00 6f 00 43 00 6f 00  6d 00 70 00 6c 00 65 00  |t.o.C.o.m.p.l.e.|
00000160  74 00 65 00 00 00 90 90  55 00 73 00 65 00 20 00  |t.e.....U.s.e. .|
00000170  41 00 6e 00 63 00 68 00  6f 00 72 00 20 00 48 00  |A.n.c.h.o.r. .H.|
00000180  6f 00 76 00 65 00 72 00  20 00 43 00 6f 00 6c 00  |o.v.e.r. .C.o.l.|
00000190  6f 00 72 00 00 00 90 90  41 00 6e 00 63 00 68 00  |o.r.....A.n.c.h.|
000001a0  6f 00 72 00 20 00 43 00  6f 00 6c 00 6f 00 72 00  |o.r. .C.o.l.o.r.|
000001b0  20 00 48 00 6f 00 76 00  65 00 72 00 00 00 00 01  | .H.o.v.e.r.....|
000001c0  01 01 07 fe ff ff 3f 00  00 00 a1 c5 52 07 00 00  |......?.....R...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

MFT Sector of sda5

00000000  46 49 4c 45 30 00 03 00  b3 a5 79 0d 00 00 00 00  |FILE0.....y.....|
00000010  01 00 01 00 38 00 01 00  a0 01 00 00 00 04 00 00  |....8...........|
00000020  00 00 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |................|
00000030  98 00 00 00 00 00 00 00  10 00 00 00 60 00 00 00  |............`...|
00000040  00 00 18 00 00 00 00 00  48 00 00 00 18 00 00 00  |........H.......|
00000050  04 56 0a ba 81 8f c9 01  04 56 0a ba 81 8f c9 01  |.V.......V......|
*
00000070  06 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 00 00 00 00 01 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  30 00 00 00 68 00 00 00  |........0...h...|
000000a0  00 00 18 00 00 00 03 00  4a 00 00 00 18 00 01 00  |........J.......|
000000b0  05 00 00 00 00 00 05 00  04 56 0a ba 81 8f c9 01  |.........V......|
000000c0  04 56 0a ba 81 8f c9 01  04 56 0a ba 81 8f c9 01  |.V.......V......|
000000d0  04 56 0a ba 81 8f c9 01  00 40 00 00 00 00 00 00  |.V.......@......|
000000e0  00 40 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |.@..............|
000000f0  04 03 24 00 4d 00 46 00  54 00 00 00 00 00 00 00  |..$.M.F.T.......|
00000100  80 00 00 00 48 00 00 00  01 00 40 00 00 00 01 00  |....H.....@.....|
00000110  00 00 00 00 00 00 00 00  c7 21 00 00 00 00 00 00  |.........!......|
00000120  40 00 00 00 00 00 00 00  00 80 1c 02 00 00 00 00  |@...............|
00000130  00 80 1c 02 00 00 00 00  00 80 1c 02 00 00 00 00  |................|
00000140  32 c8 21 00 00 0c 00 00  b0 00 00 00 50 00 00 00  |2.!.........P...|
00000150  01 00 40 00 00 00 05 00  00 00 00 00 00 00 00 00  |..@.............|
00000160  01 00 00 00 00 00 00 00  40 00 00 00 00 00 00 00  |........@.......|
00000170  00 20 00 00 00 00 00 00  e8 10 00 00 00 00 00 00  |. ..............|
00000180  e8 10 00 00 00 00 00 00  31 01 ff ff 0b 31 01 b6  |........1....1..|
00000190  a9 fa 00 e1 d8 e1 cc b9  ff ff ff ff 00 00 00 00  |................|
000001a0  00 80 00 00 00 00 00 00  31 08 00 00 0c 00 01 00  |........1.......|
000001b0  b0 00 00 00 48 00 00 00  01 00 40 00 00 00 05 00  |....H.....@.....|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001d0  40 00 00 00 00 00 00 00  00 10 00 00 00 00 00 00  |@...............|
000001e0  08 00 00 00 00 00 00 00  08 00 00 00 00 00 00 00  |................|
000001f0  31 01 ff ff 0b 00 00 00  ff ff ff ff 00 00 98 00  |1...............|
00000200

that help at all?

---

### Post by caljohnsmith on 2009-02-19
It looks like you installed Windows to sda5, but Windows' boot files are in the sda2 partition. Therefore, how about trying:
```
title Microsoft Windows XP Professional
root [COLOR="Blue"](hd0,1)[/COLOR]
savedefault
makeactive
chainloader +1
```
Let me know if that works OK or not.

---

### Post by timofthec on 2009-02-19
> **caljohnsmith said:**
> It looks like you installed Windows to sda5, but Windows' boot files are in the sda2 partition. Therefore, how about trying:
```
title Microsoft Windows XP Professional
root [COLOR="Blue"](hd0,1)[/COLOR]
savedefault
makeactive
chainloader +1
```
Let me know if that works OK or not.

That worked a treat Cal - can now get in to both windows and ubuntu.  Many thanx for that - much appreciated

---

### Post by caljohnsmith on 2009-02-19
Glad that worked OK; cheers and enjoy your dual-boot Ubuntu/Windows setup. :)

---

