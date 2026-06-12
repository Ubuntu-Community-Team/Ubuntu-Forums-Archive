---
title: "Tearing my hair out over 9.04+Vista dual-boot"
date: 2009-09-07
forum: Installation &amp; Upgrades
---

### Post by roninbk on 2009-09-07
I have spent months trying to figure out a happy dual-boot scenario. I have an existing computer that bought a SATA drive that I want to install Ubuntu to and dual boot 

Here's my drive configuration as my BIOS sees it. Devices 2 and 3 are SATA, the rest is IDE

```
Device 0 Master - NTFS (Vista System)
Device 0 Slave - NTFS (Vista Docs)
Device 1 Master - DVD ROM
Device 1 Slave - DVD R/W
Device 2 Master - NTFS (Vista Music) 
Device 3 Master - EXT3 (Ubuntu Jaunty)
```

Now for some reason that I don't follow the logic of, Ubuntu ignores my BIOS's preferred ordering, and lists the SATA drives first. 

```
/sda - NTFS (Vista Music)
/sdb - EXT3 (Ubuntu Jaunty)
/sdc - NTFS (Vista System)
/sdd - NTFS (Vista Docs)
```

Whatever. Figuring that it might help to have the root partition on /sda, I swapped /sda and sdb so that it now looks like this

```
/sda - EXT3 (Ubuntu Jaunty)
/sdb - NTFS (Vista Music)
/sdc - NTFS (Vista System)
/sdd - NTFS (Vista Docs)
```

I then installed Ubuntu as normal and rebooted... straight into Vista. Which makes sense in hindsight, because Ubuntu didn't put its GRUB onto the drive the BIOS was looking for. So I ran through the install again, clicking Advanced at the final step, and selecting /sdc from the drop-down. (Actually, I ended up pointing it directly at /sdc1 at first, which rendered the computer unbootable into either OS, I used the Windows Vista CD to fix the MBR and go back to square 1, and then installed again to /sdc)

This boots me into Ubuntu correctly, however selecting Vista gives me a GRUB Error 13: Invalid or unsupported executable format. And this is where I am stuck.

(I suppose the preferred answer would be to just junk Vista, but I can't do that for reasons I don't want to get into at this point. )

---

### Post by presence1960 on 2009-09-08
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by roninbk on 2009-09-08
Text file dump in three... two...

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on boot drive #1 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdd and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0005630e

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   306,648,719   306,648,657  83 Linux
/dev/sda2         306,648,720   312,576,704     5,927,985   5 Extended
/dev/sda5         306,648,783   312,576,704     5,927,922  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1f151f15

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   586,099,394   586,099,332   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 41.1 GB, 41110142976 bytes
240 heads, 63 sectors/track, 5310 cylinders, total 80293248 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3a053a04

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          2,048    80,289,791    80,287,744   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd9e9d9e9

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *          2,048   160,833,535   160,831,488   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="521ecba9-678d-499b-b797-31509db2b5a2" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="54edeb34-d280-42ca-9d76-16fdf3cb9ed5" TYPE="swap" 
/dev/sdb1: UUID="9C2C8DAD2C8D834E" LABEL="Music" TYPE="ntfs" 
/dev/sdc1: UUID="FC7EC5B27EC565CC" LABEL="System" TYPE="ntfs" 
/dev/sdd1: UUID="CC8EF79E8EF77F70" LABEL="Documents" TYPE="ntfs" 

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


=========================== sda1/boot/grub/menu.lst: ===========================

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

## Splash image!
splashimage /boot/grub/images/usplash.xpm.gz

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
# kopt=root=UUID=521ecba9-678d-499b-b797-31509db2b5a2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=521ecba9-678d-499b-b797-31509db2b5a2

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

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		521ecba9-678d-499b-b797-31509db2b5a2
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=521ecba9-678d-499b-b797-31509db2b5a2 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		521ecba9-678d-499b-b797-31509db2b5a2
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=521ecba9-678d-499b-b797-31509db2b5a2 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		521ecba9-678d-499b-b797-31509db2b5a2
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=521ecba9-678d-499b-b797-31509db2b5a2 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		521ecba9-678d-499b-b797-31509db2b5a2
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=521ecba9-678d-499b-b797-31509db2b5a2 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		521ecba9-678d-499b-b797-31509db2b5a2
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Windows Vista (loader)
rootnoverify	(hd2,0)
savedefault
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# / was on /dev/sda1 during installation
UUID=521ecba9-678d-499b-b797-31509db2b5a2 / ext3 relatime,errors=remount-ro 0 1
# swap was on /dev/sda5 during installation
UUID=54edeb34-d280-42ca-9d76-16fdf3cb9ed5 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0



=================== sda1: Location of files loaded by Grub: ===================


  12.5GB: boot/grub/menu.lst
  12.5GB: boot/grub/stage2
  12.4GB: boot/initrd.img-2.6.28-11-generic
  12.5GB: boot/initrd.img-2.6.28-15-generic
  12.5GB: boot/vmlinuz-2.6.28-11-generic
  12.5GB: boot/vmlinuz-2.6.28-15-generic
  12.5GB: initrd.img
  12.4GB: initrd.img.old
  12.5GB: vmlinuz
  12.5GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdf sdg sdh sdi 
```

---

### Post by presence1960 on 2009-09-08
Reboot Go into BIOS and make sure that your 160 GB disk (Ubuntu) is set to boot first and your 41 GB disk (vista) is set to boot second in the hard disk boot order. The order of the other two drives does not matter as long as they are third and fourth boot in the order. Save changes to CMOS and continue booting. Boot into Ubuntu. When the desktop loads open a terminal and run this command ```
gksu gedit /boot/grub/menu.lst
``` That is a lowercase L in .lst

Then scroll down to your windows entry at the bottom and change it to this:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Windows Vista (loader)
rootnoverify	(hd1,0)
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


```
Click Save on the toolbar. Close the file and reboot. Try booting into Vista. Should be good to go.

FYI in the future when chainloading in menu.lst and using rootnoverify (hdx,y) or root (hdx,y) it is the order of hard disk booting in BIOS that determines the x in (hdx,y) and (hdx). Numbering starts at zero for devices (x) and partitions (y). We set your 41 GB (sdc) as second in boot order & windows is the first partition on that disk so we use (hd1,0).

---

### Post by roninbk on 2009-09-08
Yeah it works. 

I'm still a bit confused as to why the GRUB resulted in such a mess. Where in my initial install process did I go wrong, or was I going to have to manually edit GRUB anyways?

---

### Post by presence1960 on 2009-09-08
> **roninbk said:**
> Yeah it works. 

I'm still a bit confused as to why the GRUB resulted in such a mess. Where in my initial install process did I go wrong, or was I going to have to manually edit GRUB anyways?

There is sometimes a difference in the way Ubuntu (fdisk -l) reads the order of disks and what is actually in BIOS. Regardless of how fdisk reports the order of disks, it is the order in which those disks boot that we need to know when using root (hdx,y) & rootnoverify (hdx,y) to point to from GRUB. Why is that? Because BIOS basically controls all hardware and the order in which the disks boot is the actual order of the hard disks no matter what fdisk reports.

Sabayon Linux has a great tool in their installer which allows you to change the order of booting reported by Sabayon to match the order of booting in BIOS. Doing this eliminates a lot of confusion for people. maybe one day Ubuntu will have something like that in it's installation.

Another note along the lines of how the order of disks is reported comes from Gparted Live CD. My only IDE disk is reported as hda and before my  2 SATA disks which are reported as sda & sdb. But in my BIOS the IDE disk is last (third) to boot. So again BIOS controls how your machine uses it's hardware in spite of what Gparted Live CD reports. My IDE disk is third in boot order(hd2) while gparted reports it as first in the order (hd0)

---

