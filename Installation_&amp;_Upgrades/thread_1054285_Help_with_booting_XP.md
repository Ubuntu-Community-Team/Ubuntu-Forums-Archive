---
title: "Help with booting XP"
date: 2009-01-29
forum: Installation &amp; Upgrades
---

### Post by Ghostnik11 on 2009-01-29
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTLDR /NTDETECT.COM /ntdetect.com

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 100.0 GB, 100030242816 bytes
240 heads, 63 sectors/track, 12921 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcccdcccd

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   185,114,159   185,114,097   7 HPFS/NTFS
/dev/sda2         185,114,160   195,365,519    10,251,360  12 Compaq diagnostics


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0002d7f3

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   938,742,209   938,742,147   c W95 FAT32 (LBA)
/dev/sdb2         938,742,210 1,465,144,064   526,401,855   5 Extended
/dev/sdb5         938,742,273 1,459,135,754   520,393,482  83 Linux
/dev/sdb6       1,459,135,818 1,465,144,064     6,008,247  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="2C708A90708A6086" LABEL="IBM_PRELOAD" TYPE="ntfs" 
/dev/sda2: LABEL="IBM_SERVICE" UUID="1B33-0A00" TYPE="vfat" 
/dev/sdb1: LABEL="Elements" UUID="1559-0184" TYPE="vfat" 
/dev/sdb5: UUID="8a20c352-6752-40ff-b342-d92ca68ac835" TYPE="ext3" 
/dev/sdb6: UUID="1ae2e47e-0058-466f-80c4-99c980cec62a" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sdb5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/nikolai/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=nikolai)
/dev/sdb1 on /media/Elements type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sda1 on /media/IBM_PRELOAD type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

================================ sda2/boot.ini: ================================

[boot loader]

timeout=0

default=C:\

[operating systems]

multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

C:\ = "PC-DOS"


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
# kopt=root=UUID=8a20c352-6752-40ff-b342-d92ca68ac835 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=8a20c352-6752-40ff-b342-d92ca68ac835

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		8a20c352-6752-40ff-b342-d92ca68ac835
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8a20c352-6752-40ff-b342-d92ca68ac835 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		8a20c352-6752-40ff-b342-d92ca68ac835
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8a20c352-6752-40ff-b342-d92ca68ac835 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		8a20c352-6752-40ff-b342-d92ca68ac835
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
rootnoverify	(hd1,1)
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
#title		Windows NT/2000/XP
#root		(hd0,)
#savedefault
#makeactive
#chainloader	+1


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb5
UUID=8a20c352-6752-40ff-b342-d92ca68ac835 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb6
UUID=1ae2e47e-0058-466f-80c4-99c980cec62a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location  of files loaded by Grub: ===================


 553.3GB: boot/grub/menu.lst
 553.3GB: boot/grub/stage2
 553.4GB: boot/initrd.img-2.6.27-11-generic
 553.5GB: boot/initrd.img-2.6.27-7-generic
 553.5GB: boot/vmlinuz-2.6.27-11-generic
 553.5GB: boot/vmlinuz-2.6.27-7-generic
 553.4GB: initrd.img
 553.5GB: initrd.img.old
 553.5GB: vmlinuz
 553.5GB: vmlinuz.old

```

---

### Post by caljohnsmith on 2009-01-29
It looks like you have at least a couple of issues preventing you from booting Windows XP right now; for one thing, it looks like your XP install on sda1 is missing the boot.ini file. You have a boot.ini file in your sda2 partition, but it is not configured correctly to boot either sda1 or sda2; so I'm not sure where it came from. And the other issue is that you have Grub correctly installed to the MBR (Master Boot Record) of both your HDDs, so I don't know which drive you are booting on start up. But to see if we can get your XP booting again, how about first downloading the attached boot.ini.txt file to your Ubuntu desktop, and then do:
```
sudo mount /dev/sda1 /mnt
sudo mv ~/Desktop/boot.ini.txt /mnt/boot.ini
```
Next open your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And replace your two Windows entries at the end with:
```
title       Windows XP (hd0)
root       (hd0,0)
chainloader +1

title       Windows XP (hd1)
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
Then reboot, try both XP entries in your Grub menu, and let me know exactly what happens. We can work from there.

---

### Post by Ghostnik11 on 2009-01-29
do you want me to erase what I have for my two windows entries and put exactly what you typed in the same order

---

### Post by Ghostnik11 on 2009-01-29
it worked the second windows xp in the grub bootloader menu allowed me to boot perfectly into windows and now I have just gone back to ubuntu. is there anything else that i should be worried about?

---

### Post by caljohnsmith on 2009-01-29
> **Ghostnik11 said:**
> it worked the second windows xp in the grub bootloader menu allowed me to boot perfectly into windows and now I have just gone back to ubuntu. is there anything else that i should be worried about?
I can't think of anything else, so if it is all booting OK now, cheers and have fun with Windows and Ubuntu. :)

---

### Post by Ghostnik11 on 2009-01-29
there is still a problem when i plug out my external it does not boot into windows it just tells me that there is an error with grub meaning that unless i have my external pluged in it won't let me boot to windows

---

### Post by caljohnsmith on 2009-01-29
OK, try this from a terminal:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
Reboot, and if you don't have the Ubuntu drive connected, you should boot straight into Windows. If you connect your Ubuntu drive, you'll need to make sure you set your BIOS to boot the Ubuntu drive if you want to boot Ubuntu. Let me know how that goes.

---

### Post by Ghostnik11 on 2009-01-29
nope didn't work it just goes to a black screen and the symbol on my laptop that tell when it is reading information just stays on

---

### Post by caljohnsmith on 2009-01-29
OK, I believe I see the problem, there's one more detail to take care of:
```
sudo sfdisk -A1 /dev/sda
```
Reboot again, and let me know if that fixes the problem.

---

### Post by Ghostnik11 on 2009-01-29
Thank You very much it worked!!!! Really appreciate it.

---

