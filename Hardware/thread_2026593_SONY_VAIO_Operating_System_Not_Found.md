---
title: "SONY VAIO: Operating System Not Found"
date: 2012-07-15
forum: Hardware
---

### Post by wewantutopia on 2012-07-15
Hello,

I'm trying to help my father in law with a computer he just got: a Sony VAIO VGN-AR350E 

The previous owner cleared his personal info then formated the hard drive.  He also, of course, lost the recovery disk.

I just installed 12.04 and it went without a hitch.  When the computer boots now thought, it says "Operating System Not Found."

I tried searching and it seems VAIOs have this as a somewhat common problem, but I could not find any solutions.

Anyone have any ideas?  Thank you!

---

### Post by Kirk Schnable on 2012-07-15
You may find this tool useful in fixing common boot problems:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If the problem presists after running the tool, please supply us with its log. (It should give you a log at the end).

Good luck!

Kirk

---

### Post by wewantutopia on 2012-07-15
Ok, I ran boot repair with no results.  Here is the log I got after running the repair.  I then rebooted and still get operating system not found.  I rebooted into the live USB session and checked the info log and the recommendation at the bottom of the new log were the exact same as this; as if the repair didn't do anything.

Any ideas?

```
 [COLOR=#000]   



         Boot Info Script 0.61-git Boot-Repair log      [4 July 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 3.63 Debian-2008-07-15
    Boot sector info:  Syslinux looks at sector 3091220 of /dev/sdb1 for its 
                       second stage. The integrity check of Syslinux failed. 
                       According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 63.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   386,531,327   386,529,280  83 Linux
/dev/sda2         386,533,374   390,721,535     4,188,162   5 Extended
/dev/sda5         386,533,376   390,721,535     4,188,160  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 31.6 GB, 31616663552 bytes
255 heads, 63 sectors/track, 3843 cylinders, total 61751296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63    61,737,794    61,737,732   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       957e8e38-1a1e-4ad0-b114-dd04b99a5c92   ext3       
/dev/sda1        6c479adb-ac9e-4df9-9653-18505df4f0f5   ext4       
/dev/sda5        6716e239-de20-4228-94c6-551de0aa0706   swap       
/dev/sdb1        5A41-368E                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 6c479adb-ac9e-4df9-9653-18505df4f0f5
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root 6c479adb-ac9e-4df9-9653-18505df4f0f5
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=10
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
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 6c479adb-ac9e-4df9-9653-18505df4f0f5
    linux    /boot/vmlinuz-3.2.0-23-generic-pae root=UUID=6c479adb-ac9e-4df9-9653-18505df4f0f5 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-23-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 6c479adb-ac9e-4df9-9653-18505df4f0f5
    echo    'Loading Linux 3.2.0-23-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-23-generic-pae root=UUID=6c479adb-ac9e-4df9-9653-18505df4f0f5 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-23-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 6c479adb-ac9e-4df9-9653-18505df4f0f5
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 6c479adb-ac9e-4df9-9653-18505df4f0f5
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=6c479adb-ac9e-4df9-9653-18505df4f0f5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=6716e239-de20-4228-94c6-551de0aa0706 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 134.139686584 = 144.031391744  boot/grub/core.img                             1
 134.134773254 = 144.026116096  boot/grub/grub.cfg                             1
   8.386665344 = 9.005113344    boot/initrd.img-3.2.0-23-generic-pae           2
 134.134029388 = 144.025317376  boot/vmlinuz-3.2.0-23-generic-pae              1
   8.386665344 = 9.005113344    initrd.img                                     2
 134.134029388 = 144.025317376  vmlinuz                                        1

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  27 b1 99 a1 b9 61 25 33  e2 84 83 ce 54 ea 16 22  |'....a%3....T.."|
00000010  3c bd 83 7f 80 02 62 11  42 38 21 d7 9c d6 29 93  |<.....b.B8!...).|
00000020  61 ec 43 31 78 ad 41 23  b9 ed 83 d0 68 e6 4c ec  |a.C1x.A#....h.L.|
00000030  ab 93 10 6c 9b 52 86 8c  25 d3 f6 97 c6 f9 08 2b  |...l.R..%......+|
00000040  23 a3 2b a0 47 10 11 1e  15 42 d7 ff 6d 95 21 52  |#.+.G....B..m.!R|
00000050  31 25 ab 28 32 4b 27 e7  3d ae 8e d9 18 8d 01 e6  |1%.(2K'.=.......|
00000060  83 e8 ce d3 a2 08 e3 4a  19 39 0a d1 c7 54 98 e4  |.......J.9...T..|
00000070  18 6c 08 3d 6f ec 10 7f  89 ac 54 f8 7e 02 d6 86  |.l.=o.....T.~...|
00000080  fc c8 4e a4 9a a8 43 4f  1b c5 3a 9f af d5 e7 d4  |..N...CO..:.....|
00000090  02 56 66 f3 0b 54 c1 38  40 22 d4 38 70 40 2b 70  |.Vf..T.8@".8p@+p|
000000a0  27 c0 a8 69 2b b5 35 d9  fd c7 0c 75 3c 6e e5 2f  |'..i+.5....u<n./|
000000b0  f0 09 a5 cf 13 58 03 02  84 ea 9e 2c 86 22 cc ec  |.....X.....,."..|
000000c0  02 d9 c9 d1 48 62 0e d6  82 fe 14 4d ac 97 c2 17  |....Hb.....M....|
000000d0  86 60 a2 d9 e1 86 0e 33  97 92 e8 81 7c 80 aa df  |.`.....3....|...|
000000e0  ba 4b ce 50 a0 26 84 c0  4f 98 c7 1d 9a e6 4d af  |.K.P.&..O.....M.|
000000f0  ad 3d 59 57 a7 81 85 5b  32 67 a0 1e 9c 2c 38 2b  |.=YW...[2g...,8+|
00000100  23 a3 34 70 47 10 11 1f  f9 4c 86 7e 90 9c c3 13  |#.4pG....L.~....|
00000110  97 6e 51 3e 3e 1f 2e bb  2c ca 41 2e f0 6d ce 9d  |.nQ>>...,.A..m..|
00000120  81 8d 16 1a ff d0 d3 48  aa 00 77 28 18 49 ed 31  |.......H..w(.I.1|
00000130  ca c4 25 53 59 df 2d d1  81 86 01 20 ed e0 00 4e  |..%SY.-.... ...N|
00000140  a6 d0 f3 5a db 90 23 07  9e ae d8 5d d3 94 c3 d3  |...Z..#....]....|
00000150  a1 06 33 42 3a a1 11 32  91 99 22 34 6d c9 da f6  |..3B:..2.."4m...|
00000160  5e d1 0b 0d 66 5f 4f 1a  45 38 e6 4c 8d 80 c0 a9  |^...f_O.E8.L....|
00000170  2b c9 95 d4 ff 17 c9 e4  cd c2 62 49 f2 cf 69 79  |+.........bI..iy|
00000180  51 21 dd bb f8 33 b5 58  e4 40 62 6e e6 bb 9b 57  |Q!...3.X.@bn...W|
00000190  cd 2b 8d 82 15 25 34 65  92 e2 f1 1e f3 d7 a7 5f  |.+...%4e......._|
000001a0  2a 22 8f bd 36 0c 63 fc  96 d3 1a f8 6a 13 16 57  |*"..6.c.....j..W|
000001b0  3b b4 33 32 64 62 ef 45  2c d0 0b 60 8c 7d 00 fe  |;.32db.E,..`.}..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 e8 3f 00 00 00  |............?...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



ADDITIONAL INFORMATION :
=================== log of boot-repair 2012-07-15__16h13 ===================
boot-repair version : 3.18-0ppa41~precise
boot-sav version : 3.191-0ppa44~precise
glade2script version : 0.3.2.1-0ppa7~precise
boot-sav-nonfree version : 3.18-0ppa10~precise
boot-repair is executed in live-session (Ubuntu 12.04 LTS , precise , Ubuntu , i686)
CPU op-mode(s):        32-bit, 64-bit

=================== os-prober:
/dev/sda1:Ubuntu 12.04 LTS (12.04):Ubuntu:linux

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/loop1: UUID="957e8e38-1a1e-4ad0-b114-dd04b99a5c92" TYPE="ext3"
/dev/sda1: UUID="6c479adb-ac9e-4df9-9653-18505df4f0f5" TYPE="ext4"
/dev/sda5: UUID="6716e239-de20-4228-94c6-551de0aa0706" TYPE="swap"
/dev/sdb1: UUID="5A41-368E" TYPE="vfat"


1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.


=================== sda1/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"





=================== sda1/etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Apr 23 06:38 grub.d
total 56
-rwxr-xr-x 1 root root 6715 Apr 17 13:16 00_header
-rwxr-xr-x 1 root root 5522 Apr 17 12:53 05_debian_theme
-rwxr-xr-x 1 root root 7399 Apr 17 13:16 10_linux
-rwxr-xr-x 1 root root 6335 Apr 17 13:16 20_linux_xen
-rwxr-xr-x 1 root root 1588 Nov 27  2011 20_memtest86+
-rwxr-xr-x 1 root root 7603 Apr 17 13:16 30_os-prober
-rwxr-xr-x 1 root root  214 Apr 17 13:16 40_custom
-rwxr-xr-x 1 root root   95 Apr 17 13:16 41_custom
-rw-r--r-- 1 root root  483 Apr 17 13:16 README




=================== dmesg | grep EFI :
BIOS is probably not EFI-compatible, and probably not setup in EFI-mode for this live-session.
[    4.213320] EFI Variables Facility v0.08 2004-May-17



=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    grubenv-ok    grub2,    grub-pc,    update-grub,    32,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    no-grldr,    no-b-bcd,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    /mnt/boot-sav/sda1.

sda    : MSDos,    not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    2048 sectors * 512 bytes

=================== parted -l:

Model: ATA FUJITSU MHV2200B (scsi)
Disk /dev/sda: 200GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
1      1049kB  198GB  198GB   primary   ext4            boot
2      198GB   200GB  2144MB  extended
5      198GB   200GB  2144MB  logical   linux-swap(v1)


Model:  Patriot Memory (scsi)
Disk /dev/sdb: 31.6GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      32.3kB  31.6GB  31.6GB  primary  fat32        boot


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sdb1 on /cdrom type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /mnt/boot-sav/sda1 type ext4 (rw)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda5 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency disk dri dvd dvdrw ecryptfs fb0 fd full fuse fw0 hpet input kmsg log mapper mcelog mem net network_latency network_throughput null oldmem port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda5 sdb sdb1 sg0 sg1 sg2 shm snapshot snd sr0 stderr stdin stdout uinput urandom usbmon0 usbmon1 usbmon2 usbmon3 usbmon4 usbmon5 vga_arbiter zero
ls /dev/mapper:  control

=================== df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  4.0G  228M  3.6G   6% /
udev           devtmpfs   999M   12K  999M   1% /dev
tmpfs          tmpfs      403M  848K  402M   1% /run
/dev/sdb1      vfat        30G  4.8G   25G  17% /cdrom
/dev/loop0     squashfs   673M  673M     0 100% /rofs
tmpfs          tmpfs     1006M  624K 1006M   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs     1006M  176K 1006M   1% /run/shm
/dev/sda1      ext4       185G  4.8G  171G   3% /mnt/boot-sav/sda1

=================== fdisk -l:

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000158df

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   386531327   193264640   83  Linux
/dev/sda2       386533374   390721535     2094081    5  Extended
/dev/sda5       386533376   390721535     2094080   82  Linux swap / Solaris

Disk /dev/sdb: 31.6 GB, 31616663552 bytes
255 heads, 63 sectors/track, 3843 cylinders, total 61751296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008e9e7

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    61737794    30868866    b  W95 FAT32



=================== Recommended repair
recommendedrepair
This setting will reinstall the grub2 of sda1 into the MBR of sda.
Additional repair will be performed: unhide-bootmenu-10s



Reinstall the GRUB of sda1 into the MBR of sda
grub-install (GRUB) 1.99-21ubuntu3
grub-install --recheck /dev/sda: Installation finished. No error reported.
exit code of grub-install /dev/sda:0
chroot /mnt/boot-sav/sda1 update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-23-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-23-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
Unhide GRUB boot menu in sda1/boot/grub/grub.cfg

Boot successfully repaired.

You can now reboot your computer.



The boot files of [Ubuntu 12.04 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair].

Download as text


[/COLOR]
```[COLOR=#000] 
                 
         
     [/COLOR]

---

### Post by UltimateCat on 2012-07-15
> **wewantutopia said:**
> Hello,

I'm trying to help my father in law with a computer he just got: a Sony VAIO VGN-AR350E 

The previous owner cleared his personal info then formated the hard drive.  He also, of course, lost the recovery disk.

I just installed 12.04 and it went without a hitch.  When the computer boots now thought, it says "Operating System Not Found."

I tried searching and it seems VAIOs have this as a somewhat common problem, but I could not find any solutions.

Anyone have any ideas?  Thank you!

Found this link with Sony...trying to help-

[http://esupport.sony.com/US/perl/model-home.pl?mdl=VGNAR350E&LOC=3&session_id=7716510b04ccf900d7bcb07b4283df8c#/howtoTab](http://esupport.sony.com/US/perl/model-home.pl?mdl=VGNAR350E&LOC=3&session_id=7716510b04ccf900d7bcb07b4283df8c#/howtoTab)

This is information about the motherboard if you need it in the future
[http://www.bztechservices.com/sonylaptop.htm](http://www.bztechservices.com/sonylaptop.htm)

Sony's # 1-877-865-7669

---

### Post by Kirk Schnable on 2012-07-15
I wonder if this could be an UEFI thing.

Check out the settings in your BIOS, and see if there's anything mentioning UEFI (Unified Extensible Firmware Interface).

If there is, you might try toggling that to "Compatibility Mode" or similar.

Just a thought.

Kirk

---

### Post by wewantutopia on 2012-07-15
Thanks for the replies.  I'm trying a few things but still no luck as of yet.  I'll have to tackle it again tomorrow night.

This computer definitely has BIOS (not UEFI) and the options are VERY sparse.

---

### Post by YannBuntu on 2012-07-18
Hello

Boot-Repair indicated an important information in its final window:
> The boot files of [Ubuntu 12.04 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair].


That may be the solution.
Detailed procedure here: [https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition)
(alternately, you can format Ubuntu, re-partition everything including the /boot partition, then reinstall 12.04)

---

