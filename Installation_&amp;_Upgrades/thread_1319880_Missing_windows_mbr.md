---
title: "Missing windows mbr"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by luckydog1942 on 2009-11-08
I downloaded Umbuntu to a dvd and installed 2.6.28-11 to my windows vista PC with dual boot.

Dual boot worked fine until I "updated" to 2.6.28-16

Now when I bring up the start screen I see both versions of Umbuntu and only Windows/vista/loader under other operating systems. When I intialize it I get "mbr missing'

I cannot initialize boot up from my windows rescue disk

Help restoring the dual boot  appreciated.:KS

---

### Post by presence1960 on 2009-11-08
Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by luckydog1942 on 2009-11-09
Howdy and thanks so much for your help!


Thanks you so much for the help!!!!!


I successfully ran the partition analysis program and the results are in a txt file on my desktop.

 Here are the results:


============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa8000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       208,844       208,782  de Dell Utility
/dev/sda2             208,896    31,666,175    31,457,280   7 HPFS/NTFS
/dev/sda3    *     31,666,176   454,889,463   423,223,288   7 HPFS/NTFS
/dev/sda4         454,896,540   625,137,344   170,240,805   5 Extended
/dev/sda5         454,896,603   618,116,939   163,220,337  83 Linux
/dev/sda6         618,117,003   625,137,344     7,020,342  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D9-0419" TYPE="vfat" 
/dev/sda2: UUID="E2F4A417F4A3EBCB" LABEL="RECOVERY" TYPE="ntfs" 
/dev/sda3: UUID="A29EA69F9EA66C0B" LABEL="OS" TYPE="ntfs" 
/dev/sda5: UUID="aca51046-56d8-4057-890f-9e522e72a4f2" TYPE="ext2" 
/dev/sda6: UUID="2edc1866-733f-4441-9e79-2af552b002ec" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext2 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-16-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/shep/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=shep)


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
# kopt=root=UUID=aca51046-56d8-4057-890f-9e522e72a4f2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=aca51046-56d8-4057-890f-9e522e72a4f2

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

title        Ubuntu 9.04, kernel 2.6.28-16-generic
uuid        aca51046-56d8-4057-890f-9e522e72a4f2
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=aca51046-56d8-4057-890f-9e522e72a4f2 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid        aca51046-56d8-4057-890f-9e522e72a4f2
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=aca51046-56d8-4057-890f-9e522e72a4f2 ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        aca51046-56d8-4057-890f-9e522e72a4f2
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=aca51046-56d8-4057-890f-9e522e72a4f2 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        aca51046-56d8-4057-890f-9e522e72a4f2
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=aca51046-56d8-4057-890f-9e522e72a4f2 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        aca51046-56d8-4057-890f-9e522e72a4f2
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title        Windows Vista (loader)
rootnoverify    (hd0,2)
savedefault
makeactive
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
UUID=aca51046-56d8-4057-890f-9e522e72a4f2 /               ext2    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=2edc1866-733f-4441-9e79-2af552b002ec none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 308.5GB: boot/grub/menu.lst
 308.4GB: boot/grub/stage2
 308.5GB: boot/initrd.img-2.6.28-11-generic
 308.5GB: boot/initrd.img-2.6.28-16-generic
 308.4GB: boot/vmlinuz-2.6.28-11-generic
 308.5GB: boot/vmlinuz-2.6.28-16-generic
 308.5GB: initrd.img
 308.5GB: initrd.img.old
 308.5GB: vmlinuz
 308.4GB: vmlinuz.old

---

### Post by presence1960 on 2009-11-09
Go [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") and download the Vista recovery console iso and burn it as an image to CD. Now this what you need to do: you are going to restore Vista to MBR and fix Vista's boot process and then restore GRUB to MBR so you can boot both OSs.

1. Boot off the Vista recovery console CD you made. Follow the directions for Vista [here]("http://ubuntuforums.org/showthread.php?t=1014708"). When done reboot and you should boot right to Vista. 

2. next boot off the Ubuntu Live CD/USB, Follow this:

1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,4)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,4)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

Reboot & check both Ubuntu & Vista is able to boot.

---

### Post by NOTmick on 2009-11-10
Hi there,

I've also been struggling with this issue since repartitioning VISTA to make room for Ubuntu 9.10.
When I boot, GRUB starts and the menu shows up fine.  when I choose Ubuntu, all is well.  When I choose VISTA, the screen blanks for a few seconds, then back to GRUB menu as if there for the first time.

I ran the boot info script and am pasting the results.txt file here.

============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTLDR /NTDETECT.COM /ntdetect.com

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1d6e91c5

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *      9,285,570   282,727,934   273,442,365   7 HPFS/NTFS
/dev/sda2                  63     9,285,569     9,285,507   b W95 FAT32
/dev/sda3         282,727,935   285,250,139     2,522,205  82 Linux swap / Solaris
/dev/sda4         285,250,140   390,716,864   105,466,725  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="7E90B26F90B22E11" TYPE="ntfs" 
/dev/sda2: LABEL="RECOVERY" UUID="6591-4D17" TYPE="vfat" 
/dev/sda3: UUID="662a9b67-1a77-4020-8add-02a8aee08b8e" TYPE="swap" 
/dev/sda4: UUID="b3a0aac9-0053-476b-a08f-3378b6e33d95" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda4 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/dad/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dad)


=========================== sda4/boot/grub/grub.cfg: ===========================

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
set root=(hd0,4)
search --no-floppy --fs-uuid --set b3a0aac9-0053-476b-a08f-3378b6e33d95
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1024x768
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
    set root=(hd0,4)
    search --no-floppy --fs-uuid --set b3a0aac9-0053-476b-a08f-3378b6e33d95
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=b3a0aac9-0053-476b-a08f-3378b6e33d95 ro  vga=773  quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,4)
    search --no-floppy --fs-uuid --set b3a0aac9-0053-476b-a08f-3378b6e33d95
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=b3a0aac9-0053-476b-a08f-3378b6e33d95 ro single  vga=773
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 7e90b26f90b22e11
    chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sda2)" {
    insmod fat
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 6591-4d17
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda4 during installation
UUID=b3a0aac9-0053-476b-a08f-3378b6e33d95 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=662a9b67-1a77-4020-8add-02a8aee08b8e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda4: Location of files loaded by Grub: ===================


 146.0GB: boot/grub/grub.cfg
 146.0GB: boot/initrd.img-2.6.31-14-generic
 146.0GB: boot/vmlinuz-2.6.31-14-generic
 146.0GB: initrd.img
 146.0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sda

00000000  eb 63 90 d0 bc 00 7c 8e  c0 8e d8 be 00 7c bf 00  |.c....|......|..|
00000010  06 b9 00 02 fc f3 a4 50  68 1c 06 cb fb b9 04 00  |.......Ph.......|
00000020  bd be 07 80 7e 00 00 7c  0b 0f 85 10 01 83 c5 10  |....~..|........|
00000030  e2 f1 cd 18 88 56 00 55  c6 46 11 05 c6 46 03 02  |.....V.U.F...F..|
00000040  ff 00 00 20 01 00 00 00  00 02 fa 90 90 f6 c2 80  |... ............|
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
000001b0  cd 10 ac 3c 00 75 f4 c3  c5 91 6e 1d 00 00 80 00  |...<.u....n.....|
000001c0  81 42 07 fe ff ff c2 af  8d 00 3d 66 4c 10 00 01  |.B........=fL...|
000001d0  01 00 0b fe bf 41 3f 00  00 00 83 af 8d 00 00 fe  |.....A?.........|
000001e0  ff ff 82 fe ff ff ff 15  da 10 5d 7c 26 00 00 fe  |..........]|&...|
000001f0  ff ff 83 fe ff ff 5c 92  00 11 65 4b 49 06 55 aa  |......\...eKI.U.|
00000200

Unknown BootLoader  on sda1

00000000  eb 63 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.c.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 c2 af 8d 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  30 66 4c 10 00 00 00 00  |........0fL.....|
00000030  00 00 0c 00 00 00 00 00  df c2 6b 01 00 00 00 00  |..........k.....|
00000040  f6 00 00 00 01 00 00 00  11 2e b2 90 6f b2 90 7e  |............o..~|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 80 3c 58 6a 11  |.....3......<Xj.|
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
000001b0  cd 10 ac 3c 00 75 f4 c3  4d 47 52 20 69 73 20 63  |...<.u..MGR is c|
000001c0  6f 6d 70 72 65 73 73 65  64 00 0d 0a 50 72 65 73  |ompressed...Pres|
000001d0  73 20 43 74 72 6c 2b 41  6c 74 2b 44 65 6c 20 74  |s Ctrl+Alt+Del t|
000001e0  6f 20 72 65 73 74 61 72  74 0d 0a 00 00 00 00 00  |o restart.......|
000001f0  00 00 00 00 00 00 00 00  80 9d b2 ca 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 

Any help to get back to being able to boot VISTA would be appreciated.  Rest of family needs it.

---

### Post by presence1960 on 2009-11-10
```
> **NOTmick said:**
> Hi there,

I've also been struggling with this issue since repartitioning VISTA to make room for Ubuntu 9.10.
When I boot, GRUB starts and the menu shows up fine.  when I choose Ubuntu, all is well.  When I choose VISTA, the screen blanks for a few seconds, then back to GRUB menu as if there for the first time.

I ran the boot info script and am pasting the results.txt file here.

============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTLDR /NTDETECT.COM /ntdetect.com

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1d6e91c5

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *      9,285,570   282,727,934   273,442,365   7 HPFS/NTFS
/dev/sda2                  63     9,285,569     9,285,507   b W95 FAT32
/dev/sda3         282,727,935   285,250,139     2,522,205  82 Linux swap / Solaris
/dev/sda4         285,250,140   390,716,864   105,466,725  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="7E90B26F90B22E11" TYPE="ntfs" 
/dev/sda2: LABEL="RECOVERY" UUID="6591-4D17" TYPE="vfat" 
/dev/sda3: UUID="662a9b67-1a77-4020-8add-02a8aee08b8e" TYPE="swap" 
/dev/sda4: UUID="b3a0aac9-0053-476b-a08f-3378b6e33d95" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda4 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/dad/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dad)


=========================== sda4/boot/grub/grub.cfg: ===========================

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
set root=(hd0,4)
search --no-floppy --fs-uuid --set b3a0aac9-0053-476b-a08f-3378b6e33d95
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1024x768
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
    set root=(hd0,4)
    search --no-floppy --fs-uuid --set b3a0aac9-0053-476b-a08f-3378b6e33d95
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=b3a0aac9-0053-476b-a08f-3378b6e33d95 ro  vga=773  quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,4)
    search --no-floppy --fs-uuid --set b3a0aac9-0053-476b-a08f-3378b6e33d95
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=b3a0aac9-0053-476b-a08f-3378b6e33d95 ro single  vga=773
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 7e90b26f90b22e11
    chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sda2)" {
    insmod fat
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 6591-4d17
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda4 during installation
UUID=b3a0aac9-0053-476b-a08f-3378b6e33d95 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=662a9b67-1a77-4020-8add-02a8aee08b8e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda4: Location of files loaded by Grub: ===================


 146.0GB: boot/grub/grub.cfg
 146.0GB: boot/initrd.img-2.6.31-14-generic
 146.0GB: boot/vmlinuz-2.6.31-14-generic
 146.0GB: initrd.img
 146.0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sda

00000000  eb 63 90 d0 bc 00 7c 8e  c0 8e d8 be 00 7c bf 00  |.c....|......|..|
00000010  06 b9 00 02 fc f3 a4 50  68 1c 06 cb fb b9 04 00  |.......Ph.......|
00000020  bd be 07 80 7e 00 00 7c  0b 0f 85 10 01 83 c5 10  |....~..|........|
00000030  e2 f1 cd 18 88 56 00 55  c6 46 11 05 c6 46 03 02  |.....V.U.F...F..|
00000040  ff 00 00 20 01 00 00 00  00 02 fa 90 90 f6 c2 80  |... ............|
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
000001b0  cd 10 ac 3c 00 75 f4 c3  c5 91 6e 1d 00 00 80 00  |...<.u....n.....|
000001c0  81 42 07 fe ff ff c2 af  8d 00 3d 66 4c 10 00 01  |.B........=fL...|
000001d0  01 00 0b fe bf 41 3f 00  00 00 83 af 8d 00 00 fe  |.....A?.........|
000001e0  ff ff 82 fe ff ff ff 15  da 10 5d 7c 26 00 00 fe  |..........]|&...|
000001f0  ff ff 83 fe ff ff 5c 92  00 11 65 4b 49 06 55 aa  |......\...eKI.U.|
00000200

Unknown BootLoader  on sda1

00000000  eb 63 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.c.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 c2 af 8d 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  30 66 4c 10 00 00 00 00  |........0fL.....|
00000030  00 00 0c 00 00 00 00 00  df c2 6b 01 00 00 00 00  |..........k.....|
00000040  f6 00 00 00 01 00 00 00  11 2e b2 90 6f b2 90 7e  |............o..~|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 80 3c 58 6a 11  |.....3......<Xj.|
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
000001b0  cd 10 ac 3c 00 75 f4 c3  4d 47 52 20 69 73 20 63  |...<.u..MGR is c|
000001c0  6f 6d 70 72 65 73 73 65  64 00 0d 0a 50 72 65 73  |ompressed...Pres|
000001d0  73 20 43 74 72 6c 2b 41  6c 74 2b 44 65 6c 20 74  |s Ctrl+Alt+Del t|
000001e0  6f 20 72 65 73 74 61 72  74 0d 0a 00 00 00 00 00  |o restart.......|
000001f0  00 00 00 00 00 00 00 00  80 9d b2 ca 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 

Any help to get back to being able to boot VISTA would be appreciated.  Rest of family needs it.


```

If you look at the very bottom of ther script you have an "unknown bootloader on sda and sda1. GRUB 2 shows up as an unknown bootloader because the boot info script is yet unmodified to detect the presence of GRUB 2.

So there is your problem. You have GRUB 2 on Vista's partition (sda1). You need to run recovery console and restore Vista's bootloader. Then you need to restore GRUB. If you don't have a Vista installation DVD (not a recovery disk) you can download an iso from [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/"), burn it as an image to disk which will allow you access to Vista recovery console to repair Vista.

Boot your Vista installation DVD or the CD you burned and follow the instructions [here]("http://ubuntuforums.org/showthread.php?t=1014708") for Vista. When done reboot without disk and you should boot right to Vista.

Now you need to restore GRUB. Follow the directions [here]("https://help.ubuntu.com/community/Grub2") for restoring GRUB 2. Scroll way down near the bottom to the heading "reinstalling from Live CD"

---

### Post by luckydog1942 on 2009-11-11
Hi..I'm back

I created the windows recovery disk but now have a basic problem. I cannot boot from CD
I have tried start up menu , F12 on start up. (There is a + next to the hard disk choice). I select cd/dvd and it goes to the hard drive Ubuntu startup.

I have tried to reset the bios (F2) and that will not work either. It is still booting from the hard disk.

---

### Post by presence1960 on 2009-11-11
> **luckydog1942 said:**
> Hi..I'm back

I created the windows recovery disk but now have a basic problem. I cannot boot from CD
I have tried start up menu , F12 on start up. (There is a + next to the hard disk choice). I select cd/dvd and it goes to the hard drive Ubuntu startup.

I have tried to reset the bios (F2) and that will not work either. It is still booting from the hard disk.

To fix this and for many other reasons you have to figure out how to boot from CD. Consult your computer documentation or go to the manufacturer's web site for the info you need.

Check your connections to the optical drive and the mobo and optical drive to power supply.

---

### Post by NOTmick on 2009-11-11
[I]If you look at the very bottom of ther script you have an "unknown bootloader on sda and sda1. GRUB 2 shows up as an unknown bootloader because the boot info script is yet unmodified to detect the presence of GRUB 2.

So there is your problem. You have GRUB 2 on Vista's partition (sda1). You need to run recovery console and restore Vista's bootloader. Then you need to restore GRUB. If you don't have a Vista installation DVD (not a recovery disk) you can download an iso from [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/"), burn it as an image to disk which will allow you access to Vista recovery console to repair Vista.

Boot your Vista installation DVD or the CD you burned and follow the instructions [here]("http://ubuntuforums.org/showthread.php?t=1014708") for Vista. When done reboot without disk and you should boot right to Vista.

Now you need to restore GRUB. Follow the directions [here]("https://help.ubuntu.com/community/Grub2") for restoring GRUB 2. Scroll way down near the bottom to the heading "reinstalling from Live CD"[/quote][/I]   

**Excellent.  I'm back up and running fine.  Thanks!!**  :p

---

### Post by presence1960 on 2009-11-11
> **NOTmick said:**
> [I]If you look at the very bottom of ther script you have an "unknown bootloader on sda and sda1. GRUB 2 shows up as an unknown bootloader because the boot info script is yet unmodified to detect the presence of GRUB 2.

So there is your problem. You have GRUB 2 on Vista's partition (sda1). You need to run recovery console and restore Vista's bootloader. Then you need to restore GRUB. If you don't have a Vista installation DVD (not a recovery disk) you can download an iso from [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/"), burn it as an image to disk which will allow you access to Vista recovery console to repair Vista.

Boot your Vista installation DVD or the CD you burned and follow the instructions [here]("http://ubuntuforums.org/showthread.php?t=1014708") for Vista. When done reboot without disk and you should boot right to Vista.

Now you need to restore GRUB. Follow the directions [here]("https://help.ubuntu.com/community/Grub2") for restoring GRUB 2. Scroll way down near the bottom to the heading "reinstalling from Live CD"[/I]   

**Excellent.  I'm back up and running fine.  Thanks!!**  :p[/QUOTE]

Glad you got it working. Enjoy Ubuntu!

---

