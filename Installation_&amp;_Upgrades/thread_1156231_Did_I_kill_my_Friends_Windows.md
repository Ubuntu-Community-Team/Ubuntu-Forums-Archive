---
title: "Did I kill my Friends Windows?"
date: 2009-05-11
forum: Installation &amp; Upgrades
---

### Post by sTpny on 2009-05-11
Hi Guys, I just installed the new Jaunty on my friends computer, and I messed something up. The computer has an 80 gig hd and a 160 gig hd. Richard, my friend, wanted me to put ubuntu on the 160 gig drive, but it had a few windows files on it, so I copied those files into a folder on the c drive, and proceeded to install Ubuntu. The install itself went fine, but when I rebooted after the install, it loaded back into windows. Ugg! so I jumped into the bios and, sure enough, there was a security feature protecting the mbr, so I disabled it, reinstalled ubuntu, and then it installed and booted into the new ubuntu, which looks really nice. Anyhow, grub didn't detect the windows, so I manually added an entry to the boot/grub/menu.lst file, but when I try to boot from it, all I get is...

```

Starting Up... 
Y%Y% 

```

only the % signs are really infinity signs. I just can't type them.

I think What I've done is install grub over the windows bootloader! Is that what happened, or is my manual entry in the boot.lst wrong? 

Here are the results of the boot info script from 
[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
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

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80032038912 bytes
147 heads, 32 sectors/track, 33229 cylinders, total 156312576 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc7dbc7db

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             32   156,309,215   156,309,184   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc790c790

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   307,291,319   307,291,257  83 Linux
/dev/sdb2         307,291,320   312,576,704     5,285,385   5 Extended
/dev/sdb5         307,291,383   312,576,704     5,285,322  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="01C948BE25AF4780" TYPE="ntfs" 
/dev/sdb1: UUID="14559413-4385-4336-b812-c0ef08efa2ba" TYPE="ext3" 
/dev/sdb5: UUID="c5dc7e65-df96-40c0-aa4f-1a53b7a4025b" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/richard/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=richard)


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
# kopt=root=UUID=14559413-4385-4336-b812-c0ef08efa2ba ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=14559413-4385-4336-b812-c0ef08efa2ba

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
uuid		14559413-4385-4336-b812-c0ef08efa2ba
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=14559413-4385-4336-b812-c0ef08efa2ba ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		14559413-4385-4336-b812-c0ef08efa2ba
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=14559413-4385-4336-b812-c0ef08efa2ba ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.27-7-generic
uuid		14559413-4385-4336-b812-c0ef08efa2ba
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=14559413-4385-4336-b812-c0ef08efa2ba ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-7-generic (recovery mode)
uuid		14559413-4385-4336-b812-c0ef08efa2ba
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=14559413-4385-4336-b812-c0ef08efa2ba ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 9.04, memtest86+
uuid		14559413-4385-4336-b812-c0ef08efa2ba
kernel		/boot/memtest86+.bin
quiet


 title		Windows Professional
 root		(hd0,0)
 makeactive
 chainloader	+1

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=14559413-4385-4336-b812-c0ef08efa2ba /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=c5dc7e65-df96-40c0-aa4f-1a53b7a4025b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


 143.5GB: boot/grub/menu.lst
 143.4GB: boot/grub/stage2
 143.3GB: boot/initrd.img-2.6.27-7-generic
 143.3GB: boot/initrd.img-2.6.28-11-generic
 143.4GB: boot/vmlinuz-2.6.27-7-generic
 143.4GB: boot/vmlinuz-2.6.28-11-generic
 143.3GB: initrd.img
 143.3GB: initrd.img.old
 143.4GB: vmlinuz
 143.4GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  eb 5b 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.[.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  20 00 93 00 20 00 00 00  |........ ... ...|
00000020  00 00 00 00 80 00 80 00  bf 16 51 09 00 00 00 00  |..........Q.....|
00000030  04 00 00 00 00 00 00 00  6b 11 95 00 00 00 00 00  |........k.......|
00000040  f6 00 00 00 01 00 00 00  80 47 af 25 be 48 c9 01  |.........G.%.H..|
00000050  fa 33 c0 8e d0 bc 00 7c  fb b8 c0 07 8e d8 e8 16  |.3.....|........|
00000060  00 b8 00 0d 8e c0 33 db  c6 06 0e 00 10 e8 53 00  |......3.......S.|
00000070  68 00 0d 68 6a 02 cb 8a  16 24 00 b4 08 cd 13 73  |h..hj....$.....s|
00000080  05 b9 ff ff 8a f1 66 0f  b6 c6 40 66 0f b6 d1 80  |......f...@f....|
00000090  e2 3f f7 e2 86 cd c0 ed  06 41 66 0f b7 c9 66 f7  |.?.......Af...f.|
000000a0  e1 66 a3 20 00 c3 b4 41  bb aa 55 8a 16 24 00 cd  |.f. ...A..U..$..|
000000b0  13 72 0f 81 fb 55 aa 75  09 f6 c1 01 74 04 fe 06  |.r...U.u....t...|
000000c0  14 00 c3 66 60 1e 06 66  a1 10 00 66 03 06 1c 00  |...f`..f...f....|
000000d0  66 3b 06 20 00 0f 82 3a  00 1e 66 6a 00 66 50 06  |f;. ...:..fj.fP.|
000000e0  53 66 68 10 00 01 00 80  3e 14 00 00 0f 85 0c 00  |Sfh.....>.......|
000000f0  e8 b3 ff 80 3e 14 00 00  0f 84 61 00 b4 42 8a 16  |....>.....a..B..|
00000100  24 00 16 1f 8b f4 cd 13  66 58 5b 07 66 58 66 58  |$.......fX[.fXfX|
00000110  1f eb 2d 66 33 d2 66 0f  b7 0e 18 00 66 f7 f1 fe  |..-f3.f.....f...|
00000120  c2 8a ca 66 8b d0 66 c1  ea 10 f7 36 1a 00 86 d6  |...f..f....6....|
00000130  8a 16 24 00 8a e8 c0 e4  06 0a cc b8 01 02 cd 13  |..$.............|
00000140  0f 82 19 00 8c c0 05 20  00 8e c0 66 ff 06 10 00  |....... ...f....|
00000150  ff 0e 0e 00 0f 85 6f ff  07 1f 66 61 c3 a0 f8 01  |......o...fa....|
00000160  e8 09 00 a0 fb 01 e8 03  00 fb eb fe b4 01 8b f0  |................|
00000170  ac 3c 00 74 09 b4 0e bb  07 00 cd 10 eb f2 c3 0d  |.<.t............|
00000180  0a 41 20 64 69 73 6b 20  72 65 61 64 20 65 72 72  |.A disk read err|
00000190  6f 72 20 6f 63 63 75 72  72 65 64 00 0d 0a 4e 54  |or occurred...NT|
000001a0  4c 44 52 20 69 73 20 6d  69 73 73 69 6e 67 00 0d  |LDR is missing..|
000001b0  0a 4e 54 4c 44 52 20 69  73 20 63 6f 6d 70 72 65  |.NTLDR is compre|
000001c0  73 73 65 64 00 0d 0a 50  72 65 73 73 20 43 74 72  |ssed...Press Ctr|
000001d0  6c 2b 41 6c 74 2b 44 65  6c 20 74 6f 20 72 65 73  |l+Alt+Del to res|
000001e0  74 61 72 74 0d 0a 00 00  00 00 00 00 00 00 00 00  |tart............|
000001f0  00 00 00 00 83 a0 b3 c9  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

So, any help for me? Or should I just backup my friends personal files and start from scratch with both OS's. 

I'll be sending the computer back today, so I'll have to finish the fix later during a visit. I'm actually hoping that after he sees how awesome Ubuntu is, that he'll just say "Screw Windows" like so many of us have, but I'd still like to know what went wrong, and how to fix it.  

Thanks :)

Tony

---

### Post by sTpny on 2009-05-14
BUMP - please guys.. I can reinstall the windows, but I'd rather not. Windows installs are just a major pain in the ***. Help me fix this.

---

### Post by Mark Phelps on 2009-05-14
Surprised that none of the "regulars" responded yet ... so ...

Which drive are you booting from, the XP drive or the Ubuntu drive?

If it's the Ubuntu drive, then the menu.lst file is pointing to the wrong drive -- but I can't tell from the UUID entries.

---

### Post by sTpny on 2009-05-15
I'm booting off of the windows drive (sda 80g).  Linux works fine(sdb 160g), but grub wont boot windows. 

from my first post... 

Unknown BootLoader  on sda1


Thanks for the interest.. :)

---

### Post by yozgoesdigital on 2009-05-15
Are you not able to fix the original windows bootloader with the FIXBOOT command when using the installation cd?

To avoid the bootloader problem you could use your BIOS to start from a different HD

probably not the most optimal solution but I think it should work.

Good Luck

---

### Post by sTpny on 2009-05-15
Would fixboot be on the Windows Cd, or is it on the ubuntu cd?

---

### Post by yozgoesdigital on 2009-05-15
It is on the installation cd of windows:

Maybe the following link will help you reinstalling your normal windows bootloader, at no. 6 an 7. 
[http://articles.techrepublic.com.com/5100-10878_11-6031733.html](http://articles.techrepublic.com.com/5100-10878_11-6031733.html)

Note that the windows bootloader will not see your linux. And if you did not do it yet, back up important files!

Good luck

---

### Post by sTpny on 2009-05-16
Yes, I think that link is just what I needed.  Thanks.

---

### Post by yozgoesdigital on 2009-05-16
Once windows is working again you could try to make dual boot (what was your intention in the first place, right ;) )

Here I have got a similair partion/disc setup. One disc with different linux distributions and a second hard disk with windows. I chose to use my BIOS bootloader to boot from the different hard disks. While starting my computer I have to press F12 (can be different) to boot from my not default hard disk.
If you want something similar you should check if your BIOS has this option, most of them have them. To be safe you can dis attach your windows disk and restore/install grub on your linux  disk, but it should be possible to install grub on your linux disk while your windows disk is on there.
Of course there are different options (check this forum), but this one works fine for me.

---

### Post by sTpny on 2009-05-18
well.. I've had some luck.  I've got both windows and ubuntu to boot, but now, in windows, the drive letters are swapped.  I'm pretty sure I can fix it using the windows recovery console and diskpart.  Should be as easy as removing the drive letter associations and then reassigning them to where they are supposed to be. Fingers crossed.. Hopefully I mark this thread as solved tomorrow.

---

### Post by sTpny on 2009-05-19
Well, I can't call it solved. The letters were reversed only in the OS.  DISKPART showed them as being correct. c:/ for windows, d:/ for rescue. It's a dead issue though.  I just installed his windows as a virtual machine. Now it sits on a cube face for him.  he loves it.  Another happy linux convert.. lol. ;)

Thanks for all the help. 

Tony

---

