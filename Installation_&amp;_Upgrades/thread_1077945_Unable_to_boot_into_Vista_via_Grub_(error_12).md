---
title: "Unable to boot into Vista via Grub (error 12)"
date: 2009-02-22
forum: Installation &amp; Upgrades
---

### Post by getmkwearmkfly on 2009-02-22
Hi guys -

As a relative newbie to Ubuntu, I seem to have done something rather foolish, but I can't work out exactly how to fix it.

Until about an hour ago, I had a triple-boot on my hard-drive (single drive, with partitions for Windows Vista, Windows 7, and Ubuntu). In a bid to free up space, I attempted to remove the Windows 7 install by using gparted to delete the partition. That worked fine, freed up the required space. Except now, when I start my computer, the Windows Vista Loader option in GRUB returns an "Error 12 - Invalid Device Requested" error, and refuses to allow to boot into either Vista (which I know to still be installed) or Windows 7 (which should now have been deleted).

I'm pretty sure this is a ridiculously rookie mistake, but if you could help me out, it'd be much appreciated.

Thanks,

M.

See boot_info_script results.txt below:

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda2: _________________________________________________________________________

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

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7ab852fc

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    36,866,047    36,864,000   7 HPFS/NTFS
/dev/sda2          36,869,175    68,356,574    31,487,400   5 Extended
/dev/sda5          36,869,238    60,308,009    23,438,772  83 Linux
/dev/sda6          60,308,073    68,356,574     8,048,502  82 Linux swap / Solaris
/dev/sda4         118,140,928   234,438,655   116,297,728   7 HPFS/NTFS

/dev/sda4 ends after the last cylinder of /dev/sda

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="DC66EC5F66EC3C40" TYPE="ntfs" 
/dev/sda4: UUID="48F8550CF854FA20" LABEL="Data" TYPE="ntfs" 
/dev/sda5: UUID="e39f59ed-5c78-45be-a8c9-083ec78b45d7" TYPE="ext3" 
/dev/sda6: UUID="196bcbc5-c39f-4d99-876a-ee0a6eefe004" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)

securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/marcus/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=marcus)


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
# kopt=root=UUID=e39f59ed-5c78-45be-a8c9-083ec78b45d7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e39f59ed-5c78-45be-a8c9-083ec78b45d7

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

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		e39f59ed-5c78-45be-a8c9-083ec78b45d7
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=e39f59ed-5c78-45be-a8c9-083ec78b45d7 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		e39f59ed-5c78-45be-a8c9-083ec78b45d7
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=e39f59ed-5c78-45be-a8c9-083ec78b45d7 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, memtest86+
uuid		e39f59ed-5c78-45be-a8c9-083ec78b45d7
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root



=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=e39f59ed-5c78-45be-a8c9-083ec78b45d7 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=196bcbc5-c39f-4d99-876a-ee0a6eefe004 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  23.3GB: boot/grub/menu.lst
  23.4GB: boot/grub/stage2
  23.3GB: boot/initrd.img-2.6.27-11-generic
  23.3GB: boot/initrd.img-2.6.27-7-generic
  23.3GB: boot/initrd.img-2.6.27-9-generic
  23.3GB: boot/vmlinuz-2.6.27-11-generic
  23.3GB: boot/vmlinuz-2.6.27-7-generic
  23.3GB: boot/vmlinuz-2.6.27-9-generic
  23.3GB: initrd.img
  23.3GB: initrd.img.old
  23.3GB: vmlinuz
  23.3GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb

---

### Post by caljohnsmith on 2009-02-22
It looks like your sda1 Vista partition might be missing some of its boot files, but the main issue right now is that your Grub entry for Vista is incorrect. How about opening your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And first, move the Windows entry you have either to the very end of the file after:
```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root

```
Or if you want Vista listed first in the Grub menu, move the Vista entry just before the following lines:
```
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below
```
Once you move it, change (hd0,1) to (hd0,0) like:
```
title Windows Vista/Longhorn (loader)
root [COLOR="Blue"](hd0,0)[/COLOR]
savedefault
makeactive
chainloader +1
```
Then reboot, try Vista from your Grub menu, and let me know what happens. I think you will probably get a "BOOTMGR missing" error, but try it first and let me know. We can work from there.

---

### Post by getmkwearmkfly on 2009-02-22
Hi caljohnsmith,

As you suspected, it now gives me the error:

"BOOTMGR.exe is missing
CTRL+ALT+DEL to restart"

What exactly have I managed to screw up here? As far as I was aware, the Vista partition was set as the "active" partition.

What do you recommend from here?

Thanks for the quick reply,

M.

---

### Post by markg48 on 2009-02-22
oh hm if i remmber right when u upgrade to win 7 beta it creates  a new partition and   moves old windows to .oldwindows inside win 7 so u deleated both <.<

but i installed over windows xp so i dnt no if this does the same as vista upgrade

---

### Post by caljohnsmith on 2009-02-22
Getting that BOOTMGR missing error means that your Vista boot files were probably in the Windows 7 partition that you deleted. I would recommend following [meierfra's tutorial]("http://ubuntuforums.org/showpost.php?p=5726832") for how to restore Vista's boot files and configure Vista to boot properly; that's probably all you need to do to get Vista booting again. Let me know how that goes or if you run into problems.

---

### Post by getmkwearmkfly on 2009-02-22
I installed all three operating systems in tandem. I didn't exactly "upgrade". I can't remember in which exact order, but this was roughly what the partition table looked like:

Partition 1: Ubuntu
Partition 2: swap
Partition 3: Vista
Partition 4: Win7
Partition 5: empty partition/storage space

Okay, I'll try restoring the bootmgr now - I'll let you know how it goes.

Thanks a lot,

M.

---

### Post by getmkwearmkfly on 2009-02-22
A combination of that tutorial and the "repair your computer" function on the Vista install disc, and I'm back in Windows successfully! Thanks a lot for all your help tonight!

M.

---

### Post by caljohnsmith on 2009-02-23
That's great news, I'm glad to hear Vista is booting again. Cheers and enjoy your dual-boot Ubuntu/Windows setup. :)

---

### Post by getmkwearmkfly on 2009-02-23
I plan to - this experience has served to increase Ubuntu's standing in my eyes :P

This was especially embarassing given I work in IT support, but let's not talk about that...

Thanks again for the help!

M.

---

