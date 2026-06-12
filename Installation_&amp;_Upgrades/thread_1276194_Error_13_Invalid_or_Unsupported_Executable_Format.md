---
title: "Error 13: Invalid or Unsupported Executable Format"
date: 2009-09-26
forum: Installation &amp; Upgrades
---

### Post by Flux45 on 2009-09-26
I have a fresh Ubuntu 9.04 install booting from an external hard drive. When I get to the boot menu i get Error 13: Invalid or Unsupported Executable Format message when I select windows vista.

my fdisk -lu is as follows:

the /dev/sda is where my vista install is located
/dev/sdb5 is where linux is

Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders, total 293046768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x63c35e74

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   293044223   146521088    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000a6bb1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   315209862   157604900   af  Unknown
/dev/sdb2       315209916   944756537   314773311    7  HPFS/NTFS
/dev/sdb3       944766585   976768064    16000740    5  Extended
/dev/sdb5       944766648   975338279    15285816   83  Linux
/dev/sdb6       975338343   976768064      714861   82  Linux swap / Solaris


my /boot/grub/menu/lst windows entry is as follows:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
chainloader    +1

what do i need to change my windows entry values to?
thank you

---

### Post by Flux45 on 2009-09-26
*bump*

please help

---

### Post by presence1960 on 2009-09-26
Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by rreese6 on 2009-09-26
sdb1 is the boot flagged partition and the file type is unknown.
as long as sb1 is that way it will not boot.
I also see you have an NFTS partition on the drive.

---

### Post by Flux45 on 2009-09-26
```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders, total 293046768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x63c35e74

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   293,044,223   293,042,176   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000a6bb1

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   315,209,862   315,209,800  af HFS
/dev/sdb2         315,209,916   944,756,537   629,546,622   7 HPFS/NTFS
/dev/sdb3         944,766,585   976,768,064    32,001,480   5 Extended
/dev/sdb5         944,766,648   975,338,279    30,571,632  83 Linux
/dev/sdb6         975,338,343   976,768,064     1,429,722  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 132 MB, 132251136 bytes
8 heads, 32 sectors/track, 1008 cylinders, total 258303 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xdb3cb800

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             32       258,302       258,271   6 FAT16


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="60CCF922CCF8F360" TYPE="ntfs" 
/dev/sdb1: UUID="B6CB101C522E1375" LABEL="Mac" TYPE="hfsplus" 
/dev/sdb2: UUID="3034238C3423545E" LABEL="WINDOWS" TYPE="ntfs" 
/dev/sdb5: UUID="1c0a48d2-cd1e-4c60-97a1-5e06b7711d0e" TYPE="ext3" 
/dev/sdb6: UUID="bb3ccbc2-226c-4146-bf88-d7b4a9e2a4ee" TYPE="swap" 
/dev/sdc1: SEC_TYPE="msdos" UUID="001B-9622" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sdb5 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/matt/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=matt)
/dev/sdb2 on /media/WINDOWS type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /media/Mac type hfsplus (rw,nosuid,nodev,uhelper=hal)
/dev/sdc1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)


=========================== sdb5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=1c0a48d2-cd1e-4c60-97a1-5e06b7711d0e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=1c0a48d2-cd1e-4c60-97a1-5e06b7711d0e

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        1c0a48d2-cd1e-4c60-97a1-5e06b7711d0e
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=1c0a48d2-cd1e-4c60-97a1-5e06b7711d0e ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        1c0a48d2-cd1e-4c60-97a1-5e06b7711d0e
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=1c0a48d2-cd1e-4c60-97a1-5e06b7711d0e ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        1c0a48d2-cd1e-4c60-97a1-5e06b7711d0e
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
chainloader    +1


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=1c0a48d2-cd1e-4c60-97a1-5e06b7711d0e /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=bb3ccbc2-226c-4146-bf88-d7b4a9e2a4ee none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 486.1GB: boot/grub/menu.lst
 486.2GB: boot/grub/stage2
 486.2GB: boot/initrd.img-2.6.28-11-generic
 486.1GB: boot/vmlinuz-2.6.28-11-generic
 486.2GB: initrd.img
 486.1GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc1

00000000  eb 3c 90 4d 53 57 49 4e  34 2e 31 00 02 04 01 00  |.<.MSWIN4.1.....|
00000010  02 00 04 00 00 f8 fc 00  20 00 3f 00 20 00 00 00  |........ .?. ...|
00000020  df f0 03 00 80 00 29 22  96 1b 00 4e 4f 20 4e 41  |......)"...NO NA|
00000030  4d 45 20 20 20 20 46 41  54 31 36 20 20 20 33 c9  |ME    FAT16   3.|
00000040  8e d1 bc fc 7b 16 07 bd  78 00 c5 76 00 1e 56 16  |....{...x..v..V.|
00000050  55 bf 22 05 89 7e 00 89  4e 02 b1 0b fc f3 a4 06  |U."..~..N.......|
00000060  1f bd 00 7c c6 45 fe 0f  38 4e 24 7d 20 8b c1 99  |...|.E..8N$} ...|
00000070  e8 7e 01 83 eb 3a 66 a1  1c 7c 66 3b 07 8a 57 fc  |.~...:f..|f;..W.|
00000080  75 06 80 ca 02 88 56 02  80 c3 10 73 ed 33 c9 fe  |u.....V....s.3..|
00000090  06 d8 7d 8a 46 10 98 f7  66 16 03 46 1c 13 56 1e  |..}.F...f..F..V.|
000000a0  03 46 0e 13 d1 8b 76 11  60 89 46 fc 89 56 fe b8  |.F....v.`.F..V..|
000000b0  20 00 f7 e6 8b 5e 0b 03  c3 48 f7 f3 01 46 fc 11  | ....^...H...F..|
000000c0  4e fe 61 bf 00 07 e8 28  01 72 3e 38 2d 74 17 60  |N.a....(.r>8-t.`|
000000d0  b1 0b be d8 7d f3 a6 61  74 3d 4e 74 09 83 c7 20  |....}..at=Nt... |
000000e0  3b fb 72 e7 eb dd fe 0e  d8 7d 7b a7 be 7f 7d ac  |;.r......}{...}.|
000000f0  98 03 f0 ac 98 40 74 0c  48 74 13 b4 0e bb 07 00  |.....@t.Ht......|
00000100  cd 10 eb ef be 82 7d eb  e6 be 80 7d eb e1 cd 16  |......}....}....|
00000110  5e 1f 66 8f 04 cd 19 be  81 7d 8b 7d 1a 8d 45 fe  |^.f......}.}..E.|
00000120  8a 4e 0d f7 e1 03 46 fc  13 56 fe b1 04 e8 c2 00  |.N....F..V......|
00000130  72 d7 ea 00 02 70 00 52  50 06 53 6a 01 6a 10 91  |r....p.RP.Sj.j..|
00000140  8b 46 18 a2 26 05 96 92  33 d2 f7 f6 91 f7 f6 42  |.F..&...3......B|
00000150  87 ca f7 76 1a 8a f2 8a  e8 c0 cc 02 0a cc b8 01  |...v............|
00000160  02 80 7e 02 0e 75 04 b4  42 8b f4 8a 56 24 cd 13  |..~..u..B...V$..|
00000170  61 61 72 0a 40 75 01 42  03 5e 0b 49 75 77 c3 03  |aar.@u.B.^.Iuw..|
00000180  18 01 27 0d 0a 49 6e 76  61 6c 69 64 20 73 79 73  |..'..Invalid sys|
00000190  74 65 6d 20 64 69 73 6b  ff 0d 0a 44 69 73 6b 20  |tem disk...Disk |
000001a0  49 2f 4f 20 65 72 72 6f  72 ff 0d 0a 52 65 70 6c  |I/O error...Repl|
000001b0  61 63 65 20 74 68 65 20  64 69 73 6b 2c 20 61 6e  |ace the disk, an|
000001c0  64 20 74 68 65 6e 20 70  72 65 73 73 20 61 6e 79  |d then press any|
000001d0  20 6b 65 79 0d 0a 00 00  49 4f 20 20 20 20 20 20  | key....IO      |
000001e0  53 59 53 4d 53 44 4f 53  20 20 20 53 59 53 7f 01  |SYSMSDOS   SYS..|
000001f0  00 41 bb 00 07 60 66 6a  00 e9 3b ff 00 00 55 aa  |.A...`fj..;...U.|
00000200
```

---

### Post by Flux45 on 2009-09-26
> **rreese6 said:**
> sdb1 is the boot flagged partition and the file type is unknown.
as long as sb1 is that way it will not boot.
I also see you have an NFTS partition on the drive.

im trying to boot windows from sda1, not sdb1

---

### Post by presence1960 on 2009-09-26
open a terminal and run this command: ```
gksu gedit /boot/grub/menu.lst
```
That is a lowecase L in .lst

Scroll down to your windows entry and change it to this:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows Vista (loader)
rootnoverify    (hd1,0)
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader    +1

```

Click Save on the toolbar, Close the file & reboot. Try booting into Vista.

---

### Post by presence1960 on 2009-09-26
For future reference. When using (hdx,y) in GRUB, x = device & y = partition. Numbering for both starts at 0. 

It is the boot order of your disks in BIOS that determines the x designation. Your sdb disk boots first so it is (hd0). sda boots second so it is (hd1). Vista is the first partition on sda (sda1) so it is (hd1,0).

When windows is not on the disk that boots first you need the map lines.

---

### Post by Flux45 on 2009-09-26
it worked!!
thank you so very much!

if there is anyway you (or anyone) could help me with my other issue it would really make my day

[http://ubuntuforums.org/showthread.php?t=1276211](http://ubuntuforums.org/showthread.php?t=1276211)

---

### Post by rreese6 on 2009-09-26
Presence that was my thinking also. and since Grub Error 13 is related to the issue I saw on sdb1....ok I will stand by and watch your magic.

---

### Post by regirock on 2009-10-07
I've got the same problem as Flux45 had.. Here's my RESULTS.txt:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd8000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    81,144,314    81,144,252  83 Linux
/dev/sda2          81,144,315   257,072,129   175,927,815   b W95 FAT32
/dev/sda3         257,072,130   300,511,889    43,439,760   7 HPFS/NTFS
/dev/sda4         300,511,890   312,576,704    12,064,815   5 Extended
/dev/sda5         300,511,953   312,576,704    12,064,752  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="9287d01a-7513-4d32-b6d7-fdfc5f25c4d8" TYPE="ext3" 
/dev/sda2: UUID="A571-4D36" TYPE="vfat" 
/dev/sda3: UUID="9CD85F36D85F0DC0" TYPE="ntfs" 
/dev/sda5: UUID="9e2c95d2-84b8-48d1-b0bf-0ee720551fe7" TYPE="swap" 

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
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/austin/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=austin)


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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

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
# title        Windows XP
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
# kopt=root=UUID=9287d01a-7513-4d32-b6d7-fdfc5f25c4d8 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9287d01a-7513-4d32-b6d7-fdfc5f25c4d8

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

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        9287d01a-7513-4d32-b6d7-fdfc5f25c4d8
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=9287d01a-7513-4d32-b6d7-fdfc5f25c4d8 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        9287d01a-7513-4d32-b6d7-fdfc5f25c4d8
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=9287d01a-7513-4d32-b6d7-fdfc5f25c4d8 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        9287d01a-7513-4d32-b6d7-fdfc5f25c4d8
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=9287d01a-7513-4d32-b6d7-fdfc5f25c4d8 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        9287d01a-7513-4d32-b6d7-fdfc5f25c4d8
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=9287d01a-7513-4d32-b6d7-fdfc5f25c4d8 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        9287d01a-7513-4d32-b6d7-fdfc5f25c4d8
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=9287d01a-7513-4d32-b6d7-fdfc5f25c4d8 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=9e2c95d2-84b8-48d1-b0bf-0ee720551fe7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  16.6GB: boot/grub/menu.lst
  16.5GB: boot/grub/stage2
  16.5GB: boot/initrd.img-2.6.28-11-generic
  16.5GB: boot/initrd.img-2.6.28-15-generic
  16.5GB: boot/vmlinuz-2.6.28-11-generic
  16.5GB: boot/vmlinuz-2.6.28-15-generic
  16.5GB: initrd.img
  16.5GB: initrd.img.old
  16.5GB: vmlinuz
  16.5GB: vmlinuz.old

================================ sda2/boot.ini: ================================

[boot loader] 
timeout=5 
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /noexecute=alwaysoff 
C:\ = "Unidentified operating system on drive C." 

================================ sda2/BOOT.INI: ================================

[boot loader] 
timeout=5 
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /noexecute=alwaysoff 
C:\ = "Unidentified operating system on drive C." 
```

---

### Post by presence1960 on 2009-10-07
Where is windows installed sda2 or sda3? I need to know so I can tell you how to proceed.

But please confirm for me.

---

### Post by regirock on 2009-10-07
sda3 on a 20gb partition

---

### Post by presence1960 on 2009-10-07
> **regirock said:**
> sda3 on a 20gb partition

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    [COLOR="Red"]Boot files/dirs: [/COLOR]  

as you can see from the output you have no boot files/dir.

That means you need to fix Windows first. You will need to boot your XP install disk. if you don't have one hopefully you have a recovery console disk for XP. I know my old HP has a recovery partition, but i was given the option of burning an HP Tools CD which has a partitioner & XP recovery console on it. Follow the instructions [here]("http://ubuntuforums.org/showthread.php?t=1014708") for XP.

When complete reboot and make sure you boot directly into windows. If you do then boot off the Ubuntu Live CD to restore GRUB to MBR like this:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,0)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,0)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

```

Boot into Ubuntu, when the desktop loads open a terminal and run this command ```
gksu gedit /boot/grub/menu.lst
``` That is a lowercase L in .lst

scroll down to this line:
**### END DEBIAN AUTOMAGIC KERNELS LIST**

skip 1 line and add this entry for windows

```
title          Windows XP
rootnoverify   (hd0,2)
chainloader    +1
```

Click Save on toolbar, close file & reboot. Try the windows entry when the GRUB menu comes up.

---

### Post by regirock on 2009-10-13
Well, I tried to boot into XP after going through the recovery console like twenty times to fix stuff like NTLDR/bootcfg/hal.dll errors and now my computer just hangs at the XP boot screen..

---

### Post by presence1960 on 2009-10-14
> **regirock said:**
> Well, I tried to boot into XP after going through the recovery console like twenty times to fix stuff like NTLDR/bootcfg/hal.dll errors and now my computer just hangs at the XP boot screen..

that will not fix hal.dll errors. You made no mention of that previously. You can try copying hal.dll from the installation disk to the proper directory in the windows folder.

---

### Post by regirock on 2009-10-14
Oh, the Hal.dll errors only started happening as soon as I tried repairing with the XP guide you linked. But yeah, I copied over the hal.dll error from the CD to fix it. Now I just need to somehow get XP to actually boot. :(

---

### Post by presence1960 on 2009-10-14
> **regirock said:**
> Oh, the Hal.dll errors only started happening as soon as I tried repairing with the XP guide you linked. But yeah, I copied over the hal.dll error from the CD to fix it. Now I just need to somehow get XP to actually boot. :(

Remember that your windows install was messed up from jump street, see this from your output:

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    [COLOR="Red"]Boot files/dirs:[/COLOR]  

Unfortunately you had no directories or files needed to boot XP. If you can't get XP running you may have to reinstall XP...sorry but there may be no other alternative.

Here is my XP from my boot info script output just for your own reference:

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

---

### Post by regirock on 2009-10-14
Well, I just finished reinstalling XP... Which set of commands should I use when I load back up into Ubuntu?

---

### Post by presence1960 on 2009-10-14
> **regirock said:**
> Well, I just finished reinstalling XP... Which set of commands should I use when I load back up into Ubuntu?

You need to restore GRUB to MBR now so you can boot Ubuntu & Windows from GRUB menu at boot. Go back to post #13 and follow the instructions where you are asked to boot the Ubuntu CD. This will restore GRUB to MBR.

Then when you boot continue to follow the instructions by booting into Ubuntu and edit the windows entry in menu.lst.

---

