---
title: "Windows won't boot"
date: 2009-10-24
forum: Installation &amp; Upgrades
---

### Post by martinic on 2009-10-24
Hello,

I set up my computer with dual boot Ubuntu 9.04 and Windows XP from previously just having Windows XP. Unfortunately, now when I select Windows from the GRUB menu, it just comes up with a blank screen with "Starting up..." at the top, and sticks on that. Is there any way to resolve this? I can access all windows files perfectly easily mounting from Ubuntu, so they're all there.

- Results of sudo fdisk -l:

> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcab10bee

Device Boot Start End Blocks Id System
/dev/sda1 * 1 5729 46018161 7 HPFS/NTFS
/dev/sda2 8996 9729 5889240 c W95 FAT32 (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3 5730 8995 26234145 5 Extended
/dev/sda5 5730 8855 25109563+ 83 Linux
/dev/sda6 8856 8995 1124518+ 82 Linux swap / Solaris
Partition table entries are not in disk order

Partition table entries are not in disk order


- Windowsy bits of menu.lst:

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Home Edition
root (hd0,0)
makeactive
chainloader +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title Windows NT/2000/XP
rootnoverify (hd0,1)
savedefault
makeactive
chainloader +1 

---

### Post by quimkaos on 2009-10-24
grub seams to be fine... have you tried to booting windows in safe mode?

---

### Post by motsteve on 2009-10-24
This may be a Hail Mary, but did you try SuperGrub?  I suggest it just because it's fast and easy.  There could be escape characters buried in the menu also.

---

### Post by martinic on 2009-10-24
I don't think it gets to a stage where it'll let me go into Safe Mode!

---

### Post by Mark Phelps on 2009-10-24
Do you get the same results selecting either of the two stanzas?

Suggest changing the first from root to rootnoverify. Other than that, they look OK.

---

### Post by presence1960 on 2009-10-24
we need a little more info.

Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by martinic on 2009-10-24
Here goes...

```
============================= Boot Info Summary: ==============================

=> Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive
in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

File system: ntfs
Boot sector type: Windows XP
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows XP
Boot files/dirs: /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

File system: vfat
Boot sector type: HP Recovery
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files/dirs: /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM
/ntdetect.com

sda3: _________________________________________________________________________

File system: Extended Partition
Boot sector type: -
Boot sector info:

sda5: _________________________________________________________________________

File system: ext3
Boot sector type: -
Boot sector info:
Operating System: Ubuntu 9.04
Boot files/dirs: /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

File system: swap
Boot sector type: -
Boot sector info:

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcab10bee

Partition Boot Start End Size Id System

/dev/sda1 * 63 92,036,384 92,036,322 7 HPFS/NTFS
/dev/sda2 144,516,960 156,295,439 11,778,480 c W95 FAT32 (LBA)
/dev/sda3 92,036,385 144,504,674 52,468,290 5 Extended
/dev/sda5 92,036,448 142,255,574 50,219,127 83 Linux
/dev/sda6 142,255,638 144,504,674 2,249,037 82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="45EE85EC730AFEC6" LABEL="PRESARIO" TYPE="ntfs"
/dev/sda2: LABEL="PRESARIO_RP" UUID="4B6E-6BC0" TYPE="vfat"
/dev/sda5: UUID="c74669e1-16c5-4914-be70-dcdb6046966a" TYPE="ext3"
/dev/sda6: UUID="9ea02603-2354-417c-98be-0928a6f17648" TYPE="swap"

=============================== "mount" output: ===============================

/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-16-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/lisa/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=lisa)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=0

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


================================ sda2/boot.ini: ================================

[boot loader]

timeout=0

default=C:\CMDCONS\BOOTSECT.DAT

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons


================================ sda2/BOOT.INI: ================================

[boot loader]

timeout=0

default=C:\CMDCONS\BOOTSECT.DAT

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons


=========================== sda5/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
# grub-install(8), grub-floppy(8),
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
# kopt=root=UUID=c74669e1-16c5-4914-be70-dcdb6046966a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=c74669e1-16c5-4914-be70-dcdb6046966a

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

title Ubuntu 9.04, kernel 2.6.28-16-generic
uuid c74669e1-16c5-4914-be70-dcdb6046966a
kernel /boot/vmlinuz-2.6.28-16-generic root=UUID=c74669e1-16c5-4914-be70-dcdb6046966a ro quiet splash
initrd /boot/initrd.img-2.6.28-16-generic
quiet

title Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid c74669e1-16c5-4914-be70-dcdb6046966a
kernel /boot/vmlinuz-2.6.28-16-generic root=UUID=c74669e1-16c5-4914-be70-dcdb6046966a ro single
initrd /boot/initrd.img-2.6.28-16-generic

title Ubuntu 9.04, kernel 2.6.28-11-generic
uuid c74669e1-16c5-4914-be70-dcdb6046966a
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=c74669e1-16c5-4914-be70-dcdb6046966a ro quiet splash
initrd /boot/initrd.img-2.6.28-11-generic
quiet

title Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid c74669e1-16c5-4914-be70-dcdb6046966a
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=c74669e1-16c5-4914-be70-dcdb6046966a ro single
initrd /boot/initrd.img-2.6.28-11-generic

title Ubuntu 9.04, memtest86+
uuid c74669e1-16c5-4914-be70-dcdb6046966a
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Home Edition
root (hd0,0)
makeactive
chainloader +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title Windows NT/2000/XP
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
UUID=c74669e1-16c5-4914-be70-dcdb6046966a / ext3 relatime,errors=remount-ro 0 1
# swap was on /dev/sda6 during installation
UUID=9ea02603-2354-417c-98be-0928a6f17648 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

=================== sda5: Location of files loaded by Grub: ===================


71.5GB: boot/grub/menu.lst
71.4GB: boot/grub/stage2
71.3GB: boot/initrd.img-2.6.28-11-generic
71.3GB: boot/initrd.img-2.6.28-16-generic
71.4GB: boot/vmlinuz-2.6.28-11-generic
71.3GB: boot/vmlinuz-2.6.28-16-generic
71.3GB: initrd.img
71.3GB: initrd.img.old
71.3GB: vmlinuz
71.4GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde
```

---

### Post by slyrDVS on 2009-10-24
It is possible that your "NTLDR" is missing from windows, It commonly happens with duals boots on my pc's.

Here's some help and good luck mate.

[http://www.quickonlinetips.com/archives/2005/12/ntldr-is-missing-press-any-key-to-restart/](http://www.quickonlinetips.com/archives/2005/12/ntldr-is-missing-press-any-key-to-restart/)

EDIT:
Sometimes just having those 2 new files moved into the C:// or install drive of windows just fixes everything.

---

### Post by presence1960 on 2009-10-24
your menu.lst looks good, but as Mark said I would suggest changing root to rootnoverify for the sda1 windows which is XP. sda2 is your recovery partition and I would change that title to recovery.

If your windows will not boot something may have happened to the boot files, even though they appear to be intact. I have an HP that I do not use and it has a recovery partition like you have but I had the option of burning a CD which contains the XP Recovery console and a partitioning tool. You need to access the recovery console function either from a CD or the recovery partition. 

Once you do that you will need to do [this]("http://ubuntuforums.org/showthread.php?t=1014708"). Follow the instructions for XP which will repair windows boot process. When complete reboot & you should boot right to windows.

Now you need to restore GRUB to the MBR as windows is on there after what you just did. Do this:

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

---

### Post by presence1960 on 2009-10-24
> **slyrDVS said:**
> It is possible that your "NTLDR" is missing from windows, It commonly happens with duals boots on my pc's.

Here's some help and good luck mate.

[http://www.quickonlinetips.com/archives/2005/12/ntldr-is-missing-press-any-key-to-restart/](http://www.quickonlinetips.com/archives/2005/12/ntldr-is-missing-press-any-key-to-restart/)

EDIT:
Sometimes just having those 2 new files moved into the C:// or install drive of windows just fixes everything.

it is there look at the script results he posted:

```
sda1: _________________________________________________________________________

File system: ntfs
Boot sector type: Windows XP
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows XP
[COLOR="Red"]Boot files/dirs: /boot.ini /ntldr /NTDETECT.COM[/COLOR]
```

---

### Post by slyrDVS on 2009-10-24
Quite possibly the case.

But what I'm saying is sometimes it is there, but not really there.
I normally put copies of NTLDR and ntdetect.com directly in my C drive outside of the windows folder when I dual boot.

---

### Post by martinic on 2009-11-03
Hello,

I have tried repairing using the recovery partition, updating the mbr using Lilo and replacing NTLDR and NTDETECT.COM, all without effect. I don't have a Windows XP cd to hand to try using that. Any other solutions anyone can think of other than formatting and starting again?

---

### Post by oldfred on 2009-11-03
Did you change the root command on your first windows menu entry to rootnoverify like on your second partition as Mark had suggested?

Did you try supergrub as motsteve suggested? It can both restore winXP or add/fix grub. You might try restoring windows to make sure it works then reinstall grub with supergrub.

---

### Post by martinic on 2009-11-04
I originally changed the rootnoverify command to root as there was some suggestion that that might solve it.

Haven't tried Supergrub yet- will do!

---

### Post by DaveRowell on 2009-11-04
Don't both sda(1) and sda(2) boot.ini files point to the second partition on his drive?  Shouldn't at least one of them point to the first partition - the one with Windoze?  

My Compaq is even weirder the recovery partition is first the Windoze partition second.  I've learned a lot from that!

---

### Post by martinic on 2009-11-08
Tried the various different options Supergrub offers but to no avail. Any suggestions other than to reformat?

---

### Post by oldfred on 2009-11-08
Without knowing exactly what changes you have done, we need you to repost a new run of the bootinfoscript to see how it is set now. It will make a results2 file as the new one if you still have the old one.

---

### Post by martinic on 2009-11-08
Bootinfoscript results:

```
============================= Boot Info Summary: ==============================

=> Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive
in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

File system: ntfs
Boot sector type: Windows XP
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows XP
Boot files/dirs: /boot.ini /ntldr /NTLDR /NTDETECT.COM

sda2: _________________________________________________________________________

File system: vfat
Boot sector type: HP Recovery
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files/dirs: /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM
/ntdetect.com

sda3: _________________________________________________________________________

File system: Extended Partition
Boot sector type: -
Boot sector info:

sda5: _________________________________________________________________________

File system: ext3
Boot sector type: -
Boot sector info:
Operating System: Ubuntu 9.04
Boot files/dirs: /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

File system: swap
Boot sector type: -
Boot sector info:

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcab10bee

Partition Boot Start End Size Id System

/dev/sda1 * 63 92,036,384 92,036,322 7 HPFS/NTFS
/dev/sda2 144,516,960 156,295,439 11,778,480 c W95 FAT32 (LBA)
/dev/sda3 92,036,385 144,504,674 52,468,290 5 Extended
/dev/sda5 92,036,448 142,255,574 50,219,127 83 Linux
/dev/sda6 142,255,638 144,504,674 2,249,037 82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="45EE85EC730AFEC6" LABEL="PRESARIO" TYPE="ntfs"
/dev/sda2: LABEL="PRESARIO_RP" UUID="4B6E-6BC0" TYPE="vfat"
/dev/sda5: UUID="c74669e1-16c5-4914-be70-dcdb6046966a" TYPE="ext3"
/dev/sda6: UUID="9ea02603-2354-417c-98be-0928a6f17648" TYPE="swap"

=============================== "mount" output: ===============================

/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-16-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/lisa/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=lisa)
//hudson.dur.ac.uk/d67jpu on /mnt/jdrive type cifs (rw,mand)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=0

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


================================ sda2/boot.ini: ================================

[boot loader]

timeout=0

default=C:\CMDCONS\BOOTSECT.DAT

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons


================================ sda2/BOOT.INI: ================================

[boot loader]

timeout=0

default=C:\CMDCONS\BOOTSECT.DAT

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons


=========================== sda5/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
# grub-install(8), grub-floppy(8),
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
# kopt=root=UUID=c74669e1-16c5-4914-be70-dcdb6046966a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=c74669e1-16c5-4914-be70-dcdb6046966a

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

title Ubuntu 9.04, kernel 2.6.28-16-generic
uuid c74669e1-16c5-4914-be70-dcdb6046966a
kernel /boot/vmlinuz-2.6.28-16-generic root=UUID=c74669e1-16c5-4914-be70-dcdb6046966a ro quiet splash
initrd /boot/initrd.img-2.6.28-16-generic
quiet

title Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid c74669e1-16c5-4914-be70-dcdb6046966a
kernel /boot/vmlinuz-2.6.28-16-generic root=UUID=c74669e1-16c5-4914-be70-dcdb6046966a ro single
initrd /boot/initrd.img-2.6.28-16-generic

title Ubuntu 9.04, kernel 2.6.28-11-generic
uuid c74669e1-16c5-4914-be70-dcdb6046966a
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=c74669e1-16c5-4914-be70-dcdb6046966a ro quiet splash
initrd /boot/initrd.img-2.6.28-11-generic
quiet

title Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid c74669e1-16c5-4914-be70-dcdb6046966a
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=c74669e1-16c5-4914-be70-dcdb6046966a ro single
initrd /boot/initrd.img-2.6.28-11-generic

title Ubuntu 9.04, memtest86+
uuid c74669e1-16c5-4914-be70-dcdb6046966a
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Home Edition
root (hd0,0)
makeactive
chainloader +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title Windows NT/2000/XP
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
UUID=c74669e1-16c5-4914-be70-dcdb6046966a / ext3 relatime,errors=remount-ro 0 1
# swap was on /dev/sda6 during installation
UUID=9ea02603-2354-417c-98be-0928a6f17648 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

=================== sda5: Location of files loaded by Grub: ===================


71.5GB: boot/grub/menu.lst
71.4GB: boot/grub/stage2
71.3GB: boot/initrd.img-2.6.28-11-generic
71.3GB: boot/initrd.img-2.6.28-16-generic
71.4GB: boot/vmlinuz-2.6.28-11-generic
71.3GB: boot/vmlinuz-2.6.28-16-generic
71.3GB: initrd.img
71.3GB: initrd.img.old
71.3GB: vmlinuz
71.4GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde
```

---

### Post by presence1960 on 2009-11-08
your boot.ini for sda2 should read like this:

```
================================ sda2/BOOT.INI: ================================

[boot loader]

timeout=0

default=C:\CMDCONS\BOOTSECT.DAT

[operating systems]

multi(0)disk(0)rdisk(0)partition[COLOR="Red"](2)[/COLOR]\WINDOWS="Microsoft Windows XP Professional" /fastdetect

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons


```

Note the red (2)

Also you cut off a lot of info from your boot info script. Only about 1/2 of your menu.lst is there and all the info following it is missing too.

---

### Post by oldfred on 2009-11-08
There is some debate whether root or rootnoverify is correct. The last thing I read in explanation was that old grub does not read NTFS so for NTFS you have to use rootnoverfy to just jump to that chainboot entry. Your boot flag (*) is set for sda1, so the makeactive is not required. It is required for the recovery boot stanza.

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Home Edition
[COLOR=DarkRed]rootnoverify[/COLOR] (hd0,0)
savedefault
chainloader +1

---

### Post by martinic on 2009-11-08
Both done, to no effect.

---

### Post by chiefrocka on 2009-11-09
I'm having the same problem. I've installed Ubuntu on top of Windows before without anything bad happening. Although this time, the only thing I can think of that is different is that I'm using the 64bit version of Ubuntu. 

While I don't think this should make any difference. Are there any major differences in the boot process for 32bit vs 64bit?

---

### Post by oldfred on 2009-11-10
Everything looks normal? I would use supergrub to reinstall the windows boot to test that it works ok on its own. Then either supergrub or the grub reinstall posted earlier to reinstall grub.

The boot process is all thru grub. The only difference now with grub is that Karmic uses grub2, all previous versions used legacy grub.

---

