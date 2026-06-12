---
title: "Windows XP after installing Hardy as dual-boot"
date: 2009-03-02
forum: Installation &amp; Upgrades
---

### Post by tron101 on 2009-03-02
Hi,

I've had a very similar problem.

I installed ubuntu 8.10 (after installing a complete system on another pc) as a dual boot with Windows XP home.

If I run:

sudo bash ~/Desktop/boot_info_script*.sh

I get the message:

No such file or directory

I also cannot change my bios to boot from windows xp, it only has one Hard drive option.

Any help much apprecaited.

---

### Post by caljohnsmith on 2009-03-02
Tron101, you have to first download the Boot Info Script to your desktop before you run that command:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

---

### Post by tron101 on 2009-03-02
Hi caljohnsmith,

Thanks for getting back to me.

My troubles don't just relate to XP. If I try firefox to access the web, I get a 'Could  not initialise'n message.

I can access the internet as update downloads etc are fine.

I've run gparted to look at the disk space and get the following:

/dev/sda1   ntfs 279.05GiB
/dec/sda2   extended 19.04GiB
  /dev/sda5 ext3 18.2GiB  17.54used 674.36MiB unused
  /dev/sda6 linux.swap 854.99MiB

As I installed I ticked (:() the 'import documents and settings', which I guess may have been too much...


Best tron101

---

### Post by tron101 on 2009-03-02
OK,

Thanks for your patience

I've moved a load of files, managed to get the boot info file to the desktop and have the following results.

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdf

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /ubuntu/winboot/menu.lst /boot.ini /ntldr 
                       /NTDETECT.COM /wubildr.mbr /ubuntu/winboot/wubildr.mbr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdf1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd52bd52b

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   585,215,819   585,215,757   7 HPFS/NTFS
/dev/sda2         585,215,820   625,137,344    39,921,525   5 Extended
/dev/sda5         585,215,883   623,386,259    38,170,377  83 Linux
/dev/sda6         623,386,323   625,137,344     1,751,022  82 Linux swap / Solaris


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 512 MB, 512753664 bytes
16 heads, 32 sectors/track, 1956 cylinders, total 1001472 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb4b80e5c

Partition  Boot         Start           End          Size  Id System

/dev/sdf1    *             32     1,001,471     1,001,440   e W95 FAT16 (LBA)


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="0048270A4826FDD2" LABEL="3365-6502" TYPE="ntfs" 
/dev/sda5: UUID="80378a32-a299-450a-a191-2b0c01555399" TYPE="ext3" 
/dev/sda6: UUID="8d03414e-e3ec-4108-8b5b-3a915bd2be9a" TYPE="swap" 
/dev/sdf1: SEC_TYPE="msdos" UUID="1314-7805" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
overflow on /tmp type tmpfs (rw,size=1048576,mode=1777)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/john/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=john)
/dev/sdf1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sda1 on /media/3365-6502 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


======================== sda1/ubuntu/winboot/menu.lst: ========================

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
	find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
	configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
	fallback 2
	find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
	configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
	fallback 3
	find --set-root --ignore-floppies /menu.lst
	configfile /menu.lst

title find /boot/grub/menu.lst
	fallback 4
	find --set-root --ignore-floppies /boot/grub/menu.lst
	configfile /boot/grub/menu.lst

title find /grub/menu.lst
	fallback 5
	find --set-root --ignore-floppies /grub/menu.lst
	configfile /grub/menu.lst

title commandline
	commandline

title reboot
	reboot

title halt
	halt

================================ sda1/boot.ini: ================================

[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

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
# kopt=root=UUID=80378a32-a299-450a-a191-2b0c01555399 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=80378a32-a299-450a-a191-2b0c01555399

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		80378a32-a299-450a-a191-2b0c01555399
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=80378a32-a299-450a-a191-2b0c01555399 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		80378a32-a299-450a-a191-2b0c01555399
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=80378a32-a299-450a-a191-2b0c01555399 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		80378a32-a299-450a-a191-2b0c01555399
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=80378a32-a299-450a-a191-2b0c01555399 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		80378a32-a299-450a-a191-2b0c01555399
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=80378a32-a299-450a-a191-2b0c01555399 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		80378a32-a299-450a-a191-2b0c01555399
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=80378a32-a299-450a-a191-2b0c01555399 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=8d03414e-e3ec-4108-8b5b-3a915bd2be9a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 304.7GB: boot/grub/menu.lst
 307.5GB: boot/grub/stage2
 307.3GB: boot/initrd.img-2.6.27-11-generic
 305.2GB: boot/initrd.img-2.6.27-7-generic
 306.1GB: boot/vmlinuz-2.6.27-11-generic
 310.4GB: boot/vmlinuz-2.6.27-7-generic
 307.3GB: initrd.img
 305.2GB: initrd.img.old
 306.1GB: vmlinuz
 310.4GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdf1

00000000  eb 3c 90 44 4f 4b 30 31  2e 30 32 00 02 20 01 00  |.<.DOK01.02.. ..|
00000010  02 00 02 00 00 f8 7b 00  20 00 10 00 20 00 00 00  |......{. ... ...|
00000020  e0 47 0f 00 80 00 29 05  78 14 13 00 00 00 00 00  |.G....).x.......|
00000030  00 00 00 00 00 00 46 41  54 31 36 20 20 20 33 c9  |......FAT16   3.|
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


=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

---

### Post by caljohnsmith on 2009-03-02
So what exactly is the problem with Windows that you are experiencing? Can you boot into Windows OK?

---

### Post by tron101 on 2009-03-02
I can't boot into Windows XP Home Edition.

On booting up I get a screen with four Ububtu options and one for Windows XP.

If I highlight the windows option either I get a blank screen and everything hangs or I get a message:

TRAP 00000006 EXCEPTION
followed by several lines of code.

(The windows files are all there and I've run the Windows repair/install disk)

Thanks

---

### Post by caljohnsmith on 2009-03-02
According to the script results, Grub is configured correctly to boot Windows, and also your Windows' boot.ini file is configured OK. Therefore, I think you clearly have a Windows problem and not a Grub problem at this point. Have you tried running a "chkdsk" on your Windows partition? That's at least the first place I would start. You can do that by booting your Windows Install CD, go to the "recovery console" and do:
```
chkdsk /r
```
And run it as many times as it takes until it reports no errors. Given the type of Windows problem you are experiencing, I'm doubtful chkdsk will cure the problem, so if you find you still can't boot Windows after running the chkdsk, I would next do a "Windows Repair" from your Windows Install CD. Good luck and let me know how it goes.

---

### Post by tron101 on 2009-03-02
Sadly this hasn't made any difference, though now I don't get any error message at all when trying to boot windows.

I ran chkdsk twice, with no errors the second time and repaired windows using the repair function on the XP install disk.

Thanks for keeping with me on this.

---

### Post by caljohnsmith on 2009-03-02
So you are still not able to boot Windows even after doing a Windows Repair from the Windows CD? If that's true, I think probably your stuck with reinstalling Windows at this point. Can you access your Windows partition in Ubuntu? How about doing:
```
sudo mkdir /media/windows
sudo mount -t ntfs-3g -o force /dev/sda1 /media/windows
nautilus /media/windows &
```
If you can access Windows with the above commands, you could save all your important files and then reinstall Windows. Good luck and let me know how it goes.

---

### Post by tron101 on 2009-03-02
I hope you won't mind me asking a question (this is for my benefit as a newbie, not to question your advice).

I think I see that what we're trying to do here is move the current windows files over to the ubuntu file structure? The windows files are 171GiB, so how does the Ubuntu partition (19GiB) cope with that volume? (I fear this question highlights my ignorance.)

thanks again

---

### Post by caljohnsmith on 2009-03-02
All those commands do is mount your Windows partition on /media/windows, and the last command will pull up a file browser so you can browse through your Windows partition (assuming the Windows partition mounted OK). The commands don't copy any of your Windows files; that's for you to do. :)

---

### Post by tron101 on 2009-03-04
Sounds like a job for the weekend. Thankfully data backed.

Thanks again for your help.

---

### Post by tron101 on 2009-03-10
For anyone coming across this thread...the conclusion to the story as follows:

I reinstalled XP on a clean hard drive and transferred the data files without any problems.

I then went back to the old disk and used the windows repair disk to run fixmbr.

This reinstalled windows on the old disk without overwriting the data files, but means that the boot into ubuntu isn't available.

I've yet to summon up enough energy to reinstall ubuntu, though with two hard drives now it shouldn't be too difficult.

thank you for your support,

Tron101

---

