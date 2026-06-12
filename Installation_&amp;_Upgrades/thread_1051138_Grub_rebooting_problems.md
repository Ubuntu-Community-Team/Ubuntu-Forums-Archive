---
title: "Grub rebooting problems"
date: 2009-01-26
forum: Installation &amp; Upgrades
---

### Post by GoldenCypress on 2009-01-26
Dear Community,

I was searching unsuccessfully for a solution to my grub problem and I hope I can find help here because I am running out of ideas!

I have got windows xp and ubuntu 8.10 installed on one computer and am using grub to boot into one of the OS.
Ubuntu is on (hd0,1) and XP is on (hd0,3).
The situation is:
Lets say I am trying to get onto Ubuntu. Grub starts to load the kernel and such, but reboots the computer one second after starting to load.
When I end up in grub yet again and am choosing ubuntu, grub loads ubuntu perfectly fine and everything is working...as long as I am not trying to get into windows. If I do, grub is playing the same game. gets windows to load for a second, computer reboots itself and I end up in grub. Now when I choose windows again, I finally end up in windows. if I choose ubuntu though, the computer reboots after I have chosen ubuntu.

I hope this makes sense. I can work on both OS if I finally get into one, but since I am switching the OS quite often, I would like to have grub working without any reboot problems - if this is possible.

I have tried to reinstall grub several times, which did not fix my problem.
Have you got any other ideas?
I really would appreciate that!

Thank you in advance!

---

### Post by lha on 2009-02-03
Hi,

Could you post the output of the [Boot Info Script]("http://bootinfoscript.sourceforge.net/")? It gathers a lot of booting-related info that might help in finding the cause of your problem.

---

### Post by GoldenCypress on 2009-02-03
THank you a lot for replying!

Sure, the output is (sda2 and sda4 are both the operating systems, the other partitions are non bootable):

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub is installed in the boot sector of sda1 and looks 
                       at sector 66351874 of the same hard drive for the 
                       stage2 file, but no stage2 files can be found at this 
                       location.
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda2 and 
                       looks at sector 70295602 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #2 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x828f7bba

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    20,973,567    20,971,520  27 Unknown
/dev/sda2          20,980,890    79,569,944    58,589,055  83 Linux
/dev/sda3          79,569,945   161,485,379    81,915,435   f W95 Ext d (LBA)
/dev/sda5          79,570,008   161,485,379    81,915,372   7 HPFS/NTFS
/dev/sda4    *    586,067,265   625,137,344    39,070,080   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda2: UUID="6cad96f6-cc11-46fc-8f52-12ec834d8483" TYPE="ext3" 
/dev/sda4: UUID="FCD045C1D04582BE" TYPE="ntfs" 
/dev/sda5: UUID="02E4345CE434545F" LABEL="Multimedia" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
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
/dev/sda5 on /media/Multimedia type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/username/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=username)

=========================== sda2/boot/grub/menu.lst: ===========================

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=6cad96f6-cc11-46fc-8f52-12ec834d8483 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=6cad96f6-cc11-46fc-8f52-12ec834d8483

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=false

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=

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
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10
#, kernel 2.6.27-11-generic
uuid		6cad96f6-cc11-46fc-8f52-12ec834d8483
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=6cad96f6-cc11-46fc-8f52-12ec834d8483 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

#title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
#uuid		6cad96f6-cc11-46fc-8f52-12ec834d8483
#kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=6cad96f6-cc11-46fc-8f52-12ec834d8483 ro  single
#initrd		/boot/initrd.img-2.6.27-11-generic

#title		Ubuntu 8.10, kernel 2.6.27-9-generic
#uuid		6cad96f6-cc11-46fc-8f52-12ec834d8483
#kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=6cad96f6-cc11-46fc-8f52-12ec834d8483 ro quiet splash 
#initrd		/boot/initrd.img-2.6.27-9-generic
#quiet

#title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
#uuid		6cad96f6-cc11-46fc-8f52-12ec834d8483
#kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=6cad96f6-cc11-46fc-8f52-12ec834d8483 ro  single
#initrd		/boot/initrd.img-2.6.27-9-generic

#title		Ubuntu 8.10, kernel 2.6.27-7-generic
#uuid		6cad96f6-cc11-46fc-8f52-12ec834d8483
#kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=6cad96f6-cc11-46fc-8f52-12ec834d8483 ro quiet splash 
#initrd		/boot/initrd.img-2.6.27-7-generic
#quiet

#title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
#uuid		6cad96f6-cc11-46fc-8f52-12ec834d8483
#kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=6cad96f6-cc11-46fc-8f52-12ec834d8483 ro  single
#initrd		/boot/initrd.img-2.6.27-7-generic

#title		Ubuntu 8.10, memtest86+
#uuid		6cad96f6-cc11-46fc-8f52-12ec834d8483
#kernel		/boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title		Other operating systems:
#root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,3)
savedefault
chainloader	+1


=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda2 :
UUID=6cad96f6-cc11-46fc-8f52-12ec834d8483 / ext3 relatime,errors=remount-ro 0 1
/dev/sdb /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
/dev/sda5 /media/Multimedia ntfs-3g defaults,locale=en_GB.UTF-8 0 0

=================== sda2: Location of files loaded by Grub: ===================


  35.9GB: boot/grub/menu.lst
  35.9GB: boot/grub/stage2
  36.0GB: boot/initrd.img-2.6.27-11-generic
  36.0GB: boot/initrd.img-2.6.27-7-generic
  36.1GB: boot/initrd.img-2.6.27-9-generic
  36.1GB: boot/vmlinuz-2.6.27-11-generic
  35.9GB: boot/vmlinuz-2.6.27-7-generic
  35.9GB: boot/vmlinuz-2.6.27-9-generic
  36.0GB: initrd.img
  36.1GB: initrd.img.old
  36.1GB: vmlinuz
  35.9GB: vmlinuz.old

================================ sda4/boot.ini: ================================

[boot loader]

timeout=0

default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Pro" /fastdetect


=============================== StdErr Messages: ===============================

/home/username/Desktop/boot_info_script024.sh: line 1043: [: =: unary operator expected


Thank you very much once again for your help!

---

### Post by lha on 2009-02-05
Thank you for providing more information. Unfortunately, I couldn't locate the cause of your problems. I have some ideas that I'd try, but this situation seems a bit odd...

Have you ever had a correctly booting setup? Perhaps a Windows-only or Ubuntu-only installation?

Could make a floppy, cd, or usb-drive that boots grub, and use it to test if you can avoid the rebooting issue with it? For example, [Super Grub Disk]("http://www.supergrubdisk.org/") could be suitable for this task. (SGD doesn't support grub's uuid command, so you'll have to be a bit careful with it: First, it might not be a good idea to reinstall grub using SGD. Second, when booting with SGD, you'll have to substitute 'root (hd0,1)' for 'uuid 6cad96f6-cc11-46fc-8f52-12ec834d8483'.)

Other boot loaders might also be worth trying. E.g., lilo is in the repositories. Just be sure that you know how to reinstall grub if something goes wrong with lilo.

---

### Post by GoldenCypress on 2009-02-18
Thank you a lot lha!
Sorry it took me so long to reply!
I do not know what you mean by "correctly booting setup", but if you mean if my booting worked with one OS then yes, it did.
And I also had already a proper working dual boot system, it was on another machine though. 
I will try your valuable suggestions, at the moment I can not risk messing around with it though, but I will do so the moment I have got less work to do on the computer :)

Thank you very much once again! I will report back the moment I have done something in this direction and either succeeded or failed :)

---

### Post by lha on 2009-02-18
> **GoldenCypress said:**
> Thank you a lot lha!
Sorry it took me so long to reply!
You're welcome. Feel free to take all the time you need.

> **GoldenCypress said:**
> 
I do not know what you mean by "correctly booting setup", but if you mean if my booting worked with one OS then yes, it did.
That's what I meant. Was this one OS, with which booting worked, Windows? If yes, you might want to re-install Windows' boot loader and add Grub into it using [BootPart]("http://www.winimage.com/bootpart.htm").

---

