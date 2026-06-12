---
title: "Grub not loading or XP"
date: 2009-01-31
forum: Installation &amp; Upgrades
---

### Post by Bunoobtu on 2009-01-31
New to Linux and wanted to create a USB bootable OS.  I tried to install Unbuntu 8.10 on a thumb drive on a box with XP pro.  I selected the proper drive for the install but I think my XP boot file has been damaged and now neither XP or Unbuntu will start.  I tried to repair XP with BootCFG with no avail.  I also tried to repair XP with the recovery on the install disk.  Plus I tried to install XP which only installed the system files.  Still on boot up all I get is a grub error.  Some times it's code 5 or 21.

I can use the Ubuntu install disk and load the "try before installing" and see the two HDDs on my box and view the files.  So I decided to install Ubuntu on my box and partition part of a drive which all worked ok but i still get the same error on restart.  Any thoughts on what to try next?  I would like to get either OS working and would prefer both.

---

### Post by dstew on 2009-01-31
I understand you installed Ubuntu into a partition on your hard drive, but you cannot get past a grub error.

When you try to boot, do you see a grub menu, or only the error number, with no explanation? I suspect it is the latter, which means that grub is mis-installed.

That is easy to fix using the Live CD to re-install grub. [Here is a tutorial on how to do it]("http://ubuntuforums.org/showthread.php?t=224351"). If you want us to walk you through it, or are having trouble with the tutorial, post back here.

---

### Post by Bunoobtu on 2009-01-31
Thanks for the reply, yea no menu only error.  let me have a try of the link and get back to you..

---

### Post by Bunoobtu on 2009-01-31
Yea, I ready tried that and still get;
"grub loading stage1.5."
"Grub loading, please wait..."
"Error 21"
_

that it....  the code has changed from 5 to 20 now 21...

anything else to try?

---

### Post by caljohnsmith on 2009-01-31
In order to get a clearer picture of your setup related to your booting problem, how about booting your Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by Bunoobtu on 2009-01-31
Here you go.  


============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

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

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9dc96e9e

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        64,259        64,197  de Dell Utility
/dev/sda2    *         64,260   156,232,124   156,167,865   7 HPFS/NTFS


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x11b9dde8

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   161,099,819   161,099,757   7 HPFS/NTFS
/dev/sdb2         161,099,820   490,223,474   329,123,655   f W95 Ext'd (LBA)
/dev/sdb5         161,099,883   248,573,744    87,473,862   7 HPFS/NTFS
/dev/sdb6         322,199,703   490,223,474   168,023,772   7 HPFS/NTFS
/dev/sdb7         248,573,808   319,083,029    70,509,222  83 Linux
/dev/sdb8         319,083,093   322,199,639     3,116,547  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D4-0111" TYPE="vfat" 
/dev/sda2: UUID="F048183B481802D0" TYPE="ntfs" 
/dev/sdb1: UUID="0070F45A70F457BC" LABEL="Backup" TYPE="ntfs" 
/dev/sdb5: UUID="6A70F8DB70F8AEC7" LABEL="Pictures" TYPE="ntfs" 
/dev/sdb6: UUID="0C30FD2530FD1684" LABEL="Music" TYPE="ntfs" 
/dev/sdb7: UUID="2317f13a-86d4-41fc-a72f-c3b0f50ca86b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb8: UUID="7ddf51f0-062a-4bdf-b5b0-b32b4aeffa37" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

================================ sda2/boot.ini: ================================

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sdb7/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=2317f13a-86d4-41fc-a72f-c3b0f50ca86b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=2317f13a-86d4-41fc-a72f-c3b0f50ca86b

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
uuid		2317f13a-86d4-41fc-a72f-c3b0f50ca86b
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2317f13a-86d4-41fc-a72f-c3b0f50ca86b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		2317f13a-86d4-41fc-a72f-c3b0f50ca86b
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2317f13a-86d4-41fc-a72f-c3b0f50ca86b ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		2317f13a-86d4-41fc-a72f-c3b0f50ca86b
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1


=============================== sdb7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb7
UUID=2317f13a-86d4-41fc-a72f-c3b0f50ca86b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb8
UUID=7ddf51f0-062a-4bdf-b5b0-b32b4aeffa37 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb7: Location  of files loaded by Grub: ===================


 146.1GB: boot/grub/menu.lst
 146.1GB: boot/grub/stage2
 140.4GB: boot/initrd.img-2.6.27-7-generic
 140.4GB: boot/vmlinuz-2.6.27-7-generic
 140.4GB: initrd.img
 140.4GB: vmlinuz

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  eb 46 90 44 65 6c 6c 20  34 2e 31 00 02 04 01 00  |.F.Dell 4.1.....|
00000010  02 00 02 00 00 f8 3f 00  3f 00 ff 00 3f 00 00 00  |......?.?...?...|
00000020  c5 fa 00 00 80 00 29 11  01 d4 07 44 65 6c 6c 55  |......)....DellU|
00000030  74 69 6c 69 74 79 46 41  54 31 36 20 20 20 00 00  |tilityFAT16   ..|
00000040  00 00 00 00 00 00 00 00  fa b8 00 00 8e d0 bc fc  |................|
00000050  7b fb fc 8e d8 81 3e 72  04 45 44 74 1d ff 0e 13  |{.....>r.EDt....|
00000060  04 8b 0e 13 04 c1 e1 06  8e c1 b9 00 01 33 f6 33  |.............3.3|
00000070  ff f3 66 a5 c7 06 72 04  45 44 8e c0 bd 00 7c e8  |..f...r.ED....|.|
00000080  21 01 0f 82 bb 00 66 0f  b7 86 16 00 66 d1 e0 66  |!.....f.....f..f|
00000090  0f b7 9e 0e 00 66 03 c3  66 03 86 1c 00 66 89 86  |.....f..f....f..|
000000a0  3e 00 8b 86 11 00 c1 e8  04 89 86 46 00 bb 00 05  |>..........F....|
000000b0  e8 aa 00 0f 82 8a 00 ba  10 00 b9 0b 00 be f2 7d  |...............}|
000000c0  8b fb f3 a6 74 16 83 c3  20 4a 75 ee 66 ff 86 3e  |....t... Ju.f..>|
000000d0  00 ff 8e 46 00 75 d6 be  e1 7d eb 6d 66 0f b7 86  |...F.u...}.mf...|
000000e0  11 00 66 ba 20 00 00 00  66 f7 e2 66 0f b7 8e 0b  |..f. ...f..f....|
000000f0  00 66 03 c1 66 48 66 f7  f1 66 01 86 3e 00 66 8b  |.f..fHf..f..>.f.|
00000100  86 3e 00 66 89 46 fc 66  0f b7 47 1a 8b f8 2d 02  |.>.f.F.f..G...-.|
00000110  00 66 0f b6 9e 0d 00 66  f7 e3 66 01 86 3e 00 bb  |.f.....f..f..>..|
00000120  00 07 c7 86 46 00 04 00  e8 32 00 72 14 81 c3 00  |....F....2.r....|
00000130  02 66 ff 86 3e 00 ff 8e  46 00 75 ec ea 00 02 70  |.f..>...F.u....p|
00000140  00 be d4 7d eb 03 be e1  7d e8 02 00 eb fe ac 3c  |...}....}......<|
00000150  00 74 09 b4 0e bb 07 00  cd 10 eb f2 c3 66 8b 86  |.t...........f..|
00000160  3e 00 66 33 d2 66 0f b7  8e 18 00 66 f7 f1 66 42  |>.f3.f.....f..fB|
00000170  88 96 45 00 66 33 d2 66  0f b7 8e 1a 00 66 f7 f1  |..E.f3.f.....f..|
00000180  88 96 44 00 89 86 42 00  b8 01 02 8b 8e 42 00 c0  |..D...B......B..|
00000190  e5 06 0a ae 45 00 86 e9  8a b6 44 00 8a 96 24 00  |....E.....D...$.|
000001a0  cd 13 c3 80 3e c2 07 06  74 29 b8 01 02 bb 00 06  |....>...t)......|
000001b0  b9 01 00 b6 00 8a 96 24  00 cd 13 72 16 c6 06 c2  |.......$...r....|
000001c0  07 06 b8 01 03 bb 00 06  b9 01 00 b6 00 8a 96 24  |...............$|
000001d0  00 cd 13 c3 44 69 73 6b  20 65 72 72 6f 72 0d 0a  |....Disk error..|
000001e0  00 4d 69 73 73 69 6e 67  20 6c 6f 61 64 65 72 0d  |.Missing loader.|
000001f0  0a 00 49 4f 20 20 20 20  20 20 53 59 53 00 55 aa  |..IO      SYS.U.|
00000200

---

### Post by caljohnsmith on 2009-01-31
A Grub error 21 is not a good sign, because that means "selected disk does not exist," and you have two drives so it should exist. For you to get that Grub error, it looks like you must be booting your Windows sda drive on start up, because your Windows drive also has Grub installed to its MBR (Master Boot Record). Can you change your BIOS to boot the Ubuntu sdb drive on start up? If so, there's one more thing to do to make sure the Ubuntu drive is bootable:
```
sudo sfdisk -A1 /dev/sdb
```
Then reboot, set your BIOS to boot the sdb Ubuntu drive, and let me know how far you get. We can work from there.

---

### Post by Bunoobtu on 2009-01-31
Thanks but no worky... tried your script but still got an error code.  This time it was 22 instead of 21.  Checked Bios and no option to boot other than primary IDE drive.

---

### Post by caljohnsmith on 2009-01-31
OK, how about downloading the [Super Grub Disk]("http://www.supergrubdisk.org"), boot that, and at the first main menu press "c" to get the command line. Then do:
```
grub> geometry (hd0)
grub> geometry (hd1)
```
And please post the output of those commands.

---

### Post by Bunoobtu on 2009-01-31
downloaded and burned a CD with the iso file on it but when I reboot all i get is the error code.  It's not booting the iso on the disk.

---

### Post by dstew on 2009-01-31
You have to burn the Supergrub disk as an image, not simply copy the .iso to the CD.

---

### Post by Bunoobtu on 2009-01-31
> **dstew said:**
> You have to burn the Supergrub disk as an image, not simply copy the .iso to the CD.

Oops yup did it wrong.  anyway created the bootable cd with the iso and now the box comes up with just a blinkling cursor and is locked up.... This is frustrating....

---

### Post by Bunoobtu on 2009-01-31
Is there anyway I can uninstall grub and just run ubuntu from XP?

---

### Post by dstew on 2009-01-31
> Is there anyway I can uninstall grub and just run ubuntu from XP?Yes, I think you can use the Windows boot loader to boot Ubuntu. You have to have grub installed somewhere, like on a floppy, copy the floppy MBR to a file, then tell the Windows to boot that file by modifying boot.ini. See [this HowTo]("http://ubuntuforums.org/showthread.php?t=56723").

I think you might be burning your image disks at too high a speed. You should burn them at 4x speed at most. Image disks are not like audio disks. If your audio disk has a few missing bits, you would never notice. But an image disk that has some bad bits might be completely ruined.

---

