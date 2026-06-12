---
title: "Ubuntu and XP (truecrypt) dual boot with 2 HDDs using GRUB"
date: 2009-05-04
forum: Installation &amp; Upgrades
---

### Post by herbie53 on 2009-05-04
Hello, I have a dual boot set up on 2 HDDs as follows

HDD 1 80GB XP with Windows Bootloader on MBR
HDD 2 20GB Ubuntu with GRUB on MBR with a reference to to boot Windows from GRUB in menu.lst (set as boot drive in BIOS)
HDD 3 Data

I recently encrypted the Windows drive with Truecrypt. Now the reference in GRUB does not boot the Windows Partition, giving an error could not initialise application or something similar. I can boot both OSs by changing the boot drive in the BIOS, but I would prefer to choose with GRUB. What should I have in my menu.lst Windows item?

---

### Post by caljohnsmith on 2009-05-04
How about first pulling up your Grub's menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And add the following two entries:
```
title       2nd Boot Drive
rootnoverify     (hd1)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title       3rd Boot Drive
rootnoverify     (hd2)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1
```
Then reboot, and let me know if either of those entries boots Windows successfully or not; if not, let me know exactly what happens when you try each entry from the Grub menu. We can work from there if you want.

John

---

### Post by herbie53 on 2009-05-04
Thank you, I have done as you suggested, but no luck.

2nd Boot drive gets to the Truecrypt bootloader, but it claims to be corrupt, suggesting running the Truecrypt recovery cd to repair. If I change the boot drive to the Windows drive in the BIOS, Truecrypt bootloader has no such problems.

3rd Boot drive goes back to GRUB.

---

### Post by caljohnsmith on 2009-05-04
OK, I think it would help to get a clearer picture of your setup at this point, so how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

John

---

### Post by herbie53 on 2009-05-05
Looking at this, I probably should say the drive names may be mixed up, I have a strange issue where my drives are mounted with their names mixed up, I think it has something to do with using a program called "NTFS configuration tool". I need to learn to add to fstab myself!

Here goes...

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #3 in 
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No known boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

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

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7d848217

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    80,276,804    80,276,742   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders, total 39102336 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9f119f11

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    18,619,334    18,619,272   7 HPFS/NTFS
/dev/sdb2          18,619,335    39,102,209    20,482,875   5 Extended
/dev/sdb5    *     18,619,398    35,198,414    16,579,017  83 Linux
/dev/sdb6          35,198,478    39,102,209     3,903,732  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   160,810,649   160,810,587   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="68185B18185AE51A" LABEL="MUSIC" TYPE="ntfs" 
/dev/sdb1: UUID="A2E0B630E0B60B15" LABEL="Secondary" TYPE="ntfs" 
/dev/sdb5: UUID="4972f213-0d6f-4261-87c0-4d1cfd99c097" TYPE="ext3" 
/dev/sdb6: UUID="44b2083e-be63-4908-a76a-f56ffcb1746f" TYPE="swap" 

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
/dev/sdb1 on /media/Windows type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda1 on /media/Secondary type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/robin/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=robin)


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
timeout        6

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
# kopt=root=UUID=4972f213-0d6f-4261-87c0-4d1cfd99c097 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=4972f213-0d6f-4261-87c0-4d1cfd99c097

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

title Windows
root (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        4972f213-0d6f-4261-87c0-4d1cfd99c097
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=4972f213-0d6f-4261-87c0-4d1cfd99c097 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        4972f213-0d6f-4261-87c0-4d1cfd99c097
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=4972f213-0d6f-4261-87c0-4d1cfd99c097 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, kernel 2.6.27-14-generic
uuid        4972f213-0d6f-4261-87c0-4d1cfd99c097
kernel        /boot/vmlinuz-2.6.27-14-generic root=UUID=4972f213-0d6f-4261-87c0-4d1cfd99c097 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.27-14-generic (recovery mode)
uuid        4972f213-0d6f-4261-87c0-4d1cfd99c097
kernel        /boot/vmlinuz-2.6.27-14-generic root=UUID=4972f213-0d6f-4261-87c0-4d1cfd99c097 ro  single
initrd        /boot/initrd.img-2.6.27-14-generic

title        Ubuntu 9.04, kernel 2.6.27-11-generic
uuid        4972f213-0d6f-4261-87c0-4d1cfd99c097
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=4972f213-0d6f-4261-87c0-4d1cfd99c097 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
uuid        4972f213-0d6f-4261-87c0-4d1cfd99c097
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=4972f213-0d6f-4261-87c0-4d1cfd99c097 ro  single
initrd        /boot/initrd.img-2.6.27-11-generic

title        Ubuntu 9.04, memtest86+
uuid        4972f213-0d6f-4261-87c0-4d1cfd99c097
kernel        /boot/memtest86+.bin
quiet

title       2nd Boot Drive
rootnoverify     (hd1)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title       3rd Boot Drive
rootnoverify     (hd2)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sdb5 :
UUID=4972f213-0d6f-4261-87c0-4d1cfd99c097 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sdb6 :
UUID=44b2083e-be63-4908-a76a-f56ffcb1746f none swap sw 0 0
/dev/scd1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sdc1 /media/Music ntfs umask=222,utf8 0 0
/dev/sdb1 /media/Windows ntfs umask=222,utf8 0 0
/dev/sda1 /media/Secondary ntfs umask=222,utf8 0 0

=================== sdb5: Location of files loaded by Grub: ===================


  16.1GB: boot/grub/menu.lst
  16.1GB: boot/grub/stage2
  16.0GB: boot/initrd.img-2.6.28-11-generic
  16.3GB: boot/vmlinuz-2.6.28-11-generic
  16.0GB: initrd.img
  16.3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdc

00000000  ea 1e 7c 00 00 20 54 72  75 65 43 72 79 70 74 20  |..|.. TrueCrypt |
00000010  42 6f 6f 74 20 4c 6f 61  64 65 72 0d 0a 00 33 c0  |Boot Loader...3.|
00000020  8e d8 f6 06 b6 7d 01 75  07 8d 36 05 7c e8 dd 00  |.....}.u..6.|...|
00000030  b8 00 90 8e c0 81 3e 13  04 5b 02 7d 05 b8 00 20  |......>..[.}... |
00000040  8e c0 32 c0 bf 00 01 b9  ff 6a fc f3 aa 8c c0 2d  |..2......j.....-|
00000050  00 08 8e c0 b1 02 b0 04  bb 00 01 e8 be 00 66 33  |..............f3|
00000060  db be 00 01 b9 00 08 e8  c4 00 66 53 bb 00 0d b1  |..........fS....|
00000070  06 b0 39 f6 06 40 7d 01  74 04 b0 1a b1 24 e8 9b  |..9..@}.t....$..|
00000080  00 66 5b be 00 0d 8b 0e  b0 7d e8 a1 00 66 3b 1e  |.f[......}...f;.|
00000090  b2 7d 74 2c f6 06 40 7d  01 75 0e c6 06 40 7d 01  |.}t,..@}.u...@}.|
000000a0  b1 20 f6 06 b7 7d 02 75  ad 8d 36 51 7d e8 5d 00  |. ...}.u..6Q}.].|
000000b0  8d 36 05 7c e8 56 00 8d  36 41 7d e8 4f 00 eb fe  |.6.|.V..6A}.O...|
000000c0  8c c0 8e d8 fa 8e d0 bc  00 80 fb 52 68 0a 0d 68  |...........Rh..h|
000000d0  00 7a 68 00 81 2e 8c 06  dd 7c 9a 00 01 00 00 83  |.zh......|......|
000000e0  c4 06 5a 8c cb 8e db 85  c0 74 09 8d 36 8b 7d e8  |..Z......t..6.}.|
000000f0  1b 00 eb fe 8a 36 b7 7d  8c c0 05 00 08 8e c0 8e  |.....6.}........|
00000100  d8 fa 8e d0 bc fc 6b fb  06 68 00 01 cb 33 db b4  |......k..h...3..|
00000110  0e fc ac 84 c0 74 04 cd  10 eb f7 c3 b5 00 b6 00  |.....t..........|
00000120  b4 02 cd 13 73 07 8d 36  43 7d e8 e0 ff c3 1e 06  |....s..6C}......|
00000130  1f 66 33 c0 fc ac 66 03  d8 66 d1 c3 e2 f7 1f c3  |.f3...f..f......|
00000140  00 07 00 44 69 73 6b 20  65 72 72 6f 72 0d 0a 07  |...Disk error...|
00000150  00 4c 6f 61 64 65 72 20  64 61 6d 61 67 65 64 21  |.Loader damaged!|
00000160  20 55 73 65 20 52 65 73  63 75 65 20 44 69 73 6b  | Use Rescue Disk|
00000170  3a 20 52 65 70 61 69 72  20 4f 70 74 69 6f 6e 73  |: Repair Options|
00000180  20 3e 20 52 65 73 74 6f  72 65 00 44 43 00 00 00  | > Restore.DC...|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 06 1a  |................|
000001b0  ae 2d b0 3f 4e 23 00 02  01 00 00 00 00 00 80 01  |.-.?N#..........|
000001c0  01 00 07 fe ff ff 3f 00  00 00 5b c6 95 09 00 00  |......?...[.....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdc1

00000000  96 f3 9d bf ae 5f b1 a8  59 44 d4 46 c5 fb ac f2  |....._..YD.F....|
00000010  06 99 9f 55 6c a5 39 0c  ed 38 4d 28 0a 28 ba 28  |...Ul.9..8M(.(.(|
00000020  0a ce 7c b5 0e 56 46 0f  9b 5e 9c aa c4 f0 89 4a  |..|..VF..^.....J|
00000030  37 52 98 7b ca a0 7e bd  ba ca 63 65 f8 55 bc cb  |7R.{..~...ce.U..|
00000040  1d c4 78 84 b4 99 4f b0  4f 7d f4 76 21 49 30 e9  |..x...O.O}.v!I0.|
00000050  0f e6 92 1f 76 40 10 c0  15 50 1c 9b a6 b7 d1 9f  |....v@...P......|
00000060  63 34 24 1b b6 21 a8 a9  cb 52 16 7e a8 b2 cc 27  |c4$..!...R.~...'|
00000070  1e 2e 09 70 d7 fe 54 79  ae 1e 5d 11 c8 60 68 c4  |...p..Ty..]..`h.|
00000080  d4 d9 f7 0c 6d ee b3 95  44 3d 29 9d 82 07 47 0d  |....m...D=)...G.|
00000090  a7 6b 07 4c 02 b8 f7 ed  7d 46 5e d0 70 a7 e6 34  |.k.L....}F^.p..4|
000000a0  d5 07 8f a5 a8 20 e7 60  b6 85 b4 40 ca 03 bf 50  |..... .`...@...P|
000000b0  94 f2 52 98 18 b9 cc 9f  c3 14 21 42 07 e6 0c 22  |..R.......!B..."|
000000c0  48 2f 4e a3 99 36 92 e3  23 01 c5 19 63 17 de e8  |H/N..6..#...c...|
000000d0  e5 e4 3f c6 f1 87 03 ae  03 51 51 d3 45 cf 0d 3d  |..?......QQ.E..=|
000000e0  5f c5 bc 38 7c 0f 24 ea  69 33 1c 74 91 7b e2 3c  |_..8|.$.i3.t.{.<|
000000f0  df fd 5a 58 bc da 26 a5  fe 5d 96 2b 7b 1e cd 38  |..ZX..&..].+{..8|
00000100  f2 6d 2a d1 a4 5b d8 a9  82 f6 0b 7a 8d ac 08 7a  |.m*..[.....z...z|
00000110  76 33 e9 be 1e 48 d7 b9  99 30 46 90 88 e0 be 6b  |v3...H...0F....k|
00000120  b4 51 42 55 41 cc 15 ae  ec ae 8d b1 91 a2 91 3f  |.QBUA..........?|
00000130  28 81 3d 5a f0 c3 16 b8  3f ba 4f e5 12 9e 35 cc  |(.=Z....?.O...5.|
00000140  15 3c ac a7 7a 38 a0 e3  37 4f b2 75 83 25 04 16  |.<..z8..7O.u.%..|
00000150  d7 db 88 97 39 d2 5d 27  6e fa 66 39 ac e9 f2 4f  |....9.]'n.f9...O|
00000160  0b 54 f1 62 28 d5 81 d1  44 a1 70 b8 2a d5 9e c3  |.T.b(...D.p.*...|
00000170  d3 c7 3c 89 50 ce 2a ab  30 19 96 d3 ec bc 85 fd  |..<.P.*.0.......|
00000180  bf 00 57 2e 1c 18 b5 e8  ae ab ce aa 6b 7a 80 5c  |..W.........kz.\|
00000190  61 4c 7e a5 3b 4e 7e 3b  dc dc 4c 79 c9 9e 1f 73  |aL~.;N~;..Ly...s|
000001a0  22 8b 7f 46 10 8b 09 2e  ce b1 3a ec 12 a8 67 6c  |"..F......:...gl|
000001b0  63 20 59 30 d0 7f 7a 9e  9f 69 f9 85 be eb 19 b2  |c Y0..z..i......|
000001c0  ab 6c 57 c0 c8 a4 e9 8c  c1 d5 30 16 ae a7 5b 8a  |.lW.......0...[.|
000001d0  02 08 d5 5f 40 37 0f e7  c1 a3 9b ad e2 6f 71 c6  |..._@7.......oq.|
000001e0  2e fa 46 65 d8 ec c3 fc  57 d7 66 2e 92 d2 26 27  |..Fe....W.f...&'|
000001f0  94 c9 6c 3e f8 9b 68 f6  cc f0 6e a8 4f 96 84 11  |..l>..h...n.O...|
00000200



```
Thanks

---

### Post by caljohnsmith on 2009-05-05
OK, how about trying these entries in your menu.lst:
```
title       2nd Boot Drive #1
rootnoverify     (hd1)
chainloader +1

title       2nd Boot Drive #2
rootnoverify     (hd1)
map        (hd0) (hd1)
chainloader +1

title       2nd Boot Drive #3
rootnoverify     (hd1)
map        (hd1) (hd0)
chainloader +1
```
Please let me know exactly what happens when you try each of those entries from your Grub menu.

John

---

### Post by herbie53 on 2009-05-05
Here is what happens

#1 - NTLDR missing, press ctrl-alt-del etc.. after entering truecrypt password
#2 - Truecrypt loader damaged
#3 - After entering truecrypt password it says booting... and hangs.

Thanks

---

### Post by caljohnsmith on 2009-05-05
So if you boot the Truecrypt drive on start up directly from your BIOS, does it still boot into Windows OK?

---

### Post by herbie53 on 2009-05-05
Last time I tried, yes, I will double check now...

I can confirm that, I am in Windows now.

---

### Post by herbie53 on 2009-05-08
Bump!

---

### Post by caljohnsmith on 2009-05-08
Since we can't get Grub to boot your truecrypt drive OK, another option is to modify the Windows XP boot loader to boot Grub; that way you could always boot your truecrypt drive on start up, but you would get the option of booting either Win XP or Grub. If you would like help giving that a try, let me know.

John

---

### Post by herbie53 on 2009-05-13
There is an option in Truecrypt to press Esc to boot other drive, last time I tried it it appeared to try to boot from my 40GB drive with no OS on it. My configuration has changed, I installed Windows 7 onto the same drive as Ubuntu in a separate partition. This blew away GRUB from the MBR, so after a while I restored GRUB to the MBR, but now I can't get GRUB to boot Windows 7. Also, my 40GB music drive seems to have given up; one day it said it had some corrupt files, now it doesn't show up in Windows at all. If I get everything sorted again then yes I would like to try and get Truecrypt to loader GRUB!

---

