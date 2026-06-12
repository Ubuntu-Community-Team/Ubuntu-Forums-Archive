---
title: "Menu.lst and boot menu does not match"
date: 2009-10-20
forum: Installation &amp; Upgrades
---

### Post by tkrisz on 2009-10-20
9.10 Beta, amd64
Dual boot with XP, separate /home partition

I have the following problem, probably a user mistake from a previously wrongly installed grub. Please help me to make order in chaos.

If i turn on the PC, i can't choose kernel 2.6.31-14.
I regulary get notification on a serious kernel problem, too.


```

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
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=c7f79323-bc77-4754-8a42-9c2b0823c95d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=c7f79323-bc77-4754-8a42-9c2b0823c95d

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

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		c7f79323-bc77-4754-8a42-9c2b0823c95d
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=c7f79323-bc77-4754-8a42-9c2b0823c95d ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		c7f79323-bc77-4754-8a42-9c2b0823c95d
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=c7f79323-bc77-4754-8a42-9c2b0823c95d ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.31-12-generic
uuid		c7f79323-bc77-4754-8a42-9c2b0823c95d
kernel		/boot/vmlinuz-2.6.31-12-generic root=UUID=c7f79323-bc77-4754-8a42-9c2b0823c95d ro quiet splash 
initrd		/boot/initrd.img-2.6.31-12-generic

title		Ubuntu 9.10, kernel 2.6.31-12-generic (recovery mode)
uuid		c7f79323-bc77-4754-8a42-9c2b0823c95d
kernel		/boot/vmlinuz-2.6.31-12-generic root=UUID=c7f79323-bc77-4754-8a42-9c2b0823c95d ro  single
initrd		/boot/initrd.img-2.6.31-12-generic

title		Ubuntu 9.10, kernel 2.6.31-11-generic
uuid		c7f79323-bc77-4754-8a42-9c2b0823c95d
kernel		/boot/vmlinuz-2.6.31-11-generic root=UUID=c7f79323-bc77-4754-8a42-9c2b0823c95d ro quiet splash 
initrd		/boot/initrd.img-2.6.31-11-generic

title		Ubuntu 9.10, kernel 2.6.31-11-generic (recovery mode)
uuid		c7f79323-bc77-4754-8a42-9c2b0823c95d
kernel		/boot/vmlinuz-2.6.31-11-generic root=UUID=c7f79323-bc77-4754-8a42-9c2b0823c95d ro  single
initrd		/boot/initrd.img-2.6.31-11-generic

title		Chainload into GRUB 2
root		c7f79323-bc77-4754-8a42-9c2b0823c95d
kernel		/boot/grub/core.img

title		Ubuntu 9.10, memtest86+
uuid		c7f79323-bc77-4754-8a42-9c2b0823c95d
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST


```

---

### Post by presence1960 on 2009-10-20
Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by tkrisz on 2009-10-20
```

============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on boot drive #2 in 
    partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

/dev/sda lemez: 250.1 GB, 250059350016 bájt
255 fej, 63 szektor, 30401 cilinder, összesen 488397168 szektor
Egység: szektorok 1 * 512 = 512 bájt
Lemezazonosító: 0x000cf2bc

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63     3,903,794     3,903,732   5 Extended
/dev/sda5                 126     3,903,794     3,903,669  82 Linux swap / Solaris
/dev/sda2    *      3,903,795    33,206,354    29,302,560  83 Linux
/dev/sda3          33,206,355   423,826,829   390,620,475  83 Linux


Drive: sdb ___________________ _____________________________________________________

/dev/sdb lemez: 82.0 GB, 81964302336 bájt
255 fej, 63 szektor, 9964 cilinder, összesen 160086528 szektor
Egység: szektorok 1 * 512 = 512 bájt
Lemezazonosító: 0xa152a152

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   160,055,594   160,055,532   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda2: UUID="c7f79323-bc77-4754-8a42-9c2b0823c95d" TYPE="ext4" 
/dev/sda3: UUID="f8040743-36bf-499a-b639-d0a2ebac4915" TYPE="ext4" 
/dev/sda5: UUID="ce123ca0-3250-4873-ad03-be494c90025e" TYPE="swap" 
/dev/sdb1: UUID="C8F0F50CF0F5018C" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda2 on / type ext4 (rw,errors=remount-ro)
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
/dev/sda3 on /home type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/krisz/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=krisz)


=========================== sda2/boot/grub/menu.lst: ===========================

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
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=c7f79323-bc77-4754-8a42-9c2b0823c95d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=c7f79323-bc77-4754-8a42-9c2b0823c95d

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

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		c7f79323-bc77-4754-8a42-9c2b0823c95d
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=c7f79323-bc77-4754-8a42-9c2b0823c95d ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		c7f79323-bc77-4754-8a42-9c2b0823c95d
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=c7f79323-bc77-4754-8a42-9c2b0823c95d ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.31-12-generic
uuid		c7f79323-bc77-4754-8a42-9c2b0823c95d
kernel		/boot/vmlinuz-2.6.31-12-generic root=UUID=c7f79323-bc77-4754-8a42-9c2b0823c95d ro quiet splash 
initrd		/boot/initrd.img-2.6.31-12-generic

title		Ubuntu 9.10, kernel 2.6.31-12-generic (recovery mode)
uuid		c7f79323-bc77-4754-8a42-9c2b0823c95d
kernel		/boot/vmlinuz-2.6.31-12-generic root=UUID=c7f79323-bc77-4754-8a42-9c2b0823c95d ro  single
initrd		/boot/initrd.img-2.6.31-12-generic

title		Ubuntu 9.10, kernel 2.6.31-11-generic
uuid		c7f79323-bc77-4754-8a42-9c2b0823c95d
kernel		/boot/vmlinuz-2.6.31-11-generic root=UUID=c7f79323-bc77-4754-8a42-9c2b0823c95d ro quiet splash 
initrd		/boot/initrd.img-2.6.31-11-generic

title		Ubuntu 9.10, kernel 2.6.31-11-generic (recovery mode)
uuid		c7f79323-bc77-4754-8a42-9c2b0823c95d
kernel		/boot/vmlinuz-2.6.31-11-generic root=UUID=c7f79323-bc77-4754-8a42-9c2b0823c95d ro  single
initrd		/boot/initrd.img-2.6.31-11-generic

title		Chainload into GRUB 2
root		c7f79323-bc77-4754-8a42-9c2b0823c95d
kernel		/boot/grub/core.img

title		Ubuntu 9.10, memtest86+
uuid		c7f79323-bc77-4754-8a42-9c2b0823c95d
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda2/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
load_env
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,2)
search --no-floppy --fs-uuid --set c7f79323-bc77-4754-8a42-9c2b0823c95d
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
menuentry "Ubuntu, Linux 2.6.31-13-generic" {
        recordfail=1
        save_env recordfail
	set quiet=1
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set c7f79323-bc77-4754-8a42-9c2b0823c95d
	linux	/boot/vmlinuz-2.6.31-13-generic root=UUID=c7f79323-bc77-4754-8a42-9c2b0823c95d ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-13-generic
}
menuentry "Ubuntu, Linux 2.6.31-13-generic (recovery mode)" {
        recordfail=1
        save_env recordfail
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set c7f79323-bc77-4754-8a42-9c2b0823c95d
	linux	/boot/vmlinuz-2.6.31-13-generic root=UUID=c7f79323-bc77-4754-8a42-9c2b0823c95d ro single 
	initrd	/boot/initrd.img-2.6.31-13-generic
}
menuentry "Ubuntu, Linux 2.6.31-12-generic" {
        recordfail=1
        save_env recordfail
	set quiet=1
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set c7f79323-bc77-4754-8a42-9c2b0823c95d
	linux	/boot/vmlinuz-2.6.31-12-generic root=UUID=c7f79323-bc77-4754-8a42-9c2b0823c95d ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-12-generic
}
menuentry "Ubuntu, Linux 2.6.31-12-generic (recovery mode)" {
        recordfail=1
        save_env recordfail
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set c7f79323-bc77-4754-8a42-9c2b0823c95d
	linux	/boot/vmlinuz-2.6.31-12-generic root=UUID=c7f79323-bc77-4754-8a42-9c2b0823c95d ro single 
	initrd	/boot/initrd.img-2.6.31-12-generic
}
menuentry "Ubuntu, Linux 2.6.31-11-generic" {
        recordfail=1
        save_env recordfail
	set quiet=1
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set c7f79323-bc77-4754-8a42-9c2b0823c95d
	linux	/boot/vmlinuz-2.6.31-11-generic root=UUID=c7f79323-bc77-4754-8a42-9c2b0823c95d ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-11-generic
}
menuentry "Ubuntu, Linux 2.6.31-11-generic (recovery mode)" {
        recordfail=1
        save_env recordfail
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set c7f79323-bc77-4754-8a42-9c2b0823c95d
	linux	/boot/vmlinuz-2.6.31-11-generic root=UUID=c7f79323-bc77-4754-8a42-9c2b0823c95d ro single 
	initrd	/boot/initrd.img-2.6.31-11-generic
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
menuentry "Microsoft Windows XP Professional - magyar (on /dev/sdb1)" {
	insmod ntfs
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set c8f0f50cf0f5018c
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=c7f79323-bc77-4754-8a42-9c2b0823c95d /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=f8040743-36bf-499a-b639-d0a2ebac4915 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=ce123ca0-3250-4873-ad03-be494c90025e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


   1.9GB: boot/grub/grub.cfg
   1.9GB: boot/grub/menu.lst
   1.9GB: boot/initrd.img-2.6.31-11-generic
   1.9GB: boot/initrd.img-2.6.31-12-generic
   1.9GB: boot/initrd.img-2.6.31-14-generic
   1.9GB: boot/vmlinuz-2.6.31-11-generic
   1.9GB: boot/vmlinuz-2.6.31-12-generic
   1.9GB: boot/vmlinuz-2.6.31-14-generic
   1.9GB: initrd.img
   1.9GB: initrd.img.old
   1.9GB: vmlinuz
   1.9GB: vmlinuz.old

================================ sdb1/boot.ini: ================================

[boot loader]

timeout=0

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional - magyar"  /sos

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sda

00000000  eb 63 90 10 8e d0 bc 00  b0 b8 00 00 8e d8 8e c0  |.c..............|
00000010  fb be 00 7c bf 00 06 b9  00 02 f3 a4 ea 21 06 00  |...|.........!..|
00000020  00 be be 07 38 04 75 0b  83 c6 10 81 fe fe 07 75  |....8.u........u|
00000030  f3 eb 16 b4 02 b0 01 bb  00 7c b2 80 8a 74 03 02  |.........|...t..|
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
000001b0  cd 10 ac 3c 00 75 f4 c3  bc f2 0c 00 00 00 00 01  |...<.u..........|
000001c0  01 00 05 fe 3f f2 3f 00  00 00 f4 90 3b 00 80 00  |....?.?.....;...|
000001d0  01 f3 83 fe ff ff 33 91  3b 00 20 1f bf 01 00 fe  |......3.;. .....|
000001e0  ff ff 83 fe ff ff 53 b0  fa 01 3b 65 48 17 00 00  |......S...;eH...|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by tkrisz on 2009-10-20
I have the boot menu like in grub.cfg.
Maybe should i run grub-mkconfig? Can this help?

---

### Post by presence1960 on 2009-10-20
You have 9.10 but you have GRUB 0.97 installed on MBR of sdb. GRUB 0.97 uses menu.lst but GRUB 2 uses these: /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

you have the GRUB 2 files but GRUB 2 is not installed. I have just started looking at GRUB 2 and do not yet know much about it. There is a forum for karmic 9.10 users. Check in here: [http://ubuntuforums.org/forumdisplay.php?f=359](http://ubuntuforums.org/forumdisplay.php?f=359)

maybe someone there can help you. Until I get up to speed on GRUB 2 I would feel remiss giving any advice. Sorry I could not help.

---

### Post by oldfred on 2009-10-20
I saw that there was an error that you had to fix if you were using grub legacy with grub2.

root        c7f79323-bc77-4754-8a42-9c2b0823c95d

should be changed to :
uuid        c7f79323-bc77-4754-8a42-9c2b0823c95d

But I am not sure if that relates to your problem or not. How can you boot without grub in sda? Or are you booting from sdb?

---

### Post by tkrisz on 2009-10-20
> **oldfred said:**
> I saw that there was an error that you had to fix if you were using grub legacy with grub2.

root        c7f79323-bc77-4754-8a42-9c2b0823c95d

should be changed to :
uuid        c7f79323-bc77-4754-8a42-9c2b0823c95d

But I am not sure if that relates to your problem or not. How can you boot without grub in sda? Or are you booting from sdb?

You mean in menu.lst in the "Chainload into GRUB 2" section?
Btw, i have no grub2 installed.

I changed every 13 to 14 manually in grub.cfg. Not a nice fix, but works.
I'm considering a new install as karmic comes out, so it's ok for this 1+ week.

---

