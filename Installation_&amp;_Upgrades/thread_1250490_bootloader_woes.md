---
title: "bootloader woes"
date: 2009-08-26
forum: Installation &amp; Upgrades
---

### Post by ajm8127 on 2009-08-26
So my friend just bought a new laptop and didn't like Vista at all. So I let him know about Ubuntu, which his brother has also had success with. He got a copy of 9.04. Initially, he installed it through Vista to which I told him that he needed to not do that, and instead create new partitions.

The plan always was to install to a USB drive because he was afraid of voiding his warranty. So thats what we did. I didn't even think about grub installing to the USB drive and rendering the computer unbootable (Grub 1.5 error 21) without it until he brought his laptop over and showed me. I figured that the BIOS would take care of boot order, booting the USB drive first if it was plugged in, and the internal hard drive in absence of the USB drive. 

So my question is how do I make it boot to Vista without the USB drive plugged in? I suppose I need to move the boot loader to the internal hard drive and off of the USB drive, but I do not want to reinstall either operating system.

---

### Post by presence1960 on 2009-08-26
Let's get a better look at your setup. Boot the Ubuntu Live CD with USB disk plugged in. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by ajm8127 on 2009-08-26
Well, I don't think there will be any diagnostics. He is leaving for school at the end of the week, and doesn't have the time to mess with it. He just bought it, so its clean, and plans on reformatting everything and starting fresh. 

Thanks anyway, presence.

---

### Post by presence1960 on 2009-08-26
> **ajm8127 said:**
> Well, I don't think there will be any diagnostics. He is leaving for school at the end of the week, and doesn't have the time to mess with it. He just bought it, so its clean, and plans on reformatting everything and starting fresh. 

Thanks anyway, presence.

??? Then why the post???

---

### Post by ajm8127 on 2009-08-27
Yeah I realize it seems like a waste, but at the time when I posted, all options were on the table. I was kind of pushing to fix the problem without reinstalls, but that was before I realized he was on a tight schedule. Sorry to waste your time.

---

### Post by presence1960 on 2009-08-27
No offense taken, was just wondering. You could have downloaded that script , ran it and posted the results in a matter of a minute. Then we could have given you suggestions to fix. Even a reinstall would only take a half hour at most. probably would have been a quick fix of editing menu.lst. Oh well, maybe next time.

---

### Post by ajm8127 on 2009-08-27
> **presence1960 said:**
> No offense taken, was just wondering. You could have downloaded that script , ran it and posted the results in a matter of a minute. Then we could have given you suggestions to fix. Even a reinstall would only take a half hour at most. probably would have been a quick fix of editing menu.lst. Oh well, maybe next time.

That's when the problems start. I was looking into the problem for him, but I don't have his computer. He didn't want to leave it with me because he needs it. It still works, it's just inconvenient to have to use the USB drive to boot off the internal drive. It wasn't my call, it was his. 

I do have grub problems of my own if you still want to help. I had two installs of 8.10 originally, one for everyday use, and one for cross compiling. I wanted to keep them separate. I realized that was pretty much useless so I decided to install 9.04 over the second 8.10 install. Now when I boot, grub loads 9.04 fine, but when I select 8.10, it gives me error 22, no such partition. 

Results.txt:
```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000c085a

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   390,716,864   390,716,802   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0e201d0c

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63       401,624       401,562  82 Linux swap / Solaris
/dev/sdb2             401,625    58,990,679    58,589,055  83 Linux
/dev/sdb3          58,990,680   117,579,734    58,589,055   5 Extended
/dev/sdb5          58,990,743   117,579,734    58,588,992  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="4813-100B" TYPE="vfat" 
/dev/sdb1: UUID="bc2dee41-31d6-44ce-977e-c245cfc57bd9" TYPE="swap" 
/dev/sdb2: UUID="4fbb67da-17d8-4c2f-9662-26246583bd6b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="185b5c48-dcc5-4dc1-bdc9-1bf51c71c45d" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sdb5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/omniscient/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=omniscient)


=========================== sdb2/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=4fbb67da-17d8-4c2f-9662-26246583bd6b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=4fbb67da-17d8-4c2f-9662-26246583bd6b

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		4fbb67da-17d8-4c2f-9662-26246583bd6b
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=4fbb67da-17d8-4c2f-9662-26246583bd6b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		4fbb67da-17d8-4c2f-9662-26246583bd6b
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=4fbb67da-17d8-4c2f-9662-26246583bd6b ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		4fbb67da-17d8-4c2f-9662-26246583bd6b
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=4fbb67da-17d8-4c2f-9662-26246583bd6b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		4fbb67da-17d8-4c2f-9662-26246583bd6b
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=4fbb67da-17d8-4c2f-9662-26246583bd6b ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		4fbb67da-17d8-4c2f-9662-26246583bd6b
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4fbb67da-17d8-4c2f-9662-26246583bd6b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		4fbb67da-17d8-4c2f-9662-26246583bd6b
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4fbb67da-17d8-4c2f-9662-26246583bd6b ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		4fbb67da-17d8-4c2f-9662-26246583bd6b
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=4fbb67da-17d8-4c2f-9662-26246583bd6b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=bc2dee41-31d6-44ce-977e-c245cfc57bd9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

192.168.1.250:/mnt/Media_1 /mnt/nas/media1 nfs rw,rsize=2048,wsize=2048 0 0 
192.168.1.250:/mnt/Media_0 /mnt/nas/media0 nfs rw,rsize=2048,wsize=2048 0 0 

/dev/sda1	/mnt/200gb	vfat	umask=000,defaults 0 0

=================== sdb2: Location of files loaded by Grub: ===================


  12.5GB: boot/grub/menu.lst
  12.4GB: boot/grub/stage2
  12.4GB: boot/initrd.img-2.6.27-11-generic
  12.4GB: boot/initrd.img-2.6.27-7-generic
  12.4GB: boot/initrd.img-2.6.27-9-generic
  12.5GB: boot/vmlinuz-2.6.27-11-generic
  12.4GB: boot/vmlinuz-2.6.27-7-generic
  12.4GB: boot/vmlinuz-2.6.27-9-generic
  12.4GB: initrd.img
  12.4GB: initrd.img.old
  12.5GB: vmlinuz
  12.4GB: vmlinuz.old

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
# kopt=root=UUID=185b5c48-dcc5-4dc1-bdc9-1bf51c71c45d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=185b5c48-dcc5-4dc1-bdc9-1bf51c71c45d

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
uuid		185b5c48-dcc5-4dc1-bdc9-1bf51c71c45d
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=185b5c48-dcc5-4dc1-bdc9-1bf51c71c45d ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		185b5c48-dcc5-4dc1-bdc9-1bf51c71c45d
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=185b5c48-dcc5-4dc1-bdc9-1bf51c71c45d ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		185b5c48-dcc5-4dc1-bdc9-1bf51c71c45d
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb2.
title		Ubuntu 8.10, kernel 2.6.27-11-generic (on /dev/sdb2)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=4fbb67da-17d8-4c2f-9662-26246583bd6b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb2.
title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode) (on /dev/sdb2)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=4fbb67da-17d8-4c2f-9662-26246583bd6b ro single 
initrd		/boot/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb2.
title		Ubuntu 8.10, kernel 2.6.27-9-generic (on /dev/sdb2)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=4fbb67da-17d8-4c2f-9662-26246583bd6b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb2.
title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode) (on /dev/sdb2)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=4fbb67da-17d8-4c2f-9662-26246583bd6b ro single 
initrd		/boot/initrd.img-2.6.27-9-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb2.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sdb2)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4fbb67da-17d8-4c2f-9662-26246583bd6b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb2.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sdb2)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4fbb67da-17d8-4c2f-9662-26246583bd6b ro single 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb2.
title		Ubuntu 8.10, memtest86+ (on /dev/sdb2)
root		(hd1,1)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=185b5c48-dcc5-4dc1-bdc9-1bf51c71c45d /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb1 during installation
UUID=bc2dee41-31d6-44ce-977e-c245cfc57bd9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


  52.5GB: boot/grub/menu.lst
  52.5GB: boot/grub/stage2
  52.5GB: boot/initrd.img-2.6.28-11-generic
  52.5GB: boot/vmlinuz-2.6.28-11-generic
  52.5GB: initrd.img
  52.5GB: vmlinuz
```

---

### Post by ajm8127 on 2009-08-27
You are going to hate me even more now. I copied portions of the 8.10 install's menu.lst to the 9.04 install's menu.lst and now it works. Seems the 9.04 install's menu.lst should use (hd0,1) for the 8.10 installs and not (hd1,1).

That script is awesome though. Thanks for that!

---

### Post by presence1960 on 2009-08-27
=========================== sdb5/boot/grub/menu.lst: ===========================
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
# kopt=root=UUID=185b5c48-dcc5-4dc1-bdc9-1bf51c71c45d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=185b5c48-dcc5-4dc1-bdc9-1bf51c71c45d

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
uuid		185b5c48-dcc5-4dc1-bdc9-1bf51c71c45d
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=185b5c48-dcc5-4dc1-bdc9-1bf51c71c45d ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		185b5c48-dcc5-4dc1-bdc9-1bf51c71c45d
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=185b5c48-dcc5-4dc1-bdc9-1bf51c71c45d ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		185b5c48-dcc5-4dc1-bdc9-1bf51c71c45d
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb2.
[COLOR="Red"]title		Ubuntu 8.10, kernel 2.6.27-11-generic (on /dev/sdb2)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=4fbb67da-17d8-4c2f-9662-26246583bd6b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb2.
title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode) (on /dev/sdb2)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=4fbb67da-17d8-4c2f-9662-26246583bd6b ro single 
initrd		/boot/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb2.
title		Ubuntu 8.10, kernel 2.6.27-9-generic (on /dev/sdb2)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=4fbb67da-17d8-4c2f-9662-26246583bd6b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb2.
title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode) (on /dev/sdb2)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=4fbb67da-17d8-4c2f-9662-26246583bd6b ro single 
initrd		/boot/initrd.img-2.6.27-9-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb2.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sdb2)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4fbb67da-17d8-4c2f-9662-26246583bd6b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb2.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sdb2)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4fbb67da-17d8-4c2f-9662-26246583bd6b ro single 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb2.
title		Ubuntu 8.10, memtest86+ (on /dev/sdb2)
root		(hd1,1)
kernel		/boot/memtest86+.bin  
savedefault
boot[/COLOR]
```

get rid of the above red text in jaunty's menu.lst and chainload Intrepid. Fist off the UUID for Intrepid is incorrect. Also every time Intrepid updates a kernel you are going to have to manually edit Jaunty's menu.lst to boot the new kernel. Chainloading intrepid from Jaunty's menu.lst will allow you to pass off to intrepids menu.lst which will always be updated automatically after each kernel update. get rid of all those Intrepid entries and add this instead:

```
title         Ubuntu 8.10
rootnoverify  (hd1,1)
chainloader   +1



```

Also you have a boot flag on sdb1 which is swap. boot off the live CD and use gparted (Partition Editor) to remove the boot flag from sdb1.

---

### Post by presence1960 on 2009-08-27
> **ajm8127 said:**
> You are going to hate me even more now. I copied portions of the 8.10 install's menu.lst to the 9.04 install's menu.lst and now it works. Seems the 9.04 install's menu.lst should use (hd0,1) for the 8.10 installs and not (hd1,1).

That script is awesome though. Thanks for that!

In that case I would still chainload but make it root (hd0,1) that's because you have your sdb disk booting first in BIOS

---

