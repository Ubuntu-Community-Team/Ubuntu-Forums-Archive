---
title: "Boot Problem! active HDD!"
date: 2012-05-26
forum: Hardware
---

### Post by DrAlbert on 2012-05-26
Hi
I have a Ideapad Y560 laptop. I had windows 7 installed on it. recently i wanted to use ubuntu in a dual boot method but after several time that i installed ubuntu (because it crashed) I thought maybe windows 7 had bad effect on ubuntu so i formatted the entire disk and during this process i change it to dynamic disk by mistake and then I change it to basic again. because of this mistake i wanted to see what happened and i reistalled windows 7 again and I realize that I can only boot to windows if i press F12 key during bios startup and select the HDD. I checked the bios to see if HDD is in first place in bios and it was there. I booted to windows and I saw that it is not an active disk. i repartitioned the disk again with acronis disk management and marked the disk as active and  installed only ubuntu 12.04 on it. but the problem still exist and it wont boot to disk automatically and I should press F12 and select HDD during startup. what should I do?

---

### Post by 2F4U on 2012-05-26
Did you install Ubuntu's boot loader in MBR?

---

### Post by DrAlbert on 2012-05-26
yes I installed Grub on MBR.
as I mentioned before I can use bios boot option to select HDD and ubuntu will start. but normally it will not start from HDD. it only show a blinking cursur. I dont know what happened but windows didn't start normally too. I should every time press F12 to select HDD from boot option.

---

### Post by wilee-nilee on 2012-05-26
> **DrAlbert said:**
> yes I installed Grub on MBR.
as I mentioned before I can use bios boot option to select HDD and ubuntu will start. but normally it will not start from HDD. it only show a blinking cursur. I dont know what happened but windows didn't start normally too. I should every time press F12 to select HDD from boot option.

I you made the HD dynamic the mbr is the least of your problem, wait for an informed post on the app to maybe fix this.

I forget the link to the tool/tools.

---

### Post by oldfred on 2012-05-26
I would like to see all the details of what your install looks like now, since you have reinstalled several times. If you cannot boot Ubuntu, you can use liveCD.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

---

### Post by DrAlbert on 2012-05-27
Thanks for reply. this is the result.

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /etc/fstab

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       194,559       192,512  83 Linux
/dev/sda2             196,606   226,758,655   226,562,050   5 Extended
/dev/sda5             196,608    15,818,751    15,622,144  82 Linux swap / Solaris
/dev/sda6          15,820,800    35,350,527    19,529,728  83 Linux
/dev/sda7          35,352,576   164,257,791   128,905,216  83 Linux
/dev/sda8         164,259,840   207,226,879    42,967,040  83 Linux
/dev/sda9         207,228,928   226,758,655    19,529,728  83 Linux
/dev/sda3         226,758,656   812,695,551   585,936,896  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        936c7ea3-ab54-45d6-8b8d-b8fa1c85461f   ext4       
/dev/sda3        f2329d47-b723-41f4-9c69-5c1d1f185b7b   ext4       
/dev/sda5        35bc31bd-2808-4d76-bf92-9c5d6258bbd9   swap       
/dev/sda6        9337eddb-2fe6-4ef4-ab79-19092c4efe4a   ext4       
/dev/sda7        d13f9e70-4ada-4e02-b5f9-34321734f1f7   ext4       
/dev/sda8        c2fa9b28-0aca-4d28-9210-8c872b3d2736   ext4       
/dev/sda9        6c48978f-6475-409f-81c5-87ac6a27d6cc   ext4       
/dev/sr0                                                iso9660    Ubuntu 12.04 LTS amd64

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /boot                    ext4       (rw)
/dev/sda3        /home                    ext4       (rw)
/dev/sda6        /                        ext4       (rw,errors=remount-ro)
/dev/sda7        /usr                     ext4       (rw)
/dev/sda8        /var                     ext4       (rw)
/dev/sda9        /tmp                     ext4       (rw)
/dev/sr0         /media/Ubuntu 12.04 LTS amd64 iso9660    (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500,uhelper=udisks)


============================= sda1/grub/grub.cfg: ==============================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set=root d13f9e70-4ada-4e02-b5f9-34321734f1f7
if loadfont /share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root 936c7ea3-ab54-45d6-8b8d-b8fa1c85461f
  set locale_dir=($root)/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
	set gfxpayload="$1"
	if [ "$1" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 936c7ea3-ab54-45d6-8b8d-b8fa1c85461f
	linux	/vmlinuz-3.2.0-24-generic root=UUID=9337eddb-2fe6-4ef4-ab79-19092c4efe4a ro   quiet splash $vt_handoff
	initrd	/initrd.img-3.2.0-24-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 936c7ea3-ab54-45d6-8b8d-b8fa1c85461f
	echo	'Loading Linux 3.2.0-24-generic ...'
	linux	/vmlinuz-3.2.0-24-generic root=UUID=9337eddb-2fe6-4ef4-ab79-19092c4efe4a ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-3.2.0-24-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-17-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 936c7ea3-ab54-45d6-8b8d-b8fa1c85461f
	linux	/vmlinuz-3.2.0-17-generic root=UUID=9337eddb-2fe6-4ef4-ab79-19092c4efe4a ro   quiet splash $vt_handoff
	initrd	/initrd.img-3.2.0-17-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 936c7ea3-ab54-45d6-8b8d-b8fa1c85461f
	echo	'Loading Linux 3.2.0-17-generic ...'
	linux	/vmlinuz-3.2.0-17-generic root=UUID=9337eddb-2fe6-4ef4-ab79-19092c4efe4a ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-3.2.0-17-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 936c7ea3-ab54-45d6-8b8d-b8fa1c85461f
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 936c7ea3-ab54-45d6-8b8d-b8fa1c85461f
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.081080437 = 0.087059456    grub/core.img                                  1
   0.012706757 = 0.013643776    grub/grub.cfg                                  1
   0.078871727 = 0.084687872    initrd.img-3.2.0-17-generic                    2
   0.092326164 = 0.099134464    initrd.img-3.2.0-24-generic                    4
   0.021218300 = 0.022782976    vmlinuz-3.2.0-17-generic                       1
   0.046618462 = 0.050056192    vmlinuz-3.2.0-24-generic                       1

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=9337eddb-2fe6-4ef4-ab79-19092c4efe4a /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=936c7ea3-ab54-45d6-8b8d-b8fa1c85461f /boot           ext4    defaults        0       2
# /home was on /dev/sda3 during installation
UUID=f2329d47-b723-41f4-9c69-5c1d1f185b7b /home           ext4    defaults        0       2
# /tmp was on /dev/sda9 during installation
UUID=6c48978f-6475-409f-81c5-87ac6a27d6cc /tmp            ext4    defaults        0       2
# /usr was on /dev/sda7 during installation
UUID=d13f9e70-4ada-4e02-b5f9-34321734f1f7 /usr            ext4    defaults        0       2
# /var was on /dev/sda8 during installation
UUID=c2fa9b28-0aca-4d28-9210-8c872b3d2736 /var            ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=35bc31bd-2808-4d76-bf92-9c5d6258bbd9 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   7.635294914 = 8.198335488    initrd.img                                     4
   7.621840477 = 8.183888896    initrd.img.old                                 2
   7.589587212 = 8.149257216    vmlinuz                                        1
   7.564187050 = 8.121984000    vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  54 b1 b9 a0 23 b4 ac 50  6e 90 92 b2 cb ba b0 70  |T...#..Pn......p|
00000010  ff 93 eb ba 3b 9f 95 83  ca a2 c5 72 e4 3f 22 22  |....;......r.?""|
00000020  ce e7 c6 cc 4f ac b2 73  57 5f 6d 86 da 06 11 5e  |....O..sW_m....^|
00000030  16 05 b3 18 62 7c 6b 9c  2c ce b0 a6 bb 94 77 e9  |....b|k.,.....w.|
00000040  0b f7 8d e1 4c 23 c3 c3  81 1f a3 7a 3f 33 38 49  |....L#.....z?38I|
00000050  cc b5 ee f3 7b f7 45 c7  fc 20 97 13 d2 52 1b cd  |....{.E.. ...R..|
00000060  ff c1 9b da 1f 51 c0 a6  30 08 db dd 14 29 8e bf  |.....Q..0....)..|
00000070  78 9a 0f 00 62 c8 7c 4a  98 71 83 7a eb 93 4d ee  |x...b.|J.q.z..M.|
00000080  32 7d b7 f5 e5 37 b4 dd  ae 57 f1 42 5b 65 6f 46  |2}...7...W.B[eoF|
00000090  3f 83 e7 0a e5 fd d9 5e  16 07 b0 28 e7 59 6b db  |?......^...(.Yk.|
000000a0  fb 4a 67 d6 80 c4 0b 72  24 d6 f5 1a 8a d2 6a 73  |.Jg....r$.....js|
000000b0  86 d8 c2 53 5b bb 4c ac  46 a6 c2 44 4e 3b 0d 65  |...S[.L.F..DN;.e|
000000c0  7e ea b7 b2 b6 8a 72 1f  94 99 1e 58 ce 26 53 95  |~.....r....X.&S.|
000000d0  da 7c 35 fb cd 5b b4 7c  a8 e0 e8 13 7b 2f 04 2d  |.|5..[.|....{/.-|
000000e0  14 53 b7 f8 7b d4 ed 1c  33 93 9b bf 46 23 f5 73  |.S..{...3...F#.s|
000000f0  2c 91 03 72 27 84 24 dd  49 ae a2 0d 78 a6 2c 08  |,..r'.$.I...x.,.|
00000100  ed fd cd 63 b4 d6 68 f2  e2 9a 06 2a c8 1f b7 eb  |...c..h....*....|
00000110  c1 85 03 ca dd 6c b6 ec  a6 fb 21 72 d3 47 00 a2  |.....l....!r.G..|
00000120  4f 0a 00 d4 43 2d 60 73  3a 50 74 5b 27 80 00 68  |O...C-`s:Pt['..h|
00000130  35 a6 a8 df 79 62 b8 62  4f ce c3 87 8b 0e 26 00  |5...yb.bO.....&.|
00000140  1e 01 ed 37 c2 8b 43 82  3f 02 50 11 b0 c0 54 c2  |...7..C.?.P...T.|
00000150  3a 7b 2e 3d c8 de 5d e8  fd ba 7b 60 f3 5b c8 08  |:{.=..]...{`.[..|
00000160  21 72 fc 53 99 6c a2 82  e3 43 42 71 e6 ca 5f a4  |!r.S.l...CBq.._.|
00000170  04 aa 63 9a fd 35 07 7c  35 73 a6 13 cf b3 47 5a  |..c..5.|5s....GZ|
00000180  7d 3f a0 70 cb ff 5a 63  c8 9f f7 56 bc 5f 71 4a  |}?.p..Zc...V._qJ|
00000190  7a e3 1a f3 5a ae 7e 01  93 04 46 16 77 46 84 03  |z...Z.~...F.wF..|
000001a0  b4 d0 b2 b7 95 aa 5f a8  76 1c 94 03 34 f2 6c 2e  |......_.v...4.l.|
000001b0  3f 6c fa bf a6 70 83 69  d9 65 44 98 dc 97 00 3c  |?l...p.i.eD....<|
000001c0  31 0c 82 ab d3 d8 02 00  00 00 00 60 ee 00 00 ab  |1..........`....|
000001d0  d4 d8 05 fe ff ff 02 60  ee 00 00 08 2a 01 00 00  |.......`....*...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt

```

---

### Post by oldfred on 2012-05-27
For a normal desktop I do not suggest the separate system partitions, but do not see anything wrong with your install.

Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

Perhaps a BIOS setting? Does this have UEFI as well as bIOS to boot?

These have all been reported as BIOS issues, see if any might apply.
> BIOS in not updated to latest revision
BIOS not set to boot CD or USB first
BIOS shows floppy or firewire and you do not have those
changing newer BIOS SATA 6 Gbit/s  from 6 Gbs to a SATA II - 3Gbs 
BIOS & disable "Boot Sector Virus Protection"
Other BIOS settings - Security or locked down Boot sector, Bitlocker
Old BIOS, new drive 137GB max boot size
Disable Quickboot in BIOS
turning off UDMA in the BIOS my problem has gone away.(old system & may make system slower)
BIOS setting, Keyboard response in grub really slow
Fast Boot setting prevents keyboard from working & other issues
Bios not loading no key works - disconnected power for about 10-15 minutes and the bios reset itself.
After update, It had reset to the BIOS defaults, setting the video to ONBOARD and switching off the dynamic video memory allocation (manually allocating 32Mb instead of leaving it as AUTO).
The mode for the disc was set to AUTO. Changed it to LBA. Then it worked.
Sometimes specific issues by motherboard like this:
[Natty] Marvell 88SE9120 IDE-Part not working 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/777325](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/777325)
External drive needed separate power supply
Asus m4a87td  core unlocker feature on usb3 was causing the problem
Asus - Security> I / O interface Security> "New interface card" or so. SET IT TO LOCKED!!! 
In the Asus BIOS I selected Advanced Mode>Advanced>SATA Configuration.
Changed IDE Mode to AHCI Mode
Then,when the SATA3G_1 selection appears in the drive list below,select the Enabled option.


---

### Post by DrAlbert on 2012-05-27
I checked the bios again and there is nothing to change. every thing is correct. I think it is something about HDD. because after I changed the HDD to Dynamic and change it again to normal(simple or basic-I dont remember) this happened. maybe it is not an active disk. maybe I should install windows again and check if it is active?

---

### Post by wilee-nilee on 2012-05-27
> **DrAlbert said:**
> I checked the bios again and there is nothing to change. every thing is correct. I think it is something about HDD. because after I changed the HDD to Dynamic and change it again to normal(simple or basic-I dont remember) this happened. maybe it is not an active disk. maybe I should install windows again and check if it is active?

Your HD is not dynamic, or wasn't from the boot script earlier.

---

