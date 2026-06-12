---
title: "Grub won't boot into windows after upgrade!"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by jimmyboy09 on 2009-04-25
Hallo der.  I was on a dual boot w/ xp and intrepid.

I then upgraded to Jaunty (keeping my orig menu.lst and "read ahead?" b/c I was afraid of ruining my dual-bootability).  Well, turns out I ruined it anyways.  Couldn't boot into Jaunty (as grub still only recognized intrepid) so I manually changed the kernel name in grub first (didn't work), then later did an update-grub.  The update-grub meant grub doesn't even show the option to boot into windows anymore.  On top of that, I still couldn't boot into Jaunty  :(  Useless laptop.

So I decided to just do a fresh install of intrepid again, remounting my separate /home partition.  I also "fixed" my menu.lst although I'm pretty sure it's a botched job.  So the option to boot into windows shows, but when I select it, it clears the screen and redisplays the grub menu.

Can anyone tell me how to fix this?

```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda1 and 
                       looks at sector 230554056 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #3 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xec59a4b2

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   156,328,514   156,328,452   7 HPFS/NTFS
/dev/sda2         156,328,515   212,957,639    56,629,125   5 Extended
/dev/sda5         156,328,578   208,764,674    52,436,097  83 Linux
/dev/sda6         208,764,738   212,957,639     4,192,902  82 Linux swap / Solaris
/dev/sda3         212,957,640   265,393,799    52,436,160  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda3: UUID="94f21851-1ed3-4134-b236-dc9dd951e637" TYPE="ext3" 
/dev/sda5: UUID="f616ca05-da60-4510-8708-e8914b6a89d1" TYPE="ext3" 
/dev/sda6: UUID="190635f2-f810-489e-a7f2-ae72e8197ab2" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda3 on / type ext3 (rw,relatime,errors=remount-ro)
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
/dev/sda5 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/dominic/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dominic)


=========================== sda3/boot/grub/menu.lst: ===========================

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
# hiddenmenu

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
# kopt=root=UUID=94f21851-1ed3-4134-b236-dc9dd951e637 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=94f21851-1ed3-4134-b236-dc9dd951e637

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
uuid		94f21851-1ed3-4134-b236-dc9dd951e637
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=94f21851-1ed3-4134-b236-dc9dd951e637 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		94f21851-1ed3-4134-b236-dc9dd951e637
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=94f21851-1ed3-4134-b236-dc9dd951e637 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, memtest86+
uuid		94f21851-1ed3-4134-b236-dc9dd951e637
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional Edition
rootnoverify        (hd0,0)
savedefault
makeactive
chainloader    +1
boot

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=94f21851-1ed3-4134-b236-dc9dd951e637 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=f616ca05-da60-4510-8708-e8914b6a89d1 /home           ext3    relatime        0       2
# /dev/sda6
UUID=190635f2-f810-489e-a7f2-ae72e8197ab2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


 127.3GB: boot/grub/menu.lst
 127.3GB: boot/grub/stage2
 127.3GB: boot/initrd.img-2.6.27-11-generic
 127.4GB: boot/initrd.img-2.6.27-7-generic
 127.3GB: boot/vmlinuz-2.6.27-11-generic
 127.3GB: boot/vmlinuz-2.6.27-7-generic
 127.3GB: initrd.img
 127.4GB: initrd.img.old
 127.3GB: vmlinuz
 127.3GB: vmlinuz.old
```

---

### Post by jimmyboy09 on 2009-04-25
Btw, I've also noticed that fstab and uuid don't show any signs of my windows partition, which I know still exists.

---

### Post by jimmyboy09 on 2009-04-25
Please help.  Please.

---

### Post by meierfra. on 2009-04-25
> Please help. Please.
Please wait for 24 hours before bumping your thread,

To fix your problem, you need to restore the boot sector of your Windows partition:  Download the [testdisk-6.10.linux26.tar.bz2 package](http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2) to your desktop, and then do:

```


cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static /dev/sda

```


Choose "proceed" on the first screen, then
"intel"
"advanced",
Select the Windows partition (although it should be selected already) and choose
"boot"
"BackupBS"
Type "Y" to confirm
  

Then press "q" a few times to quit  testdisk, reboot and see whether you can boot into Windows.

---

