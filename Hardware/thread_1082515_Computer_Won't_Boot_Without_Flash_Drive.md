---
title: "Computer Won't Boot Without Flash Drive"
date: 2009-02-27
forum: Hardware
---

### Post by north.cascades on 2009-02-27
I recently installed Ubuntu 7.10 off a live CD onto a flash drive to use for work.  The new OS works great when I boot to it.

Trouble is that when I remove the flash drive, I can't boot my computer to either my Ubuntu Intrepid or Windows Vista partitions...all it does is say something to the effect of "Grub loading, please wait" and then gives Error 21.  I can't get to Windows or Intrepid.

When I insert the USB drive (a simple Sandisk Cruzer), I can boot to either it, Intrepid, or Vista, but I can't do this if I take it out.

I need to have my personal computer back - I have to be able to boot without this flash drive plugged in!  What can I do?

---

### Post by sgosnell on 2009-02-27
When you did the install, you should have had grub put onto the flash drive, not the HDD.  Have you tried going into the BIOS before the boot starts, and making the first boot drive the HD?  That usually works for me.

---

### Post by caljohnsmith on 2009-02-28
I think you will find the solution to your problem in either of these threads:

[http://ubuntuforums.org/showthread.php?p=6665548](http://ubuntuforums.org/showthread.php?p=6665548)
[http://ubuntuforums.org/showthread.php?p=6452340](http://ubuntuforums.org/showthread.php?p=6452340)

Let me know how that goes or if you run into problems.

---

### Post by north.cascades on 2009-02-28
Thanks!  I can now boot straight to Windows.

If you can tell me how to either get into Intrepid (I've tried F8 and F12...they don't seem to do anything other than enter BIOS) or remove/erase the Intrepid partition and use that free space for Vista, that would be outstanding.

'preciate it.

---

### Post by caljohnsmith on 2009-03-01
It would help to get a clearer picture of your setup first, so how about downloading the **Boot Info Script** to your Ubuntu Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

---

### Post by north.cascades on 2009-03-02
Here 'tis.

```

============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda2': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda2 sda2 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda2 sda2 ntfs-3g defaults,force 0 0
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda2': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda2 sda2 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda2 sda2 ntfs-3g defaults,force 0 0

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7776c59a

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    13,916,159    13,914,112  27 Hidden HPFS/NTFS
/dev/sda2    *     13,916,160   221,179,831   207,263,672   7 HPFS/NTFS
/dev/sda4         221,190,480   234,435,599    13,245,120   5 Extended
/dev/sda5         233,755,263   234,435,599       680,337  82 Linux swap / Solaris
/dev/sda6         221,190,606   230,942,879     9,752,274  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="9076637E76636446" LABEL="ServiceV002" TYPE="ntfs" 
/dev/sda2: UUID="28F26805F267D61A" LABEL="Lenovo" TYPE="ntfs" 
/dev/sda5: UUID="0ba61154-769b-42ab-9d7e-fabccd2607f1" TYPE="swap" 
/dev/sda6: UUID="af205766-4764-4a67-b0c2-b0f8462e77c6" SEC_TYPE="ext2" TYPE="ext3" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)


=========================== sda6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=af205766-4764-4a67-b0c2-b0f8462e77c6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=af205766-4764-4a67-b0c2-b0f8462e77c6 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=af205766-4764-4a67-b0c2-b0f8462e77c6 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=af205766-4764-4a67-b0c2-b0f8462e77c6 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=af205766-4764-4a67-b0c2-b0f8462e77c6 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.24-23-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=af205766-4764-4a67-b0c2-b0f8462e77c6 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=af205766-4764-4a67-b0c2-b0f8462e77c6 ro  single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.10, kernel 2.6.22-14-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=af205766-4764-4a67-b0c2-b0f8462e77c6 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=af205766-4764-4a67-b0c2-b0f8462e77c6 ro  single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,5)
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


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=af205766-4764-4a67-b0c2-b0f8462e77c6 /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/sda1
UUID=9076637E76636446 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=28F26805F267D61A /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=0ba61154-769b-42ab-9d7e-fabccd2607f1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

=================== sda6: Location of files loaded by Grub: ===================


 114.5GB: boot/grub/menu.lst
 114.5GB: boot/grub/stage2
 114.6GB: boot/initrd.img-2.6.22-14-generic
 114.4GB: boot/initrd.img-2.6.22-14-generic.bak
 114.8GB: boot/initrd.img-2.6.24-23-generic
 114.4GB: boot/initrd.img-2.6.24-23-generic.bak
 115.2GB: boot/initrd.img-2.6.27-11-generic
 116.9GB: boot/initrd.img-2.6.27-9-generic
 114.4GB: boot/vmlinuz-2.6.22-14-generic
 114.5GB: boot/vmlinuz-2.6.24-23-generic
 115.2GB: boot/vmlinuz-2.6.27-11-generic
 114.9GB: boot/vmlinuz-2.6.27-9-generic
 115.2GB: initrd.img
 116.9GB: initrd.img.old
 115.2GB: vmlinuz
 114.9GB: vmlinuz.old
```

---

### Post by caljohnsmith on 2009-03-02
OK, how about doing:
```
sudo grub
grub> root (hd0,5)
grub> setup (hd0)
grub> quit
```
Reboot, and let me know if you can boot OK into Ubuntu and Vista again.

---

### Post by north.cascades on 2009-03-02
It worked!  Thanks so much for your help.

Do you know if there's anything I could have done to prevent this from happening?  All I did was use the live CD to install 7,1 to a USB drive...perhaps I should have disconnected my internal HDD before doing the install?

---

### Post by caljohnsmith on 2009-03-02
> **north.cascades said:**
> 
Do you know if there's anything I could have done to prevent this from happening? 
Sure, just click the "Advanced" button near the end of the installation process, and there you can specify where Grub is installed to. You would want to specify "/dev/sdb" or whichever is the drive you are installing Ubuntu to. Anyway, glad you can boot Ubuntu and Windows again; cheers and enjoy your dual-boot setup. :)

---

### Post by north.cascades on 2009-03-02
Sweet :)

---

