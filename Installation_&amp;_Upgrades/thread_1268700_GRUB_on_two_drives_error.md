---
title: "GRUB on two drives error"
date: 2009-09-17
forum: Installation &amp; Upgrades
---

### Post by shadetree1 on 2009-09-17
Hello people,

I am new and at a few weeks testing with ubuntu.:P  I was duel booting hardy and xp on my old intell test box, later losing the pci controller.  So I removed the hdd and added it to another puter thinking to run ubunty only on that drive.

The new pc is 64 XP.  I formated the entire old drive ntfs and then installed Ubuntu 64v.  When ever I booted, it has the grub error 17 and just stopped their.

Thinking the old drive is now starting 1st, I went to the bios and made the original disk load first.  Now grub on that drive works fine, but when my old disk starts that has ubuntu, I get the error 17 for a while then ubuntu loads ok.

Is there a way to wipe the grub from the old drive to avoid the booting delay issue?  That is why I formated the entire old drive first to avoid problems. 

shadetree

---

### Post by presence1960 on 2009-09-17
Let's get a better look at your setup. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by shadetree1 on 2009-09-17
OK and thanks for the quick reply.:P

I did one thing before reading your post.  I went in and checked the second HDD and the balance of the drive was unallocated after installing.  I cleared this section and made a partition and formated to NTFS and gained a few MB of space then rebooted.

It boots way better but I still see the error screen for a second.  I will post the results in a bit.

shadetree

---

### Post by shadetree1 on 2009-09-17
> **presence1960 said:**
> Let's get a better look at your setup. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

OK

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
240 heads, 63 sectors/track, 25841 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcab10bee

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   372,965,039   372,964,977   7 HPFS/NTFS
/dev/sda2         372,980,160   390,715,919    17,735,760   c W95 FAT32 (LBA)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders, total 120103200 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6eef6eef

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    39,070,079    39,070,017  83 Linux
/dev/sdb2          39,070,080    41,030,009     1,959,930   5 Extended
/dev/sdb5          39,070,143    41,030,009     1,959,867  82 Linux swap / Solaris
/dev/sdb3          41,030,010   120,085,874    79,055,865   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="101F60F13F572DA1" LABEL="HP_PAVILION" TYPE="ntfs" 
/dev/sda2: LABEL="HP_RECOVERY" UUID="4B6E-6BC0" TYPE="vfat" 
/dev/sdb1: UUID="f3c374ef-0ed8-43f5-ad0d-0f05f0de3ee2" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb3: UUID="8E4CFDE34CFDC5CD" LABEL="New Volume" TYPE="ntfs" 
/dev/sdb5: UUID="b4cf91a2-445d-4633-91fa-ad5086553641" TYPE="swap" 

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


================================ sda1/boot.ini: ================================

[boot loader]
timeout=6
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons

================================ sda2/boot.ini: ================================

[boot loader]
timeout=0
default=C:\CMDCONS\BOOTSECT.DAT
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons

================================ sda2/BOOT.INI: ================================

[boot loader]
timeout=0
default=C:\CMDCONS\BOOTSECT.DAT
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons

=========================== sdb1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=f3c374ef-0ed8-43f5-ad0d-0f05f0de3ee2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f3c374ef-0ed8-43f5-ad0d-0f05f0de3ee2

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		f3c374ef-0ed8-43f5-ad0d-0f05f0de3ee2
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=f3c374ef-0ed8-43f5-ad0d-0f05f0de3ee2 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		f3c374ef-0ed8-43f5-ad0d-0f05f0de3ee2
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=f3c374ef-0ed8-43f5-ad0d-0f05f0de3ee2 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		f3c374ef-0ed8-43f5-ad0d-0f05f0de3ee2
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows NT/2000/XP
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=f3c374ef-0ed8-43f5-ad0d-0f05f0de3ee2 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=b4cf91a2-445d-4633-91fa-ad5086553641 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  14.1GB: boot/grub/menu.lst
  14.1GB: boot/grub/stage2
  14.2GB: boot/initrd.img-2.6.28-11-generic
  14.2GB: boot/vmlinuz-2.6.28-11-generic
  14.2GB: initrd.img
  14.2GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 


```

Wow interesting info.

shadetree

---

### Post by presence1960 on 2009-09-17
here is what I would do. Boot off the Ubuntu Live CD. Choose "try Ubuntu without any changes". When the desktop loads do this:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd1,0)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd1,0)"
6. Type "setup (hd1)", to install GRUB to MBR, 
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

Reboot & go into BIOS. Set the 61 GB disk as first in the hard disk boot order. Save changes to CMOS and continue booting. At the GRUB menu choose Ubuntu. When the desktop loads open a terminal and run this command ```
gksu gedit /boot/grub/menu.lst
```

that is a lowercase L in .lst

make your windows entry below this line: 
### END DEBIAN AUTOMAGIC KERNELS LIST
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
rootnoverify	(hd1,0)
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		HP recovery
rootnoverify	(hd1,1)
chainloader	+1
```

Click Save on the top toolbar. Close file. reboot. You should be good to go.

---

### Post by shadetree1 on 2009-09-17
Ok were working.  =D>

I wish you many thanks for helping with this issue.

I have learned a little and will continue to learn and contribute a lot.

Oh......my presence? 03-04-1960 :) 

shadetree

---

### Post by presence1960 on 2009-09-18
> **shadetree1 said:**
> Ok were working.  =D>

I wish you many thanks for helping with this issue.

I have learned a little and will continue to learn and contribute a lot.

Oh......my presence? 03-04-1960 :) 

shadetree

me 5/12/1960. 1960 was a good year!

Glad you got it working! Enjoy Ubuntu.

---

