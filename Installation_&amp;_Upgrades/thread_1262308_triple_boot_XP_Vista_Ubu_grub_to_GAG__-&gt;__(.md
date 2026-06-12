---
title: "triple boot XP Vista Ubu grub to GAG  -&gt;  :("
date: 2009-09-09
forum: Installation &amp; Upgrades
---

### Post by soumo on 2009-09-09
Any help is appreciated!

I have posted elsewhere to no avail, but I will now try here:

I have an asus eee pc netbook without a cd drive. It came with xp, I added vista, no probs, the bootloader offered me vista or "an earlier version of windows" (xp), both worked.

I added ubuntu into a 3rd extended partitions (there was already a 4th which is either a boot partition or boot booster/optimizer or some such bios related enhancer). As in the screencap attached, the extended partition has a shared ntfs storage space, then the linux root partition, and finally a swap partition. This worked as well, and all was fine til I tried GAG loader, which did not let me use any OS. I reinstalled ubuntu and eliminated GAG in the process.

```
grub> find /boot/grub/stage1
 (hd0,5)
```

I think this means I installed grub in the root partition, though I thought it was the first partition. **Is there a way to check?** I may have mixed things up on the 2nd install.

On start up now, grub offers me the linux kernals which work, and vista which offers me the sub choices xp & vista. But when I select those I get either a

```
/netldr
```

or

```
/windows/system32/winload.exe
```

error codes 0xc000000e

From these forums I gather the file systems are not corrupt but that they are incorrectly pointed to. 

Can I use BCD to fix things?
Can I get it to tri-boot?
Can I do this from linux (only accessible OS, though I have a live boot linux usb key as well) aas I have Wine installed?
Can I run BCD from a usb key on boot up?

Running a diagnostic script from these forums:

```
============================= Boot Info Summary: ==============================

=> Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

File system: ntfs
Boot sector type: Windows Vista
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows XP
Boot files/dirs: /boot.ini /bootmgr /Boot/BCD /grldr /ntldr 
/NTDETECT.COM

sda2: _________________________________________________________________________

File system: ntfs
Boot sector type: Windows Vista
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows Vista
Boot files/dirs: /Windows/System32/winload.exe

sda3: _________________________________________________________________________

File system: Extended Partition
Boot sector type: -
Boot sector info: 

sda5: _________________________________________________________________________

File system: ntfs
Boot sector type: Windows Vista
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: 
Boot files/dirs: 

sda6: _________________________________________________________________________

File system: ext4
Boot sector type: -
Boot sector info: 
Operating System: Ubuntu 9.04
Boot files/dirs: /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

File system: swap
Boot sector type: -
Boot sector info: 

sda4: _________________________________________________________________________

File system: 
Boot sector type: Grub
Boot sector info: Grub is installed in the boot sector of sda4 and looks 
at sector 135445212 of the same hard drive for the 
stage2 file, but no stage2 files can be found at this 
location.
Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0001b1fe

Partition Boot Start End Size Id System

/dev/sda1 * 63 12,289,724 12,289,662 7 HPFS/NTFS
/dev/sda2 12,289,725 135,170,909 122,881,185 7 HPFS/NTFS
/dev/sda3 135,170,910 312,496,379 177,325,470 5 Extended
/dev/sda5 222,387,795 304,303,229 81,915,435 7 HPFS/NTFS
/dev/sda6 135,171,036 222,387,794 87,216,759 83 Linux
/dev/sda7 304,303,293 312,496,379 8,193,087 82 Linux swap / Solaris
/dev/sda4 312,496,380 312,576,704 80,325 ef EFI (FAT-12/16/32)


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="A4EC3CCCEC3C9B0E" LABEL="XP" TYPE="ntfs" 
/dev/sda2: UUID="11C16CF535C1E69B" LABEL="Vista" TYPE="ntfs" 
/dev/sda5: UUID="2E0FFDEC29C2AB5D" LABEL="Cyclone" TYPE="ntfs" 
/dev/sda6: UUID="52ebc803-4411-49c7-ace8-045eb3407739" TYPE="ext4" 
/dev/sda7: UUID="9940f63e-83ec-46e9-8449-e0b26ce1958b" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda6 on / type ext4 (rw,relatime,errors=remount-ro)
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
/dev/sda1 on /media/XP type fuseblk (rw,noexec,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda2 on /media/Vista type fuseblk (rw,noexec,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda5 on /media/Cyclone type fuseblk (rw,noexec,nosuid,nodev,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/soumo/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=soumo)


================================ sda1/boot.ini: ================================

;
;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /NOEXECUTE=OPTIN /FASTDETECT

=========================== sda6/boot/grub/menu.lst: ===========================

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
timeout 5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
# color cyan/blue white/blue
color red/light-gray white/magenta

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gKhU8/$aW87kMN1LfV3P2b7znUoe/
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
# kopt=root=UUID=52ebc803-4411-49c7-ace8-045eb3407739 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=52ebc803-4411-49c7-ace8-045eb3407739

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
# howmany=2

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

title Ubuntu 9.04, kernel 2.6.28-15-generic
uuid 52ebc803-4411-49c7-ace8-045eb3407739
kernel /boot/vmlinuz-2.6.28-15-generic root=UUID=52ebc803-4411-49c7-ace8-045eb3407739 ro quiet splash 
initrd /boot/initrd.img-2.6.28-15-generic
quiet

title Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid 52ebc803-4411-49c7-ace8-045eb3407739
kernel /boot/vmlinuz-2.6.28-15-generic root=UUID=52ebc803-4411-49c7-ace8-045eb3407739 ro single
initrd /boot/initrd.img-2.6.28-15-generic

title Ubuntu 9.04, kernel 2.6.28-11-generic
uuid 52ebc803-4411-49c7-ace8-045eb3407739
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=52ebc803-4411-49c7-ace8-045eb3407739 ro quiet splash 
initrd /boot/initrd.img-2.6.28-11-generic
quiet

title Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid 52ebc803-4411-49c7-ace8-045eb3407739
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=52ebc803-4411-49c7-ace8-045eb3407739 ro single
initrd /boot/initrd.img-2.6.28-11-generic

title Ubuntu 9.04, memtest86+
uuid 52ebc803-4411-49c7-ace8-045eb3407739
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows Vista (loader)
rootnoverify (hd0,0)
savedefault
##makeactive
chainloader +1

#title Windows XP
#find --set-root /ntldr
#chainloader /ntldr

#title Windows Vista
#find --set-root /winload
#chainloader /winload

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# / was on /dev/sda6 during installation
UUID=52ebc803-4411-49c7-ace8-045eb3407739 / ext4 relatime,errors=remount-ro 0 1
# swap was on /dev/sda7 during installation
UUID=9940f63e-83ec-46e9-8449-e0b26ce1958b none swap sw 0 0
# XP /dev/sda1
UUID=A4EC3CCCEC3C9B0E /media/XP ntfs uid=1000,users,umask=0022 0 0
# Vista /dev/sda2
UUID=11C16CF535C1E69B /media/Vista ntfs uid=1000,users,umask=0022 0 0
# Cyclone /dev/sda5
UUID=2E0FFDEC29C2AB5D /media/Cyclone ntfs uid=1000,users,umask=0022 0 0


=================== sda6: Location of files loaded by Grub: ===================


72.3GB: boot/grub/menu.lst
69.3GB: boot/grub/stage2
70.9GB: boot/initrd.img-2.6.28-11-generic
70.9GB: boot/initrd.img-2.6.28-15-generic
71.2GB: boot/vmlinuz-2.6.28-11-generic
69.7GB: boot/vmlinuz-2.6.28-15-generic
70.9GB: initrd.img
70.9GB: initrd.img.old
69.7GB: vmlinuz
71.2GB: vmlinuz.old
```

Thanks in advance, any clues might help.

---

### Post by soumo on 2009-09-18
OK, as I thought it was not file corruption:

I prepared a boot usb, via vista recovery tool.
I then chose the repair option and within 0.000001s it detected a windows vista install that was not found.  I chose to repair. 

It rebooted, and let me log on to vista!

Only I do not have the correct permissions on my desktop so all I get is a blank blue screen.  I'm guessing it has to do with mount/accessing in ubu.

I will now try to remedy that...

BTW, before this I tried a myriad attempts to fix the boot sector and somehow messed up my ubuntu :( on start up I get an error:
Gave up waiting for root device.
ALERT! /dev/disk/by-uuid/###################### does not exist, dropping to a shell!
Then it goes into busybox (initramfs)

I am thinking recovery at this point, but may try a few more options first.
If anyone needs info on getting a boot usb let me know.


XP is still not finding /ntldr, but I imagine all I need to do is a similar XP restore...

---

### Post by stlsaint on 2009-09-19
need to install grub on (hd0) instead of being (hd0,5)
hopefully then Grub will start looking in the right places for other OS's!

 1. Boot your computer up with Ubuntu CD
   2. Open a terminal window or switch to a tty.
   3. Go SuperUser (that is, type "sudo -s"). Enter root passwords as necessary.
   4. Type "grub"
   5. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". Use whatever your computer spits out for the following lines.
   6. Type "root (hd0,1)", or whatever your hard disk + boot partition numbers are for Ubuntu.
   7. Type "setup (hd0)", to install GRUB to MBR
   8. Quit grub by typing "quit".
   9. Reboot and remove the bootable CD.

---

### Post by soumo on 2009-09-19
Thank you for your help!

-the find command gave me (hd0,5)
-the setup gave me;
Checking if stages 1, 2, 1_5 exit...yes
> Running "embed /boot/grub/e2fs_stage1_5 (hd0)"... 17 sectors are embedded.
succeeded
Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0.5)/boot/grub/stage2 /boot/grub/menu.lst"... failed

Error 22: No such partition

Messed up.

---

### Post by soumo on 2009-09-19
Okay, so now I can't even boot into ubuntu busybox :(

It hangs at: 
GRUB Loading stage1.5

If i try booting off an XP usb key I get:
BOOTMGR is missing (error from my xp key)

It then tries to go into
GRUB Loading stage1.5
again, but this time I get the message:
Missing operating system.

---

### Post by soumo on 2009-09-19
Tried rebooting into live usb, partition editor shows my hard drive has one big unallocated partition.  Does that mean it's fried now?!

Am I looking at a reinstall?

---

