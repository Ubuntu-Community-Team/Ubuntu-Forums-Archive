---
title: "Grub fails to load after 8.10 install."
date: 2009-02-09
forum: Installation &amp; Upgrades
---

### Post by theonlyfox on 2009-02-09
The situation.  I have Vista64 system using NVRaid.  I bought a second HD to install ubuntu.  I used the 8.10 alternate CD and all went well during the install.  The installer recognized the raid as a single drive of the correct size and recognized the installation of windows.  I partitioned and formatted the second HD and installed ubuntu.  At the end it asked if I wanted to be able to boot to other OS installs provided in the list.  The only install found was the Windows Vista.  I said "okedoke" and let the install finish.  After the install was completed I set my Bios to boot from the second HD instead of the Raid array.  

Now the problems start, I never get a Grub loader.  The system just hangs after the BIOS checks for bootable cd's.  There are no system messages.  I can still boot to the Windows partition on the Raid by simply changing the BIOS to boot from the Raid.  I can use live CD to get a terminal to mount and examine the files on the secondary HD.  The grub folder is there under /boot and there is a menu.lst.   You can see the menu.lst here [http://pastebin.com/m2839e0cc](http://pastebin.com/m2839e0cc)

As you can see there is no mention of the Windows install.  Im about 10minutes old as far as Linux goes and not sure where to go from here.  Any help is appreciated.

---

### Post by Pumalite on 2009-02-09
Install Grub to it's own partition; change the boot order; edit menu.lst and make an entry for Vista.
Post:
sudo fdisk -lu

---

### Post by caljohnsmith on 2009-02-09
It sounds like you might need to install Grub to the MBR (Master Boot Record) of your Ubuntu drive, so how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
sudo grub
grub> find /boot/grub/stage1
```
The command above should return your main Ubuntu partition in the form of (hdX,Y) where X and Y are numbers, for example (hd1,0), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Then reboot, set your BIOS to boot the Ubuntu drive, and let me know how far you get. If you still have problems, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu Live CD desktop, open a terminal again and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by theonlyfox on 2009-02-09
Woot, that was brilliant.:p  It booted great after that.  Now I just need to get windows added to the grub list and then find out what it will take to read files on the raid array.  Partition manager seed the drive as one volume formatted with NTFS but is unable to read the file system.  Any help on the above items will be greatly appreciated.

Here is the boot_info:

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdh

sda1: _________________________________________________________________________

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

sdc1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdh1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xdda33979

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   976,791,551   976,789,504   7 HPFS/NTFS

/dev/sda1 ends after the last sector of /dev/sda

Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8a963307

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   488,394,751   488,392,704   7 HPFS/NTFS

/dev/sdb1 ends after the last cylinder of /dev/sdb

Drive sdc: _____________________________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000797e0

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          2,048   970,737,663   970,735,616  83 Linux
/dev/sdc2       1,939,832,685 1,953,520,064    13,687,380   5 Extended
/dev/sdc5       1,939,848,750 1,953,520,064    13,671,315  82 Linux swap / Solaris


Drive sdh: _____________________________________________________________________

Disk /dev/sdh: 1025 MB, 1025507328 bytes
1 heads, 32 sectors/track, 62592 cylinders, total 2002944 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x147532cf

Partition  Boot         Start           End          Size  Id System

/dev/sdh1    *             32     2,002,943     2,002,912   6 FAT16


blkid -c /dev/null: ____________________________________________________________

/dev/sdc1: UUID="a81ebe8e-8b35-4be5-becb-bbb5c9b09f7d" TYPE="ext2" 
/dev/sdc5: UUID="15c1714c-a810-4dcc-aed4-50610f676cbc" TYPE="swap" 
/dev/mapper/nvidia_cebjejee1: UUID="D4145B9C145B8082" TYPE="ntfs" 
/dev/sdh1: SEC_TYPE="msdos" LABEL="CORSAIR" UUID="407D-F209" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sdc1 on / type ext2 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/fox/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=fox)
/dev/sdh1 on /media/CORSAIR type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

=========================== sdc1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=a81ebe8e-8b35-4be5-becb-bbb5c9b09f7d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a81ebe8e-8b35-4be5-becb-bbb5c9b09f7d

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
uuid		a81ebe8e-8b35-4be5-becb-bbb5c9b09f7d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=a81ebe8e-8b35-4be5-becb-bbb5c9b09f7d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		a81ebe8e-8b35-4be5-becb-bbb5c9b09f7d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=a81ebe8e-8b35-4be5-becb-bbb5c9b09f7d ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		a81ebe8e-8b35-4be5-becb-bbb5c9b09f7d
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=a81ebe8e-8b35-4be5-becb-bbb5c9b09f7d /               ext2    relatime,errors=remount-ro 0       1
# /dev/sdc5
UUID=15c1714c-a810-4dcc-aed4-50610f676cbc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


 343.7GB: boot/grub/menu.lst
 343.6GB: boot/grub/stage2
 343.6GB: boot/initrd.img-2.6.27-7-generic
 343.6GB: boot/vmlinuz-2.6.27-7-generic
 343.6GB: initrd.img
 343.6GB: vmlinuz

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  4d 5a 90 00 03 00 00 00  04 00 00 00 ff ff 00 00  |MZ..............|
00000010  b8 00 00 00 00 00 00 00  40 00 00 00 00 00 00 00  |........@.......|
00000020  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000030  00 00 00 00 00 00 00 00  00 00 00 00 e8 00 00 00  |................|
00000040  0e 1f ba 0e 00 b4 09 cd  21 b8 01 4c cd 21 54 68  |........!..L.!Th|
00000050  69 73 20 70 72 6f 67 72  61 6d 20 63 61 6e 6e 6f  |is program canno|
00000060  74 20 62 65 20 72 75 6e  20 69 6e 20 44 4f 53 20  |t be run in DOS |
00000070  6d 6f 64 65 2e 0d 0d 0a  24 00 00 00 00 00 00 00  |mode....$.......|
00000080  97 84 a1 95 d3 e5 cf c6  d3 e5 cf c6 d3 e5 cf c6  |................|
00000090  d3 e5 ce c6 57 e5 cf c6  f4 23 b4 c6 d0 e5 cf c6  |....W....#......|
000000a0  f4 23 b2 c6 d0 e5 cf c6  f4 23 a2 c6 d6 e5 cf c6  |.#.......#......|
000000b0  f4 23 be c6 cb e5 cf c6  f4 23 b3 c6 d2 e5 cf c6  |.#.......#......|
000000c0  f4 23 b7 c6 d2 e5 cf c6  52 69 63 68 d3 e5 cf c6  |.#......Rich....|
000000d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000e0  00 00 00 00 00 00 00 00  50 45 00 00 64 86 0c 00  |........PE..d...|
000000f0  ea b3 49 45 00 00 00 00  00 00 00 00 f0 00 22 00  |..IE..........".|
00000100  0b 02 08 00 00 2e 01 00  00 36 00 00 00 00 00 00  |.........6......|
00000110  e8 a6 01 00 00 10 00 00  00 00 01 00 00 00 00 00  |................|
00000120  00 10 00 00 00 02 00 00  06 00 00 00 06 00 00 00  |................|
00000130  06 00 00 00 00 00 00 00  00 e0 01 00 00 04 00 00  |................|
00000140  85 dd 01 00 01 00 00 00  00 00 04 00 00 00 00 00  |................|
00000150  00 10 00 00 00 00 00 00  00 00 10 00 00 00 00 00  |................|
00000160  00 10 00 00 00 00 00 00  00 00 00 00 10 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  f8 a8 01 00 28 00 00 00  |............(...|
00000180  00 c0 01 00 18 04 00 00  00 80 00 00 10 0b 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 d0 01 00 48 00 00 00  |............H...|
000001a0  20 54 00 00 1c 00 00 00  00 00 00 00 00 00 00 00  | T..............|
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001d0  00 50 00 00 18 04 00 00  00 00 00 00 00 00 00 00  |.P..............|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  2e 74 65 78 74 00 00 00  61 2c 00 00 00 10 00 00  |.text...a,......|
00000200

Unknown BootLoader  on sdb1

00000000  33 d2 44 8d 42 06 49 8b  cd e8 ba af ff ff 89 44  |3.D.B.I........D|
00000010  24 24 33 d2 44 8d 42 05  49 8b cd e8 a8 af ff ff  |$$3.D.B.I.......|
00000020  8b d8 89 44 24 24 41 0f  ba e7 11 72 4a 4d 8d b5  |...D$$A....rJM..|
00000030  f8 02 00 00 b2 01 49 8b  ce ff 15 51 1e ff ff 49  |......I....Q...I|
00000040  39 bc 24 48 01 00 00 74  25 41 8b 94 24 50 01 00  |9.$H...t%A..$P..|
00000050  00 49 8b 8c 24 48 01 00  00 e8 4a be ff ff 41 89  |.I..$H....J...A.|
00000060  bc 24 50 01 00 00 49 89  bc 24 48 01 00 00 49 8b  |.$P...I..$H...I.|
00000070  ce ff 15 a1 1d ff ff b2  01 48 8b ce ff 15 0e 1e  |.........H......|
00000080  ff ff 41 b6 01 44 88 74  24 20 eb 46 41 0f ba e7  |..A..D.t$ .FA...|
00000090  12 73 38 49 8d b5 d0 00  00 00 48 8b ce ff 15 75  |.s8I......H....u|
000000a0  1d ff ff 40 88 7c 24 20  49 8b cd e8 80 7e ff ff  |...@.|$ I....~..|
000000b0  8b d8 89 44 24 24 b2 01  48 8b ce ff 15 cf 1d ff  |...D$$..H.......|
000000c0  ff 41 b6 01 44 88 74 24  20 eb 07 49 8d b5 d0 00  |.A..D.t$ ..I....|
000000d0  00 00 3b df 0f 8c 09 01  00 00 41 8b 84 24 f8 00  |..;.......A..$..|
000000e0  00 00 83 f8 03 0f 84 f8  00 00 00 83 f8 02 75 63  |..............uc|
000000f0  41 0f ba e7 11 72 75 41  c7 84 24 f8 00 00 00 01  |A....ruA..$.....|
00000100  00 00 00 49 8d 85 f8 02  00 00 b2 01 48 8b c8 ff  |...I........H...|
00000110  15 7b 1d ff ff 49 39 bc  24 48 01 00 00 74 25 41  |.{...I9.$H...t%A|
00000120  8b 94 24 50 01 00 00 49  8b 8c 24 48 01 00 00 e8  |..$P...I..$H....|
00000130  74 bd ff ff 41 89 bc 24  50 01 00 00 49 89 bc 24  |t...A..$P...I..$|
00000140  48 01 00 00 49 8d 8d f8  02 00 00 ff 15 c7 1c ff  |H...I...........|
00000150  ff eb 19 41 0f ba e7 11  73 12 41 c7 84 24 f8 00  |...A....s.A..$..|
00000160  00 00 02 00 00 00 8b df  89 5c 24 24 3b df 7c 73  |.........\$$;.|s|
00000170  41 8b 84 24 f8 00 00 00  83 f8 02 74 66 83 f8 01  |A..$.......tf...|
00000180  75 61 41 0f ba e7 10 72  5a 48 8b ce ff 15 86 1c  |uaA....rZH......|
00000190  ff ff 44 8a f7 40 88 7c  24 20 33 d2 44 8d 42 07  |..D..@.|$ 3.D.B.|
000001a0  49 8b cd e8 20 ae ff ff  8b d8 89 44 24 24 3b c7  |I... ......D$$;.|
000001b0  7c 31 b2 01 48 8b ce ff  15 d3 1c ff ff 41 b6 01  ||1..H........A..|
000001c0  44 88 74 24 20 41 89 bc  24 f8 00 00 00 eb 14 bb  |D.t$ A..$.......|
000001d0  0d 00 00 c0 89 5c 24 24  eb 09 bb 0d 00 00 c0 89  |.....\$$........|
000001e0  5c 24 24 44 3a f7 74 0d  49 8d 8d d0 00 00 00 ff  |\$$D:.t.I.......|
000001f0  15 23 1c ff ff 4c 3b ef  74 08 49 8b cd e8 72 95  |.#...L;.t.I...r.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

 sdd .
 sde .
 sdf .
 sdg .

=============================== StdErr Messages: ===============================

/home/fox/Desktop/boot_info_script024.sh: line 1043: [: =: unary operator expected
/home/fox/Desktop/boot_info_script024.sh: line 1043: [: =: unary operator expected
```

---

### Post by caljohnsmith on 2009-02-09
OK, booting Windows on your RAID array from Grub can be tricky sometimes, so how about first opening your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And then add the following entries for Windows at the very end:
```
title       Windows Vista (hd1)
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title       Windows Vista (hd2)
rootnoverify     (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1
```
Reboot, try each Vista entry from your Grub menu, and let me know exactly what happens. We can work from there.

---

### Post by theonlyfox on 2009-02-09
I didn't HD2 since I know thats where Ubuntu resides.  This code:
```
title       Windows Vista (hd1)
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```

Puts the windows in the Grub load list and then when selected loads windows beautifully like it always has pre Ubuntu.

That just leaves the file access and then wonder why the installer failed to do these steps.

---

