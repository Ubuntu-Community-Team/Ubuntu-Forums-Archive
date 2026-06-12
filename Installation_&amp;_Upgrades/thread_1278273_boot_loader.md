---
title: "boot loader"
date: 2009-09-29
forum: Installation &amp; Upgrades
---

### Post by bavman on 2009-09-29
I have found several places that show how to restore grub boot loader after you reinstall vista. My question is, though, i used to have vista and ubuntu dual booting, but i upgraded to windows 7 and now the grub boot loader is gone again. 

Ive used something like this when i had to recover vista : 
[http://www.undercostruction.eu/2009/08/06/restore-grub-after-windows-installation/](http://www.undercostruction.eu/2009/08/06/restore-grub-after-windows-installation/)

but if i restore it, will windows 7 be an option in the dual boot screen or will it just be the old vista one?

---

### Post by presence1960 on 2009-09-29
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

This will give us the info needed to get your ubuntu up & running again.

---

### Post by bavman on 2009-10-16
Wow sorry it took me so long to reply, I've been away at college and didn't get back until yesterday, and i didnt have time to reply because of all my midterms. Anyways here is the results file boot info created. I hope your still around to help me. Thanks again.

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda5 and 
                       looks at sector 590159466 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6bec5864

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   542,531,114   542,531,052   7 HPFS/NTFS
/dev/sda2         542,531,115   605,586,239    63,055,125   5 Extended
/dev/sda5         542,531,178   602,903,384    60,372,207  83 Linux
/dev/sda6         602,903,448   605,586,239     2,682,792  82 Linux swap / Solaris
/dev/sda3         605,587,456   625,135,615    19,548,160   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="4A72768E72767F0F" TYPE="ntfs" 
/dev/sda3: UUID="3040CD6F40CD3C7A" LABEL="HP_RECOVERY" TYPE="ntfs" 
/dev/sda5: UUID="1cea59e1-f99d-434a-9eac-3e862750ef5f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="eedcd77d-9365-4694-81e2-afae2d60899f" TYPE="swap" 

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


=========================== sda5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=1cea59e1-f99d-434a-9eac-3e862750ef5f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=1cea59e1-f99d-434a-9eac-3e862750ef5f

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
uuid        1cea59e1-f99d-434a-9eac-3e862750ef5f
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=1cea59e1-f99d-434a-9eac-3e862750ef5f ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        1cea59e1-f99d-434a-9eac-3e862750ef5f
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=1cea59e1-f99d-434a-9eac-3e862750ef5f ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        1cea59e1-f99d-434a-9eac-3e862750ef5f
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=1cea59e1-f99d-434a-9eac-3e862750ef5f ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        1cea59e1-f99d-434a-9eac-3e862750ef5f
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=1cea59e1-f99d-434a-9eac-3e862750ef5f ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        1cea59e1-f99d-434a-9eac-3e862750ef5f
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title        Windows Vista (loader)
rootnoverify    (hd0,2)
savedefault
makeactive
chainloader    +1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=1cea59e1-f99d-434a-9eac-3e862750ef5f /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=eedcd77d-9365-4694-81e2-afae2d60899f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 302.2GB: boot/grub/menu.lst
 302.1GB: boot/grub/stage2
 300.7GB: boot/initrd.img-2.6.28-11-generic
 300.6GB: boot/initrd.img-2.6.28-15-generic
 300.6GB: boot/vmlinuz-2.6.28-11-generic
 300.6GB: boot/vmlinuz-2.6.28-15-generic
 300.6GB: initrd.img
 300.7GB: initrd.img.old
 300.6GB: vmlinuz
 300.6GB: vmlinuz.old
```

---

### Post by oldfred on 2009-10-16
I see you are still booting windows. It probably is giving you two choices in windows for booting. win7 moves its boot to the partition flagged as boot.

Vista copies boot manager to one 
[http://members.iinet.net/~herman546/p15.html#BOOTMGR_is_missing](http://members.iinet.net/~herman546/p15.html#BOOTMGR_is_missing)
Moral of the story - look on other NTFS partitions for the missing bootmgr and Boot directory.

IF you have not yet done anything with Win7 you may want to uninstall it, fix vista and change the boot flag to the new win7 partition. Supposedly that prevents it from combining windows boot.
Make sure you keep the Win7 partition as primary.

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

Then you can go back and reinstall grub and both entries to windows should work.

---

### Post by bavman on 2009-10-16
I'm not sure I follow, but i dont have vista on my computer anymore, just windows 7. I guess the problem is grub still has the boot files for vista saved. The problem is that i dont know how to change windows 7 with vista in grub and than restore grub loader again.

---

### Post by oldfred on 2009-10-16
The script does not identify Vista and Win7. Are you booting Win7 from sda1? If so you do not have a problem, just reinstall grub. But if your Win7 is in sda3,  you are still booting from the original Vista install.

---

### Post by presence1960 on 2009-10-16
```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,4)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,4)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

That will restore GRUB to MBR

---

### Post by Mark Phelps on 2009-10-17
Windows 7 installs two very different ways -- depending on whether or not you have it installed to a pre-existing partition, or whether you let it create its own partitions on an empty drive.

Since you say you "upgraded", I'm presuming you did the first; but if you did the second, you're not going to be able to get GRUB to work.

---

### Post by louieb on 2009-10-17
Does not matter if you have Win 7, Vista and XP installed in a partition 
The GRUB entry for Win 7, Vista and XP are all the same. 

As long a Win7 is in the same partition you once had Vista in  and you haven't added or removed any partitions or hard drives - your old Win OS entry should work. 

[presence1960]("http://ubuntuforums.org/member.php?u=657448")              in post #7 describes how to restore Grub - it will work.

In your case the 1st vista entry should work of Win 7 is in sda1 - the 2nd entry will work if Win 7 is on sda3 (look at the **root** statement - see the difference.

Grub is just going to chainload to the whatever version of Windows boot loader.

---

