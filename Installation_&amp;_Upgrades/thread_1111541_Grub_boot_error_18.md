---
title: "Grub boot error 18"
date: 2009-03-30
forum: Installation &amp; Upgrades
---

### Post by boarder428 on 2009-03-30
I got a Grub boot error 18 and was not able to boot into Windows Xp aswell as Ubuntu after installing Ubuntu 8.10,  do I need a specific boot manager to get this up and running?

---

### Post by meierfra. on 2009-03-30
Is this a fresh install?
Does the Grub menu appear at boot up?

Grub  Error  18 usually means that  your bios can not read the whole hard drive. 
Sometimes this is the due to some wrong setting in your bios.  Make sure that "LBA" mode is enabled. But if "LBA" mode is enabled try "normal" mode instead  (Depending on your bios  those modes might have different names) 

Who old is your computer? Some older bios are  only able to read the first 137 GB of your hard drive.    Sometimes updating the bios can cure the problem.

If none of this helps,  you will have to create small separate boot partition at the beginning of the hard drive. 

But before we get into that I  would like to get a better picture of your setup: 

Boot  from the Ubuntu LiveCD and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

---

### Post by boarder428 on 2009-03-31
> **meierfra. said:**
> Is this a fresh install? [COLOR="Red"]]It's a fresh install off a cd but I have had other problems trying to get this pc to multi boot. The only os I can get this pc to boot to is Xp (which is what it came with)  I have installed Vista as well and it wouldnt boot to vista so I decided to try Linux and see if I had the same problems.  Pc is older IBM NetVista p4[/COLOR]

Does the Grub menu appear at boot up? [COLOR="Red"]I don't think so?[/COLOR]

Grub  Error  18 usually means that  your bios can not read the whole hard drive. 
Sometimes this is the due to some wrong setting in your bios.  Make sure that "LBA" mode is enabled. But if "LBA" mode is enabled try "normal" mode instead  (Depending on your bios  those modes might have different names) 

Who old is your computer?[COLOR="Red"]older p4[/COLOR] Some older bios are  only able to read the first 137 GB of your hard drive.    Sometimes updating the bios can cure the problem. [COLOR="Red"]I'll have to look into this![/COLOR]

If none of this helps,  you will have to create small separate boot partition at the beginning of the hard drive. [COLOR="Red"]I'm not famaliar with this process![/COLOR]

But before we get into that I  would like to get a better picture of your setup: [COLOR="Red"]I don't know if this information will be accurate since I have alrady run some code ```
sudo lilo -M /dev/sda mbr
``` from the terminal in the Live CD to return  my pc to a bootable stage.  I found this code from another post, it did get my system to boot back into windows xp!  I can run the terminal from the cd though and get the current info if it will help!  I know that Ububtu and Vista are both there I just don't know how to make them boot[/COLOR] 

Boot  from the Ubuntu LiveCD and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

[COLOR="Red"]Results.txt [/COLOR]
```
============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/menu.lst /ubuntu/winboot/wubildr.mbr

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0754010c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   204,796,619   204,796,557   7 HPFS/NTFS
/dev/sda2         204,796,620   307,194,929   102,398,310   7 HPFS/NTFS
/dev/sda3         307,194,930   488,392,064   181,197,135   5 Extended
/dev/sda5         307,194,993   315,131,039     7,936,047  83 Linux
/dev/sda6         481,580,568   488,392,064     6,811,497  82 Linux swap / Solaris
/dev/sda7         315,131,103   474,768,944   159,637,842  83 Linux
/dev/sda8         474,769,008   481,580,504     6,811,497  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="BA4CCD294CCCE16D" TYPE="ntfs" 
/dev/sda2: UUID="6AB034A3B03477A1" LABEL="New Volume" TYPE="ntfs" 
/dev/sda5: UUID="d162bf53-7041-42db-b432-3812efc8dc57" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="341c0633-9560-425c-92c1-7c5274e1d4cf" TYPE="swap" 
/dev/sda7: UUID="1cf93a3b-d5a6-48bf-bd19-105a12a67478" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda8: UUID="c3ee3821-5666-4cca-9cb3-a70377eea92f" TYPE="swap" 
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


================================ sda1/boot.ini: ================================

;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /NOEXECUTE=OPTIN /FASTDETECT


======================== sda2/ubuntu/winboot/menu.lst: ========================

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
	find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
	configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
	fallback 2
	find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
	configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
	fallback 3
	find --set-root --ignore-floppies /menu.lst
	configfile /menu.lst

title find /boot/grub/menu.lst
	fallback 4
	find --set-root --ignore-floppies /boot/grub/menu.lst
	configfile /boot/grub/menu.lst

title find /grub/menu.lst
	fallback 5
	find --set-root --ignore-floppies /grub/menu.lst
	configfile /grub/menu.lst

title commandline
	commandline

title reboot
	reboot

title halt
	halt

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
# kopt=root=UUID=d162bf53-7041-42db-b432-3812efc8dc57 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d162bf53-7041-42db-b432-3812efc8dc57

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
uuid		d162bf53-7041-42db-b432-3812efc8dc57
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d162bf53-7041-42db-b432-3812efc8dc57 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		d162bf53-7041-42db-b432-3812efc8dc57
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d162bf53-7041-42db-b432-3812efc8dc57 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		d162bf53-7041-42db-b432-3812efc8dc57
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=d162bf53-7041-42db-b432-3812efc8dc57 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=341c0633-9560-425c-92c1-7c5274e1d4cf none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 159.5GB: boot/grub/menu.lst
 159.5GB: boot/grub/stage2
 159.5GB: boot/initrd.img-2.6.27-7-generic
 159.5GB: boot/vmlinuz-2.6.27-7-generic
 159.5GB: initrd.img
 159.5GB: vmlinuz

=========================== sda7/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=1cf93a3b-d5a6-48bf-bd19-105a12a67478 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=1cf93a3b-d5a6-48bf-bd19-105a12a67478

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
uuid		1cf93a3b-d5a6-48bf-bd19-105a12a67478
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1cf93a3b-d5a6-48bf-bd19-105a12a67478 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		1cf93a3b-d5a6-48bf-bd19-105a12a67478
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1cf93a3b-d5a6-48bf-bd19-105a12a67478 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		1cf93a3b-d5a6-48bf-bd19-105a12a67478
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d162bf53-7041-42db-b432-3812efc8dc57 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d162bf53-7041-42db-b432-3812efc8dc57 ro single 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.10, memtest86+ (on /dev/sda5)
root		(hd0,4)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=1cf93a3b-d5a6-48bf-bd19-105a12a67478 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=c3ee3821-5666-4cca-9cb3-a70377eea92f none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


 188.9GB: boot/grub/menu.lst
 188.8GB: boot/grub/stage2
 188.8GB: boot/initrd.img-2.6.27-7-generic
 188.8GB: boot/vmlinuz-2.6.27-7-generic
 188.8GB: initrd.img
 188.8GB: vmlinuz
``` 

[COLOR="Red"]Thanks for the help![/COLOR]

---

### Post by meierfra. on 2009-03-31
> I don't know if this information will be accurate since I have alrady run some code

sudo lilo -M /dev/sda mbr

That only overwrites the MBR . So the information of the boot info script still will be valuable. Mostly I want to see  the  exact physical 
location of the  boot files on the hard drive. 


> I'm not famaliar with this process!
I"ll  give  you detailed instruction once you  decided to take  that  course of action. But here is a quick overview:
Before the installation create a 200MB ext3 partition at the beginning of the hard drive. Then install ubuntu again. Choose manual partitioning  and mount the 200MB partition at /boot.
You might also consider creating a /home or /Data partition.  Then it will be much easier to reinstall Ubuntu if you  ever have to (or want to).

---

### Post by boarder428 on 2009-04-01
> **meierfra. said:**
> That only overwrites the MBR . So the information of the boot info script still will be valuable. Mostly I want to see  the  exact physical 
location of the  boot files on the hard drive. 



I"ll  give  you detailed instruction once you  decided to take  that  course of action. But here is a quick overview:
Before the installation create a 200MB ext3 partition at the beginning of the hard drive. Then install ubuntu again. Choose manual partitioning  and mount the 200MB partition at /boot.
You might also consider creating a /home or /Data partition.  Then it will be much easier to reinstall Ubuntu if you  ever have to (or want to).

Thanks, I'm not exactly sure how to create a partition at the beginning of the drive, I've just been using windows disk management to create my partitions, do I need to use partition magic or some partitioning software? This is my first attempt to use Linux os's, I've signed up for some unix courses through our community college unfortunatly they don't star until June and I'm trying to get a jump on things!
Thanks for the help!
Corey

---

### Post by meierfra. on 2009-04-01
> Last edited by boarder428; 1 Day Ago at 02:07 AM.. 

Just for future reference.  Since  you edited a previous post instead  of adding RESULTS.txt to a new post, I had no way of knowing that you had posted the RESULTS.txt (otherwise I would have responded much earlier)

> 159.5GB: boot/grub/stage2

Your boot files are indeed outside the 137GB limit.
Everything else seems to be perfectly normal. 
So creating a separate boot partition is your best chance to fix your problem.

Moving the start point of  Vista partition can lead to unnecessary complications and since the end of your Vista partition is inside the 137 GB limit, I  suggest to shrink your Vista partition  by 200MB and use the free space to create a boot partition after your Vista partition,

To shrink the Vista partition I recommend using the Vista disk management:
[http://www.vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista](http://www.vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista)

After you resized the Vista partition you should reboot, and make sure that Vista is still in working order.

Before  I give you instructions how to create the boot partition and reinstall Ubuntu, I have a couple of more questions:

It looks like you did install Ubuntu twice: Do you want   two different Ubuntus or did this happen by accident?
Also would you like to have  a home partition?

---

### Post by boarder428 on 2009-04-02
> **meierfra. said:**
> Just for future reference.  Since  you edited a previous post instead  of adding RESULTS.txt to a new post, I had no way of knowing that you had posted the RESULTS.txt (otherwise I would have responded much earlier)


Your boot files are indeed outside the 137GB limit.
Everything else seems to be perfectly normal. 
So creating a separate boot partition is your best chance to fix your problem.

Moving the start point of  Vista partition can lead to unnecessary complications and since the end of your Vista partition is inside the 137 GB limit, I  suggest to shrink your Vista partition  by 200MB and use the free space to create a boot partition after your Vista partition,

To shrink the Vista partition I recommend using the Vista disk management:
[http://www.vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista](http://www.vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista)

After you resized the Vista partition you should reboot, and make sure that Vista is still in working order.

Before  I give you instructions how to create the boot partition and reinstall Ubuntu, I have a couple of more questions:

It looks like you did install Ubuntu twice: Do you want   two different Ubuntus or did this happen by accident?
Also would you like to have  a home partition? I only need 1 install of Ubuntu, I have attempted to install it more than once and on a different partition, I deleted the partition in disk management before doing so and it still seems to show both so I'm not exactly sure what went wrong, also I have never had success getting Vista boot.  I have been on another forum trying to resolve that issue.  I keep getting the error that the winload.exe file is missing or corrupt.  I can't tell you how many times I've installed vista and used easy bcd to set up the boot all to get the same error.  That's why I deceided to try to get Ubuntu to install to see if I had the same problems.  For some reason I'm getting the idea that this pc just may not be muliti bootable but I don't know enough about editing/reading  the MBR to tell where the problem exists.  I have another newer pc that I built and have had no problems getting it to dual boot to xp and vista, i've thought about adding Ubuntu to it as well but have not wanted to create a problem since it is operating fine.  I did'nt have to do anything with it, I installed xp and then I installed vista on it and it booted to both successfully the first time with no additional steps so I figure I must have gotten lucky on that pc!  I need to learn about the MBR if you have any links I would appreciate it.
Thanks again for all your help
Corey

---

### Post by Magzee on 2009-04-02
Hi guys if I could just squeeze in with a suggestion.

If you can still log into a ubuntu install, or if not, can use an Install cd as a rescue disk then I can help.  I had a similar prob happen to me just recently.  I installed Ubuntu studio on my old desktop, on Hard drive number 2. rebooted to make sure windows was still there, rebooted into studio and it went through its updating (200 odd files!)  Anyway some of these were Linux generic kernels.  I was actually asked if I wanted Grub to be amended to show the changes, I said yes and it bumped windows off.  

So here is how you fix it.  You need to tell Grub bootloader what you have been up to.  Also my understanding is that lilo is different to grub, I think an older boot loader? and it did have limits to what is can achieve.  Grub is very versatile. 

Here is something about grub from another forum site (presume I can quote this)

"There are only two methods available to Grub to boot an operating system.

(D.1) Direct booting

When Grub can read a filing system it goes into the required partition to load its kernel and also the ram disk file "initrd" if used. This is how Grub boots all Linux and some BSDs when being employed as their boot loader. Typical instructions to tell Grub to carry out this task are
Code:

title rPath 0.99 @ hdc31
kernel /boot/vmlinuz-2.6.13.4-1-.x86.i386.cmov ro root=/dev/hdc31 quiet
initrd /boot/initrd-2.6.13.4-1-.x86.i386.cmov.img

The first line identifies the root partition to be booted. The second line "kernel" command is to fetch the kernel named as "vmlinuz-2.6.13.4-1-.x86.i386.cmov". The initrd command of the third line is to load the ram disk file "initrd-2.6.13.4-1-.x86.i386.cmov.img".

(D.2) Indirect booting

When Grub can't read a file system foreign to itself it boots that system's own boot loader instead. It is up to that boot loader to boot its own master. This method is known as chainloading in which the first 512 byte of Grub is "cut" and "paste" with a second boot loader starting at its 513th byte position. This is the "general" method used by all other boot loaders, like NTlrd and Lilo, capable of multi boot.

Every boot loader needs to have a stage-1 and stage-2 because the former is always 512 bytes large ready to be read by the BIOS if this boot loader is in the MBR. The duty of Stage-1 is to load the Stage-2 which in turn does the actual loading of the system."


Boot into ubuntu (if u can...) Open as root.. /boot/grub/menu.lst (note that is an L and not a one)  Now right down the bottom under End of Default Options will be the grub menu that should pop up when you start your computer.  Also note just above that line is a question of auto amending menu.lst (remember those pesky generics) changing that to false hopefully will stop this from happening again. 

I have included a copy here for you of my amended menu.lst.  I have put windows first because I do use that a lot and so I want it to load automatically if I am away from my desk:

Open a terminal

gksudo gedit /boot/grub/menu.lst

then navigate to...

## should update-grub adjust the value of the default booted system
## can be true or false
 updatedefaultentry=false

## ## End Default Options ##

title			Microsoft Windows XP Home Edition
rootnoverify	(hd0,0)
makeactive
chainloader	+1
savedefault


title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=58301981-2622-487d-8bc0-8df19c737d23 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=58301981-2622-487d-8bc0-8df19c737d23 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Microsoft Windows XP Home Edition
root		(hd0,2)
makeactive
chainloader	+1



Ok now the fun bit (Can you tell I have been down this road a few times now!)  I have 2 windows partitions, XP, I hate Vista, a backup XP partition cloned from a fresh install.  and two ubuntu partitions.  Note the boot folder is located on the second hard drive second partition after a storage partition that i dont need to boot into.  Sounds confusing huh, but its sooo easy.  Get this app GParted!!!!  It allows you to shrink, clone enlarge as many partitions as you like (review carefully though as it can delete whole partitions and reformat like new).  Did I say clone??  I meant cut and paste!  thats how I did my backup XP drive.  I dont let windows go anywhere near the bootloader or partitions.

So my ubuntu install holds the files /boot/grub/menu.lst and stages 1 and 2, but GRUB is actually a very small file sitting right at the beginning of your first harddrive.  Thats why it shouldnt matter how far away your ubuntu install is, GRUB just needs to know how to find it.  Thats prob what your boot error means, "cant load as I dont know what you want me to do"

But first you need to know what you want to do and where things are located.  

Here is some more stuff from the other forum
"(H) Recommendations for users intending to multi boot

(H.1) It is always better to partition the disk first. You will know exactly where the systems are going to reside in. Your own data in other partitions are safer from inadvertent damage. You are less likely to be confused by the installer.

(H.2) Try not to mix your personal data with an operating system. An operating system can go down any time so it pays to keep the personal data on a separate partition that can be read and written by all systems. The personal data will be a lot easier to backup and maintained.
Grub can also be installed without a system in a tiny partition with nothing except itself. Grub can be installed anywhere in a bootable media like a floppy, a CD, the MBR of the first bootable disk, any root partition of a system"

So reboot and hopefully something of Grub is there, type c for a command line.

"A user can get confused with Grub shell with a Grub prompt. The former is what you get when typing at Bash shell the command "grub". At which time the Linux would have already been in operation in a "protected" mode and many Grub's booting instructions would have been disabled to protected the Linux. Small amount of commands are still usable. A Grub prompt is obtained after booting Grub only and "without" a Linux presence. At a Grub prompt one can choose any system to boot and all the Grub commands are operable."

so at the Grub prompt with no OS loaded
type find /boot/grub/menu.lst
Grub:  (hd0,1), (hd1,1)

[I](hd0,1) (remember two ubuntu systems, one on each hard drive this one is hard drive 1 partition 2 in Grub speak)

(hd1,1) (this is Ubuntu Studio second hard drive, second partition, and this is the one that I want Grub to get its info from.  the other menu.lst will be wrong anyway).[/I]

Grub:  root (hd1,1)  
(*tells Grub hard drive and partition location of the boot files to use)*
Grub:  setup (hd0) 
 *(tells Grub to write this info at the start of the first hard drive, the MBR if you will)*

Grub:  quit  *(this never works for me unless I am in a terminal - at the prompt I type reboot.)*

Well hope that helps, here is the link to the How to I have been quoting from, also the Grub manual. Oh and the name of the link is: 

[B]A grub menu booting 100+ systems of Dos, Windows, Linux, BSD and Solaris         How I Did It! 
[http://www.justlinux.com/forum/showthread.php?t=143973](http://www.justlinux.com/forum/showthread.php?t=143973)
[/B]

Its worth looking at.
If you need help cos you cant find grub prompt or /boot/grub/menu.lst  let me know.  I have had way too many rebuilds in my short life.

Cheers
Magz

---

### Post by meierfra. on 2009-04-02
boarder428: I don't have much time right now. so  just a couple of quick question to confirm you current setup:
Is this correct:

XP is installed in /dev/sda1 (the  100GB partition)
Vista is installed on /dev/sda2 ((the 50GB partition)
Then you boot, the Vista Boot menu appears and you are able to boot into XP, but booting into Vista gives you the "winload.exe is missing" message

Usually to fix the winload.exe message one just needs to reconfigure the Vista BCD.
But the boot_info_script did not correctly identify   Vista. Could be  a bug in the script, but it might also means that there are some real problems with  your Vista partition.

So maybe the best option would be to use gparted  to delete everything but the XP partition, and  create   partitions for Ubuntu boot, Vista, Ubuntu root and Ubuntu home.  
After that reinstall Vista and Ubuntu.

If that sounds like a good idea, let me know and I can give you detailed instruction.



[QUOTE=Magzee]Its worth looking at.[/QUOTE]
Sorry, but none of that has any relevance in case of Grub error 18.

---

### Post by boarder428 on 2009-04-02
> **Magzee said:**
> Hi guys if I could just squeeze in with a suggestion.

If you can still log into a ubuntu install, or if not, can use an Install cd as a rescue disk then I can help.  I had a similar prob happen to me just recently.  I installed Ubuntu studio on my old desktop, on Hard drive number 2. rebooted to make sure windows was still there, rebooted into studio and it went through its updating (200 odd files!)  Anyway some of these were Linux generic kernels.  I was actually asked if I wanted Grub to be amended to show the changes, I said yes and it bumped windows off.  

So here is how you fix it.  You need to tell Grub bootloader what you have been up to.  Also my understanding is that lilo is different to grub, I think an older boot loader? and it did have limits to what is can achieve.  Grub is very versatile. 

Here is something about grub from another forum site (presume I can quote this)

"There are only two methods available to Grub to boot an operating system.

(D.1) Direct booting

When Grub can read a filing system it goes into the required partition to load its kernel and also the ram disk file "initrd" if used. This is how Grub boots all Linux and some BSDs when being employed as their boot loader. Typical instructions to tell Grub to carry out this task are
Code:

title rPath 0.99 @ hdc31
kernel /boot/vmlinuz-2.6.13.4-1-.x86.i386.cmov ro root=/dev/hdc31 quiet
initrd /boot/initrd-2.6.13.4-1-.x86.i386.cmov.img

The first line identifies the root partition to be booted. The second line "kernel" command is to fetch the kernel named as "vmlinuz-2.6.13.4-1-.x86.i386.cmov". The initrd command of the third line is to load the ram disk file "initrd-2.6.13.4-1-.x86.i386.cmov.img".

(D.2) Indirect booting

When Grub can't read a file system foreign to itself it boots that system's own boot loader instead. It is up to that boot loader to boot its own master. This method is known as chainloading in which the first 512 byte of Grub is "cut" and "paste" with a second boot loader starting at its 513th byte position. This is the "general" method used by all other boot loaders, like NTlrd and Lilo, capable of multi boot.

Every boot loader needs to have a stage-1 and stage-2 because the former is always 512 bytes large ready to be read by the BIOS if this boot loader is in the MBR. The duty of Stage-1 is to load the Stage-2 which in turn does the actual loading of the system."


Boot into ubuntu (if u can...) Open as root.. /boot/grub/menu.lst (note that is an L and not a one)  Now right down the bottom under End of Default Options will be the grub menu that should pop up when you start your computer.  Also note just above that line is a question of auto amending menu.lst (remember those pesky generics) changing that to false hopefully will stop this from happening again. 

I have included a copy here for you of my amended menu.lst.  I have put windows first because I do use that a lot and so I want it to load automatically if I am away from my desk:

Open a terminal

gksudo gedit /boot/grub/menu.lst [COLOR="Red"]Ok, I ran this command and got nothing except another prompt ie. "Ubuntu@Ubuntu: -$"[/COLOR]

then navigate to...

## should update-grub adjust the value of the default booted system
## can be true or false
 updatedefaultentry=false

## ## End Default Options ##

title			Microsoft Windows XP Home Edition
rootnoverify	(hd0,0)
makeactive
chainloader	+1
savedefault


title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=58301981-2622-487d-8bc0-8df19c737d23 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=58301981-2622-487d-8bc0-8df19c737d23 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Microsoft Windows XP Home Edition
root		(hd0,2)
makeactive
chainloader	+1



Ok now the fun bit (Can you tell I have been down this road a few times now!)  I have 2 windows partitions, XP, I hate Vista, a backup XP partition cloned from a fresh install.  and two ubuntu partitions.  Note the boot folder is located on the second hard drive second partition after a storage partition that i dont need to boot into.  Sounds confusing huh, but its sooo easy.  Get this app GParted!!!!  It allows you to shrink, clone enlarge as many partitions as you like (review carefully though as it can delete whole partitions and reformat like new).  Did I say clone??  I meant cut and paste!  thats how I did my backup XP drive.  I dont let windows go anywhere near the bootloader or partitions.

So my ubuntu install holds the files /boot/grub/menu.lst and stages 1 and 2, but GRUB is actually a very small file sitting right at the beginning of your first harddrive.  Thats why it shouldnt matter how far away your ubuntu install is, GRUB just needs to know how to find it.  Thats prob what your boot error means, "cant load as I dont know what you want me to do"

But first you need to know what you want to do and where things are located.  

Here is some more stuff from the other forum
"(H) Recommendations for users intending to multi boot

(H.1) It is always better to partition the disk first. You will know exactly where the systems are going to reside in. Your own data in other partitions are safer from inadvertent damage. You are less likely to be confused by the installer.

(H.2) Try not to mix your personal data with an operating system. An operating system can go down any time so it pays to keep the personal data on a separate partition that can be read and written by all systems. The personal data will be a lot easier to backup and maintained.
Grub can also be installed without a system in a tiny partition with nothing except itself. Grub can be installed anywhere in a bootable media like a floppy, a CD, the MBR of the first bootable disk, any root partition of a system"

So reboot and hopefully something of Grub is there, type c for a command line.

"A user can get confused with Grub shell with a Grub prompt. The former is what you get when typing at Bash shell the command "grub". At which time the Linux would have already been in operation in a "protected" mode and many Grub's booting instructions would have been disabled to protected the Linux. Small amount of commands are still usable. A Grub prompt is obtained after booting Grub only and "without" a Linux presence. At a Grub prompt one can choose any system to boot and all the Grub commands are operable."

so at the Grub prompt with no OS loaded
type find /boot/grub/menu.lst
Grub:  (hd0,1), (hd1,1)

[I](hd0,1) (remember two ubuntu systems, one on each hard drive this one is hard drive 1 partition 2 in Grub speak)

(hd1,1) (this is Ubuntu Studio second hard drive, second partition, and this is the one that I want Grub to get its info from.  the other menu.lst will be wrong anyway).[/I]

Grub:  root (hd1,1)  
(*tells Grub hard drive and partition location of the boot files to use)*
Grub:  setup (hd0) 
 *(tells Grub to write this info at the start of the first hard drive, the MBR if you will)*

Grub:  quit  *(this never works for me unless I am in a terminal - at the prompt I type reboot.)*

Well hope that helps, here is the link to the How to I have been quoting from, also the Grub manual. Oh and the name of the link is: 

[B]A grub menu booting 100+ systems of Dos, Windows, Linux, BSD and Solaris         How I Did It! 
[http://www.justlinux.com/forum/showthread.php?t=143973](http://www.justlinux.com/forum/showthread.php?t=143973)
[/B]

Its worth looking at.
If you need help cos you cant find grub prompt or /boot/grub/menu.lst  let me know.  I have had way too many rebuilds in my short life.

Cheers
Magz

Wow, this is some great info.   Thanks although it's way above my skill level I'm going to have to let all this sink in and do some review & experimenting!
Corey

---

### Post by boarder428 on 2009-04-03
> **meierfra. said:**
> boarder428: I don't have much time right now.[COLOR="Red"]Quite understandable, if and when you have time is ok, i appreciate the help!
[/COLOR] so  just a couple of quick question to confirm you current setup:
Is this correct:

XP is installed in /dev/sda1 (the  100GB partition)[COLOR="Red"]I don't understand the sda lingo but if sda1 is partition 1 and so on then yes xp is sda1
[/COLOR]
[COLOR="Red"]Vista would be sda2[/COLOR]Vista is installed on /dev/sda2 ((the 50GB partition)
Then you boot, the Vista Boot menu appears and you are able to boot into XP, but booting into Vista gives you the "winload.exe is missing" message [COLOR="Red"]Yes previously this was the case before I added the Ubuntu os, after ubuntu I did'nt get a boot menu it was just the grub boot error. I recently removed the Vista entry using easy bcd because I could never get it to boot and I saw no reason to have a boot menu if I could'nt boot to those os's. The reason there is probably 2 entries for ubuntu must be because I tried installing it twice and I did'nt seem to understand the partitioner that came with it so I let it decide what to do![/COLOR]

Usually to fix the winload.exe message one just needs to reconfigure the Vista BCD.[COLOR="Red"]Yeah, Ive never been familliar with the vista bcd until recently, I did'nt even know it exisisted!I googled, read some posts, downloaded Easy BCD to try to fix it and it either did'nt work or I did'nt know what I was doing![/COLOR]
But the boot_info_script did not correctly identify   Vista. Could be  a bug in the script, but it might also means that there are some real problems with  your Vista partition.[COLOR="Red"]You could very well be right but I tried loading Vista numerous times from 2 different install cd's (oem retails at that)alway to get the same error and it happens immediatly after the initial boot after install so I always question if the install process even completed.
[/COLOR]

So maybe the best option would be to use gparted  to delete everything but the XP partition, and  create   partitions for Ubuntu boot, Vista, Ubuntu root and Ubuntu home.  
After that reinstall Vista and Ubuntu. [COLOR="Red"]I might be interested in trying this, I'll have to find gparted and have to get back to you on this one[/COLOR]

If that sounds like a good idea, let me know and I can give you detailed instruction.

[COLOR="Red"]Last off, I have one other computer I am interested in putting ubuntu on and it already has a working dual boot with Xp and Vista on it I just have'nt wanted to ruin the boot sector on it since it works. It has 2 seperate HD's though,  Also it has Sata drives and I was wondering if they are compatiable with ubuntu?[/COLOR]


Thank You
Corey

---

### Post by meierfra. on 2009-04-03
Gparted is on the Ubuntu Live CD. So I suggest to do the following.


**Step 1 Partition your Hard drive**

Boot from the Ubuntu LiveCD.

Open gparted via:

 "System->Administration->Partition Editor" 

RightClick each of the partition and whenever you have an option  to "Unmount" or "SwapOff", choose that option.

RightClick each of the partition (except the XP partition) and  choose "delete"

After you did this you should have  only your XP partition and lots of unallocated space.


RightClick the unallocated space and choose "New".
In the Pop Up window:
       Create a primary partition of size 200MB and File System Ext2
      (leave no free space before the partition)
       Click add.
(This is you boot partition. /dev/sda2)

In the same way:

Create a primary partition of size 50 GB and type ntfs
(your Vista Partition, /dev/sda3)

Create an extended partition using all the available space.
 (this is just a container for remaining partition, /dev/sda4)

Create a logical partition of size 15 GB and type ext3.
(your Ubuntu "/" partition, /dev/sda5)

Create a logical partition of size 3 GB and type swap
(your swap partition, /dev/sda6)


Create a logical partition of type ext3 using all the available space.
(your home partition, /dev/sda7)

Finally  click on "Apply"

Of course the sizes of the partition are just suggestions.  Feel free to change them to your liking.  You might also consider to make the home partition smaller and create an extra ntfs partition  for sharing with XP and Vista.


**Step 2 Install Vista**

Install Vista and make sure you install it on the third partition (the 50 GB ntfs partition)

If you again run into  the "winload.exe missing" problem, come back here and ask for help  (I have a fair amount of experience with editing the BCD)
Also I suggest to not install Ubuntu, until you got Vista to boot.


** Step 3 Install Ubuntu **

Choose manual partitioning

Select /dev/sda2 and click on "edit partition".
Choose mount point /boot.

Similarly choose mount pount "/" for /dev/sda5  and mount point "/home" for /dev/sda7.

You might also choose mount points for your XP and Vista partition. For example /media/XP and /media/Vista.

---

### Post by meierfra. on 2009-04-03
> Also it has Sata drives and I was wondering if they are compatiable with ubuntu?

Ubuntu works just fine on Sata drives.

---

### Post by boarder428 on 2009-04-03
> **meierfra. said:**
> Gparted is on the Ubuntu Live CD. So I suggest to do the following.


**Step 1 Partition your Hard drive**

Boot from the Ubuntu LiveCD.

Open gparted via:

 "System->Administration->Partition Editor" 

RightClick each of the partition and whenever you have an option  to "Unmount" or "SwapOff", choose that option.

RightClick each of the partition (except the XP partition) and  choose "delete"

After you did this you should have  only your XP partition and lots of unallocated space.


RightClick the unallocated space and choose "New".
In the Pop Up window:
       Create a primary partition of size 200MB and File System Ext2
      (leave no free space before the partition)
       Click add.
(This is you boot partition. /dev/sda2)

In the same way:

Create a primary partition of size 50 GB and type ntfs
(your Vista Partition, /dev/sda3)

Create an extended partition using all the available space.
 (this is just a container for remaining partition, /dev/sda4)

Create a logical partition of size 15 GB and type ext3.
(your Ubuntu "/" partition, /dev/sda5)

Create a logical partition of size 3 GB and type swap
(your swap partition, /dev/sda6)


Create a logical partition of type ext3 using all the available space.
(your home partition, /dev/sda7)

Finally  click on "Apply"

Of course the sizes of the partition are just suggestions.  Feel free to change them to your liking.  You might also consider to make the home partition smaller and create an extra ntfs partition  for sharing with XP and Vista.


**Step 2 Install Vista**

Install Vista and make sure you install it on the third partition (the 50 GB ntfs partition)

If you again run into  the "winload.exe missing" problem, come back here and ask for help  (I have a fair amount of experience with editing the BCD)
Also I suggest to not install Ubuntu, until you got Vista to boot.


** Step 3 Install Ubuntu **

Choose manual partitioning

Select /dev/sda2 and click on "edit partition".
Choose mount point /boot.

Similarly choose mount pount "/" for /dev/sda5  and mount point "/home" for /dev/sda7. 
You might also choose mount points for your XP and Vista partition. For example /media/XP and /media/Vista.[COLOR="Red"]Ok, gotta stupid question here, "What exactly is a mount point"[/COLOR]


Great, thanks for the info, i'll do some experimenting and get back to you! I may try installing on another pc as well but I'm determined to find out why I can't get this IBM to cooperate
Corey

---

### Post by meierfra. on 2009-04-03
> "What exactly is a mount point"

That's a place where you can access another partition. Say you mount  your Vista Partition at /media/Vista. Then  the Ubuntu folder /media/Vista  will contain the files and folders from your Vista partition.

During the installation you can choose the mount points for  your various partitions.

---

### Post by meierfra. on 2009-04-03
I spend some time googeling "winload.exe"  (your case just did not seem to be the typical "just edit bcd" scenario)  and  I think I found the cause of your problem:  It's the bios fault (just as Grub error 18 )

I found various "winload.exe missing cases" which occurred since winload.exe was outside the reach of the bios. Reinstalling Vista (or shrinking Vista) so that it stays within the 137GB limit cured the problem.

So I think we need to revise plans:

If you want to be able to boot Vista, you need to  shrink XP (or reinstall XP on a smaller partition), so you have enough space to reinstall  Vista  within the 137GB limit. (or one could  even use gparted  to move your Vista partition.

To shrink XP  from 100GB to 50GB might not be all that easy. At least you will have to defrag XP a few times. How full is the XP partition? 

Since all you OS seem to be pretty new installs, erasing everything and starting from scratch is probably the easiest and  cleanest  solution.
Or you could decide to  keep XP as it is and forgot about Vista.
Just let me know what you would like to do.

---

### Post by boarder428 on 2009-04-04
> **meierfra. said:**
> I spend some time googeling "winload.exe"  (your case just did not seem to be the typical "just edit bcd" scenario)  and  I think I found the cause of your problem:  It's the bios fault (just as Grub error 18 )

I found various "winload.exe missing cases" which occurred since winload.exe was outside the reach of the bios. Reinstalling Vista (or shrinking Vista) so that it stays within the 137GB limit cured the problem.

So I think we need to revise plans:

If you want to be able to boot Vista, you need to  shrink XP (or reinstall XP on a smaller partition), so you have enough space to reinstall  Vista  within the 137GB limit. (or one could  even use gparted  to move your Vista partition.

To shrink XP  from 100GB to 50GB might not be all that easy. At least you will have to defrag XP a few times. How full is the XP partition? 

Since all you OS seem to be pretty new installs, erasing everything and starting from scratch is probably the easiest and  cleanest  solution.
Or you could decide to  keep XP as it is and forgot about Vista.
Just let me know what you would like to do.

[COLOR="Red"]I think it's best to forget Vista for now, this is an older pc and I just wanted to see if it was capable of running vista  It barley meets the minimum requirements!  I may try running it through VM at a later time but lets focus on Ubuntu for now.  I have already wiped everything except Xp and currently have 135GB of unallocated space, do I still need to create the 200MB boot partition and if so do i manually need to label it /dev/sda2?  Reason I ask is because I was playing around with it and noticed that it names the partiton "New Partition" if you leave the lable entry blank![/COLOR]

---

### Post by meierfra. on 2009-04-04
> I think it's best to forget Vista for now, 

OK 

> do I still need to create the 200MB boot partition

No. As long as your Ubuntu "/" partition stays inside the 137 GB limit you should be ok.

> Reason I ask is because I was playing around with it and noticed that it names the partiton "New Partition" i
Gparted will assign the device names (/dev/sda5,/dev/sda6, ...) automatically  after you click on apply.

---

### Post by boarder428 on 2009-04-04
[COLOR="Red"]Do I still need to create 2 partitions for Ubuntu within the 137 GB or do I just let the install utility on the live cd take care of it?  I have'nt created any partitions yet other than the one Xp is on!  I still have 135 GB of unallocated space.[/COLOR]

---

### Post by meierfra. on 2009-04-04
> Do I still need to create 2 partitions for Ubuntu or do I just let the install utility take care of it?

The install utility would place your ubuntu partition outside the 137 GB limit. So yes, create the partitions before hand.

---

### Post by boarder428 on 2009-04-04
> **meierfra. said:**
> The install utility would place your ubuntu partition outside the 137 GB limit. So yes, create the partitions before hand.

[COLOR="Red"]what type and file system? I only have the option of Primary and Extended![/COLOR]

---

### Post by meierfra. on 2009-04-04
The Ubuntu "/":  primary ext3
    home      :  logical ext3
    swap      : logical swap
and if you would like
   share    :    logical ntfs

---

### Post by meierfra. on 2009-04-04
Just saw your edit:

after you create the Ubuntu "/",  create an extended partition using all the unallocated space.

Then inside the extended partition, you can create the logical partitions.

---

### Post by boarder428 on 2009-04-04
Ok, Im haveing troubles installing, when I choose manual install and get to the prepare partitions screen I choose to install to /dev/sda2 which is a 20 gb primary partition type ext3 I get the error "No root file system is defined.  Please correct this from the partitioning menu"

---

### Post by meierfra. on 2009-04-05
At the partition screen, select the 20 GB ubuntu partition.
Click on edit partition. In the pop window choose:


use as :       ext3
format :        x
mount point :   /


Similary edit the other partition (but do NOT format any of the other partitions)

For the home partition
use as: ext3
format 
mount point  /home

for the XP partition
use as: ntfs
format:
mount point: /media/XP

---

### Post by Magzee on 2009-04-05
"Open a terminal

gksudo gedit /boot/grub/menu.lst "Ok, I ran this command and got nothing except another prompt ie. "Ubuntu@Ubuntu: -$"

Ok On mine it opens the boot folder in a separate window.
So once you have reinstalled Ubuntu open up your boot folder, its under root, so in your drop down menu go places computer then filesystem.  Here you will find your boot folder.  Open the boot folder then open the grub folder.

Are you able to do this and if so in the Grub folder can you see menu.lst?

I bring this up because it is here that you tell your computer what it can boot into at start up.

I also perused your results.txt entry from a few days ago.  The problem as I see it was in the menu.lst (s) there was a menu list file in partition 5 and also in partition 7,(two ubuntu installs)  both of these listed Vista as located in Partition 1, neither listed XP and as there were two menu lists, GRUB (ie the bootloader) would have needed to have been configured at start up and told which one to use, otherwise I imagine it would generate an error code.

If you would like further information I will be happy to advise you further.  

If you haven't deleted the partitions yet, vista, xp and ubuntu may be salvagable, but it looks like you are reinstalling on partition 2, so that will overwrite XP.

---

### Post by Magzee on 2009-04-05
> **boarder428 said:**
> Wow, this is some great info.   Thanks although it's way above my skill level I'm going to have to let all this sink in and do some review & experimenting!
Corey

The point of what I wrote was that it certainly is not above your skill level!  You just need to know where things are partitioned, what they are called and tell your bootloader (grub) where to find the info.

If you would like further info I will be happy to advise, perhaps under a new thread.

---

### Post by boarder428 on 2009-04-05
> **meierfra. said:**
> At the partition screen, select the 20 GB ubuntu partition.
Click on edit partition. In the pop window choose:


use as :       ext3
format :        x
mount point :   / [COLOR="Red"]ok, here comes the rookie questions... what does "/" designate or do?[/COLOR]


Similary edit the other partition (but do NOT format any of the other partitions)

For the home partition
use as: ext3
format 
mount point  /home

for the XP partition
use as: ntfs
format:
mount point: /media/XP

[COLOR="Red"]I have not edited anything yet, I am posting a screen shot from gparted which is my current setup, I seem to have went wrong somewhere, possibly in creating my "Home" partition also I never entered anything in the mount point fields[/COLOR]
[IMG]http://img19.picoodle.com/img/img19/3/4/5/cjb428/f_GParted1m_8724fd6.jpg[/IMG]

---

### Post by meierfra. on 2009-04-05
> ok, here comes the rookie questions... what does "/" designate or do?

"/"  is the main directory (folder) of a partition, the directory containing all other directrories ."/" is also called the root directory. During the Ubuntu installation, the partition with mount point "/" will be the partition where the Ubuntu operating  system will be installed.


> I seem to have went wrong somewhere,

Why?  Your screen shot from gparted looks perfect.

---

### Post by boarder428 on 2009-04-05
Well, I'm pleased to say I have successfull boot between both opearting systems!  I wish I knew more about the whole process!  I do have new questions now that it boots.

my boot menu is as follows...
Ubuntu 8.10, Kernel 7.6.27-7-generic
Ubuntu 8.10, Kernel 7.6.27-7-generic(recovery mode)
Ubuntu 8.10, memtest86+
Other Windows Operating Systems:
Windows Vista/Longhorn(loader)

so I assume this is probably correct as this is my first actual visual of a "Grub" boot menu!

First off and not too important is that Xp is showing up as Windows Vista/Longhorn(loader), it boots into xp correctly from here and may just be how grub displays Xp? I don't know!

Second off, is there a way to edit this menu so that it defaults to boot xp?

Now that I have a working install of Ubutu I need to do some reading to actually learn how to use Ubuntu, I have the pocket guide but have not read much of it yet due to the great support I have gotten here.  I really must thank you for all the help but now i'm interested! I don't 100% understand all the steps we went through to get this to work but I want to.  I want to install this on more pc's aswell!

Does the pocket guide have any indepth literature about gparted and some of the stuff we covered here?

Earlier in the post I thought you mentioned that my situation was somewhat unique!  Do you think I would have the same problems trying this install on a few of my other pc's

---

### Post by meierfra. on 2009-04-05
> have successfull boot between both opearting systems
Great.


> First off and not too important is that Xp is showing up as Windows Vista/Longhorn(loader),
Due to your previous Vista install, you still have the Vista boot files on your XP partition. So Ubuntu  thinks you actually have Vista installed.

But you can easily change the title:

Open  a terminal in Ubuntu and type
```
gksudo gedit /boot/grub/menu.lst
```

This opens the file "menu.lst".  
Just edit the line:

title Windows Vista/Longhorn(loader)

You can change "Windows Vista/Longhorn(loader)" to anything you want to.


> Second off, is there a way to edit this menu so that it defaults to boot xp?

Sure. In   menu.lst,   move the whole XP item so that it appears   between these two lines:

# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST


> Does the pocket guide have any indepth literature about gparted and some of the stuff we covered here?


No it doesn't.  There are many tutorials on the "guided" Ubunu installation, but I have not  been able to  find a good tutorial for the "manual" installation .

But here are a couple of sites with lots of information on ubuntu:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)



> Earlier in the post I thought you mentioned that my situation was somewhat unique! Do you think I would have the same problems trying this install on a few of my other pc's


Unlikely. Grub error 18 only happens on a small numbers of computer and mostly only on older computers.

---

### Post by boarder428 on 2009-04-05
> **meierfra. said:**
> 

Unlikely. Grub error 18 only happens on a small numbers of computer and mostly only on older computers.

so it's probably not wise to try to install Ubuntu on a p3 huh? Lol!

Thanks again for all your time & help!
Corey

---

### Post by meierfra. on 2009-04-05
> so it's probably not wise to try to install Ubuntu on a p3 huh? Lol!

You can always try.  I have a 11 year old p2 in my basement running Xubuntu with 128MB of ram.

---

### Post by boarder428 on 2009-04-05
[QUOTE=meierfra.;7020368]



# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

[COLOR="Red"]# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1[/COLOR]

### BEGIN AUTOMAGIC KERNELS LIST[/QUOTE
Like so?

---

### Post by meierfra. on 2009-04-05
Yes. But don't forget to change the title.

---

### Post by boarder428 on 2009-04-06
that worked great although I noticed another 2 entries in my boot menu which I suspect are due to the 238 updates ubuntu prompted me to dl!

Windows Xp(loader)
Ubuntu 8.10, Kernel 7.6.27-11-generic
Ubuntu 8.10, Kernel 7.6.27-11-generic(recovery mode)
Ubuntu 8.10, Kernel 7.6.27-7-generic
Ubuntu 8.10, Kernel 7.6.27-7-generic(recovery mode)
Ubuntu 8.10, memtest86+

do I just delete the 2 older entries?
Corey!

---

### Post by meierfra. on 2009-04-06
> do I just delete the 2 older entries?

You can, but I recommend keeping it.  If something goes wrong with the first kernel (say during a kernel update)  you might need the second kernel for booting. But I suggest to change

# howmany=all

in menu.lst to

# howmany=2

Then you will never have more than 2 sets of kernels on the Grub menu.

---

### Post by boarder428 on 2009-04-07
Got cha! I need to learn more about Grub boot menu.  New experience for me here although I gotta say I feel somewhat accomplished thanks to all your effort meierfra!  Also I'd like to thank Magzee for participating as well!  All information has been valued and this has been an exciting learning experience for me!

My next attempt is going to be my Gateway p4 notebook!  I ran the cd on it for a while and so far the only issue I have come up with is the ability to connect to my network wirelessly! My network uses WPA2-psk security and I could not get Ubuntu to acceppt the 128 bit encryption key  I'm sure there is a work around for that as well I just need to do some reading!  It has a 40gb HD with Xp only on it so I assume the partition must be shruk to add Ubuntu so would a guided install be my best bet there?
Corey

---

### Post by meierfra. on 2009-04-07
> has a 40gb HD with Xp only on it so I assume the partition must be shruk to add Ubuntu so would a guided install be my best bet there?
Yes. The guided install should be the easiest and safest approach.

```
I need to learn more about Grub boot menu. 
```
Have a look at [Hermanzone's Grub page ]("http://users.bigpond.net.au/hermanzone/p15.htm")

---

### Post by boarder428 on 2009-04-30
> **meierfra. said:**
> 
Your boot files are indeed outside the 137GB limit.


May I ask where you got this information or is this pretty much standard with Linux installs!

---

### Post by meierfra. on 2009-04-30
> May I ask where you got this information or is this pretty much standard with Linux installs! 


From RESULTS.txt (see post 3):


```
=================== sda5: Location of files loaded by Grub: ===================


 159.5GB: boot/grub/menu.lst
 159.5GB: boot/grub/stage2
 159.5GB: boot/initrd.img-2.6.27-7-generic
 159.5GB: boot/vmlinuz-2.6.27-7-generic
 159.5GB: initrd.img
 159.5GB: vmlinuz

```

---

### Post by boarder428 on 2009-06-09
thanks for the info, I think I'm starting to catch on with your help and a bit of research.  The problem has been solved but I still find myself coming back to this post for review.
Corey

---

