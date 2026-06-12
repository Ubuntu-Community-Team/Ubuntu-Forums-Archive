---
title: "Grub error 18"
date: 2009-10-18
forum: Installation &amp; Upgrades
---

### Post by Hyrum on 2009-10-18
I just installed Ubuntu on the extra space on my laptop for the first time. I thought that I would be able to boot into ubuntu or windows but when I start my computer it just says "grub error 18". I searched the forum for someone with a similar problem (error 17) but those fixes didn't do anything. I posted in that thread but nobody responded. I think its just too old and people aren't looking there.
In that post I found, the guy with the problem was asked to run a script that gets boot info. I ran the script and you can see below what I got. 

My computer is a Dell D600 with a 160 GB IDE HD. Its a very popular model so I'm surprised I'm the only one with this problem.

Please Help!

Thanks,
Hyrum

> ============================= Boot Info Summary: ==============================

=> Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive
in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: __________________________________________________ _______________________

File system: vfat
Boot sector type: Dell Utility: Fat16
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files/dirs:

sda2: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows XP
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows XP
Boot files/dirs: /boot.ini /ntldr /NTDETECT.COM

sda3: __________________________________________________ _______________________

File system: Extended Partition
Boot sector type: -
Boot sector info:

sda5: __________________________________________________ _______________________

File system: ext3
Boot sector type: -
Boot sector info:
Operating System: Ubuntu 9.04
Boot files/dirs: /boot/grub/menu.lst /etc/fstab

sda6: __________________________________________________ _______________________

File system: swap
Boot sector type: -
Boot sector info:

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ __________________________________________________ ___

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb08bb08b

Partition Boot Start End Size Id System

/dev/sda1 63 112,454 112,392 de Dell Utility
/dev/sda2 * 112,455 269,040,554 268,928,100 7 HPFS/NTFS
/dev/sda3 269,040,555 312,576,704 43,536,150 5 Extended
/dev/sda5 269,040,618 310,681,034 41,640,417 83 Linux
/dev/sda6 310,681,098 312,576,704 1,895,607 82 Linux swap / Solaris


blkid -c /dev/null: __________________________________________________ __________

/dev/loop0: TYPE="squashfs"
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D4-090A" TYPE="vfat"
/dev/sda2: UUID="9E84E65C84E63705" TYPE="ntfs"
/dev/sda5: UUID="76b08d64-1f33-46d2-8010-fecf08c3716c" TYPE="ext3"
/dev/sda6: UUID="755f2571-fd37-4f84-9e37-b6c08d806cb3" TYPE="swap"
/dev/ramzswap0: TYPE="swap"

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda2 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5 on /media/disk-1 type ext3 (rw,nosuid,nodev,uhelper=hal)


================================ sda2/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOW S



[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Micro soft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda5/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(, info grub, update-grub(
# grub-install(, grub-floppy(,
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=76b08d64-1f33-46d2-8010-fecf08c3716c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=76b08d64-1f33-46d2-8010-fecf08c3716c

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
## indomU=true
## indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title Ubuntu 9.04, kernel 2.6.28-11-generic
uuid 76b08d64-1f33-46d2-8010-fecf08c3716c
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=76b08d64-1f33-46d2-8010-fecf08c3716c ro quiet splash
initrd /boot/initrd.img-2.6.28-11-generic
quiet

title Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid 76b08d64-1f33-46d2-8010-fecf08c3716c
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=76b08d64-1f33-46d2-8010-fecf08c3716c ro single
initrd /boot/initrd.img-2.6.28-11-generic

title Ubuntu 9.04, memtest86+
uuid 76b08d64-1f33-46d2-8010-fecf08c3716c
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title Microsoft Windows XP Professional
rootnoverify (hd0,1)
savedefault
makeactive
chainloader +1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# / was on /dev/sda5 during installation
UUID=76b08d64-1f33-46d2-8010-fecf08c3716c / ext3 relatime,errors=remount-ro 0 1
# swap was on /dev/sda6 during installation
UUID=755f2571-fd37-4f84-9e37-b6c08d806cb3 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

=================== sda5: Location of files loaded by Grub: ===================


140.5GB: boot/grub/menu.lst
140.4GB: boot/grub/stage2
140.4GB: boot/initrd.img-2.6.28-11-generic
140.4GB: boot/vmlinuz-2.6.28-11-generic
140.4GB: initrd.img
140.4GB: vmlinuz 

---

### Post by louieb on 2009-10-18
How old is the laptop? Have you looked to see if there is a BIOS update. That might be the easiest fix. The other involves creating a boot partition close enough to the start of the disk for BIOS to be able to address it. 

Older BIOS have a 132 GB limit on how far from the start of the disk they can boot. Really old BIOS have even an lower limit. Looks like your Ubuntu install is to far from the start of the disk. 

```

=================== sda5: Location of files loaded by Grub: 
140.5GB: boot/grub/menu.lst
140.4GB: boot/grub/stage2
140.4GB: boot/initrd.img-2.6.28-11-generic
140.4GB: boot/vmlinuz-2.6.28-11-generic
140.4GB: initrd.img
140.4GB: vmlinuz 			 		

```

From the [GNU GRUB Manual 0.97]("http://www.gnu.org/software/grub/manual/grub.html")

> 
18 : Selected cylinder exceeds maximum supported by BIOSThis error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general).Don't

---

### Post by raymondh on 2009-10-18
> **louieb said:**
> How old is the laptop? Have you looked to see if there is a BIOS update. That might be the easiest fix. The other involves creating a boot partition close enough to the start of the disk for BIOS to be able to address it. 

Older BIOS have a 132 GB limit on how far from the start of the disk they can boot. Really old BIOS have even an lower limit. Looks like your Ubuntu install is to far from the start of the disk. 

```

=================== sda5: Location of files loaded by Grub: 
140.5GB: boot/grub/menu.lst
140.4GB: boot/grub/stage2
140.4GB: boot/initrd.img-2.6.28-11-generic
140.4GB: boot/vmlinuz-2.6.28-11-generic
140.4GB: initrd.img
140.4GB: vmlinuz 			 		

```

From the [GNU GRUB Manual 0.97]("http://www.gnu.org/software/grub/manual/grub.html")

Don't

+1

As LouieB mentioned .... the idea is to install the kernel within the limit (usually within 137GB).  I had a 98-vintage desktop that had the 8GB limit.  On a 2002-vintage, I found success at about 100GB.

Another workaround is to install a /boot in front of the drive (which usually takes about 250mb).  That however will depend on other factors ie. how may primary partitions you have already, etc.

Try to install within/inside 137gb.  If that does not work, we can work on creating a /boot partition.

Back-up your files, too.

Regards,

---

### Post by Hyrum on 2009-10-25
Yes, that was the problem. I reinstalled linux and only used the first 137 gb and it fixed it. There were no bios updates available. Thanks!

---

### Post by raymondh on 2009-10-26
> **Hyrum said:**
> Yes, that was the problem. I reinstalled linux and only used the first 137 gb and it fixed it. There were no bios updates available. Thanks!

glad to hear you got it fixed.  happy ubuntu-ing.

---

