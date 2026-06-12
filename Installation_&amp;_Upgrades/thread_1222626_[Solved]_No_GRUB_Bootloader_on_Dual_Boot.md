---
title: "[Solved] No GRUB Bootloader on Dual Boot"
date: 2009-07-25
forum: Installation &amp; Upgrades
---

### Post by distortedecho on 2009-07-25
OK, I have a Dell Optiplex with a 250GB Sata disk drive.

I have an additional 250GB PATA drive from my old desktop.
This is hanging (literally) from the secondary CD-ROM on the IDE Cable. So the IDE cable and power go to my D:\ then my PATA drive as it's slave.

My PATA drive still has the XP OS on it from my old desktop.

My primary drive, my SATA, is primary as it boots XP with the new OS install on it - so I know the boot order is correct, to some extent.

So, I decided I wanted to dual boot Ubuntu, and went ahead and installed it on the SATA Drive. I know it's the SATA drive because I can see the Ubuntu partition in XP's Disk Management.

In hind sight, I should really have disconnected the IDE drive but would like to avoid disconnecting everything and opening up the Dell, twice.

Is there a way I can get GRUB or Windows bootloader to see, list and boot the Ubuntu partition?

At the moment, I turn on the tower and it boots directly in to XP installed on the SATA.

Thanks

---

### Post by Herman on 2009-07-25
I'm guessing that most likely your GRUB boot loader in Ubuntu has it's pointer installed in the second hard disk's MBR instead of your first hard disk's MBR.
Normally, your computer's BIOS will only look in the first hard disk's MBR for a pointer to a boot loader, (or IPL or 'stage1', to use the proper terms).

One thing you can try to begin with would be pressing your pause key and your enter key alternately and repeatedly during boot-up to give you time to read any directions displayed on some of the boot-up screens which whiz by so quickly.
You should (hopefully), see some text on one of those screens to indicate which key you need to press for a BIOS boot menu. Often it's F12, but varies according to your computer brand and motherboard.

You should be able to select your second hard disk and boot Ubuntu that way.
I realize mine's probably a lot different from yours, but here's a link anyway, to illustrate what I mean, [How I boot from my BIOS]("http://members.iinet.net.au/%7Eherman546/p1.html#How_I_boot_from_my_BIOS_with_my_F12_key") with my F12 key.

If you can't do that, another idea would be to go download a copy of [Super Grub Disk]("http://www.supergrubdisk.org/"), that should help you boot to begin with.
You can probably also use Super Grub Disk to install GRUB's pointer (IPL) to MBR in the first hard disk too if you want.

Maybe try one of those ideas and report back on what happens.

---

### Post by presence1960 on 2009-07-25
Boot from the Ubuntu Live CD and choose "try ubuntu without any changes ". When the desktop loads open Firefox and download to your desktop Boot Info Script 0.32 from here: [http://sourceforge.net/projects/bootinfoscript/files/](http://sourceforge.net/projects/bootinfoscript/files/)
Once downloaded to your desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
```
This will create a RESULTS.txt file on your desktop. paste the entire contents of that file here. This will give us all the info on your setup and boot process including where GRUB is installed and where it points to.

---

### Post by distortedecho on 2009-07-25
Herman,

I've read a little about Super Grub Disk, but would need a little direction (holding my hand) as I would be afraid to 'eff' anything up and not be able to boot into any OS at all. 

Presence - I'll do as instructed and post the results.txt shortly.

Thank you both for your time.

---

### Post by distortedecho on 2009-07-25
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => No known boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

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

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
240 heads, 63 sectors/track, 32301 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xabb7ffe0

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   163,855,439   163,855,377   7 HPFS/NTFS
/dev/sda2         163,855,440   488,391,119   324,535,680   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x844b844b

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   315,066,779   315,066,717   7 HPFS/NTFS
/dev/sdb2         315,066,780   488,392,064   173,325,285   5 Extended
/dev/sdb5         315,066,843   485,420,039   170,353,197  83 Linux
/dev/sdb6         485,420,103   488,392,064     2,971,962  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________
Note: sector size is 2048 (not 512)

Disk /dev/sdc: 1015 MB, 1015021568 bytes
32 heads, 61 sectors/track, 253 cylinders, total 495616 sectors
Units = sectors of 1 * 2048 = 2048 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1     ?   778,135,908 1,919,645,538 1,141,509,631  72 Unknown
/dev/sdc2     ?   168,689,522 2,104,717,761 1,936,028,240  65 Novell Netware 386
/dev/sdc3     ? 1,869,881,465 3,805,909,656 1,936,028,192  79 Unknown
/dev/sdc4     ? 2,885,681,152 2,885,736,650        55,499   d Unknown

/dev/sdc1 ends after the last sector of /dev/sdc
/dev/sdc1 overlaps with /dev/sdc2
/dev/sdc1 overlaps with /dev/sdc3
/dev/sdc2 ends after the last sector of /dev/sdc
/dev/sdc2 overlaps with /dev/sdc3
/dev/sdc3 ends after the last sector of /dev/sdc
/dev/sdc3 overlaps with /dev/sdc4
/dev/sdc4 ends after the last sector of /dev/sdc

blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="9884BAFB84BADB48" TYPE="ntfs" 
/dev/sda2: UUID="5E407F3E407F1C49" LABEL="Storage" TYPE="ntfs" 
/dev/sdb1: UUID="E83CDFFB3CDFC2AC" TYPE="ntfs" 
/dev/sdb5: UUID="ed298760-5672-4486-87ba-3fc395b40e6a" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb6: TYPE="swap" UUID="febf56c9-488d-4738-91f5-ef054f686c36" 
/dev/ramzswap0: TYPE="swap" 
/dev/sdc: LABEL="RICHARD_S I" UUID="04BF-CD93" TYPE="vfat" 

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
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdc on /media/RICHARD_S I type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


================================ sdb1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


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
# kopt=root=UUID=ed298760-5672-4486-87ba-3fc395b40e6a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ed298760-5672-4486-87ba-3fc395b40e6a

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
uuid		ed298760-5672-4486-87ba-3fc395b40e6a
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=ed298760-5672-4486-87ba-3fc395b40e6a ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		ed298760-5672-4486-87ba-3fc395b40e6a
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=ed298760-5672-4486-87ba-3fc395b40e6a ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		ed298760-5672-4486-87ba-3fc395b40e6a
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
rootnoverify	(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


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
UUID=ed298760-5672-4486-87ba-3fc395b40e6a /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=febf56c9-488d-4738-91f5-ef054f686c36 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 202.7GB: boot/grub/menu.lst
 202.7GB: boot/grub/stage2
 202.7GB: boot/initrd.img-2.6.28-11-generic
 202.6GB: boot/vmlinuz-2.6.28-11-generic
 202.7GB: initrd.img
 202.6GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdc

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 08 04 20 00  |.X.MSDOS5.0... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 00 00 00  |........?.......|
00000020  00 90 07 00 f2 00 00 00  00 00 00 00 02 00 00 00  |................|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 93 cd bf 04 52  49 43 48 41 52 44 5f 53  |..)....RICHARD_S|
00000050  20 49 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  | IFAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 08  |{......|.N..V@..|
00000070  cd 13 73 05 b9 ff ff 8a  f1 66 0f b6 c6 40 66 0f  |..s......f...@f.|
00000080  b6 d1 80 e2 3f f7 e2 86  cd c0 ed 06 41 66 0f b7  |....?.......Af..|
00000090  c9 66 f7 e1 66 89 46 f8  83 7e 16 00 75 38 83 7e  |.f..f.F..~..u8.~|
000000a0  2a 00 77 32 66 8b 46 1c  66 83 c0 0c bb 00 80 b9  |*.w2f.F.f.......|
000000b0  01 00 e8 2b 00 e9 48 03  a0 fa 7d b4 7d 8b f0 ac  |...+..H...}.}...|
000000c0  84 c0 74 17 3c ff 74 09  b4 0e bb 07 00 cd 10 eb  |..t.<.t.........|
000000d0  ee a0 fb 7d eb e5 a0 f9  7d eb e0 98 cd 16 cd 19  |...}....}.......|
000000e0  66 60 66 3b 46 f8 0f 82  4a 00 66 6a 00 66 50 06  |f`f;F...J.fj.fP.|
000000f0  53 66 68 10 00 01 00 80  7e 02 00 0f 85 20 00 b4  |Sfh.....~.... ..|
00000100  41 bb aa 55 8a 56 40 cd  13 0f 82 1c 00 81 fb 55  |A..U.V@........U|
00000110  aa 0f 85 14 00 f6 c1 01  0f 84 0d 00 fe 46 02 b4  |.............F..|
00000120  42 8a 56 40 8b f4 cd 13  b0 f9 66 58 66 58 66 58  |B.V@......fXfXfX|
00000130  66 58 eb 2a 66 33 d2 66  0f b7 4e 18 66 f7 f1 fe  |fX.*f3.f..N.f...|
00000140  c2 8a ca 66 8b d0 66 c1  ea 10 f7 76 1a 86 d6 8a  |...f..f....v....|
00000150  56 40 8a e8 c0 e4 06 0a  cc b8 01 02 cd 13 66 61  |V@............fa|
00000160  0f 82 54 ff 81 c3 00 02  66 40 49 0f 85 71 ff c3  |..T.....f@I..q..|
00000170  4e 54 4c 44 52 20 20 20  20 20 20 00 00 00 00 00  |NTLDR      .....|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 52 65  |..............Re|
000001b0  6d 6f 76 65 20 64 69 73  6b 73 20 6f 72 20 6f 74  |move disks or ot|
000001c0  68 65 72 20 6d 65 64 69  61 2e ff 0d 0a 44 69 73  |her media....Dis|
000001d0  6b 20 65 72 72 6f 72 ff  0d 0a 50 72 65 73 73 20  |k error...Press |
000001e0  61 6e 79 20 6b 65 79 20  74 6f 20 72 65 73 74 61  |any key to resta|
000001f0  72 74 0d 0a 00 00 00 00  00 ac cb d8 00 00 55 aa  |rt............U.|
00000200

Unknown BootLoader  on sdc1


Unknown BootLoader  on sdc2


Unknown BootLoader  on sdc3


Unknown BootLoader  on sdc4



=============================== StdErr Messages: ===============================

hexdump: /dev/sdc1: No such file or directory
hexdump: /dev/sdc1: No such file or directory
hexdump: /dev/sdc2: No such file or directory
hexdump: /dev/sdc2: No such file or directory
hexdump: /dev/sdc3: No such file or directory
hexdump: /dev/sdc3: No such file or directory
hexdump: /dev/sdc4: No such file or directory
hexdump: /dev/sdc4: No such file or directory
```

---

### Post by presence1960 on 2009-07-25
GRUB is installed on MBR of sda. So if GRUB is not showing on boot that means your sdb drive is set to boot first. What you need to do is restore GRUB to MBR oF sdb by doing this:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd1,4)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd1,4) or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd1) to install GRUB to MBR
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

You may have to edit your windows entry in menu.lst after that, but we'll cross that bridge when we get to it. let's get GRUB on boot first.

Or you can set your sda disk as first in hard disk boot order in BIOS. Either way will work.

---

### Post by distortedecho on 2009-07-26
Many thanks Presence, but before I attack this, can you also tell me how to REMOVE Grub from sdb?

I all ready knew which MBR Grub was on from the start, and your instructions are perfect for allowing me to get GRUB onto the correct MBR - but I don't want to leave Grub on a disk that does not contain a Ubuntu partition.

If you could help me with this also I'd greatly appreciate it.

---

### Post by presence1960 on 2009-07-26
you have two options: 1) don't worry about it, it won't hurt anything. If you ever install another OS to sdb then you can write the bootloader of that OS to MBR. 2) if it is irking you that much you can restore Windows XP bootloader to sda MBR. That will entail a few steps. First go into BIOS and set sdb as first boot in your HDD boot order. If you neglect to do this and try the next step you will write to MBR of sda. Then go here for instructions after you have set sda as first boot: [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)  When complete go back in BIOS and set sdb as first boot in HDD boot order.

I would not do the above because that GRUB there is not affecting anything. I would leave well enough alone. What seems more pressing to me is you have a disk (sda) which has a second XP on it. There is no need for 2 XPs on the same machine. I would get rid of the XP on sda and free up that entire hard disk or get rid of the XP on sdb and free up that partition's space. Bottom line which ever install of XP you aren't using I would remove.

I would leave GRUB on sdb (if the XP on sdb is booting) and free up the entire sda drive. To boot if you do that go into BIOS and set sdb as first boot.:popcorn:

---

### Post by distortedecho on 2009-07-28
Presense, many thanks this worked a treat - and another Ubuntu/Linux Lesson learnt :)

Thinking about the old IDE drive, I think it's now time to remove that XP partition, and just use the drive for storage.

Thanks again

---

### Post by presence1960 on 2009-07-28
glad you got it working. Enjoy Ubuntu!

---

