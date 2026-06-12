---
title: "Grub error 17 after fresh 9.04 install"
date: 2009-10-05
forum: Installation &amp; Upgrades
---

### Post by robtom on 2009-10-05
Hi, I've been attempting to install Ubuntu for the first time onto a freshly-partitioned SATA drive. After running the installer, I get grub error 17 on boot. I've tried reinstalling Ubuntu and reinstalling grub without results. I even tried installing Ubuntu onto my IDE drive in case I was mixed up with the boot order of the drives. I've attached Boot Info Script output, and I'd be grateful if you could help me troubleshoot.

Thanks,
Rob

*Edit *10:15pm EDT 6 Oct: Ran Boot Info Script again after reinstalling Ubuntu to obliterate menu.lst tinkering. Updated output below.

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00029f59

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   224,829,674   224,829,612  83 Linux
/dev/sda2         224,829,675   234,436,544     9,606,870   5 Extended
/dev/sda5         224,829,738   234,436,544     9,606,807  82 Linux swap / Solaris


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 100.2 GB, 100256292864 bytes
255 heads, 63 sectors/track, 12188 cylinders, total 195813072 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000044c4

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   187,767,719   187,767,657  83 Linux
/dev/sdb2         187,767,720   195,800,219     8,032,500   5 Extended
/dev/sdb5         187,767,783   195,800,219     8,032,437  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="32306f4c-abc9-4273-b324-f0167e595f2a" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="31d7f4ba-bc67-47f2-8f69-88283478fca7" TYPE="swap" 
/dev/sdb1: UUID="d8009050-87cd-4064-87d4-e77e5e070506" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="4e22872f-b78e-411d-aa40-8ed07ce70fc6" TYPE="swap" 

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
/dev/sr1 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# kopt=root=UUID=32306f4c-abc9-4273-b324-f0167e595f2a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=32306f4c-abc9-4273-b324-f0167e595f2a

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        32306f4c-abc9-4273-b324-f0167e595f2a
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=32306f4c-abc9-4273-b324-f0167e595f2a ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        32306f4c-abc9-4273-b324-f0167e595f2a
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=32306f4c-abc9-4273-b324-f0167e595f2a ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        32306f4c-abc9-4273-b324-f0167e595f2a
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sdb1)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=d8009050-87cd-4064-87d4-e77e5e070506 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sdb1)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=d8009050-87cd-4064-87d4-e77e5e070506 ro single 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Ubuntu 9.04, memtest86+ (on /dev/sdb1)
root        (hd1,0)
kernel        /boot/memtest86+.bin  
savedefault
boot


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
UUID=32306f4c-abc9-4273-b324-f0167e595f2a /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=31d7f4ba-bc67-47f2-8f69-88283478fca7 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   5.6GB: boot/grub/menu.lst
   5.7GB: boot/grub/stage2
   5.7GB: boot/initrd.img-2.6.28-11-generic
   5.7GB: boot/vmlinuz-2.6.28-11-generic
   5.7GB: initrd.img
   5.7GB: vmlinuz

=========================== sdb1/boot/grub/menu.lst: ===========================

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# kopt=root=UUID=d8009050-87cd-4064-87d4-e77e5e070506 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d8009050-87cd-4064-87d4-e77e5e070506

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        d8009050-87cd-4064-87d4-e77e5e070506
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=d8009050-87cd-4064-87d4-e77e5e070506 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        d8009050-87cd-4064-87d4-e77e5e070506
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=d8009050-87cd-4064-87d4-e77e5e070506 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        d8009050-87cd-4064-87d4-e77e5e070506
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda1)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=7beead92-6682-4877-871b-284e915791ef ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda1)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=7beead92-6682-4877-871b-284e915791ef ro single 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title        Ubuntu 9.04, memtest86+ (on /dev/sda1)
root        (hd0,0)
kernel        /boot/memtest86+.bin  
savedefault
boot


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=d8009050-87cd-4064-87d4-e77e5e070506 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=4e22872f-b78e-411d-aa40-8ed07ce70fc6 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  38.7GB: boot/grub/menu.lst
  38.7GB: boot/grub/stage2
  38.7GB: boot/initrd.img-2.6.28-11-generic
  38.7GB: boot/vmlinuz-2.6.28-11-generic
  38.7GB: initrd.img
  38.7GB: vmlinuz

```

---

### Post by louieb on 2009-10-06
looks like the install on sda should boot. 
The one on sdb looks like GRUB is looking at the wrong partition. (partition #2 is an extended one) - GRUB would give an error 17 on that one. 

Quick and easy way to get it straight is with a  [Super Grub Disk]("http://linux.softpedia.com/progDownload/Super-Grub-Disk-Download-8071.html")  
Its pretty simple to use - that is unless you have never used it so here is a pretty good guide [IDBS on SuperGrub]("http://members.iinet.net.au/%7Eherman546/SuperGrubDiskPage.html")

---

### Post by robtom on 2009-10-06
Thanks Louie, and thank you for the helpful link to the guide. I won't get a chance to run it until tonight, but sounds like it will do the trick and then some. I'll update the thread to let you know.

---

### Post by presence1960 on 2009-10-06
is your 100 GB disk booting first in BIOS hard disk boot order? If so your GRUB on that disk is pointing to the wrong partition, it is pointing to partition # 2- ubuntu is on partition #1.

you can try putting sda (120 GB) disk as first in the BIOS hard disk boot order as that GRUB is pointing to the correct partition, provided that ubuntu install is still intact.

Or if you want to keep the sdb (100 GB) install then do this:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,0) (hd1,0)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd1,0)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd1)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

Make sure sdb (100GB) is set to boot first in BIOS hard disk order.

Whichever ubuntu install you get working I would remove the other by booting the Live CD and using Partition Editor to remove those Ubuntu partitions.

See [here]("http://www.gnu.org/software/grub/manual/grub.html#Stage1_002e5-errors") for GRUB errors. Error 17 says the partition or device exists but GRUB can not recognize the filesystem. Your sdb (100 GB) GRUB is pointing to partition # 2 which is an extended partition which contains sdb5 swap. Thus the error 17.

---

### Post by robtom on 2009-10-08
Thanks to both of you for your help. You're right that my sdb drive wasn't configured properly. I launched my BIOS and discovered that the boot order was off, something I thought I'd already checked. Now I'm up and running without a care in the world!

---

### Post by presence1960 on 2009-10-08
> **robtom said:**
> Thanks to both of you for your help. You're right that my sdb drive wasn't configured properly. I launched my BIOS and discovered that the boot order was off, something I thought I'd already checked. Now I'm up and running without a care in the world!

Glad you got it working! Enjoy Ubuntu.

---

### Post by ubunone on 2009-10-12
Wonderful participants on this forum!  I just signed-up and I'm coming from the Dark Side (new to Linux but remembering the Unix days and wondering why I didn't stay with it so I'd remember the command line better). 
 
However, I'm trying to install 9.10 beta but having the same GRUB Error 17 problem.  After several partitionings and formattings, I still get no success.  What I noticed is that I get an error with 427.208060 end_request I/O Error fd0, and then another of the same error with a different starting number: 427.232043.  These are after trying to solve the issue with some of the threaded suggestions. 
 
Would anyone here know why I get this error?  I'm installing 9.10Beta desktop version (32-bit) from an ISO-generated CD download on a PC with a CD-R/W, DVD, Floppy Drive, 80G HD, and 5M RAM.  Nothing special.  The drive had SUSE 10 with KDE 3.4 before my Ubuntu install attempt (SUSE is too difficult for my kids to grasp). 
 
Thanks in advance.

---

### Post by shredder12 on 2009-10-12
I just have a slight doubt.. I am unable to see the flaw in the ubuntu on /dev/sdb..
how do I know that it points to #2 partition??

---

### Post by oldfred on 2009-10-12
Shredder 12 These two entries show the problem.

 Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sdb2: ____________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

If you go back and look the install on the second drive is in sdb1.

ubunone
You issue is not related to 9.04 but the new Karmic. You will do much better starting a new thread in Karmic area. The error seems to be fd0 which is the floppy? Is it not working? or is there a bug in Karmic for your system?

---

