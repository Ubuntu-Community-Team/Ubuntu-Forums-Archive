---
title: "Installation Troubles"
date: 2009-10-13
forum: Installation &amp; Upgrades
---

### Post by chrisrabior on 2009-10-13
motherboard - AV49V v1.0  
Intel Celeron 2.00 GHz processor
2.5 GB Ram

I got tired of XP being so buggy, and I need a more stable system, so I'm jumping to Ubuntu.  I used the 7.04 distribution on an old laptop and it was awesome, so I didn't second guess switching the desktop over.

I have a few drives I'd like to have in it: 100, 120, 120 gigs.  Right now, for simplicity, only a single 120 gig drive is hooked up.  The other 120 is NTFS and filled with photos and mp3s, and the other 100 is the old XP drive which I plan on formatting once the system is up and running.

Tossed in the 7.04 disk (which came straight from Ubuntu).  The Live CD worked as expected, and I went through the installation to use the entire 120gig disk, everything went off without a hitch, but when I rebooted I got an error.
> DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER
So I tossed the Live CD back in, chose "boot from first hard disk" and get another error. 
> Booting from local disk...
isolinux: Disk error 05: AX = 0000, drive 80
Boot failed: press a key to retryI've experienced some issues with grub before, so I rebooted with the Live CD again, hit sourceforge for the bootinfoscript.
               > ============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/hda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/hdc

hda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 7.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

hda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

hda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: hda ___________________ _____________________________________________________

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/hda1    *             63   224,829,674   224,829,612  83 Linux
/dev/hda2         224,829,675   234,436,544     9,606,870   5 Extended
/dev/hda5         224,829,738   234,436,544     9,606,807  82 Linux swap / Solaris


Drive: hdc ___________________ _____________________________________________________
Note: sector size is 2048 (not 512)

Disk /dev/hdc: 732 MB, 732104704 bytes
255 heads, 63 sectors/track, 22 cylinders, total 357473 sectors
Units = sectors of 1 * 2048 = 2048 bytes

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found


blkid -c /dev/null: ____________________________________________________________

/dev/hda1: UUID="c6f4ad01-422e-4e1e-8d6e-e91ac1dd3142" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda5: TYPE="swap" UUID="70550826-c519-4f84-a493-c063472efd8b" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw,mode=0755)
/dev/bus/usb on /proc/bus/usb type none (rw,bind)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)


=========================== hda1/boot/grub/menu.lst: ===========================

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=c6f4ad01-422e-4e1e-8d6e-e91ac1dd3142 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

## ## End Default Options ##

title        Ubuntu, kernel 2.6.20-15-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=c6f4ad01-422e-4e1e-8d6e-e91ac1dd3142 ro quiet splash
initrd        /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title        Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=c6f4ad01-422e-4e1e-8d6e-e91ac1dd3142 ro single
initrd        /boot/initrd.img-2.6.20-15-generic

title        Ubuntu, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== hda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=c6f4ad01-422e-4e1e-8d6e-e91ac1dd3142 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=70550826-c519-4f84-a493-c063472efd8b none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

=================== hda1: Location of files loaded by Grub: ===================


  85.6GB: boot/grub/menu.lst
  85.6GB: boot/grub/stage2
  85.6GB: boot/initrd.img-2.6.20-15-generic
  85.7GB: boot/initrd.img-2.6.20-15-generic.bak
  85.7GB: boot/vmlinuz-2.6.20-15-generic
  85.6GB: initrd.img
  85.7GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

hdd 
 I don't think I see any issues with the way grub is set up, so I'm at a bit of a loss.  The drive is relatively new, very low hours, very little use, and still running as quiet as the day I bought it.  I've also had the system setup previously as a dual boot, so I can't imagine there's anything wrong with the bios settings.  I checked anyways of course.

I'm miffed.  I'd use the latest disk, but my desktop is my burner.  I'm downloading it anyways, might try installing from an external drive with the hopes that the more recent version might more intelligently overcome whatever issues I'm having.  If anyone has any suggestions, I'm open to anything.

---

### Post by Muskegman on 2009-10-13
DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER , sounds to me like your BIOS is booting into an empty HD

---

### Post by chrisrabior on 2009-10-13
> **Muskegman said:**
> DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER , sounds to me like your BIOS is booting into an empty HD

If I boot from the Live CD, I can navigate the drive and everything is where it's supposed to be.  The partitioning is what I expected to see from the installation, the system files are all in place, I have a root and a home.  I can't figure out why it doesn't recognize any of it when it's booting, as this is the only HD installed.

---

### Post by chrisrabior on 2009-10-13
I'm now at a total loss.  I rebooted, and grub loaded fine.. but I didn't change anything that I'm aware of.  I burned a copy of the 9.04 version and I was going to boot with that, but was slow on putting the CD in, and it decided to boot 7.04 from the drive.

Somewhat freaky that it might be a hardware issue, but I think I'm set.  Would still like insight as to what may be causing this if anyone has any ideas.

---

### Post by chrisrabior on 2009-10-13
It appears that one of my IDE cables had a slight tear.  Oddly, not the cable that goes to the HD, but to the DVD drive.  Perhaps that was causing issues.

Used 7.04 to download the 9.04 .iso file, burned the CD, and installing the latest ubuntu version now.  Still no clue what was causing the disk to not be recognized, but I think the problem's subsided, so hopefully the 9.04 install will go better than the 7.04 did.

---

### Post by kammaui on 2009-10-14
hi chris
you are a guy who believes the line I'll still love you in the morning(ironic-smiley)
there is nothing easy or facile in ubuntu
the help pages are no doubt correct in their explanation however they are written by someone who lives &breathes computers-not your averages joe
the help pages do not explain but rather conveys to one the fact that one doesnt know jack.Ubuntu is for self flagellants-not a tool at all

---

