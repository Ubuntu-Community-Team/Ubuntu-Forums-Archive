---
title: "Vista Hates my Linux"
date: 2009-04-10
forum: Installation &amp; Upgrades
---

### Post by gumbyiscool on 2009-04-10
Ok so here it goes. I have one hard drive (320gig). I went into liveCD of 8.1 64-bit and split the drive in half making one ntfs and one unallocated. I then Installed Vista premium 64-bit and booted into fine. I then was ready for Ubuntu. I went back to liveCD opened partition editor and proceeded with the other half of my drive I made into my swap (8gig) and the rest I made ext3. I installed my Ubuntu (ext3 making /) just like I have done before. Hoping Grub would take over and when I restarted I booted right into Vista. I went back to LiveCD and tried moving my boot flag (which was on vista still) to linux and when I restarted it said no operating system. I also tried moving the flag to the swap partition and same thing came up. As soon as I put the boot flag back on vista it boots up into vista. I have now deleted the partitions and added them to Vista's HD. Im hoping someone can help me out. Vista is angry with me :( I just want my Linux

---

### Post by meierfra. on 2009-04-10
Seems grub did not get installed.
In order to get a clearer picture of your setup, I suggest to boot  from the Ubuntu LiveCD and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post (use the code tags)

---

### Post by gumbyiscool on 2009-04-10
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00057fcd

Partition  Boot         Start           End          Size  Id System



Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9c119c11

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   250,822,844   250,822,782   7 HPFS/NTFS
/dev/sdb2         250,822,845   267,209,144    16,386,300  82 Linux swap / Solaris
/dev/sdb3         267,209,145   488,392,064   221,182,920  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sdb1: UUID="20B5143F7990DA34" TYPE="ntfs" 
/dev/sdb2: UUID="e917e033-129d-4491-a143-0e41809e035b" TYPE="swap" 
/dev/sdb3: UUID="7deb4301-0e08-4c3f-a022-aa5b0217c715" SEC_TYPE="ext2" TYPE="ext3" 
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
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


=========================== sdb3/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=7deb4301-0e08-4c3f-a022-aa5b0217c715 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7deb4301-0e08-4c3f-a022-aa5b0217c715

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
uuid		7deb4301-0e08-4c3f-a022-aa5b0217c715
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=7deb4301-0e08-4c3f-a022-aa5b0217c715 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		7deb4301-0e08-4c3f-a022-aa5b0217c715
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=7deb4301-0e08-4c3f-a022-aa5b0217c715 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		7deb4301-0e08-4c3f-a022-aa5b0217c715
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


=============================== sdb3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb3
UUID=7deb4301-0e08-4c3f-a022-aa5b0217c715 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb2
UUID=e917e033-129d-4491-a143-0e41809e035b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb3: Location of files loaded by Grub: ===================


 246.6GB: boot/grub/menu.lst
 246.7GB: boot/grub/stage2
 246.7GB: boot/initrd.img-2.6.27-7-generic
 246.6GB: boot/vmlinuz-2.6.27-7-generic
 246.7GB: initrd.img
 246.6GB: vmlinuz


I hope this helps.....

---

### Post by gumbyiscool on 2009-04-10
This help?

---

### Post by meierfra. on 2009-04-10
> I have one hard drive (320gig).

This does not match  the results of the boot info script:

> Disk /dev/sda: 640.1 GB, 
Disk /dev/sdb: 250.0 GB, 

Anyway, it seem Grub is correctly configured to boot of the 640GB drive.

So I suggested to set you bios to boot from  640GB drive. Then you should get the grub menu and should be able to choose between Ubuntu and Vista.

But if you prefer, I can show you how to install Grub the the MBR of your Vista/Ubuntu drive.

---

### Post by gumbyiscool on 2009-04-10
see whats weird is that linux is seeing my 640gig HD as my main but its not suppose to be. I wanted to split the small one and use the larger one for storage for both. So your saying it saying my grub in on my 640gig? how can that be when its unallocated?

---

### Post by meierfra. on 2009-04-10
> So your saying it saying my grub in on my 640gig? 
Yes. More precisely one small part is on the 640gig.  The main part is on the 250gig.


> how can that be when its unallocated?
Grubs is located in extended MBR (the first 63 sector of the hard drive).  The extended MBR comes before any partitions and it does not matter to grub whether the drive is formated or not.

---

### Post by gumbyiscool on 2009-04-10
I have my 250 as boot already is why im asking. What should I do?

---

### Post by meierfra. on 2009-04-10
> I have my 250 as boot already is why im asking. What should I do?

What did you mean with  "have my 250 as boot" ( boot flags are irrelevant if you use grub for booting)

Do your bios allow you  change the boot priority order? If yes, just make sure that the 640 gig is listed before the 250  gig in the bios.


But if you prefer to not mess with your bios, just install grub to the MBR of the 250 gig:

Boot from the Ubuntu Live CD, open a terminal  and type

```
sudo grub
```

and at the grub prompt:


```
root (hd1,2)
setup (hd1)
quit
```


Reboot and see whether you can boot into Ubuntu.

---

### Post by gumbyiscool on 2009-04-10
Ok I will do this...what Im saying is that before I installed anything I made sure that my 250gig is first to boot before the 640gig

---

### Post by gumbyiscool on 2009-04-10
not flag i mean i changed it in bios

---

### Post by meierfra. on 2009-04-10
> I made sure that my 250gig is first to boot before the 640gig

But Ubuntu has no knowledge of the boot order in the bios and put Grub onto the 640 gig.


So you now have two options

1) Change the boot order in the bios so that the  640 gig is before  250 gig 

or

2)  Follow  my instructions from my previous post and install grub to the MBR of the 250gig.

---

### Post by gumbyiscool on 2009-04-10
maybe I should have went with option 1

Grub is now found and Im able to boot into my linux but, When I try to boot into windows(longhorn boot loader) it says "error 22:no such partition press any key to continue" 

What now?

---

### Post by meierfra. on 2009-04-10
> What now?
You need to edit menu.lst.

Open a terminal in Ubuntu and type

```
gksudo gedit /boot/grub/menu.lst
```
This open the file "menu.lst"

Change

title Windows Vista/Longhorn (loader)
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1


to 

title  Windows Vista
rootnoverify  (hd0,0)
chainloader +1

Save the file and you should be able to boot into Vista

---

### Post by gumbyiscool on 2009-04-10
That done the trick...thanks so much..cant thank you enough

---

### Post by meierfra. on 2009-04-10
> That done the trick.
Great.  Have fun with Vista and Ubuntu

---

