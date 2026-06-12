---
title: "Can't get grub to work properly"
date: 2009-08-08
forum: Installation &amp; Upgrades
---

### Post by OrangeCrush112 on 2009-08-08
I'm not quite sure what I'm doing wrong.

Me and my brother share a computer, and he went about installing XP around xubuntu.

However, he didn't back up grub.
So, I reinstalled it.

And I'm pretty sure that XP is at (hd0,1).
So thats how I set it up:
title           Microsoft Windows XP Home Edition
root            (hd0,1)
savedefault
makeactive
chainloader+1

However, when I select it in grub, nothing happens. Not even error message.
If its notable, gparted gives an error when it opens
"Failed to mount "Windows XP"
The enclosing drive for the volume is locked."

Also, windows XP is marked as 'boot.'
I'm new to linux, so I can't really say I know what that means.:confused:
What am I doing wrong?

---

### Post by louieb on 2009-08-08
Need more information about your setup.  Please follow [Boot Info Script Instructions]("http://ubuntuforums.org/showpost.php?p=6725571&postcount=3") 
Note: the instructions say to run from a live CD but you can run them from your Xubuntu hard drive install. 

Put the results.txt file in your next post.

---

### Post by OrangeCrush112 on 2009-08-08
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa70da70d

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   143,364,059   143,363,997  83 Linux
/dev/sda2    *    143,364,060   309,604,679   166,240,620   7 HPFS/NTFS
/dev/sda3         309,604,680   312,576,704     2,972,025   5 Extended
/dev/sda5         309,604,743   312,576,704     2,971,962  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="d6a28e3a-8e99-41d5-9b35-4970e27baa5e" TYPE="ext3" 
/dev/sda2: UUID="4E2FF5DF4F5D3E7F" LABEL="Windows XP" TYPE="ntfs" 
/dev/sda5: UUID="653cf32e-c190-4741-8aeb-d2f9e592445b" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-14-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
none on /proc/fs/vmblock/mountPoint type vmblock (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)


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
# kopt=root=UUID=d6a28e3a-8e99-41d5-9b35-4970e27baa5e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d6a28e3a-8e99-41d5-9b35-4970e27baa5e

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

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		d6a28e3a-8e99-41d5-9b35-4970e27baa5e
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=d6a28e3a-8e99-41d5-9b35-4970e27baa5e ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		d6a28e3a-8e99-41d5-9b35-4970e27baa5e
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=d6a28e3a-8e99-41d5-9b35-4970e27baa5e ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		d6a28e3a-8e99-41d5-9b35-4970e27baa5e
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=d6a28e3a-8e99-41d5-9b35-4970e27baa5e ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		d6a28e3a-8e99-41d5-9b35-4970e27baa5e
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=d6a28e3a-8e99-41d5-9b35-4970e27baa5e ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		d6a28e3a-8e99-41d5-9b35-4970e27baa5e
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=d6a28e3a-8e99-41d5-9b35-4970e27baa5e ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		d6a28e3a-8e99-41d5-9b35-4970e27baa5e
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=d6a28e3a-8e99-41d5-9b35-4970e27baa5e ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		d6a28e3a-8e99-41d5-9b35-4970e27baa5e
kernel		/boot/memtest86+.bin
quiet

title           Microsoft Windows XP Home Edition
root            (hd0,1)
savedefault
makeactive
chainloader+1
### END DEBIAN AUTOMAGIC KERNELS LIST


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=d6a28e3a-8e99-41d5-9b35-4970e27baa5e /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=653cf32e-c190-4741-8aeb-d2f9e592445b none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .4GB: boot/grub/menu.lst
  21.0GB: boot/grub/stage2
  21.1GB: boot/initrd.img-2.6.28-11-generic
  21.0GB: boot/initrd.img-2.6.28-13-generic
  21.0GB: boot/initrd.img-2.6.28-14-generic
  21.0GB: boot/vmlinuz-2.6.28-11-generic
  21.0GB: boot/vmlinuz-2.6.28-13-generic
  21.1GB: boot/vmlinuz-2.6.28-14-generic
  21.0GB: initrd.img
  21.0GB: initrd.img.old
  21.1GB: vmlinuz
  21.0GB: vmlinuz.old

================================ sda2/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 

```

there you go.

---

### Post by merlinus on 2009-08-08
Move this:

title           Microsoft Windows XP Home Edition
root            (hd0,1)
savedefault
makeactive
chainloader+1

to below:

### END DEBIAN AUTOMAGIC KERNELS LIST

You also might change

root (hd0,1)

to

rootnoverify (hd0,1)

and restart.

It also looks like you have to press Esc very quickly in order for the grub menu to appear.  This can be changed by placing a hashmark (#) in front of 

hiddenmenu

Finally, exactly what did you do to reinstall grub?

---

### Post by louieb on 2009-08-08
What you did looks good to me.
Just a couple of changes to suggest. What you did should have worked.
Change root to rootnoverify - makes grub skip  some checks
**put a space between chainloader and the +1**
 Just tried the chainloader command without the space  - lol my laptops screen when blank and rebooted.  Learn something new everyday.

```

title           Microsoft Windows XP Home Edition
rootnoverify (hd0,1)
savedefault
makeactive
chainloader +1

```oh and glad merlinus caught that - do move the entry and change the hiddenmenu option as he suggested.

---

### Post by OrangeCrush112 on 2009-08-08
Thanks a lot guys!

your suggestions worked.

Merlinus, I reinstalled grub using the Live CD method.

---

