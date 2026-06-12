---
title: "failin to install grub"
date: 2009-05-30
forum: Installation &amp; Upgrades
---

### Post by vikasmk on 2009-05-30
I have a ubuntu 8.04 already installed on my system. Since i got the live cds of ubuntu 9.04 from canonical, I tried installing it in a new partition.The installation failed , because it couldnt install the grub.It said it was a fatal error. 
  SO, i thought why, I can install the grub myself and installed it 
 ```
sudo grub
 find /boot/grub/stage1 
bla bla bla.....same old.
```
BUt now boot menu only shows 8.04 and not 9.04 .......am I missing something?

---

### Post by presence1960 on 2009-05-30
To get a better look at your machine's setup download the Boot Info Script to your Desktop from here: [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

Then run this command in terminal > sudo bash ~/Desktop/boot_info_script*.sh This will create a RESULTS.txt file on your Desktop. Paste the contents of that file here. Then highlight the text you just pasted and click the # sign on the toolbar to place Code tags around the text. Then we'll see what you have there.

---

### Post by vikasmk on 2009-05-30
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

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

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x05f405f3

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    20,482,874    20,482,812  83 Linux
/dev/sda2          20,482,875   156,280,319   135,797,445   f W95 Ext d (LBA)
/dev/sda5          20,482,938    61,448,624    40,965,687   e W95 FAT16 (LBA)
/dev/sda6    *     61,448,688    98,558,774    37,110,087  83 Linux
/dev/sda7          98,558,838   102,414,374     3,855,537  82 Linux swap / Solaris
/dev/sda8         102,414,438   156,280,319    53,865,882   e W95 FAT16 (LBA)


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="01fad6e6-55b8-4b49-9c00-7730d108f3da" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="83287e63-6a93-4ef1-9874-a81b8ef5e88c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="f80fe926-f179-42d5-a45d-d698936aea5c" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="02c38430-594c-52a2-be13-63f8b1378c6b" 
/dev/sda8: UUID="717dc10e-38cf-4108-85e7-b6bc510b20a5" SEC_TYPE="ext2" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/vikasmk/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=vikasmk)


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
# kopt=root=UUID=f80fe926-f179-42d5-a45d-d698936aea5c ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title		Ubuntu 8.04, kernel 2.6.24-23-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=f80fe926-f179-42d5-a45d-d698936aea5c ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=f80fe926-f179-42d5-a45d-d698936aea5c ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:



# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/sda6
UUID=f80fe926-f179-42d5-a45d-d698936aea5c  /              ext3         relatime,errors=remount-ro  0  1  
# /dev/sda8
UUID=02c38430-594c-52a2-be13-63f8b1378c6b  none           swap         sw                          0  0  
/dev/scd1                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/scd0                                  /media/cdrom1  udf,iso9660  user,noauto,exec,utf8       0  0  

=================== sda6: Location of files loaded by Grub: ===================


  47.5GB: boot/grub/menu.lst
  47.6GB: boot/grub/stage2
  44.6GB: boot/initrd.img-2.6.24-16-generic
  44.5GB: boot/initrd.img-2.6.24-16-generic.bak
  44.6GB: boot/initrd.img-2.6.24-23-generic
  44.6GB: boot/initrd.img-2.6.24-23-generic.bak
  44.5GB: boot/vmlinuz-2.6.24-16-generic
  44.5GB: boot/vmlinuz-2.6.24-23-generic
  44.6GB: initrd.img
  44.6GB: initrd.img.old
  44.5GB: vmlinuz
  44.5GB: vmlinuz.old

=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda8 during installation
UUID=717dc10e-38cf-4108-85e7-b6bc510b20a5 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=02c38430-594c-52a2-be13-63f8b1378c6b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda8: Location of files loaded by Grub: ===================


  79.0GB: boot/grub/stage2
  79.0GB: boot/initrd.img-2.6.28-11-generic
  79.0GB: boot/vmlinuz-2.6.28-11-generic
  79.0GB: initrd.img
  79.0GB: vmlinuz
```

---

### Post by presence1960 on 2009-05-30
your 9.04 is in sda8. you don't have GRUB installed on that partition. This is what I would do. I would boot the Ubuntu Live CD & choose try Ubuntu without any changes, when the Desktop is ready do this

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

At #5 enter root (hd0,7)
At #6 enter setup (hd0)
Follow #7 & 8 then see if GRUB comes up with jaunty 9.04.

If it does you still have one more step to set up a chainload for Hardy. You want to chainload Hardy off Jaunty's GRUB this way when each version updates their kernels you wont have to keep editing menu.lst. 

Let's see if that works and if it does then we can add hardy to jaunty's GRUB list

---

### Post by presence1960 on 2009-05-30
If that doesn't work, I just saw something that indicates why it may not work: In the Results.txt file at the top your Boot Info Summary shows sda8 as 9.04 and ext3 with no menu.lst, but you have fstab.

The next heading on that list Drive/Partition Info has sda8 as FAT16.
You did say you had an error on the install process. You may have to do a clean install...sorry I just noticed this

---

### Post by vikasmk on 2009-06-01
hmm....i'll do a fresh install and seee.........

---

