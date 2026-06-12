---
title: "Vista won't boot after I installed Ubuntu + Grub"
date: 2009-09-13
forum: Installation &amp; Upgrades
---

### Post by theplague on 2009-09-13
Hi guys,
I recently installed Ubuntu 9.04 on my laptop which had Windows Vista and now even though there is an entry on Grub to load Vista it won't work, when I try to load it, it will say "starting..." and then takes me back to the Grub screen. I´m posting my config here, do you think that you guys can help me?
Thanks a lot.

GRUB'S MENU.LST
=========================
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
chainloader    +1

```MY PARTITION TABLE
=========================
```

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825        7296    27888840    f  W95 Ext'd (LBA)
/dev/sda5            3825        6809    23976981    7  HPFS/NTFS
/dev/sda6            6810        7267     3678853+  83  Linux
/dev/sda7            7268        7296      232911   82  Linux swap / Solaris

```

---

### Post by Mark Phelps on 2009-09-13
Did you use Ubuntu to shrink the Vista OS partition to make room? If so, you may need to boot from your Vista DVD and run Startup Repair several times to get Vista boot capability back?

---

### Post by theplague on 2009-09-14
I shrunk the secondary partition, not the primary Vista partition. I will use the DVD to see if it fixes it.
Thanks

---

### Post by presence1960 on 2009-09-14
Let's get a better look at your setup. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by theplague on 2009-09-14
Using Vista's DVD and took care of it in less than 10 minutes, I think that I need to install easy BCD now to make sure I can boot both OS's now.
Thanks for the tip!

---

### Post by presence1960 on 2009-09-14
You don't need to install Easy BCD, GRUB will boot both OSs. If you post the results of the boot info script I asked you to run I can show you how to configure GRUB. I boot 4 OSs off GRUB: Ubuntu 9.04, Sabayon 4.1. Masonux 9.04 and Windows XP.

Besides GRUB is way more configurable and can do a lot more than Easy BCD.

---

### Post by theplague on 2009-09-14
Here you go buddy...

> ============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sda2: _________________________________________________________________________

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

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0f4738c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    61,432,559    61,432,497   7 HPFS/NTFS
/dev/sda2          61,432,560   117,210,239    55,777,680   f W95 Ext d (LBA)
/dev/sda5          61,432,623   109,386,584    47,953,962   7 HPFS/NTFS
/dev/sda6         109,386,648   116,744,354     7,357,707  83 Linux
/dev/sda7         116,744,418   117,210,239       465,822  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="64B4C8B6B4C88C4C" TYPE="ntfs" 
/dev/sda5: UUID="F4E8874BE8870AD6" TYPE="ntfs" 
/dev/sda6: UUID="503d0001-0b0f-4ec2-b116-f678d2beb5f0" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="f8548ad3-677c-4dd6-b64e-e7fbe1e1e50c" TYPE="swap" 

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
default        6

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        5

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
# kopt=root=UUID=503d0001-0b0f-4ec2-b116-f678d2beb5f0 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=503d0001-0b0f-4ec2-b116-f678d2beb5f0

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
uuid        503d0001-0b0f-4ec2-b116-f678d2beb5f0
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=503d0001-0b0f-4ec2-b116-f678d2beb5f0 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        503d0001-0b0f-4ec2-b116-f678d2beb5f0
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=503d0001-0b0f-4ec2-b116-f678d2beb5f0 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        503d0001-0b0f-4ec2-b116-f678d2beb5f0
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=503d0001-0b0f-4ec2-b116-f678d2beb5f0 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        503d0001-0b0f-4ec2-b116-f678d2beb5f0
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=503d0001-0b0f-4ec2-b116-f678d2beb5f0 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        503d0001-0b0f-4ec2-b116-f678d2beb5f0
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
chainloader    +1


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=503d0001-0b0f-4ec2-b116-f678d2beb5f0 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=f8548ad3-677c-4dd6-b64e-e7fbe1e1e50c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


  56.5GB: boot/grub/menu.lst
  56.6GB: boot/grub/stage2
  56.6GB: boot/initrd.img-2.6.28-11-generic
  56.8GB: boot/initrd.img-2.6.28-15-generic
  56.7GB: boot/vmlinuz-2.6.28-11-generic
  56.8GB: boot/vmlinuz-2.6.28-15-generic
  56.8GB: initrd.img
  56.6GB: initrd.img.old
  56.8GB: vmlinuz
  56.7GB: vmlinuz.old

---

### Post by baltadt on 2009-09-14
> **theplague said:**
> 

GRUB'S MENU.LST
=========================
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
chainloader    +1

```MY PARTITION TABLE

[/code]
  
I had the same problem when I was running ubuntu from a usb on a vista laptop. I don't no why it is giving you problems when booting from the HDD but this post solved my problem.
[http://ubuntuforums.org/showthread.php?t=282545](http://ubuntuforums.org/showthread.php?t=282545)

Although I am a noob so don't just take my word.

---

### Post by presence1960 on 2009-09-14
you want to install GRUB to MBR of your disk. Do this:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,5)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,5)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

Try booting Vista. It's entry in menu.lst looks good. When the GRUB menu comes up choose Vista.

---

### Post by Arla on 2009-09-15
I'm having similar issues, it's using the new Grub for 9.10 (which may or may not matter) after installing Ubuntu Vista wasn't on GRUB menu at all, running 

sudo update-grub

Creates two Vista options (which makes sense, one for the actual Vista partition, and one for the recovery partition) the recovery one seems to work fine, the original just hangs with GRUB showing on the screen (top left corner).

I've attached the results of the boot script? Unfortunately trying to follow the instructions in the prior post (to reinstall/rerun grub) doesn't seem to work, probably due to the new version of grub.

---

### Post by dalem on 2009-10-21
Hi guys! I just installed 9.10 and have lost my vista bootup option in grub also. What may have happened is I shrunk my linux partition and made a separate partition to increase the size of windoze. 

But, I just want to get vista back, there are some things I need on it. Your help is greatly appreciated!!

I'm including the startup information script as shown above..

thanks!

---

### Post by raprap30 on 2009-10-21
BTW easybcd WILL NOT WORK most of the time if grub is not installed on the target partition itself.

---

### Post by Mark Phelps on 2009-10-21
> **dalem said:**
> ... What may have happened is I shrunk my linux partition and made a separate partition to increase the size of windoze....

Not clear what you did ... Did you resize the Vista OS partition? Or did you just create another NTFS partition to use for data?

If you did the first, did you use the Vista Disk Management utility? OR did you use GParted?

---

