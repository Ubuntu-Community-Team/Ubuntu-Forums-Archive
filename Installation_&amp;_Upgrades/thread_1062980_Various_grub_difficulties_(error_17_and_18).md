---
title: "Various grub difficulties (error 17 and 18)"
date: 2009-02-07
forum: Installation &amp; Upgrades
---

### Post by Nearyan on 2009-02-07
Well, here is my story.

I wanted to install Ubuntu on my external hard disk. To this end, I created a partition on it, on the end of the drive. Then I installed Ubuntu. My initial approach was to install Grub on the external disk as well, so that I can just tell my BIOS to boot from the external disk which then shows Grub, or tell it to boot my internal disk, bypassing Grub and Ubuntu altogether.

But it didn't work; after the installation, Grub immediately gave an error 17, after the message that it's loading but before showing any boot menu. I've done a lot of browsing around and changing menu.lst, but nothing works. Another strange thing is that even if I make the external disc the primary one in my BIOS, the live disc keeps putting it on /dev/sdc, while I would expect it to be sda, since it's the primary one.

Then I decided to create a boot partition on a bit of leftover space at the end of my internal hard disk, and install Grub on that. The installation worked; Grub shows me a bootmenu when it boots, it can boot Windows, but not Ubuntu; it now gives me error 18, "Selected cylinder exceeds maximum supported by BIOS."

It seems to me that this error cannot be about the bootpartition itself, because if it is, then Grub wouldn't be able to boot from this partition in the first place. Furthermore, LBA (for this internal disc) is enabled in my BIOS. However, since my external disc is, in fact, external, I have no way to enable LBA for it in the BIOS (or check if it is enabled), so then I thought that the error may be about the Ubuntu-partition itself, on the external hard disc, since it is at the end of the drive. But now this no longer makes sense to me - as soon as Grub is loaded, it should be able to boot any OS, regardless of its position of the hard disk - right?

So summarizing, this is the layout of my drives:
sda, the internal drive:
- sda1: Windows
- sda2: data
- sda3: Grub boot partition
sdb - not important, just data
sdc, the external drive, MBR contains Grub:
- sdc1: data
- sdc2: a logical partition, containing sdc5 and sdc6 (no idea why the installer did it this way)
- sdc5: Ubuntu
- sdc6: swap

Any ideas what's the matter, and what I can do to fix it?

Here is the output of the boot info script:
```

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /Boot/BCD /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda2 starts at sector 94365810.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda3 and 
                       looks at sector 319475378 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #3 for 
                       /grub/menu.lst.
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb7537d8a

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    94,365,809    94,365,747   7 HPFS/NTFS
/dev/sda2          94,365,810   317,476,529   223,110,720   7 HPFS/NTFS
/dev/sda3    *    317,476,530   321,669,494     4,192,965  83 Linux


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
133 heads, 17 sectors/track, 216822 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xed1040a2

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   490,231,807   490,229,760   7 HPFS/NTFS


Drive sdc: _____________________________________________________________________

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000c2ce6

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   404,564,894   404,564,832   7 HPFS/NTFS
/dev/sdc2         404,564,895   488,392,064    83,827,170   5 Extended
/dev/sdc5         404,564,958   484,857,764    80,292,807  83 Linux
/dev/sdc6         484,857,828   488,392,064     3,534,237  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="74E0AECFE0AE96C0" LABEL="XP" TYPE="ntfs" 
/dev/sda2: UUID="2404E8BF04E89558" LABEL="Data" TYPE="ntfs" 
/dev/sda3: UUID="b28bd1ca-506f-4bbb-8821-216b8e01a2ad" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="568C86C98C86A35B" LABEL="Data2" TYPE="ntfs" 
/dev/sdc1: UUID="2CBCF53ABCF4FF60" LABEL="Externe HD" TYPE="ntfs" 
/dev/sdc5: UUID="4d14466a-50c6-46a5-a9fd-686c040ee313" TYPE="ext3" 
/dev/sdc6: TYPE="swap" UUID="e3f899ea-3e9f-4def-aa9e-2b79788487c9" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd1 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdc5 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sdc1 on /media/Externe HD type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1 on /media/XP type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

================================ sda1/boot.ini: ================================

[boot loader]
timeout=0
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /noexecute=alwaysoff

============================= sda3/grub/menu.lst: =============================

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
timeout		5

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
# kopt=root=UUID=4d14466a-50c6-46a5-a9fd-686c040ee313 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b28bd1ca-506f-4bbb-8821-216b8e01a2ad

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
uuid		4d14466a-50c6-46a5-a9fd-686c040ee313
kernel		(hd0,2)/vmlinuz-2.6.27-7-generic ro 
initrd		(hd0,2)/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		4d14466a-50c6-46a5-a9fd-686c040ee313
kernel		(hd0,2)/vmlinuz-2.6.27-7-generic ro  single
initrd		(hd0,2)/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		4d14466a-50c6-46a5-a9fd-686c040ee313
kernel		(hd0,2)/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP
rootnoverify	(hd0,0)
savedefault
chainloader	+1


=================== sda3: Location of files loaded by Grub: ===================


 163.5GB: grub/menu.lst
 163.5GB: grub/stage2
 162.5GB: initrd.img-2.6.27-7-generic
 162.5GB: vmlinuz-2.6.27-7-generic

=========================== sdc5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=4d14466a-50c6-46a5-a9fd-686c040ee313 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=4d14466a-50c6-46a5-a9fd-686c040ee313

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
uuid		4d14466a-50c6-46a5-a9fd-686c040ee313
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4d14466a-50c6-46a5-a9fd-686c040ee313 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		4d14466a-50c6-46a5-a9fd-686c040ee313
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4d14466a-50c6-46a5-a9fd-686c040ee313 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		4d14466a-50c6-46a5-a9fd-686c040ee313
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
chainloader	+1


=============================== sdc5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc5
UUID=4d14466a-50c6-46a5-a9fd-686c040ee313 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc6
UUID=e3f899ea-3e9f-4def-aa9e-2b79788487c9 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdc5: Location of files loaded by Grub: ===================


 217.4GB: boot/grub/menu.lst
 217.4GB: boot/grub/stage2
 217.3GB: boot/initrd.img-2.6.27-7-generic
 217.3GB: boot/vmlinuz-2.6.27-7-generic
 217.3GB: initrd.img
 217.3GB: vmlinuz

```

---

### Post by caljohnsmith on 2009-02-07
I think at least part of the problem is that you have sda3 set up as your boot partition for Ubuntu, yet the sdc5 Ubuntu install is not yet configured for your sda3 boot partition. Also your sda3 menu.lst needs some tweaking. How about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
sudo mkdir /mnt/sda3 /mnt/sdc5
sudo mount /dev/sda3 /mnt/sda3
sudo mount /dev/sdc5 /mnt/sdc5
gksudo gedit /mnt/sda3/boot/grub/menu.lst
```
And copy/paste the following boot stanzas into it to replace the ones you have:
```
title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		b28bd1ca-506f-4bbb-8821-216b8e01a2ad
kernel		/vmlinuz-2.6.27-7-generic root=UUID=4d14466a-50c6-46a5-a9fd-686c040ee313 ro quiet splash 
initrd		/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		b28bd1ca-506f-4bbb-8821-216b8e01a2ad
kernel		/vmlinuz-2.6.27-7-generic root=UUID=4d14466a-50c6-46a5-a9fd-686c040ee313 ro  single
initrd		/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		b28bd1ca-506f-4bbb-8821-216b8e01a2ad
kernel		/memtest86+.bin
quiet
```
Next do:
```
sudo mv /mnt/sdc5/boot /mnt/sdc5/boot_backup
sudo mkdir /mnt/sdc5/boot
gksudo gedit /mnt/sdc5/etc/fstab
```
And then add the following lines in your fstab:
```
#/dev/sda3 boot partition:
UUID=b28bd1ca-506f-4bbb-8821-216b8e01a2ad /boot ext3  relatime,errors=remount-ro 0 0
```
Then reboot, and let me know how far you get when booting Ubuntu. We can work from there.

---

### Post by Nearyan on 2009-02-07
That's it! It worked.

I still don't understand why Grub chose to show error 18, though, and I also don't understand why my initial setup didn't work. But no matter - I'm happy that this one does.

Thanks a lot! :)

---

### Post by caljohnsmith on 2009-02-07
Glad to hear that worked OK; cheers and enjoy your new Ubuntu install. :)

---

