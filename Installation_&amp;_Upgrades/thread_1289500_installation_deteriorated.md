---
title: "installation deteriorated"
date: 2009-10-12
forum: Installation &amp; Upgrades
---

### Post by shadowjack22 on 2009-10-12
I have an acer one netbook that I wanted to dual-boot the netbook-remix on. I made an ext3 partition of 60 GB for it to reside on. I downloaded the remix image and used the products listed to load it onto a flash card for installation. The installation went  well with no seeming hassles. I then used the loader menu to select the Ubuntu, loaded up and did a quick checkout. Every thing seemed ok.
  I then tried to boot into the native XP. It would not load: it would just go into the driver loading GUI and the moving bars would go about three times across and die then go back to the GRUB. I had to reinstall XP, which does now work ok.
   Now, though, when I boot into Ubuntu, I get an error message that there is not enough space to do anything and promptly backs out to the logout and does nothing. The time before when I logged in, I got stuck on a page that could not even bring up Firefox. The file browser worked but Terminal would not accept an input nor would entering the root password get me into other areas that require said word.
   Basically, it was an install that had some problems (cancer) that spread quickly and has rendered the install into an effective coma. I like the idea of Ubuntu and eventually would like to put it dual-boot on my desktop, but this makes me think twice. What may be done to become properly functional again? Thanks.

---

### Post by presence1960 on 2009-10-13
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by shadowjack22 on 2009-10-13
Tried what you said, but terminal kept saying nobody home and did not run the script. Next? Thanks.

---

### Post by presence1960 on 2009-10-13
> **shadowjack22 said:**
> Tried what you said, but terminal kept saying nobody home and did not run the script. Next? Thanks.

why don't you try it again & take a screenshot of terminal saying no one is home and post it back here. You can take a screenshot on the Live CD/USB by going Applications > Accessories > Take Screenshot

---

### Post by shadowjack22 on 2009-10-13
[IMG]http://%7Edesktop[/IMG]I hope this comes out.[IMG]file:///tmp/moz-screenshot.jpg[/IMG][IMG]file:///tmp/moz-screenshot-1.jpg[/IMG]

---

### Post by presence1960 on 2009-10-13
> **shadowjack22 said:**
> [IMG]http://%7Edesktop[/IMG]I hope this comes out.[IMG]file:///tmp/moz-screenshot.jpg[/IMG][IMG]file:///tmp/moz-screenshot-1.jpg[/IMG]

there is no pic in your post. Take the screenshot and then click the paper clip in the toolbar to attach the image. When image is attached submit post. Like this:

---

### Post by shadowjack22 on 2009-10-14
[IMG]file:///tmp/moz-screenshot.jpg[/IMG][IMG]http://ubuntuforums.org/clipboard[/IMG]The screenshot doesn't seem to work quite as expected for me. I see no paper clip in the quick reply box area and if I save to clipboard then hit paste in the active area, it comes up with a "type in URL" entry to which I do not know the path. In any event, the terminal starts with Ubuntu@ubuntu:~ at which I type in sudo bash ~/desktop/boot_info_script*.sh, hit ENTER and it then comes up with bash: /home/ubuntu/desktop/boot_info_script*.sh: No such file or directory.

---

### Post by presence1960 on 2009-10-14
> **shadowjack22 said:**
> [IMG]file:///tmp/moz-screenshot.jpg[/IMG][IMG]http://ubuntuforums.org/clipboard[/IMG]The screenshot doesn't seem to work quite as expected for me. I see no paper clip in the quick reply box area and if I save to clipboard then hit paste in the active area, it comes up with a "type in URL" entry to which I do not know the path. In any event, the terminal starts with Ubuntu@ubuntu:~ at which I type in sudo bash ~/desktop/boot_info_script*.sh, hit ENTER and it then comes up with bash: /home/ubuntu/desktop/boot_info_script*.sh: No such file or directory.

if you use quick reply hit the go advanced button to enable all functions such as an attachment. personally I never use quick reply, I use quote or new reply

as far as running the script the output you posted : > "bash: /home/ubuntu/desktop/boot_info_script*.sh: No such file or directory." indicates that the boot info script you downloaded is not on the desktop, it must be on the desktop when you run that command from terminal.

---

### Post by shadowjack22 on 2009-10-14
Most interesting. The file does appear on Desktop; I just went back to the desktop and verified that it was there by using PROPERTIES for the file size. I have the desktop file browser open: maybe that's the problem?

---

### Post by presence1960 on 2009-10-14
> **shadowjack22 said:**
> Most interesting. The file does appear on Desktop; I just went back to the desktop and verified that it was there by using PROPERTIES for the file size. I have the desktop file browser open: maybe that's the problem?

Linux is case sensitive Desktop has a capital "D", you typed lowercase "d"

copy and paste the command into terminal : ```
sudo bash ~/Desktop/boot_info_script*.sh
```

---

### Post by shadowjack22 on 2009-10-14
/home/ubuntu/Desktop/RESULTS.txt

---

### Post by shadowjack22 on 2009-10-14
=========================== Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No known boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd2107a38

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    12,594,959    12,594,897  12 Compaq diagnostics
/dev/sda2    *     12,595,200   184,472,800   171,877,601   7 HPFS/NTFS
/dev/sda3         184,474,395   189,711,584     5,237,190   5 Extended
/dev/sda5         184,474,458   189,358,154     4,883,697  83 Linux
/dev/sda6         189,358,218   189,711,584       353,367  82 Linux swap / Solaris
/dev/sda4         189,711,585   312,576,704   122,865,120  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 3963 MB, 3963617280 bytes
122 heads, 62 sectors/track, 1023 cylinders, total 7741440 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8ef631df

Partition  Boot         Start           End          Size  Id System

/dev/sdb1     ? 2,112,536,064 4,071,284,395 1,958,748,332  66 Unknown
/dev/sdb2     ? 3,449,352,939 7,393,689,600 3,944,336,662   7 HPFS/NTFS
/dev/sdb3     ? 3,279,813,678 5,233,273,711 1,953,460,034  7d Unknown
/dev/sdb4     ? 4,179,361,792 4,187,684,891     8,323,100  6f Unknown

/dev/sdb1 ends after the last sector of /dev/sdb
/dev/sdb1 overlaps with /dev/sdb2
/dev/sdb1 overlaps with /dev/sdb3
/dev/sdb2 ends after the last sector of /dev/sdb
/dev/sdb2 overlaps with /dev/sdb3
/dev/sdb2 overlaps with /dev/sdb4
/dev/sdb3 ends after the last sector of /dev/sdb
/dev/sdb3 overlaps with /dev/sdb4
/dev/sdb4 ends after the last sector of /dev/sdb

blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="6648DBE748DBB3D1" LABEL="PQSERVICE" TYPE="ntfs" 
/dev/sda2: UUID="A2B6B6B0B6B68477" LABEL="ACER" TYPE="ntfs" 
/dev/sda4: UUID="6368746f-2074-616b-6f65-207575696400" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="b617d722-2db9-42af-8494-9b9ce0f92615" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="36af1b62-b46a-41b1-8706-70a3c92c1313" TYPE="swap" 
/dev/sdb: UUID="49ED-21FF" TYPE="vfat" 

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
/dev/sdb on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

=========================== sda5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=b617d722-2db9-42af-8494-9b9ce0f92615 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b617d722-2db9-42af-8494-9b9ce0f92615

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
uuid        b617d722-2db9-42af-8494-9b9ce0f92615
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=b617d722-2db9-42af-8494-9b9ce0f92615 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        b617d722-2db9-42af-8494-9b9ce0f92615
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=b617d722-2db9-42af-8494-9b9ce0f92615 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        b617d722-2db9-42af-8494-9b9ce0f92615
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


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Microsoft Windows XP Home Edition
rootnoverify    (hd0,1)
savedefault
chainloader    +1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=b617d722-2db9-42af-8494-9b9ce0f92615 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=36af1b62-b46a-41b1-8706-70a3c92c1313 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  94.7GB: boot/grub/menu.lst
  96.3GB: boot/grub/stage2
  96.3GB: boot/initrd.img-2.6.28-11-generic
  95.7GB: boot/vmlinuz-2.6.28-11-generic
  96.3GB: initrd.img
  95.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdb

00000000  eb 58 90 6d 6b 64 6f 73  66 73 00 00 02 08 20 00  |.X.mkdosfs.... .|
00000010  02 00 00 00 00 f8 00 00  20 00 40 00 00 00 00 00  |........ .@.....|
00000020  c0 96 1d 00 62 07 00 00  00 00 00 00 02 00 00 00  |....b...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 ff 21 ed 49 20  20 20 20 20 20 20 20 20  |..).!.I         |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c0 8e d0  |  FAT32   ..1...|
00000060  bc b4 7b 06 57 8e c0 b9  08 00 bf b4 7b f3 a5 8e  |..{.W.......{...|
00000070  d8 bb 78 00 0f b4 37 0f  a0 56 88 16 21 c7 20 d2  |..x...7..V..!. .|
00000080  78 15 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |x....?.G..d....||
00000090  88 4d f8 cd 13 eb 27 f6  45 f0 7f 75 08 66 8b 45  |.M....'.E..u.f.E|
000000a0  f8 66 a3 1c 7c b4 08 cd  13 72 13 20 e4 75 0f c1  |.f..|....r. .u..|
000000b0  ea 08 42 89 16 1a 7c 83  e1 3f 89 0e 18 7c fb bb  |..B...|..?...|..|
000000c0  aa 55 b4 41 8a 16 21 c7  cd 13 72 10 81 fb 55 aa  |.U.A..!...r...U.|
000000d0  75 0a f6 c1 01 74 05 c6  06 05 7d 00 66 a1 f8 7d  |u....t....}.f..}|
000000e0  bb 00 7e e8 10 00 66 81  3e 2c 7e e8 e1 06 77 0f  |..~...f.>,~...w.|
000000f0  85 c6 00 e9 42 02 bd 01  00 66 03 06 1c 7c 66 31  |....B....f...|f1|
00000100  d2 e9 00 00 eb 4f 55 e8  d5 00 66 0f b7 fd b9 10  |.....OU...f.....|
00000110  00 66 52 66 50 06 53 57  6a 10 89 e6 66 60 8a 16  |.fRfP.SWj...f`..|
00000120  21 c7 1e 16 1f b4 42 cd  13 1f 66 61 8d 64 10 72  |!.....B...fa.d.r|
00000130  10 5d 66 01 f8 29 fd c1  e7 09 01 fb 21 ed 75 c6  |.]f..)......!.u.|
00000140  c3 66 60 31 c0 8a 16 21  c7 cd 13 66 61 e2 c2 c6  |.f`1...!...fa...|
00000150  06 05 7d 4f 5d 66 52 66  50 55 53 66 0f b7 36 18  |..}O]fRfPUSf..6.|
00000160  7c 66 0f b7 3e 1a 7c 66  f7 f6 31 c9 87 ca 66 f7  ||f..>.|f..1...f.|
00000170  f7 e8 6b 00 29 ce 39 f5  76 02 89 f5 c0 e4 06 41  |..k.).9.v......A|
00000180  08 e1 88 c5 88 d6 8a 16  21 c7 95 b4 02 bd 10 00  |........!.......|
00000190  66 60 cd 13 66 61 72 17  66 0f b6 c8 c1 e0 09 5b  |f`..far.f......[|
000001a0  01 c3 5d 66 58 66 5a 66  01 c8 29 cd 75 a7 c3 4d  |..]fXfZf..).u..M|
000001b0  75 de 95 d1 2e fc 7d 75  df 31 f6 8e d6 bc b0 7b  |u.....}u.1.....{|
000001c0  8e de 66 8f 06 78 00 be  ea 7d ac 20 c0 74 09 b4  |..f..x...}. .t..|
000001d0  0e bb 07 00 cd 10 eb f2  98 cd 16 cd 19 eb fe 3b  |...............;|
000001e0  2e fc 7d 76 04 8b 2e fc  7d c3 42 6f 6f 74 20 65  |..}v....}.Boot e|
000001f0  72 72 6f 72 0d 0a 00 00  1c f9 1c 00 7f 00 55 aa  |rror..........U.|
00000200

Unknown BootLoader  on sdb1


Unknown BootLoader  on sdb2


Unknown BootLoader  on sdb3


Unknown BootLoader  on sdb4



=============================== StdErr Messages: ===============================

hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb2: No such file or directory
hexdump: /dev/sdb2: No such file or directory
hexdump: /dev/sdb3: No such file or directory
hexdump: /dev/sdb3: No such file or directory
hexdump: /dev/sdb4: No such file or directory
hexdump: /dev/sdb4: No such file or directory

---

### Post by presence1960 on 2009-10-14
according to your output your Ubuntu partition size is 4,883,697. Mine is 37,752,687 (18 GB). You do the math your partition is only about 2.3 GB.

Did you choose to do a side by side install and not move the slider on the graphic to allocate how much to give Ubuntu? See attached pic.

here is my output, my Ubuntu is 18 GB and on sdc6:

```
=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x85858585

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   488,392,064   488,392,002  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00072abb

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   976,768,064   976,768,002  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x02020202

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    83,891,429    83,891,367   7 HPFS/NTFS
/dev/sdc2          83,891,430   155,203,964    71,312,535   5 Extended
/dev/sdc5          83,891,493    92,277,359     8,385,867  82 Linux swap / Solaris
/dev/sdc6          92,277,423   130,030,109    37,752,687  83 Linux
/dev/sdc7         130,030,173   155,203,964    25,173,792  83 Linux

```

You are going to have to reinstall to a larger partition for Ubuntu.

---

### Post by shadowjack22 on 2009-10-14
I made a 60 GB ext3 partition originally for Ubuntu to reside in and did not use any partitioning by Ubuntu to set things up. Sounds like I should do a reinstall and go through the partitioning to give about 45 GB for the main Ubuntu with the rest for the swap file and whatever else it wants.

---

### Post by presence1960 on 2009-10-14
> **shadowjack22 said:**
> I made a 60 GB ext3 partition originally for Ubuntu to reside in and did not use any partitioning by Ubuntu to set things up. Sounds like I should do a reinstall and go through the partitioning to give about 45 GB for the main Ubuntu with the rest for the swap file and whatever else it wants.

Are you aware that if you create a partition for ubuntu that you must use the "Manual" option when doing the install? You do have a sizable partition at sda4 which is ext 3, but no OS is installed on it.

If you do a "install side by side" option you have to use the slider to split the Windows partition up and create how much space you want Ubuntu to use. But it only uses the space in the windows partition, not the partition you created at sda4.

---

### Post by shadowjack22 on 2009-10-15
Ouch! it sounds as if the best thing to do is to get back into my Windows partition and use the partitioning app to wipe the ext3 parts and add them back into the main partition, e.g. the original state, then redo the installation again using the side-by-side and the slider.
Two things to ask: (1) when I originally installed the Ubuntu, the GRUB loader messed with the XP load so it would not load. I had to reinstall XP to get it back in operation. Would the GRUB survive a format/install and/or would my XP get zapped again? It is not like my other computers that have quite an array  of programs & setups that would take a LOT of backup and time to replicate, but it does take time. I get the feeling that doing a dual boot of any thing has its quirks. Thanks.
Speaking of other computers, my desktop at home has a pair of HDD that have multiple partitions on them. What must I do to install Ubuntu onto a specific partition and make it behave properly,including a dual-boot that will let me load each OS properly? The netbook messup has me a bit concerned.

---

### Post by phillw on 2009-10-15
One the clearest methods for installing dual boot can be found here.

[http://apcmag.com/howto_search.htm?q=Keyword&catid=198](http://apcmag.com/howto_search.htm?q=Keyword&catid=198)

You'll want the install linux on existing XP system howto - that will cover the setting up of the partition to put ubuntu into & also ensure that grub includes XP in its boot list.

Hope that helps.

Phill.

---

### Post by shadowjack22 on 2009-10-15
Thanks for the site for dual-booting; it looks very straightforward but then, I found Ubuntu to be very nice during the set-up. According to one of the screenshots, one of the setup areas Ubuntu looks for would be free space. Since the HDD I plan to install Ubunu to has 4 partitions (3 for my XP Pro-System, Programs, Data and one to put the Ubunu on, currently formatted in ext3 format.) It would seem that it would be better to convert it back into free space for detection and resizing by Ubuntu for installation. My worry would be the GRUB: would it foul up the XP boot loading as it did with my netbook? My XP is a mature system with lotsa data and programs to reinstall.

---

### Post by phillw on 2009-10-15
> **shadowjack22 said:**
> Thanks for the site for dual-booting; it looks very straightforward but then, I found Ubuntu to be very nice during the set-up. According to one of the screenshots, one of the setup areas Ubuntu looks for would be free space. Since the HDD I plan to install Ubunu to has 4 partitions (3 for my XP Pro-System, Programs, Data and one to put the Ubunu on, currently formatted in ext3 format.) It would seem that it would be better to convert it back into free space for detection and resizing by Ubuntu for installation. My worry would be the GRUB: would it foul up the XP boot loading as it did with my netbook? My XP is a mature system with lotsa data and programs to reinstall.

It's a while since I did a dual boot install. I follow what you mean. Yeah, I'd go to making the partition you are going to use 'free'. And follow the instructions from the part it says you have sliced the disk.
Which is about here .....

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm?page=3](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm?page=3)

Or, you can just manually slice it and not use the auto-method - It's entirely up to you. I used manual slicing as i only wanted a 1GB SWAP area.

Phill.

---

### Post by shadowjack22 on 2009-10-15
That sounds good for both the netbook and the desktop. Still, I have the worry about the GRUB: would (or could) it mess with the XP loading up as it did with the netbook? How can this be prevented?

---

### Post by shadowjack22 on 2009-10-15
All right! time to end this post. thanks to the good offices of the nice people above, I decided to do a reinstall of the netbook mix and used the Ubuntu partitioner to set up the appropriate partition. Viola! complete success! Everything does as it is supposed to. Now for the fun of learning its little quirks and tweaks. That'll keep me busy for a while. Thanks to all who answered. Grazi!

---

