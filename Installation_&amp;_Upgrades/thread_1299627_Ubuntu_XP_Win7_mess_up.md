---
title: "Ubuntu XP Win7 mess up"
date: 2009-10-24
forum: Installation &amp; Upgrades
---

### Post by txp561 on 2009-10-24
Hi Guys (and girls maybe),

I have a problem, well more of an anoyance as i solved my main problem. Firstly I was given a copy of windows 7 to try so i partitioned my XP setup and installed ubuntu 9.04 on a partition and windows 7 in another. 

I then decided that I didnt want the windows 7 install so deleted away the partition (without formatting as i am an idiot) I then also did the same for the ubuntu install (as i am an idiot) and then resized my partition of XP back to the full size of my hard drive

GRUB 22 error....

fixed this problem by installing ubuntu again. However now Ubuntu doesnt recognise my XP as XP but as Vista(loader). it allows me to get to XP by following a couple of pages at bootup  by clickign on run earlier version of windows (windows 7 link is dead). Basically i was wondering if there was a way to change the Grub to ignote the windows 7.Vista (loader) as it is called and just go straight to Ubuntu or XP? 

I have looked in the menu.lst and the only non linux OS there is windows Vista (loader) and not XP.

The annoyance is having to go through the various menus at startup. if it is not solvabel i shall have to live with it but i was hoping somebody would be able to give me sum tips on how to getback to just ubuntu and XP

---

### Post by skyiscrying on 2009-10-24
This is what I would do. Start from scratch. Format the whole drive with the XP disc and install your copy of *that* windows OS. Then go and download the Wubi Ubuntu Installer. Install 9.04 Ubuntu from there. It is very simple. When all is done and you re-boot, you will have a choice of using XP, which is the default, or selecting your Ubuntu system which is in a folder within XP.

---

### Post by txp561 on 2009-10-24
that idea had crossed my mind however i would quite like to not reinstall windows as i have lots of uni work and programs. could always back up and do that if there is no ohter way to sort it out. thanx for the reply

---

### Post by grizzler on 2009-10-24
It sounds like something has gone missing, but form you post I can't figure out exactly what. If it's part of the menu.lst file that's incorrect, you can change that manually. The bit for XP should be something like this:

```
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```
That is provided the XP partition is the first one on the (first) disk and provided we're talking about legacy grub (which is likely, as you mention Ubuntu 9.04).

If the XP boot structure is still intact, that should do it. However, the fact that Ubuntu offers you a Vista loader, suggests that it isn't.
In that case, you may have to recreate the XP bootloader. Maybe using bootcfg to create a new boot.ini and copying NTLDR from somewhere would be enough, but you might have to use fixmbr (and possibly fixboot) from the XP install disk. This will remove grub from the MBR of course, so you'll have to fix that again afterwards (SuperGrubDisk?).

Not sure if this is of any use, but that's how I would go about it.

---

### Post by presence1960 on 2009-10-24
Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by txp561 on 2009-10-24
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

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

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x12231222

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    48,612,689    48,612,627   7 HPFS/NTFS
/dev/sda2          48,612,690    89,674,829    41,062,140   5 Extended
/dev/sda5          48,612,753    50,604,749     1,991,997  82 Linux swap / Solaris
/dev/sda6          50,604,813    89,674,829    39,070,017  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd492d492

Partition  Boot         Start           End          Size  Id System

/dev/sdb2              16,065   320,159,384   320,143,320   f W95 Ext d (LBA)
/dev/sdb5              16,128   320,159,384   320,143,257   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="7E6019D7601996CD" LABEL="WinXP" TYPE="ntfs" 
/dev/sda5: TYPE="swap" UUID="fcb78512-21b1-4e5d-8f71-6f1314c9bdd5" 
/dev/sda6: UUID="d2753e6a-2981-4abe-b722-643475428afb" TYPE="ext3" 
/dev/sdb5: UUID="3654A28C54A24F05" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/tony/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=tony)


================================ sda1/boot.ini: ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT 
c:\wubildr.mbr="Ubuntu"  

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
# kopt=root=UUID=d2753e6a-2981-4abe-b722-643475428afb ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d2753e6a-2981-4abe-b722-643475428afb

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
uuid        d2753e6a-2981-4abe-b722-643475428afb
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=d2753e6a-2981-4abe-b722-643475428afb ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        d2753e6a-2981-4abe-b722-643475428afb
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=d2753e6a-2981-4abe-b722-643475428afb ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        d2753e6a-2981-4abe-b722-643475428afb
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
UUID=d2753e6a-2981-4abe-b722-643475428afb /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=fcb78512-21b1-4e5d-8f71-6f1314c9bdd5 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


  42.2GB: boot/grub/menu.lst
  42.2GB: boot/grub/stage2
  42.2GB: boot/initrd.img-2.6.28-11-generic
  42.2GB: boot/vmlinuz-2.6.28-11-generic
  42.2GB: initrd.img
  42.2GB: vmlinuz



```

---

### Post by txp561 on 2009-10-24
> **grizzler said:**
> It sounds like something has gone missing, but form you post I can't figure out exactly what. If it's part of the menu.lst file that's incorrect, you can change that manually. The bit for XP should be something like this:

```
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1
```That is provided the XP partition is the first one on the (first) disk and provided we're talking about legacy grub (which is likely, as you mention Ubuntu 9.04).

If the XP boot structure is still intact, that should do it. However, the fact that Ubuntu offers you a Vista loader, suggests that it isn't.


I changed the menu.lst file to this rather than the vista and as it loads it gives me the options of Ubuntu or XP however when clicking on XP it then offers me the same Windows 7 or earlier version of windows screne.

in short it jsut renamed the 1st link but did not change anything

---

### Post by bumanie on 2009-10-24
You will have both win7 and xp boot loader files in your mbr. To get rid of the win7 bootloader files you will have go into repair mode with an xp disk and type FIXBOOT followed by FIXMBR whilst in console mode. This will also overwrite the grub bootloader. If you still want ubuntu in dual boot with xp, you will have to reinstall grub. I won't explain that yet unless you confirm that you want xp/ubuntu in dual boot configuration. By the way, you are not an idiot for not formatting, it is the information recorded in the mbr that is the problem, not the issue of whether you formatted or not post uninstalling.

---

### Post by txp561 on 2009-10-24
ok so use my xp boot disc to revoer not install and mess around with the file there? just delte out windows 7 from the file?

am i also correct in my thinking that grub can be restored form a live cd instead of a fresh ubuntu install? i seem to have read this somehwere

---

### Post by presence1960 on 2009-10-24
> **txp561 said:**
> ok so use my xp boot disc to revoer not install and mess around with the file there? just delte out windows 7 from the file?

am i also correct in my thinking that grub can be restored form a live cd instead of a fresh ubuntu install? i seem to have read this somehwere

This will be a two step process as bumanie accurately explained. The first part you need to boot off the XP install disk and follow the instructions [here]("http://ubuntuforums.org/showthread.php?t=1014708") for XP. This will repair XP bootloader.

Now you need to restore GRUB to MBR as windows will be there after last operation you did. Do this:

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

Boot into Ubuntu and open a terminal and run this command ```
gksu gedit /boot/grub/menu.lst
```That is a lowercase L in .lst

Scroll down to bottom of file and edit the windows entry to look like this:

```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows XP
rootnoverify    (hd0,0)
chainloader     +1
```

Clich Save on top toolbar & close file. You should now be good to go.

---

### Post by txp561 on 2009-10-26
I try and run fixboot and the comp asks for an administration password.

I have no idea what this is as i dont belive i hae ever set one. I read somwhere usually leave it blank but that does not work either. Is there any way of finding the password out?

---

### Post by txp561 on 2009-10-26
problem solved i figured out my admin password and now its all sorted. thanx for your help

---

### Post by presence1960 on 2009-10-26
Glad you got it working. For future reference Windows always asks to set up an administrator password during installation.

---

