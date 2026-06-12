---
title: "Grub doesn't load after installing Windows 7 and then Ubuntu 9.04 or 9.10"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by timos_m on 2009-11-08
Hello! I hope someone can help me with this.

_*The problem:*_ I had Windows 7 installed and I tried to manually install Ubuntu 9.04 using the live CD. After the installation finished, I restarted the computer but it just boots into Windows as if I had never installed Linux.
Edit: The same happened with Ubuntu 9.10. Please read 5th post of the thread.

_*Details:*_ Windows 7 is installed on the first partition of the hard disk. I have another NTFS primary partition. From the rest of the space, I made an extended partition, which contains two logical ext4 partitions and one logical swap partition. I defined the first ext4 partition as "/" (root), and the second one as /home. I also left unpartitioned space of 8 mb between each partition for safety reasons (I read somewhere online that it's a good thing to do so).

When this happened, **I followed a guide to restore Grub, but nothing changed.** I decided to re-install Ubuntu (with the same setup) but nothing changed again.. What should I do? :-?

Any help will be appreciated. Thank you beforehand for your answers! :)


edit: Here is my menu.lst, without the commented lines it had on top:
> 
title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		e69d954f-e7a8-401f-8598-e1b810bb3a63
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=e69d954f-e7a8-401f-8598-e1b810bb3a63 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		e69d954f-e7a8-401f-8598-e1b810bb3a63
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=e69d954f-e7a8-401f-8598-e1b810bb3a63 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		e69d954f-e7a8-401f-8598-e1b810bb3a63
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
title		Windows Vista (loader)
rootnoverify	(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


---

### Post by valnuke on 2009-11-09
Hi, I don't want to hijack the post but just to say that I have posted the same problem, a few hours ago...

it's very similar to yours, but with ubuntu 9.10

Ubuntu installation (twice), after windows 7 pro on the same hard disk. (2 hd in RAID1, if it matters)

Partitions: win7 and another nfts as primary, and then empty space where I installed ubuntu. so total of 2 + the 100MB reserved to win7 system partition + ubuntu ext4 + ubuntu swap

grub doesn't show up, windows 7 boots as linux isn't there...
I tried to reinstall grub, no luck

---

### Post by true_friend on 2009-11-09
So found any solution?
I have same issue.. Installed XP on C:, then Winwos 7 on D: and now Ubuntu on E. But it didnt installed the Grub on MBR. Simple Windows 7 boot loader.

---

### Post by oldfred on 2009-11-10
Windows, Ubuntu & Grub do not always agree on which drive is first. BIOS only boots from the first drive, so if you are still booting windows it is the first drive. You may have installed grub to the second drive. Try switching drive order in BIOS.

---

### Post by timos_m on 2009-11-11
@ oldfred: As I have stated on my first post, I am using separate partitions of a single drive for Windows and Ubuntu, not separate drives.


I downloaded and installed **Ubuntu 9.10**, which by itself had no result (I still had the same problem). Then, I followed some instructions on restoring GRUB2 which finally solved my problem. However, I don't consider the issue as solved, as I still haven't figured out what I did wrong. I can't believe that everyone who is dual-booting Windows 7 and Ubuntu has to manually install GRUB in order to boot into Ubuntu. So, please, someone give me a hint for future reference.

Thanks!

---

### Post by DJCalarco on 2009-11-11
[http://ubuntuforums.org/showthread.php?t=1321149](http://ubuntuforums.org/showthread.php?t=1321149)

This might help you, the situation is sorta similar to yours.

---

### Post by Mark Phelps on 2009-11-11
> **timos_m said:**
> @ oldfred: As I have stated on my first post, I am using separate partitions of a single drive for Windows and Ubuntu, not separate drives.


I downloaded and installed **Ubuntu 9.10**, which by itself had no result (I still had the same problem). Then, I followed some instructions on restoring GRUB2 which finally solved my problem. However, I don't consider the issue as solved, as I still haven't figured out what I did wrong. I can't believe that everyone who is dual-booting Windows 7 and Ubuntu has to manually install GRUB in order to boot into Ubuntu. So, please, someone give me a hint for future reference.

Thanks!

Don't what you did wrong, but from what you said, and what was in your menu.lst file, the error is that the entries in the menu.lst file for MS Windows OS's presume two physical drives -- hd0 & hd1, but you said you had only one drive -- which would be hd0.

So, first off, the map commands are only needed when you (1) have more than one physical drive, and (2) you're NOT booting from the driver that contains MS Windows.

Second, when you install a second MS Windows OS, be it Vista or Seven, it writes its bootloader files to the first MS Windows-compatible partition it finds. So, if you have, say, XP & Vista, the XP loader files AND the Vista loader files are all in the XP partition.

The result is that you can only have ONE MS Windows stanza in your menu.lst (if you have only one physical drive), and that has to point to the partition containing the boot loader files.

Had you shown some patience and posted more details, we could have helped you figure this out without you having to install anything.

---

### Post by presence1960 on 2009-11-11
> **timos_m said:**
> Hello! I hope someone can help me with this.

_*The problem:*_ I had Windows 7 installed and I tried to manually install Ubuntu 9.04 using the live CD. After the installation finished, I restarted the computer but it just boots into Windows as if I had never installed Linux.
Edit: The same happened with Ubuntu 9.10. Please read 5th post of the thread.

_*Details:*_ Windows 7 is installed on the first partition of the hard disk. I have another NTFS primary partition. From the rest of the space, I made an extended partition, which contains two logical ext4 partitions and one logical swap partition. I defined the first ext4 partition as "/" (root), and the second one as /home. I also left unpartitioned space of 8 mb between each partition for safety reasons (I read somewhere online that it's a good thing to do so).

When this happened, **I followed a guide to restore Grub, but nothing changed.** I decided to re-install Ubuntu (with the same setup) but nothing changed again.. What should I do? :-?

Any help will be appreciated. Thank you beforehand for your answers! :)


edit: Here is my menu.lst, without the commented lines it had on top:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by timos_m on 2009-11-11
First of all, I'd like to thank you for your attention and your answer, Mark Phelps.
I'm sorry, but I'm not sure I understood what you said the problem was (I'm not a native english speaker). Let me try to say what I understood, in my own words, adding some extra details about the case, and please correct me where I'm wrong or add what you want to:

You saw in the menu.lst the entries about Windows XP and Windows 7, which refer to separate drives. Actually, I indeed have more than one drives; i have four. What I said is that Windows 7 and Ubuntu are installed in the same physical drive. The other drives do not contain any OS. After having resolved my problem (but not figured out its cause) -by installing Karmic Koala and re-installing GRUB2- I noticed that I had a strange listing in GRUB: one about Windows XP. And I say strange, because Windows XP is not installed on my system. What I suppose that must have happened is that it was some kind of remains of a really old installation, because I hadn't used this drive for an OS for a long time. Then, I went to this drive and deleted some small files that seemed to be either useless or causing that little problem (listing of Windows XP in GRUB), one of them being boot.ini or something like that, that I believe that was the one that caused the situation. I also unchecked the "Bootable" option of this drive in the Disk Utility that I found in the System-->Administration menu of Ubuntu 9.10. What I understood from your post is that the problem is the fact that I had Windows 7 and Ubuntu in the same drive, but also a little part of some older Windows XP remained in another drive.

Is that correct? If yes, please confirm that, in your opinion, now that I deleted Windows XP in the way described above, next time that I would probably install Ubuntu, everything will be ok.
Also, if this was the problem, I have another question: Before installing Windows 7, I used to have Windows XP on the same partition that I now keep Windows 7. I also had an older version of Ubuntu installed on a second partition of the same physical drive, in the same way that I do now. Why didn't I face the problem that I faced now?

About that:
[QUOTE="Mark Phelps"]Had you shown some patience and posted more details, we could have helped you figure this out without you having to install anything.[/QUOTE]
Had I known what you needed, I was willing to post any possible detail. Also (about what you said about my patience), if you were me, would you have stayed waiting for someone to answer your post, or would you try to apply any idea you probably had, in order to solve your problem? :)


@ presence1960: Thank you too for your attention.
This is my RESULTS.txt:
```
============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda
 => No known boot loader is installed in the MBR of /dev/sdb
 => No known boot loader is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

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
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

sdb7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x596d881b

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   781,417,664   781,417,602   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd8f5d8f5

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    81,915,434    81,915,372   7 HPFS/NTFS
/dev/sdb2          81,931,500   249,087,824   167,156,325   7 HPFS/NTFS
/dev/sdb3         249,103,890   312,576,704    63,472,815   5 Extended
/dev/sdb5         249,103,953   251,144,144     2,040,192  83 Linux
/dev/sdb6         251,160,273   271,643,084    20,482,812  83 Linux
/dev/sdb7         271,659,213   300,110,264    28,451,052  83 Linux
/dev/sdb8         300,126,393   312,576,704    12,450,312  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x20f448ca

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   976,768,064   976,768,002   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe8900690

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="9E84865D84863833" TYPE="ntfs" 
/dev/sdb1: UUID="41DA52C616A60540" TYPE="ntfs" 
/dev/sdb2: UUID="127713C560C5D6DB" TYPE="ntfs" 
/dev/sdb5: UUID="8f20f943-0215-47d5-9fb9-90f267026429" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb6: UUID="96e1b43a-521e-43ab-85a0-ccc00af511f5" TYPE="ext4" 
/dev/sdb7: UUID="d02cb03d-deb0-467f-bf79-3d09dd0d72ae" TYPE="ext4" 
/dev/sdb8: UUID="68a6e7a2-e93a-4088-b9ee-c89ae0f99eaf" TYPE="swap" 
/dev/sdc1: UUID="55D123D9E79ABF54" TYPE="ntfs" 
/dev/sdd1: UUID="7A28EC8528EC422D" LABEL="My Book" TYPE="ntfs" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr1 on /cdrom type iso9660 (rw)
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


============================= sdb5/grub/grub.cfg: =============================

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
set default="4"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,6)
search --no-floppy --fs-uuid --set 96e1b43a-521e-43ab-85a0-ccc00af511f5
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
  set timeout=2
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
	set root=(hd1,5)
	search --no-floppy --fs-uuid --set 8f20f943-0215-47d5-9fb9-90f267026429
	linux	/vmlinuz-2.6.31-14-generic root=UUID=96e1b43a-521e-43ab-85a0-ccc00af511f5 ro   quiet splash
	initrd	/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,5)
	search --no-floppy --fs-uuid --set 8f20f943-0215-47d5-9fb9-90f267026429
	linux	/vmlinuz-2.6.31-14-generic root=UUID=96e1b43a-521e-43ab-85a0-ccc00af511f5 ro single 
	initrd	/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
	insmod ntfs
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 41da52c616a60540
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=================== sdb5: Location of files loaded by Grub: ===================


 127.5GB: grub/grub.cfg
 127.5GB: initrd.img-2.6.31-14-generic
 127.5GB: vmlinuz-2.6.31-14-generic

=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb6 during installation
UUID=96e1b43a-521e-43ab-85a0-ccc00af511f5 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdb5 during installation
UUID=8f20f943-0215-47d5-9fb9-90f267026429 /boot           ext3    defaults        0       2
# /home was on /dev/sdb7 during installation
UUID=d02cb03d-deb0-467f-bf79-3d09dd0d72ae /home           ext4    defaults        0       2
# swap was on /dev/sdb8 during installation
UUID=68a6e7a2-e93a-4088-b9ee-c89ae0f99eaf none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sda

00000000  eb 63 90 d0 bc 00 7c fb  50 07 50 1f fc be 1b 7c  |.c....|.P.P....||
00000010  bf 1b 06 50 57 b9 e5 01  f3 a4 cb bd be 07 b1 04  |...PW...........|
00000020  38 6e 00 7c 09 75 13 83  c5 10 e2 f4 cd 18 8b f5  |8n.|.u..........|
00000030  83 c6 10 49 74 19 38 2c  74 f6 a0 b5 07 b4 03 02  |...It.8,t.......|
00000040  80 00 00 20 01 00 00 00  00 02 fa 90 90 f6 c2 80  |... ............|
00000050  75 02 b2 80 ea 59 7c 00  00 31 00 80 01 00 00 00  |u....Y|..1......|
00000060  00 00 00 00 ff fa eb 07  f6 c2 80 75 02 b2 80 ea  |...........u....|
00000070  74 7c 00 00 31 c0 8e d8  8e d0 bc 00 20 fb a0 64  |t|..1....... ..d|
00000080  7c 3c ff 74 02 88 c2 52  be 88 7d e8 24 01 be 05  ||<.t...R..}.$...|
00000090  7c f6 c2 80 74 48 b4 41  bb aa 55 cd 13 5a 52 72  ||...tH.A..U..ZRr|
000000a0  3d 81 fb 55 aa 75 37 83  e1 01 74 32 31 c0 89 44  |=..U.u7...t21..D|
000000b0  04 40 88 44 ff 89 44 02  c7 04 10 00 66 8b 1e 5c  |.@.D..D.....f..\|
000000c0  7c 66 89 5c 08 66 8b 1e  60 7c 66 89 5c 0c c7 44  ||f.\.f..`|f.\..D|
000000d0  06 00 70 b4 42 cd 13 72  05 bb 00 70 eb 73 b4 08  |..p.B..r...p.s..|
000000e0  cd 13 73 0a f6 c2 80 0f  84 d8 00 e9 82 00 66 0f  |..s...........f.|
000000f0  b6 c6 88 64 ff 40 66 89  44 04 0f b6 d1 c1 e2 02  |...d.@f.D.......|
00000100  88 e8 88 f4 40 89 44 08  0f b6 c2 c0 e8 02 66 89  |....@.D.......f.|
00000110  04 66 a1 60 7c 66 09 c0  75 4e 66 a1 5c 7c 66 31  |.f.`|f..uNf.\|f1|
00000120  d2 66 f7 34 88 d1 31 d2  66 f7 74 04 3b 44 08 7d  |.f.4..1.f.t.;D.}|
00000130  37 fe c1 88 c5 30 c0 c1  e8 02 08 c1 88 d0 5a 88  |7....0........Z.|
00000140  c6 bb 00 70 8e c3 31 db  b8 01 02 cd 13 72 29 8c  |...p..1......r).|
00000150  c3 60 1e b9 00 01 8e db  31 f6 bf 00 80 8e c6 fc  |.`......1.......|
00000160  f3 a5 1f 61 ff 26 5a 7c  be 8e 7d e8 44 00 eb 0e  |...a.&Z|..}.D...|
00000170  be 93 7d e8 3c 00 eb 06  be 9d 7d e8 34 00 be a2  |..}.<.....}.4...|
00000180  7d e8 2e 00 cd 18 eb fe  47 52 55 42 20 00 47 65  |}.......GRUB .Ge|
00000190  6f 6d 00 48 61 72 64 20  44 69 73 6b 00 52 65 61  |om.Hard Disk.Rea|
000001a0  64 00 20 45 72 72 6f 72  0d 0a 00 bb 01 00 b4 0e  |d. Error........|
000001b0  cd 10 ac 3c 00 75 f4 c3  1b 88 6d 59 00 00 00 01  |...<.u....mY....|
000001c0  01 00 07 fe ff ff 3f 00  00 00 82 7c 93 2e 00 00  |......?....|....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown MBR on /dev/sdb

00000000  eb 63 90 d0 bc 00 7c 8e  c0 8e d8 be 00 7c bf 00  |.c....|......|..|
00000010  06 b9 00 02 fc f3 a4 50  68 1c 06 cb fb b9 04 00  |.......Ph.......|
00000020  bd be 07 80 7e 00 00 7c  0b 0f 85 0e 01 83 c5 10  |....~..|........|
00000030  e2 f1 cd 18 88 56 00 55  c6 46 11 05 c6 46 10 00  |.....V.U.F...F..|
00000040  b4 41 bb aa 55 cd 13 5d  72 0f 81 fb 55 aa 75 09  |.A..U..]r...U.u.|
00000050  f7 c1 01 00 74 03 fe 46  10 66 00 80 01 00 00 00  |....t..F.f......|
00000060  00 00 00 00 ff fa eb 07  f6 c2 80 75 02 b2 80 ea  |...........u....|
00000070  74 7c 00 00 31 c0 8e d8  8e d0 bc 00 20 fb a0 64  |t|..1....... ..d|
00000080  7c 3c ff 74 02 88 c2 52  be 88 7d e8 24 01 be 05  ||<.t...R..}.$...|
00000090  7c f6 c2 80 74 48 b4 41  bb aa 55 cd 13 5a 52 72  ||...tH.A..U..ZRr|
000000a0  3d 81 fb 55 aa 75 37 83  e1 01 74 32 31 c0 89 44  |=..U.u7...t21..D|
000000b0  04 40 88 44 ff 89 44 02  c7 04 10 00 66 8b 1e 5c  |.@.D..D.....f..\|
000000c0  7c 66 89 5c 08 66 8b 1e  60 7c 66 89 5c 0c c7 44  ||f.\.f..`|f.\..D|
000000d0  06 00 70 b4 42 cd 13 72  05 bb 00 70 eb 73 b4 08  |..p.B..r...p.s..|
000000e0  cd 13 73 0a f6 c2 80 0f  84 d8 00 e9 82 00 66 0f  |..s...........f.|
000000f0  b6 c6 88 64 ff 40 66 89  44 04 0f b6 d1 c1 e2 02  |...d.@f.D.......|
00000100  88 e8 88 f4 40 89 44 08  0f b6 c2 c0 e8 02 66 89  |....@.D.......f.|
00000110  04 66 a1 60 7c 66 09 c0  75 4e 66 a1 5c 7c 66 31  |.f.`|f..uNf.\|f1|
00000120  d2 66 f7 34 88 d1 31 d2  66 f7 74 04 3b 44 08 7d  |.f.4..1.f.t.;D.}|
00000130  37 fe c1 88 c5 30 c0 c1  e8 02 08 c1 88 d0 5a 88  |7....0........Z.|
00000140  c6 bb 00 70 8e c3 31 db  b8 01 02 cd 13 72 29 8c  |...p..1......r).|
00000150  c3 60 1e b9 00 01 8e db  31 f6 bf 00 80 8e c6 fc  |.`......1.......|
00000160  f3 a5 1f 61 ff 26 5a 7c  be 8e 7d e8 44 00 eb 0e  |...a.&Z|..}.D...|
00000170  be 93 7d e8 3c 00 eb 06  be 9d 7d e8 34 00 be a2  |..}.<.....}.4...|
00000180  7d e8 2e 00 cd 18 eb fe  47 52 55 42 20 00 47 65  |}.......GRUB .Ge|
00000190  6f 6d 00 48 61 72 64 20  44 69 73 6b 00 52 65 61  |om.Hard Disk.Rea|
000001a0  64 00 20 45 72 72 6f 72  0d 0a 00 bb 01 00 b4 0e  |d. Error........|
000001b0  cd 10 ac 3c 00 75 f4 c3  f5 d8 f5 d8 00 00 80 01  |...<.u..........|
000001c0  01 00 07 fe ff ff 3f 00  00 00 ec ed e1 04 00 fe  |......?.........|
000001d0  ff ff 07 fe ff ff ec 2c  e2 04 65 9a f6 09 00 fe  |.......,..e.....|
000001e0  ff ff 05 fe ff ff 12 06  d9 0e af 84 c8 03 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown MBR on /dev/sdc

00000000  e8 12 01 b9 f0 01 be 10  7c bf 10 06 57 f3 a4 c3  |........|...W...|
00000010  8b 4e 14 83 f9 0e 75 08  8d 5e 07 43 02 07 e2 fb  |.N....u..^.C....|
00000020  8c 56 0c 8c 56 0e 75 69  8a 56 10 84 d2 79 62 e8  |.V..V.ui.V...yb.|
00000030  f6 00 bb aa 55 cd 13 72  6f 3b 5e 5c 75 6a d1 e9  |....U..ro;^\uj..|
00000040  73 66 b4 42 c6 46 02 01  eb 66 89 b6 f6 fe 8a 44  |sf.B.F...f.....D|
00000050  04 84 c0 74 0f 3c 05 74  0b 3c 0f 74 07 8a 14 80  |...t.<.t.<.t....|
00000060  e2 80 75 cb 83 c6 10 06  c4 5c 08 89 5e 08 8c 46  |..u......\..^..F|
00000070  0a 07 fe 8e f9 fe 75 d2  b0 31 c6 46 d5 50 88 46  |......u..1.F.P.F|
00000080  d2 be 68 07 ac 84 c0 74  08 b4 0e b3 07 cd 10 eb  |..h....t........|
00000090  f3 e8 81 00 88 46 11 be  ae 07 3c 05 75 c6 cd 16  |.....F....<.u...|
000000a0  33 d2 89 56 08 89 56 0a  e8 7d 00 72 1b b8 01 02  |3..V..V..}.r....|
000000b0  bf 05 00 8b dc 56 50 50  32 e4 cd 13 58 8b f5 cd  |.....VPP2...X...|
000000c0  13 58 5e 73 03 4f 75 eb  b0 32 72 b2 40 8a 66 11  |.X^s.Ou..2r.@.f.|
000000d0  9e 7b 04 c6 47 02 0e 72  35 75 0c 88 57 40 c4 4e  |.{..G..r5u..W@.N|
000000e0  08 89 4f 1c 8c 47 1e 79  06 8a 4e 12 88 4f 25 80  |..O..G.y..N..O%.|
000000f0  c7 02 81 7f fe 55 aa 75  85 81 7f fc cd 19 75 09  |.....U.u......u.|
00000100  c6 47 fc e9 c7 47 fd 92  88 e8 1c 00 ff e4 74 ce  |.G...G........t.|
00000110  88 57 24 eb c9 5d 33 c0  8e d8 8e c0 8e d0 bc 00  |.W$..]3.........|
00000120  7c 55 bd a2 07 fc fb c3  b4 08 52 06 cd 13 07 33  ||U........R....3|
00000130  db 8a de 8b 46 0a 33 d2  83 e1 3f f7 f1 91 97 8b  |....F.3...?.....|
00000140  46 08 f7 f7 42 87 ca 3b  da 72 17 43 f7 f3 8a f2  |F...B..;.r.C....|
00000150  86 c5 d1 e8 d1 e8 0a c8  d0 cc d0 cc 0a f4 84 e4  |................|
00000160  74 02 b4 41 5b 8a d3 c3  0d 0a 4d 42 52 20 45 72  |t..A[.....MBR Er|
00000170  72 6f 72 20 00 0d 0a 00  72 65 73 73 20 61 6e 79  |ror ....ress any|
00000180  20 6b 65 79 20 74 6f 20  62 6f 6f 74 20 66 72 6f  | key to boot fro|
00000190  6d 20 66 6c 6f 70 70 79  2e 2e 2e 00 00 00 00 00  |m floppy........|
000001a0  00 00 10 00 01 00 00 7c  00 00 00 00 00 00 00 00  |.......|........|
000001b0  00 00 00 00 00 00 00 00  ca 48 f4 20 00 00 00 01  |.........H. ....|
000001c0  01 00 07 fe ff ff 3f 00  00 00 02 4c 38 3a 00 00  |......?....L8:..|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

DJCalarco, the problem in the linked thread is a different one. Thanks however.


Thanks everyone for your time.

---

### Post by presence1960 on 2009-11-11
well according to the script it looks like it is ok now because grub.cfg is showing vista as a menu option.

Note on the boot info script at the very top GRUB 2 shows as No known bootloader because when the script was written it was written to detect GRUB Legacy, Lilo and Windows bootloaders. AS of yet the script has not been modified to detect GRUB 2.

But at the very bottom of the script it lists unknown bootloaders on sda, sdb & sdc. So it is safe to say you have GRUB 2 installed on all three of those disks.

In almost all circumstances where help is asked in relation to boot problems I insist on the boot info script being run, which as you can see can tell us a great deal about your setup. Plus in my experience people with problems do not intentionally mislead us, but a majority of times the boot info script reveals their set up is different than what they said it is. This is not to say that applies to you.

The bottom line is you got it working. Enjoy Ubuntu!

---

### Post by timos_m on 2009-11-11
> **presence1960 said:**
> well according to the script it looks like it is ok now because grub.cfg is showing vista as a menu option.
[...]
The bottom line is you got it working. Enjoy Ubuntu!
Thank you. However, I already knew that I got it working... What remains now, in order to consider the issue as solved, as I have already explained, is to answer the questions, "Why did this happen?" and "How can I prevent it from happening in the future?".

---

### Post by presence1960 on 2009-11-11
> **timos_m said:**
> Thank you. However, I already knew that I got it working... What remains now, in order to consider the issue as solved, as I have already explained, is to answer the questions, "Why did this happen?" and "How can I prevent it from happening in the future?".

Unfortunately without seeing a "before" and "after" boot info script output I have no evidence to say why any of this has happened. We have the "after" script results which shows your setup now, but nothing conclusive to let us know your setup prior. I don't like to "guess" without having any hard evidence to base my assumption(s) on. So I will have to pass on trying to answer how this happened in the first place.

---

### Post by timos_m on 2009-11-12
I can see that the tool in your signature is very useful and needs to be promoted.
However, descriptions are useful too. If you read the story described, you will probably be able to answer my questions. Or maybe not, but please, if you have the time, try, and don't quit because you don't have a computer-generated report. Thanks again.

---

### Post by presence1960 on 2009-11-12
> **timos_m said:**
> I can see that the tool in your signature is very useful and needs to be promoted.
However, descriptions are useful too. If you read the story described, you will probably be able to answer my questions. Or maybe not, but please, if you have the time, try, and don't quit because you don't have a computer-generated report. Thanks again.
I reread your original problem and the only reason I can think of that GRUB would not take over at boot is you installed GRUB to the Ubuntu partition during the install. That would leave windows on MBR which would be why you boot straight to windows. But again this is all speculation as we have no evidence as to where GRUB was actually installed. The boot info script would have let us know where GRUB was actually installed.

---

