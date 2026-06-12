---
title: "Grub Error 21"
date: 2009-02-01
forum: Installation &amp; Upgrades
---

### Post by tiffmc on 2009-02-01
Hi,

I am very new to Ubuntu as I have never used anything other than Windows so I apologise in advance.

I decided that I wanted to install Ubuntu on my external USB hard drive while keeping Windows Vista on my internal notebook hard drive. It worked ok and now I have Ubuntu installed on my external hard drive, but I think I went wrong somewhere. Everytime I try to boot into Vista without my external hard drive plugged in, it comes up with "Grub Error 21". However, if my external hard drive is plugged in, it will take me to the menu where it allows me to select which operating system I want to go into.

How can I fix it so I don't need to plug my external hard drive in to boot into Vista?

Any help would be very much appreciated. Thank you!

---

### Post by TaskmasterC on 2009-02-01
To my knowledge, you must have it connected to the machine. I am however, new to linux as well, so I may be wrong. I run 3 OS's, XP, Vista and Ubuntu UE2. If I disconnect my second HD, I cannot load XP. It is the only OS on my primary drive, so I can only presume that the grub loader will not function unless it finds more than one OS. Hope this helps.

---

### Post by tiffmc on 2009-02-02
Really? I was under the impression that you could boot into windows without the external hard drive.

I've been searching the forums and I think I should've installed Grub to my external hard drive, but by default it installed on my internal hard drive. Any idea how to fix this?

Also, when I set my boot order and set it to boot from the USB drive before the internal drive, it doesn't go to the menu.. it is just a black screen with a blinking cursor. I have to have the boot order set to boot the internal hard drive before the external USB hard drive and then the menu appears.

---

### Post by caljohnsmith on 2009-02-02
Tiffmc, if your BIOS supports booting from the USB Ubuntu drive, then what you can do is install Grub to the MBR (Master Boot Record) of your Ubuntu drive, and also restore a Windows MBR to your Windows drive. That way when you have the Ubuntu drive connected, you will be able to boot into Ubuntu (or Windows too if you add an entry for Windows in your Grub menu), and when you disconnect the Ubuntu drive you should be able to boot into Windows. If that sounds good, how about opening a terminal in Ubuntu (Applications > Accessories > Terminal) and do:
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
Then to restore a Windows MBR to your Windows drive, you can do:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
Then reboot, try booting the Ubuntu drive, and let me know how far you get. Also try booting your Windows drive and let me know if you can boot into Windows OK again. We can work from there.

---

### Post by tiffmc on 2009-02-02
Thank you so so much! It worked and all is running smoothly! I can't thank you enough!! :D

---

### Post by caljohnsmith on 2009-02-02
Great, glad to hear that worked OK; cheers and enjoy your new Ubuntu install. :)

---

### Post by Robgould on 2009-02-17
This was AWESOME!!!  Thank you so much!

---

### Post by Jarige on 2009-02-18
Thank you, you've solved my problem either. I'm very gratefull caljohnsmith!

Thank you!:D

---

### Post by Jarige on 2009-11-19
Ok, my installation went slow and boggy.
So I wanted to reinstall it, using the instructions I got before:
[http://ubuntuforums.org/showthread.php?t=1069951]("http://ubuntuforums.org/showthread.php?t=1069951")

Well, installation went without problems, and I expected it to have problems with grub again, and to be able to solve it with the commands described here.
It was only now that I realised that I installed grub2, and that it might be different.
Without external harddrive, it will say this:

```
GRUB loading.
error: no such disk
grub rescue>_
```

(Where _ is a place I can type something)

With external harddrive, it will say this:

```
GRUB Loading stage1.5.
GRUB loading, please wait...
Error 15
```

The commands you've described here are unknown commands to Ubuntu 9.10.

How do I get the same result using Ubuntu 9.10?

---

### Post by presence1960 on 2009-11-19
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB with your external plugged in. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.35 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Jarige on 2009-11-19
Well thats called a huge output.
3 more things:
1. I reinstalled the mbr on drive 1 using Lilo, and using the command as described above
2. I tried dpkg-reconfigure grub-pc to install grub2 on my third hard drive (my external hdd) but it didn't solve the problem
3. There's an (bootable) USB drive in my computer, you should see the difference I guess. There are 4 drives on my computer now:
- Hard drive 1: Vista and some HP recovery crap
- Hard drive 2: data
- Hard drive 3: External hdd, NTFS partition for a lot of data, and Ext4 partitions for Ubuntu
- USB drive 4: some bootable partitioning software, I used this to move the script over and back to some other computer, since I don't have internet on Ubuntu.

Thank you for your fast reply, and I hope you can help :O

```
============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Grub0.97 is installed in the MBR of /dev/sdd and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sde

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdd3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2bda47a4

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   294,889,139   294,889,077   7 HPFS/NTFS
/dev/sda2         294,889,140   312,576,704    17,687,565   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0adc4429

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   312,576,704   312,576,642   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe3414533

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63   520,279,742   520,279,680   7 HPFS/NTFS
/dev/sdd2         520,281,090   536,281,829    16,000,740  83 Linux
/dev/sdd3         536,281,830   540,282,014     4,000,185  82 Linux swap / Solaris
/dev/sdd4         540,282,015   625,137,344    84,855,330   5 Extended
/dev/sdd5         540,282,078   625,137,344    84,855,267  83 Linux


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 493 MB, 493879296 bytes
64 heads, 32 sectors/track, 471 cylinders, total 964608 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *             32       960,511       960,480   e W95 FAT16 (LBA)


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="12D746180E12D220" LABEL="OS" TYPE="ntfs" 
/dev/sda2: UUID="2C88743C8874071C" LABEL="HP_RECOVERY" TYPE="ntfs" 
/dev/sdb1: UUID="B4B04414B043DC0C" LABEL="DATA" TYPE="ntfs" 
/dev/sdd1: UUID="DCC81103C810DE18" LABEL="FREECOM_HDD" TYPE="ntfs" 
/dev/sdd2: UUID="22f27d0f-1692-42d2-88fd-e49aa44007f1" TYPE="ext4" 
/dev/sdd3: UUID="53ea486c-49b9-40c9-993e-257dbaa71df5" TYPE="swap" 
/dev/sdd5: UUID="a3ba66b2-6998-4c7a-83d8-1c7b3dc7bd42" TYPE="ext4" 
/dev/sde1: SEC_TYPE="msdos" LABEL="HDDREG" UUID="067B-1A2C" TYPE="vfat" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdd5 on /media/a3ba66b2-6998-4c7a-83d8-1c7b3dc7bd42 type ext4 (rw,nosuid,nodev,uhelper=devkit)
/dev/sdd2 on /media/22f27d0f-1692-42d2-88fd-e49aa44007f1 type ext4 (rw,nosuid,nodev,uhelper=devkit)
/dev/sdd1 on /media/FREECOM_HDD type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=512)
/dev/sde1 on /media/HDDREG type vfat (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sdd2/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd2,2)
search --no-floppy --fs-uuid --set 22f27d0f-1692-42d2-88fd-e49aa44007f1
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd2,2)
	search --no-floppy --fs-uuid --set 22f27d0f-1692-42d2-88fd-e49aa44007f1
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=22f27d0f-1692-42d2-88fd-e49aa44007f1 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd2,2)
	search --no-floppy --fs-uuid --set 22f27d0f-1692-42d2-88fd-e49aa44007f1
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=22f27d0f-1692-42d2-88fd-e49aa44007f1 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 12d746180e12d220
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
	insmod ntfs
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 2c88743c8874071c
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdd2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc2 during installation
UUID=22f27d0f-1692-42d2-88fd-e49aa44007f1 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdc5 during installation
UUID=a3ba66b2-6998-4c7a-83d8-1c7b3dc7bd42 /home           ext4    defaults        0       2
# swap was on /dev/sdc3 during installation
UUID=53ea486c-49b9-40c9-993e-257dbaa71df5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdd2: Location of files loaded by Grub: ===================


 266.3GB: boot/grub/grub.cfg
 266.3GB: boot/initrd.img-2.6.31-14-generic
 266.3GB: boot/vmlinuz-2.6.31-14-generic
 266.3GB: initrd.img
 266.3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sde1

00000000  eb 3c 90 4d 53 57 49 4e  34 2e 31 00 02 40 01 00  |.<.MSWIN4.1..@..|
00000010  02 00 02 00 00 f8 f6 00  20 00 40 00 20 00 00 00  |........ .@. ...|
00000020  e0 a7 0e 00 80 00 29 2c  1a 7b 06 48 44 44 52 45  |......),.{.HDDRE|
00000030  47 20 20 20 20 20 46 41  54 31 36 20 20 20 33 c9  |G     FAT16   3.|
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

### Post by Jarige on 2009-11-19
BTW, fixing the mbr using Lilo made Vista boot again.
Thank you for that again, caljohnsmith :D

---

### Post by Jarige on 2009-11-19
Ok, I already fixed this problem myself by Googling around a bit.
I found my answer on some Dutch site.
I'll post here what I did to get it working:

I booted the LiveCD.
First I executed this command to list the devices and their partitions:
```
sudo fdisk -l
```
Find out where Ubuntu is installed, and note that location.
Should be something like /dev/sdb1
Then mount that location:
```
sudo mount /dev/sdb1 /mnt
```
Where /dev/sdb1 is the partition you installed Ubuntu to.

Then I executed this command:

```
grub-install --root-directory=/mnt /dev/sdb

```
Where /dev/sdb is the device where Ubuntu is (the external harddrive in my case).
Now everything works again :D

Thank you all :D

---

### Post by presence1960 on 2009-11-19
> **Jarige said:**
> Ok, I already fixed this problem myself by Googling around a bit.
I found my answer on some Dutch site.
I'll post here what I did to get it working:

I booted the LiveCD.
First I executed this command to list the devices and their partitions:
```
sudo fdisk -l
```
Find out where Ubuntu is installed, and note that location.
Should be something like /dev/sdb1
Then mount that location:
```
sudo mount /dev/sdb1 /mnt
```
Where /dev/sdb1 is the partition you installed Ubuntu to.

Then I executed this command:

```
grub-install --root-directory=/mnt /dev/sdb

```
Where /dev/sdb is the device where Ubuntu is (the external harddrive in my case).
Now everything works again :D

Thank you all :D

Glad you got it working, I was tied up prior to this. I would have suggested installing GRUB to MBR of the external device also. The problem with the way you had it before was GRUB was on MBR of an internal disk that boots first, and it points to /boot/grub/grub.cfg in your Ubuntu install- if that external is not plugged in that is why you get the error. 

The only thing I would have done differently is instead of lilo I would have restore windows to MBR of sda. But either way will work.

---

