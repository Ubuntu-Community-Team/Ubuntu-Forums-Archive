---
title: "Three disks, grub2, cannot boot old ubuntu drive"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by billrad1 on 2009-11-06
Hi all,

well 9.10 has me playing detective again...athlon 64

here is the deal- I have a new drive #1 with 9.10 and the bootloader grub2 - works fine.

I have a second drive #2 with windows vista, boots fine off the grub bootloader in 9.10 #1

I have a third, #3,  a 9.10 install (an upgrade install) with the previously used grub (old gub) bootloader on it.

from the new 9.10 grub2 bootloader #1, I cannot have it fire up the other ubuntu drive. It boots Vista fine.

when connected by itself, the old ubuntu grub boots itself fine.

#1 and #2 are sata, #3 is PATA (ide) jumpered as master

I have run update-grub on the new drive, and now I get a few errors. 

> Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
grub-probe: error: Cannot find a GRUB drive for /dev/sdb1.  Check your device.map.

grub-probe: error: Cannot find a GRUB drive for /dev/sdb1.  Check your device.map.

Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
Found Ubuntu 9.10 (9.10) on /dev/sdc1
grub-probe: error: Cannot find a GRUB drive for /dev/sdc1.  Check your device.map.

grub-probe: error: Cannot find a GRUB drive for /dev/sdc1.  Check your device.map.

grub-probe: error: Cannot find a GRUB drive for /dev/sdc1.  Check your device.map.

grub-probe: error: Cannot find a GRUB drive for /dev/sdc1.  Check your device.map.

grub-probe: error: Cannot find a GRUB drive for /dev/sdc1.  Check your device.map.

grub-probe: error: Cannot find a GRUB drive for /dev/sdc1.  Check your device.map.

grub-probe: error: Cannot find a GRUB drive for /dev/sdc1.  Check your device.map.

done
billrad@billrad-desktop-9:~$ 



any ideas?

thanks

billrad1

---

### Post by oldfred on 2009-11-06
Are you sure of drive order. Many motherboards seem to boot the pata before the sata.

To see exactly how your system is booting:
Boot Info Script 0.32 courtesy of forum member meierfra
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
Instructions and info:
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
cd to directory saved to:
chmod 755 boot_info_script032.sh
sudo ./boot_info_script032.sh
or as example if on desktop
sudo bash ~/Desktop/boot_info_script*.sh
This will create a RESULTS.txt file in the same directory. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by billrad1 on 2009-11-06
here is s, thanks a bunch!

> ============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No known boot loader is installed in the MBR of /dev/sdb
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x78a64c9a

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   976,771,071   976,769,024   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00023f30

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   937,167,839   937,167,777  83 Linux
/dev/sdb2         937,167,840   976,768,064    39,600,225   5 Extended
/dev/sdb5         937,167,903   976,768,064    39,600,162  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3b51c0ad

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   970,711,559   970,711,497  83 Linux
/dev/sdc2         970,711,560   976,768,064     6,056,505   5 Extended
/dev/sdc5         970,711,623   976,768,064     6,056,442  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="3AB6E0D8B6E095A3" TYPE="ntfs" 
/dev/sdb1: UUID="c9f6fddb-4855-4d41-a07d-54883f55e9ca" TYPE="ext4" 
/dev/sdb5: UUID="85e26260-86f3-4014-8bd6-db9bd997105f" TYPE="swap" 
/dev/sdc1: UUID="f87d3cae-c94a-41e5-8cba-fe0947cfeec5" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc5: TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sdb1 on / type ext4 (rw,errors=remount-ro)
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
gvfs-fuse-daemon on /home/billrad/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=billrad)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
	linux	/boot/vmlinuz-2.6.31-14-generic root=/dev/sdb1 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	linux	/boot/vmlinuz-2.6.31-14-generic root=/dev/sdb1 ro single 
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
	search --no-floppy --fs-uuid --set 3ab6e0d8b6e095a3
	chainloader +1
}
menuentry "Ubuntu 9.10, kernel 2.6.31-14-generic-pae (on /dev/sdc1)" {
	linux /boot/vmlinuz-2.6.31-14-generic-pae root=UUID=f87d3cae-c94a-41e5-8cba-fe0947cfeec5 ro quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic-pae
}
menuentry "Ubuntu 9.10, kernel 2.6.31-14-generic-pae (recovery mode) (on /dev/sdc1)" {
	linux /boot/vmlinuz-2.6.31-14-generic-pae root=UUID=f87d3cae-c94a-41e5-8cba-fe0947cfeec5 ro single
	initrd /boot/initrd.img-2.6.31-14-generic-pae
}
menuentry "Ubuntu 9.10, kernel 2.6.31-14-generic (on /dev/sdc1)" {
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=f87d3cae-c94a-41e5-8cba-fe0947cfeec5 ro quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode) (on /dev/sdc1)" {
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=f87d3cae-c94a-41e5-8cba-fe0947cfeec5 ro single
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.28-16-server (on /dev/sdc1)" {
	linux /boot/vmlinuz-2.6.28-16-server root=UUID=f87d3cae-c94a-41e5-8cba-fe0947cfeec5 ro quiet splash
	initrd /boot/initrd.img-2.6.28-16-server
}
menuentry "Ubuntu 9.10, kernel 2.6.28-16-server (recovery mode) (on /dev/sdc1)" {
	linux /boot/vmlinuz-2.6.28-16-server root=UUID=f87d3cae-c94a-41e5-8cba-fe0947cfeec5 ro single
	initrd /boot/initrd.img-2.6.28-16-server
}
menuentry "Ubuntu 9.10, memtest86+ (on /dev/sdc1)" {
	linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Grub 1 Bootloader" {

set root=(hd2,1)

chainloader +1

}
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=c9f6fddb-4855-4d41-a07d-54883f55e9ca /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=85e26260-86f3-4014-8bd6-db9bd997105f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: initrd.img
    .0GB: vmlinuz

=========================== sdc1/boot/grub/menu.lst: ===========================

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		30

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
# hiddenmenu

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=UUID=f87d3cae-c94a-41e5-8cba-fe0947cfeec5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title		Ubuntu 9.10, kernel 2.6.31-14-generic-pae
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.31-14-generic-pae root=UUID=f87d3cae-c94a-41e5-8cba-fe0947cfeec5 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic-pae
quiet

title		Ubuntu 9.10, kernel 2.6.31-14-generic-pae (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.31-14-generic-pae root=UUID=f87d3cae-c94a-41e5-8cba-fe0947cfeec5 ro  single
initrd		/boot/initrd.img-2.6.31-14-generic-pae

title		Ubuntu 9.10, kernel 2.6.31-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=f87d3cae-c94a-41e5-8cba-fe0947cfeec5 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=f87d3cae-c94a-41e5-8cba-fe0947cfeec5 ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.28-16-server
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-16-server root=UUID=f87d3cae-c94a-41e5-8cba-fe0947cfeec5 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-server
quiet

title		Ubuntu 9.10, kernel 2.6.28-16-server (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-16-server root=UUID=f87d3cae-c94a-41e5-8cba-fe0947cfeec5 ro  single
initrd		/boot/initrd.img-2.6.28-16-server

title		Ubuntu 9.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title              Windows Vista
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1 (hd1) (hd0)

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=f87d3cae-c94a-41e5-8cba-fe0947cfeec5 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=2bbdbf6d-6e0d-4ac5-8e5f-c21f0b158dcf none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  msdos    rw,user,noauto  0       0
# USB for vmware/vbox
none /proc/bus/usb usbfs devgid=128,devmode=664 0 0

=================== sdc1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/menu.lst
    .0GB: boot/grub/stage2
    .0GB: boot/initrd.img-2.6.17-10-generic
    .0GB: boot/initrd.img-2.6.17-11-generic
    .0GB: boot/initrd.img-2.6.17-11-generic.bak
    .0GB: boot/initrd.img-2.6.20-15-generic
    .0GB: boot/initrd.img-2.6.20-15-generic.bak
    .0GB: boot/initrd.img-2.6.20-16-generic
    .0GB: boot/initrd.img-2.6.20-16-generic.bak
    .0GB: boot/initrd.img-2.6.22-14-generic
    .0GB: boot/initrd.img-2.6.22-14-generic.bak
    .0GB: boot/initrd.img-2.6.24-21-generic
    .0GB: boot/initrd.img-2.6.24-21-generic.bak
    .0GB: boot/initrd.img-2.6.24-21-server
    .0GB: boot/initrd.img-2.6.24-21-server.bak
    .0GB: boot/initrd.img-2.6.27-11-generic
    .0GB: boot/initrd.img-2.6.27-7-generic
    .0GB: boot/initrd.img-2.6.28-16-server
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/initrd.img-2.6.31-14-generic-pae
    .0GB: boot/vmlinuz-2.6.17-10-generic
    .0GB: boot/vmlinuz-2.6.17-11-generic
    .0GB: boot/vmlinuz-2.6.20-15-generic
    .0GB: boot/vmlinuz-2.6.20-16-generic
    .0GB: boot/vmlinuz-2.6.22-14-generic
    .0GB: boot/vmlinuz-2.6.24-21-generic
    .0GB: boot/vmlinuz-2.6.24-21-server
    .0GB: boot/vmlinuz-2.6.27-11-generic
    .0GB: boot/vmlinuz-2.6.27-7-generic
    .0GB: boot/vmlinuz-2.6.28-16-server
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic-pae
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdb

00000000  eb 63 90 10 8e d0 bc 00  b0 b8 00 00 8e d8 8e c0  |.c..............|
00000010  fb be 00 7c bf 00 06 b9  00 02 f3 a4 ea 21 06 00  |...|.........!..|
00000020  00 be be 07 38 04 75 0b  83 c6 10 81 fe fe 07 75  |....8.u........u|
00000030  f3 eb 16 b4 02 b0 01 bb  00 7c b2 80 8a 74 01 8b  |.........|...t..|
00000040  4c 02 cd 13 ea 00 7c 00  00 eb fe 00 00 00 00 00  |L.....|.........|
00000050  00 00 00 00 00 00 00 00  00 00 00 80 01 00 00 00  |................|
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
000001b0  cd 10 ac 3c 00 75 f4 c3  30 3f 02 00 00 00 80 01  |...<.u..0?......|
000001c0  01 00 83 fe ff ff 3f 00  00 00 a1 0b dc 37 00 fe  |......?......7..|
000001d0  ff ff 05 fe ff ff e0 0b  dc 37 61 40 5c 02 00 00  |.........7a@\...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

    

---

### Post by oldfred on 2009-11-06
The script does not id grub2 correctly but it is in sdb, windows is in sda and oldgrub is in sdc. If you are booting into grub2 it is your current sdb that is first. I would check your BIOS to see what settings you have. The system should be booting from the first drive in BIOS and both old grub and new grub have not always agreed with drive order and it seems to be worse with mixed sata & pata systems. I had issues a couple of years ago but changing old grub to use UUID instead of root commands solved my problem.
Some users have had issues where grub uses BIOS where windows and ubuntu seem to map the drives themselves. I would double check BIOS then possibly change mapping in Ubuntu. (I am on my windows machine and will be for another week so I do not remember exactly how to adjust mapping).

---

### Post by billrad1 on 2009-11-06
I believe you are right. I'll need to do some more playing around with the settings. I have the boot oder set in the bios.


I also had the same problem you describe on previous upgrades, and had to edit things.

When I figure it out, I'll post a solution.

thanks

Bill

---

### Post by Joe Ker1086 on 2009-11-06
Why don't you check this out. [[COLOR="Blue"][SIZE="5"]GAG[/SIZE][/COLOR]]("http://gag.sourceforge.net/index.html")Tell me what you think.

---

### Post by billrad1 on 2009-11-06
I may try it

thanks

---

### Post by Joe Ker1086 on 2009-11-06
No problem, Let me know what you think.

---

