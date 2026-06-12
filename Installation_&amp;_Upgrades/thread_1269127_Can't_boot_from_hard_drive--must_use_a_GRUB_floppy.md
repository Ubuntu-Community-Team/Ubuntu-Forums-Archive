---
title: "Can't boot from hard drive--must use a GRUB floppy to point to kernel.  Suggestions?"
date: 2009-09-17
forum: Installation &amp; Upgrades
---

### Post by KillrBuckeye on 2009-09-17
I'm running Ubuntu on an old P3 rig that serves as my home file server and http server.  It has been running great for 3 years.  The only catch?  I can only load the kernel image by booting from a GRUB floppy (or a Live CD) and then pointing to the image on the hard drive.  For some reason, GRUB won't load from the hard drive, and instead I get this error:

DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER

I've tried putting the hard drive at various places in the boot priority list in the BIOS setup and it doesn't make a difference.  Now at one point, this system was booting fine from the hard drive.  The trouble started when I downloaded a new kernel image over 3 years ago, and GRUB started giving me an error saying that the BIOS couldn't read past cylinder XXX on the hard drive.  I ended up having to make a small /boot partition at the beginning of the disk and rearranging my partitions to solve this.  However, ever since then I haven't been able to boot from the hard drive.

At one point, I attached the hard drive to a more modern computer, and GRUB booted fine from the hard drive.  This leads me to believe that this old P3 rig is having problems dealing with the partition structure on the hard drive.  I've read that some older computers have trouble dealing with extended partitions.  Does this sound reasonable to anyone?

Here is the output of the Boot Info Script that I found by searching the forums:
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/hda and looks on the same drive 
    in partition #1 for /grub/stage2 and /grub/menu.lst.

hda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

hda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 6.06.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

hda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

hda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

hda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

hda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: hda ___________________ _____________________________________________________

Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/hda1                  63       819,314       819,252  83 Linux
/dev/hda2             819,315    31,535,594    30,716,280  83 Linux
/dev/hda3          31,535,595    33,077,834     1,542,240  82 Linux swap / Solaris
/dev/hda4          33,077,835   463,153,949   430,076,115   5 Extended
/dev/hda5          33,077,898    53,560,709    20,482,812  83 Linux
/dev/hda6          53,560,773   463,153,949   409,593,177  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/hda1: UUID="5bb7fb2a-d117-4bd7-b7d4-42bead0d36dd" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda2: UUID="387f4854-fa08-4530-8435-33d9d597db33" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda3: TYPE="swap" 
/dev/hda5: UUID="699edeec-4253-4972-8c67-42f34795d950" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda6: UUID="67501e19-f226-4465-afde-dca4a822cfe0" SEC_TYPE="ext2" TYPE="ext3" 
/dev/evms/hda1: UUID="5bb7fb2a-d117-4bd7-b7d4-42bead0d36dd" SEC_TYPE="ext2" TYPE="ext3" 
/dev/evms/hda2: UUID="387f4854-fa08-4530-8435-33d9d597db33" SEC_TYPE="ext2" TYPE="ext3" 
/dev/evms/hda3: TYPE="swap" 
/dev/evms/hda5: UUID="699edeec-4253-4972-8c67-42f34795d950" SEC_TYPE="ext2" TYPE="ext3" 
/dev/evms/hda6: UUID="67501e19-f226-4465-afde-dca4a822cfe0" SEC_TYPE="ext2" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/hda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-26-386/volatile type tmpfs (rw)
/dev/hda1 on /boot type ext3 (rw)
/dev/hda5 on /home type ext3 (rw)
/dev/hda6 on /share type ext3 (rw,noexec,nosuid,nodev)


============================= hda1/grub/menu.lst: =============================

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=/dev/hda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-28-386
root		(hd0,0)
kernel		/vmlinuz-2.6.15-28-386 root=/dev/hda2 ro quiet splash
initrd		/initrd.img-2.6.15-28-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.15-28-386 root=/dev/hda2 ro single
initrd		/initrd.img-2.6.15-28-386
boot

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,0)
kernel		/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro quiet splash
initrd		/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro single
initrd		/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro quiet splash
initrd		/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro single
initrd		/initrd.img-2.6.15-26-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,0)
kernel		/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro quiet splash
initrd		/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro single
initrd		/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

=================== hda1: Location of files loaded by Grub: ===================


    .3GB: grub/menu.lst
    .3GB: grub/stage2
    .0GB: initrd.img-2.6.15-23-386
    .0GB: initrd.img-2.6.15-26-386
    .0GB: initrd.img-2.6.15-27-386
    .0GB: initrd.img-2.6.15-28-386
    .0GB: vmlinuz-2.6.15-23-386
    .0GB: vmlinuz-2.6.15-26-386
    .0GB: vmlinuz-2.6.15-27-386
    .0GB: vmlinuz-2.6.15-28-386

=========================== hda2/boot/grub/menu.lst: ===========================

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=/dev/hda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-28-386
root		(hd0,0)
kernel		/vmlinuz-2.6.15-28-386 root=/dev/hda2 ro quiet splash
initrd		/initrd.img-2.6.15-28-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.15-28-386 root=/dev/hda2 ro single
initrd		/initrd.img-2.6.15-28-386
boot

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,0)
kernel		/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro quiet splash
initrd		/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro single
initrd		/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro quiet splash
initrd		/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro single
initrd		/initrd.img-2.6.15-26-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,0)
kernel		/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro quiet splash
initrd		/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro single
initrd		/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== hda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /boot           ext3    defaults        0       2
/dev/hda5       /home           ext3    defaults        0       2
/dev/hda6	/share	        ext3    defaults,user   0       0
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

=================== hda2: Location of files loaded by Grub: ===================


    .7GB: boot/grub/menu.lst
    .7GB: boot/grub/stage2
    .4GB: boot/initrd.img-2.6.15-23-386
    .4GB: boot/initrd.img-2.6.15-26-386
    .4GB: boot/initrd.img-2.6.15-27-386
    .4GB: boot/initrd.img-2.6.15-28-386
    .4GB: boot/vmlinuz-2.6.15-23-386
    .4GB: boot/vmlinuz-2.6.15-26-386
    .4GB: boot/vmlinuz-2.6.15-27-386
    .4GB: boot/vmlinuz-2.6.15-28-386
    .4GB: initrd.img
    .4GB: initrd.img.old
    .4GB: vmlinuz
    .4GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

hdc 

```

The motherboard is an Asus model from an OEM HP machine.  The BIOS has been updated to the latest version I can find.  Am I out of luck unless I start from scratch?  I'd hate to have to reinstall since I have everything working the way I want it to right now.

Any help you can provide would be appreciated.

EDIT:  Here's a screenshot from GParted that makes it easier to understand my partition structure:
[IMG]http://i7.photobucket.com/albums/y299/KillrBuckeye/Ubuntu-PIII_GParted_SS.jpg[/IMG]

hda1 is /boot
hda2 is /
hda3 is swap
hda4 defines the extended partition
hda5 is /home
had6 is a large share partition

---

### Post by louieb on 2009-09-17
> DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER
 Thats the message I would expect to see if I asked the PC to boot from CD and there was a music CD in the drive. Or boot from floppy and the floppy was not boot-able. 

but your hard drive has bootable code in the MBR
> => Grub0.97 is installed in the MBR of /dev/hda and looks on the same drive 
    in partition #1 for /grub/stage2 and /grub/menu.lst.Just wondering does the boot floppy have a menu.lst or grub.conf file? might be good to take a look at it.

> 
At one point, I attached the hard drive to a more modern computer, and [COLOR=Red]GRUB booted [/COLOR]fine from the hard drive. This leads me to believe that this old P3 rig is having problems dealing with the partition structure on the hard drive.[COLOR=Red] I've read that some older computers have trouble dealing with extended partitions.[/COLOR] Does this sound reasonable to anyone?
Not really.  Your partition structure looks well thought out.  I have an P2 built around 1997.  It would refuse to boot when a hard drive larger that 30 GB was installed. (A BIOS update fixed that) But it had  no problems with extended partitions. 

But I am curious - even though Linux does not need a boot flag - just wonder about your PC BIOS -  It would not hurt to set the boot flag to on for partition hda1.  

Have you checked to see if there is a BIOS update for your motherboard?

---

### Post by KillrBuckeye on 2009-09-18
> **louieb said:**
> but your hard drive has bootable code in the MBR
Just wondering does the boot floppy have a menu.lst or grub.conf file? might be good to take a look at it.Yes, GRUB is installed on the floppy and loads menu.lst from the floppy.  Here is the menu.lst file on the floppy:

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=/dev/hda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro quiet splash
initrd		/initrd.img-2.6.15-26-386
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro single
initrd		/initrd.img-2.6.15-26-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,0)
kernel		/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro quiet splash
initrd		/initrd.img-2.6.15-23-386
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro single
initrd		/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

```

> **louieb said:**
> Not really.  Your partition structure looks well thought out.  I have an P2 built around 1997.  It would refuse to boot when a hard drive larger that 30 GB was installed. (A BIOS update fixed that) But it had  no problems with extended partitions. 

But I am curious - even though Linux does not need a boot flag - just wonder about your PC BIOS -  It would not hurt to set the boot flag to on for partition hda1.  

Have you checked to see if there is a BIOS update for your motherboard?Could you explain what you mean by boot flag in the BIOS?  I don't recall seeing anything about a boot flag in the BIOS setup.  Where would this typically be?

Unfortunately, the motherboard in this computer (Asus CUV-NT) is from an OEM HP machine, and I can't seem to find an updated BIOS.

---

### Post by KillrBuckeye on 2009-09-18
BUMP

Anybody?  I actually did manage to flash the BIOS on the motherboard to the latest version, and the behavior is still the same.  I also tried plugging in the HDD to secondary IDE channel to no avail.  I still need that GRUB floppy in order to boot.

---

### Post by louieb on 2009-09-18
What i mean is BIOS may be looking for a partition that has the boot flag turned on. Just a shot in the dark really.

You can use Gparted to set the boot flag - Right click on hda1 > manage flags.  Just check mark the boot flag and apply.  Probably going to have run Gparted from the live CD.  

Something changed when you had to add the /boot partition to get around the GRUB error 18. Just wondering if the boot flag getting turned off was it.

---

### Post by KillrBuckeye on 2009-09-18
louieb, you are a GENIUS!  I enabled the boot flag for partition hda1 and this solved the problem!  Goodbye GRUB floppy!  You will not be missed.

Just a note for anyone who might reference this thread:  I did have to download and burn the .iso for 9.04 to run an updated version of GParted, because the version that comes bundled with 6.06 doesn't have the "Manage Flags" capability.  

Thanks so much louieb!  I was about to give up.

---

### Post by louieb on 2009-09-19
Thanks for the kind words. "Even a blind squirrel finds a nut every now and then."

---

### Post by Pxonix on 2009-09-19
just boot adn run gparted. roght click on any partition (ex. swap) and click Edit Flags, then jus check the flag "boot" and save. computer must reboot normaly.

---

