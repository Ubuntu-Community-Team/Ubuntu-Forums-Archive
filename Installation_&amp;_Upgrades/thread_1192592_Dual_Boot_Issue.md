---
title: "Dual Boot Issue"
date: 2009-06-20
forum: Installation &amp; Upgrades
---

### Post by ktyson on 2009-06-20
I installd Ubuntu to dual boot with Windows XP.  Grub is installed but I can't get it work properly.  The only way I can get Ubuntu to load is to go into the bios and change the hard drive boot order.  I'd really appreciate any help you can give.  I have run boot_info and here are the results:

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => No known boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdc2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdc3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdc4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0cb1318

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   392,243,039   392,242,977  83 Linux
/dev/sda2         392,243,040   398,283,479     6,040,440   5 Extended
/dev/sda5         392,243,103   398,283,479     6,040,377  82 Linux swap / Solaris


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2a282a27

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   268,414,019   268,413,957   7 HPFS/NTFS
/dev/sdb2         268,414,020   488,392,064   219,978,045   f W95 Ext d (LBA)
/dev/sdb5         268,414,083   488,392,064   219,977,982   7 HPFS/NTFS


Drive sdc: _____________________________________________________________________

Disk /dev/sdc: 18 MB, 18612224 bytes
1 heads, 36 sectors/track, 1009 cylinders, total 36352 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6f20736b

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found
/dev/sdc1     ?   778,135,908 1,919,645,538 1,141,509,631  72 Unknown
/dev/sdc2     ?   168,689,522 2,104,717,761 1,936,028,240  65 Novell Netware 386
/dev/sdc3     ? 1,869,881,465 3,805,909,656 1,936,028,192  79 Unknown
/dev/sdc4     ?             0 3,637,226,495 3,637,226,496   d Unknown

/dev/sdc1 ends after the last sector of /dev/sdc
/dev/sdc1 overlaps with /dev/sdc2
/dev/sdc1 overlaps with /dev/sdc3
/dev/sdc1 overlaps with /dev/sdc4
/dev/sdc2 ends after the last sector of /dev/sdc
/dev/sdc2 overlaps with /dev/sdc3
/dev/sdc2 overlaps with /dev/sdc4
/dev/sdc3 ends after the last sector of /dev/sdc
/dev/sdc3 overlaps with /dev/sdc4
/dev/sdc4 ends after the last sector of /dev/sdc

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="52e28f34-061c-4dbf-a6e2-8bfd8658d099" TYPE="ext3" 
/dev/sda5: UUID="ac48f196-ad58-4bb0-bfb0-79ad7d34c206" TYPE="swap" 
/dev/sdb1: UUID="147C07677C0742CA" TYPE="ntfs" 
/dev/sdb5: UUID="E65CBBAF5CBB793F" LABEL="Data" TYPE="ntfs" 
/dev/sdc: SEC_TYPE="msdos" LABEL="PHONE" UUID="E80E-4DE6" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-13-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/kevin/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=kevin)
/dev/sdc on /media/PHONE type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

=========================== sda1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=52e28f34-061c-4dbf-a6e2-8bfd8658d099 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=52e28f34-061c-4dbf-a6e2-8bfd8658d099

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

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		52e28f34-061c-4dbf-a6e2-8bfd8658d099
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=52e28f34-061c-4dbf-a6e2-8bfd8658d099 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		52e28f34-061c-4dbf-a6e2-8bfd8658d099
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=52e28f34-061c-4dbf-a6e2-8bfd8658d099 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.27-11-generic
uuid		52e28f34-061c-4dbf-a6e2-8bfd8658d099
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=52e28f34-061c-4dbf-a6e2-8bfd8658d099 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
uuid		52e28f34-061c-4dbf-a6e2-8bfd8658d099
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=52e28f34-061c-4dbf-a6e2-8bfd8658d099 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 9.04, memtest86+
uuid		52e28f34-061c-4dbf-a6e2-8bfd8658d099
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdd1
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=52e28f34-061c-4dbf-a6e2-8bfd8658d099 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=ac48f196-ad58-4bb0-bfb0-79ad7d34c206 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


 121.2GB: boot/grub/menu.lst
 121.3GB: boot/grub/stage2
 121.3GB: boot/initrd.img-2.6.27-11-generic
 121.3GB: boot/initrd.img-2.6.28-13-generic
 121.2GB: boot/vmlinuz-2.6.27-11-generic
 121.2GB: boot/vmlinuz-2.6.28-13-generic
 121.3GB: initrd.img
 121.2GB: vmlinuz

================================ sdb1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn


=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdc

00000000  eb 3c 90 4d 53 44 4f 53  35 2e 30 00 02 01 06 00  |.<.MSDOS5.0.....|
00000010  02 00 02 00 8e f8 8d 00  3f 00 ff 00 00 00 00 00  |........?.......|
00000020  00 00 00 00 00 00 29 e6  4d 0e e8 4e 4f 20 4e 41  |......).M..NO NA|
00000030  4d 45 20 20 20 20 46 41  54 31 36 20 20 20 33 c9  |ME    FAT16   3.|
00000040  8e d1 bc f0 7b 8e d9 b8  00 20 8e c0 fc bd 00 7c  |....{.... .....||
00000050  38 4e 24 7d 24 8b c1 99  e8 3c 01 72 1c 83 eb 3a  |8N$}$....<.r...:|
00000060  66 a1 1c 7c 26 66 3b 07  26 8a 57 fc 75 06 80 ca  |f..|&f;.&.W.u...|
00000070  02 88 56 02 80 c3 10 73  eb 33 c9 8a 46 10 98 f7  |..V....s.3..F...|
00000080  66 16 03 46 1c 13 56 1e  03 46 0e 13 d1 8b 76 11  |f..F..V..F....v.|
00000090  60 89 46 fc 89 56 fe b8  20 00 f7 e6 8b 5e 0b 03  |`.F..V.. ....^..|
000000a0  c3 48 f7 f3 01 46 fc 11  4e fe 61 bf 00 00 e8 e6  |.H...F..N.a.....|
000000b0  00 72 39 26 38 2d 74 17  60 b1 0b be a1 7d f3 a6  |.r9&8-t.`....}..|
000000c0  61 74 32 4e 74 09 83 c7  20 3b fb 72 e6 eb dc a0  |at2Nt... ;.r....|
000000d0  fb 7d b4 7d 8b f0 ac 98  40 74 0c 48 74 13 b4 0e  |.}.}....@t.Ht...|
000000e0  bb 07 00 cd 10 eb ef a0  fd 7d eb e6 a0 fc 7d eb  |.........}....}.|
000000f0  e1 cd 16 cd 19 26 8b 55  1a 52 b0 01 bb 00 00 e8  |.....&.U.R......|
00000100  3b 00 72 e8 5b 8a 56 24  be 0b 7c 8b fc c7 46 f0  |;.r.[.V$..|...F.|
00000110  3d 7d c7 46 f4 29 7d 8c  d9 89 4e f2 89 4e f6 c6  |=}.F.)}...N..N..|
00000120  06 96 7d cb ea 03 00 00  20 0f b6 c8 66 8b 46 f8  |..}..... ...f.F.|
00000130  66 03 46 1c 66 8b d0 66  c1 ea 10 eb 5e 0f b6 c8  |f.F.f..f....^...|
00000140  4a 4a 8a 46 0d 32 e4 f7  e2 03 46 fc 13 56 fe eb  |JJ.F.2....F..V..|
00000150  4a 52 50 06 53 6a 01 6a  10 91 8b 46 18 96 92 33  |JRP.Sj.j...F...3|
00000160  d2 f7 f6 91 f7 f6 42 87  ca f7 76 1a 8a f2 8a e8  |......B...v.....|
00000170  c0 cc 02 0a cc b8 01 02  80 7e 02 0e 75 04 b4 42  |.........~..u..B|
00000180  8b f4 8a 56 24 cd 13 61  61 72 0b 40 75 01 42 03  |...V$..aar.@u.B.|
00000190  5e 0b 49 75 06 f8 c3 41  bb 00 00 60 66 6a 00 eb  |^.Iu...A...`fj..|
000001a0  b0 4e 54 4c 44 52 20 20  20 20 20 20 0d 0a 52 65  |.NTLDR      ..Re|
000001b0  6d 6f 76 65 20 64 69 73  6b 73 20 6f 72 20 6f 74  |move disks or ot|
000001c0  68 65 72 20 6d 65 64 69  61 2e ff 0d 0a 44 69 73  |her media....Dis|
000001d0  6b 20 65 72 72 6f 72 ff  0d 0a 50 72 65 73 73 20  |k error...Press |
000001e0  61 6e 79 20 6b 65 79 20  74 6f 20 72 65 73 74 61  |any key to resta|
000001f0  72 74 0d 0a 00 00 00 00  00 00 00 ac cb d8 00 00  |rt..............|
00000200

Unknown BootLoader  on sdc1


Unknown BootLoader  on sdc2


Unknown BootLoader  on sdc3


Unknown BootLoader  on sdc4



=============================== StdErr Messages: ===============================

hexdump: /dev/sdc1: No such file or directory
hexdump: /dev/sdc1: No such file or directory
/home/kevin/Desktop/boot_info_script024.sh: line 1043: [: =: unary operator expected
hexdump: /dev/sdc2: No such file or directory
hexdump: /dev/sdc2: No such file or directory
/home/kevin/Desktop/boot_info_script024.sh: line 1043: [: =: unary operator expected
hexdump: /dev/sdc3: No such file or directory
hexdump: /dev/sdc3: No such file or directory
/home/kevin/Desktop/boot_info_script024.sh: line 1043: [: =: unary operator expected
hexdump: /dev/sdc4: No such file or directory
hexdump: /dev/sdc4: No such file or directory
/home/kevin/Desktop/boot_info_script024.sh: line 1043: [: =: unary operator expected

---

### Post by lindsay7 on 2009-06-20
You need to change the drive map. Your windows is on hd1 not hd2.  So, type this in the terminal.

Sudo gedit /boot.grub/menu.lst   that is the letter l not the number 1.  You will get a file that you can edit change the drive number as I show and save the file. Do not change or move anything else.  Reboot your computer and see if that does it. Let me know how you make out.

Now shows...

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdd1
title Microsoft Windows XP Professional
root (hd2,0)
savedefault
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1


``` 



Change to 

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdd1
title Microsoft Windows XP Professional
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1


```


My thanks to Merlinus,

Also change the root line to root (hd1,0) as shown.

---

### Post by merlinus on 2009-06-20
Hi Lindsay.  Wouldn't he also need to change root to:

root (hd1,0)

?

---

### Post by Tinman131 on 2009-06-20
I don't mean to hijack your thread, but I really hate posting new threads unnecessarily.  I did the same thing, got mine to work and all, but ... when I boot Windows it instead takes me to a diagnostics program for the motherboard.

When I just try to boot from the Windows HDD, it gives me the same thing (the diagnostic program).  Any idea what happened?  Did I somehow eliminate my ability to boot the Windows drive?

If I did, that's okay.  I already have all of my music and critical files on an external hard drive, so it's not a big issue--I just still like to game every now and then and enjoy iTunes music store items.  So, if possible, I'd like to get that figured out.

To be helpful and contribute to the thread: is that the only thing wrong with your setup--that Ubuntu is acting as slave and Windows is booting as master?

---

### Post by lindsay7 on 2009-06-20
Merlinus,  you correct!  I got wrapped up with the mapping and forgot about the root line.  Thanks for pickin this up or the fix would not have worked.

Regards,

L7

---

### Post by merlinus on 2009-06-20
@L7

We lobos have to stick together!

@tinman131

A new thread would have been fine.  Nevertheless, results of these terminal commands may help:

```

sudo fdisk -l
cat /boot/grub/menu.lst

```

---

### Post by Tinman131 on 2009-06-20
Merlinus - 

Duly noted--look for my sister thread in this subforum.  I'll post the results of your terminal commands there.

---

### Post by lindsay7 on 2009-06-20
Tinman131,

Start a new post with the description of the problem and what ever specs you can provide.

Post the output of 

sudo fdisk -l    that is the letter l

and also 

sudo gedit /boot/grub/menu.lst   again that is the letter l

Send me a private message with the link for the post and I will follow it.

---

### Post by ktyson on 2009-06-20
Thank you so much Lindsay and Merlin!  That was the ticket.. I am happily dual booting now!  Thanks again!!!

---

### Post by merlinus on 2009-06-20
Excellent!  Happy ubuntuing, and post back if you run into other difficulties.

---

