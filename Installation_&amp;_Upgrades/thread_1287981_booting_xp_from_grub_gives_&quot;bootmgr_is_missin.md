---
title: "booting xp from grub gives &quot;bootmgr is missing&quot;, happens after resolved grub issues"
date: 2009-10-10
forum: Installation &amp; Upgrades
---

### Post by PureRumble on 2009-10-10
Hello.

I have a 320GB SATA HD and a 750GB SATA HD.

The 320GB had Windows XP 64 and Ubuntu 8.04.

I decided to get a fresh install of Ubuntu 9.04.

In the installation process, I deleted the old Ubuntu partition & swap partition.

Then I created new partitions, ext3 and swap, and installed 9.04.

After reboot, Grub would give Error 17.

I found a solution: Booting up from Live CD, I did

1) sudo grub
2) find /boot/grub/stage 1. This gave (hd1,4)
3) root (hd1,4)
4) setup (hd1)

Then after reboot, grub menu appeared but choosing Windows XP gives "bootmgr is missing".

I have done bootcfg /default and fixboot from the XP repair console, no use.

Any help, please? :-(

I should mention that while I was fixing the first grub issue, I once did setup (hd0) instead of (hd1). This is because a post told me to do (hd0) but I'm guessing the author didn't think of the case that boot may be done from some other HD than hd0.

This is my fdisk -lu

```
Disk /dev/sda: 750.1 GB, 750156374016 bytes
3 heads, 50 sectors/track, 9767661 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x98c730a7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1465143295   732570624    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x25649a59

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   415424834   207712386    7  HPFS/NTFS
/dev/sdb2       415424835   617136974   100856070    5  Extended
/dev/sdb3       617136975   625137344     4000185   82  Linux swap / Solaris
/dev/sdb5       415424898   617136974   100856038+  83  Linux
```

And here comes my cat /boot/grub/menu.lst

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
# kopt=root=UUID=847bde4a-b342-4952-9687-7b8da083c9a5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=847bde4a-b342-4952-9687-7b8da083c9a5

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
uuid		847bde4a-b342-4952-9687-7b8da083c9a5
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=847bde4a-b342-4952-9687-7b8da083c9a5 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		847bde4a-b342-4952-9687-7b8da083c9a5
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=847bde4a-b342-4952-9687-7b8da083c9a5 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		847bde4a-b342-4952-9687-7b8da083c9a5
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows XP Professional x64 Edition
rootnoverify	(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

---

### Post by stlsaint on 2009-10-10
you need to ensure that you have the first hdd (hd0) as being the one to boot first in bios! then you can use the xp recovery disc to install the bootloader back onto your second hdd!

---

### Post by PureRumble on 2009-10-10
Hey. Thanks for fast reply.

I _think_ (hd0) is the 750GB drive, but I have xp + ubuntu on the (hd1) 320GB drive.

Are you sure that I got to set the 750GB drive as the one to boot in bios before I use the recovery disc?

By the way, it isn't a recovery disc really, but the xp installation disc.

I insert it, wait until the installer has loaded and I can press R for the repair tool. Just to be clear.

Thanks for your help.

> **stlsaint said:**
> you need to ensure that you have the first hdd (hd0) as being the one to boot first in bios! then you can use the xp recovery disc to install the bootloader back onto your second hdd!

---

### Post by PureRumble on 2009-10-10
By the way, when I'm using the XP disc to repair, am I using the correct commands:

1) BOOTCFG /DEFAULT
2) FIXBOOT

---

### Post by stlsaint on 2009-10-10
no in that case you want hd1 as your primary hdd in bios. also you will need to edit that menu.lst as you shouldnt need to map anything to hd0 if it has nothing on it. and i will have to double check on the mbr cmds...also see my sigs for help with all...no its late so you can reference back to this post later!! please dont hesitate to ask for more help...

Welcome to Ubuntu

---

### Post by PureRumble on 2009-10-10
Heya, thx for your reply.

Clearly something is wrong with the XP partition, right?

I mean this is _not_ a GRUB issue, is it?

---

### Post by PureRumble on 2009-10-10
Hi.

Here's the deal:

If I remove map (hd1) (hd0) then I get nothing at all when I boot XP.

Having selected XP in grub, it says "starting up..." as usual, but nothing else happens.

But if I _also_ remove map (hd0) (hd1) then we're back at the "bootmgr is missing"

What is going on here? What does this map-thing do anyway?

If you don't mind then I'm gonna sleep now and hopefully when I wake up I'll think that all this was just a bad dream...

Thanks for helping me out :)

---

### Post by PureRumble on 2009-10-11
Shameless bump, still get the bootmgr is missing.

Could it be that grub tries to boot from the 750GB HD (that is ntfs) when I choose windows xp?

There is nothing but data on the 750GB HD!

Both windows and ubuntu are on the 320GB HD!

That would explain the missing bootmgr!

But if that's so then I still can't see what's the cause

Check my fdisk -lu and menu.lst in the post above if you want.

Tell me if you want more information.

Thanks.

---

### Post by louieb on 2009-10-11
Boot order is important to GRUB - the map commands are to fake windows into thinking its on the 1st drive in the boot order - when its not . 

Depending on which drive is 1st in the boot order your windows entry will look different. 

Please download [Boot Info Script - SourceForge.net]("http://sourceforge.net/projects/bootinfoscript/") it creates file results.txt. Put its content in your next post.
to run
```
sudo bash ~/Desktop/boot_info_script*.sh
```

---

### Post by PureRumble on 2009-10-11
Thx for reply & info & hlp. OK, here comes the results.txt.

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 750.1 GB, 750156374016 bytes
3 heads, 50 sectors/track, 9767661 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x98c730a7

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048 1,465,143,295 1,465,141,248   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x25649a59

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   415,424,834   415,424,772   7 HPFS/NTFS
/dev/sdb2         415,424,835   617,136,974   201,712,140   5 Extended
/dev/sdb5         415,424,898   617,136,974   201,712,077  83 Linux
/dev/sdb3         617,136,975   625,137,344     8,000,370  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="0E16CDAD16CD965D" LABEL="New Volume" TYPE="ntfs" 
/dev/sdb1: UUID="287CAA717CAA3988" TYPE="ntfs" 
/dev/sdb3: UUID="9e283790-dc82-4af6-8a1a-06ee10acc554" TYPE="swap" 
/dev/sdb5: UUID="847bde4a-b342-4952-9687-7b8da083c9a5" TYPE="ext3" 

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
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/purerumble/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=purerumble)
/dev/sdb1 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1 on /media/New Volume type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


================================ sdb1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Professional x64 Edition" /noexecute=optin /fastdetect

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
# kopt=root=UUID=847bde4a-b342-4952-9687-7b8da083c9a5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=847bde4a-b342-4952-9687-7b8da083c9a5

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
uuid		847bde4a-b342-4952-9687-7b8da083c9a5
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=847bde4a-b342-4952-9687-7b8da083c9a5 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		847bde4a-b342-4952-9687-7b8da083c9a5
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=847bde4a-b342-4952-9687-7b8da083c9a5 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		847bde4a-b342-4952-9687-7b8da083c9a5
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows XP Professional x64 Edition
rootnoverify	(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


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
UUID=847bde4a-b342-4952-9687-7b8da083c9a5 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb3 during installation
UUID=9e283790-dc82-4af6-8a1a-06ee10acc554 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 222.5GB: boot/grub/menu.lst
 222.5GB: boot/grub/stage2
 222.5GB: boot/initrd.img-2.6.28-11-generic
 222.6GB: boot/initrd.img-2.6.28-15-generic
 222.6GB: boot/vmlinuz-2.6.28-11-generic
 222.5GB: boot/vmlinuz-2.6.28-15-generic
 222.6GB: initrd.img
 222.5GB: initrd.img.old
 222.5GB: vmlinuz
 222.6GB: vmlinuz.old
```

---

### Post by louieb on 2009-10-11
> Could it be that grub tries to boot from the 750GB HD (that is ntfs) when I choose windows xp?Thats would be my guess too. Looks like you are setup to boot to grub from either hard drive. 
> 
 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.


Depending on which is 1st in the boot order one of these should work. 

if the 750gb drive is 1st in boot order
```

title        Windows XP Professional x64 Edition
map        (hd0) (hd1)
map        (hd1) (hd0)
rootnoverify    (hd1,0)
savedefault
makeactive

chainloader    +1



```if the 320 drive is 1st in boot order
```

title        Windows XP Professional x64 Edition
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1

```

---

### Post by PureRumble on 2009-10-11
You are houdini! That solved it!

I checked bios and the 320 drive was indeed 1st in order.

So I replaced the last part of menu.lst with this:

```
title        Windows XP Professional x64 Edition
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1
```

And now XP boots flawlessly, thank you!

BUT...

... I wanna know what's going on here?

Remember the initial problem I had with grub?

I solved it by entering the grub prompt and writing

1) root (hd1,4)
2) setup (hd1)

The grub menu wouldn't even show up before I did that.

Instead I got error 17.

Indeed, your observation that grub is set on both hd's mbr is correct.

This is because the post that was guiding me to fix the error 17 said I should run setup (hd0) which is incorrect.

But if there is this distinction between hd0 and hd1, if the former is the 750 drive with all the data and the latter is the 320 drive with the xp and linux...

... then why was this problem solved by writing rootnoverify (hd0,0) in menu.lst? Isn't hd0 the 750 drive?

Is it perhaps so that it works differently when you set up grub internally in ubuntu and when grub is gonna boot the partition of your choice?

Is there somehow a mismatch where (hd1) in the former case is (hd0) in the latter case?

Is this somehow related to the boot order in bios?

A newb is pondering big questions here :-(

But the first thing I'm gonna do is to tell the author of the error 17 thread so that he can fix his instructions :).

Also I was thinking that perhaps we can create a HOWTO thread for this problem.

And one last thing, if this is some kind of bug then shouldn't we report it?

It's a nasty one, your system won't boot after installing ubuntu! Doesn't make for good commercial!

Thanks.

---

### Post by louieb on 2009-10-11
Its not anything that going to change in GRUB legacy (v0.97). Its a known problem with grub-install  this excerpt from the [GNU GRUB Manual 0.97]("http://www.gnu.org/software/grub/manual/grub.html")  .   

> there are several ways in which your computer can become unbootable. For example, most operating systems don't tell GRUB how to map BIOS drives to OS devices correctly—GRUB merely guesses the mapping. This will succeed in most cases, but not always.

Starting with Karmic (v9.10)  Ubuntu is going to use GRUB2 (v1.9x). Don't know how much better its going to be at the initial setup. I guess we'll see.

---

