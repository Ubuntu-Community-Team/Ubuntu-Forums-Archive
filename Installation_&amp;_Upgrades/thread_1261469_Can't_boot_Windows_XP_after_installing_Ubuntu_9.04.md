---
title: "Can't boot Windows XP after installing Ubuntu 9.04 (seperate partition)"
date: 2009-09-08
forum: Installation &amp; Upgrades
---

### Post by ztevin on 2009-09-08
Ok, so I'm new to Ubuntu, but not to computers (I'm a software engineer, and feel like an idiot even posting this.)

That said, I first installed Windows XP on my C: drive.  After that, I repartitioned to make a new Ext3 drive for ubuntu.  I also gave 2gb to a "swap" partition (still unsure what this does for me).

That said, I chose to install ubuntu on the empty partition, and it runs great.  I am able to boot to ubuntu through GRUB perfectly.

The problem stems when I'm trying to boot to Windows XP from GRUB.  It just sits at the screen that says, "Starting Up..." and I have to reboot and can only get to Ubuntu.

Here is my menu.lst file

```

default         0
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

title           Ubuntu 9.04, kernel 2.6.28-15-generic
uuid            f8da0836-06e1-43e0-a317-2fc050d4c4c8
kernel          /boot/vmlinuz-2.6.28-15-generic root=UUID=f8da0836-06e1-43e0-a317-2fc050d4c4c8 ro quiet splash
initrd          /boot/initrd.img-2.6.28-15-generic
quiet

title           Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid            f8da0836-06e1-43e0-a317-2fc050d4c4c8
kernel          /boot/vmlinuz-2.6.28-15-generic root=UUID=f8da0836-06e1-43e0-a317-2fc050d4c4c8 ro  single
initrd          /boot/initrd.img-2.6.28-15-generic

title           Ubuntu 9.04, kernel 2.6.28-11-generic
uuid            f8da0836-06e1-43e0-a317-2fc050d4c4c8
kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=f8da0836-06e1-43e0-a317-2fc050d4c4c8 ro quiet splash
initrd          /boot/initrd.img-2.6.28-11-generic
quiet

title           Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid            f8da0836-06e1-43e0-a317-2fc050d4c4c8
kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=f8da0836-06e1-43e0-a317-2fc050d4c4c8 ro  single
initrd          /boot/initrd.img-2.6.28-11-generic

title           Ubuntu 9.04, memtest86+
uuid            f8da0836-06e1-43e0-a317-2fc050d4c4c8
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader     +1

```Really hoping I can get back into XP keeping GRUB.

Thanks :guitar:

---

### Post by ztevin on 2009-09-08
Subscribing to my own thread... :lolflag:

---

### Post by ronparent on 2009-09-08
It sounds like you have a problem with windows. The 'starting up' indicates you have reached the windows boot loader.

It is highly unlikely that grub can be faulted for that outcome. It's possible that partitioning did cause a windows partition filesystem error. I'm to rusty with windows recovery to reccomment specific steps to remedy.

---

### Post by presence1960 on 2009-09-08
Did you defrag XP at least once or twice prior to resizing the Xp partition. And possibly turned off system restore. You should do this as windows makes a habit of haphazardly throwing files all over the disk from one end to the other. When you resized if you didn't defrag that may have caused a problem such as data loss/corruption on the windows partition.

Just to be safe do this so we can see exactly what you have on your setup & boot process:

Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by ztevin on 2009-09-08
You guys are great.  I'm hoping I didn't mess up the Windows Partition as it was JUST installed...Literally the day before I installed ubuntu.

Regardless here is the requested info.

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc4a07d68

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   312,576,704   312,576,642   7 HPFS/NTFS
/dev/sda2         312,576,705   621,233,549   308,656,845  83 Linux
/dev/sda3         621,233,550   625,137,344     3,903,795   5 Extended
/dev/sda5         621,233,613   625,137,344     3,903,732  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6c676c67

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x44fdfe06

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="EEB4C83BB4C80853" TYPE="ntfs" 
/dev/sda2: LABEL="linux" UUID="f8da0836-06e1-43e0-a317-2fc050d4c4c8" TYPE="ext3" 
/dev/sda5: UUID="d9d2cf89-29e3-48d6-8725-925ed0f062f1" TYPE="swap" 
/dev/sdb1: UUID="2CDC1FC5DC1F87EA" TYPE="ntfs" 
/dev/sdc1: UUID="5E2C78AC2C7880B7" LABEL="MyBook" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/maynard/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=maynard)
/dev/sdc1 on /media/MyBook type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer 

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
# kopt=root=UUID=f8da0836-06e1-43e0-a317-2fc050d4c4c8 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f8da0836-06e1-43e0-a317-2fc050d4c4c8

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

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        f8da0836-06e1-43e0-a317-2fc050d4c4c8
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=f8da0836-06e1-43e0-a317-2fc050d4c4c8 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        f8da0836-06e1-43e0-a317-2fc050d4c4c8
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=f8da0836-06e1-43e0-a317-2fc050d4c4c8 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        f8da0836-06e1-43e0-a317-2fc050d4c4c8
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=f8da0836-06e1-43e0-a317-2fc050d4c4c8 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        f8da0836-06e1-43e0-a317-2fc050d4c4c8
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=f8da0836-06e1-43e0-a317-2fc050d4c4c8 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        f8da0836-06e1-43e0-a317-2fc050d4c4c8
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=f8da0836-06e1-43e0-a317-2fc050d4c4c8 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=d9d2cf89-29e3-48d6-8725-925ed0f062f1 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


 283.6GB: boot/grub/menu.lst
 283.7GB: boot/grub/stage2
 283.7GB: boot/initrd.img-2.6.28-11-generic
 283.7GB: boot/initrd.img-2.6.28-15-generic
 283.7GB: boot/vmlinuz-2.6.28-11-generic
 283.7GB: boot/vmlinuz-2.6.28-15-generic
 283.7GB: initrd.img
 283.7GB: initrd.img.old
 283.7GB: vmlinuz
 283.7GB: vmlinuz.old
```

Very much appreciated!

Bryan

---

### Post by presence1960 on 2009-09-08
Everything looks good. your windows entry in menu.lst is ok, your bootloader for sda1 for windows is fine. You may have to reinstall windows. But first try this:

Boot off your windows XP install disk and do [this]("http://ubuntuforums.org/showthread.php?t=1014708"), scroll down to instructions for XP. When complete reboot and see if you boot right into windows. If you do boot into windows you need to restore GRUB now by doing this:

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

**In # 6 use setup (hd0)**

You will then be good to go.

If after using the XP install Cd you can't boot into windows you may have to reinstall XP. Then follow the above process to restore GRUB after XP is installed.

---

