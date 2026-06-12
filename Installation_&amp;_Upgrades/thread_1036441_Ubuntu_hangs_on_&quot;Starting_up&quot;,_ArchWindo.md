---
title: "Ubuntu hangs on &quot;Starting up&quot;, Arch/Windows boot fine"
date: 2009-01-10
forum: Installation &amp; Upgrades
---

### Post by specificallygeneric on 2009-01-10
I figured this was the best place to put this.

I've been messing around in Arch for a while, but I'm back in school now and need a more stable Linux distribution, hence I'm going back to Ubuntu, some for its community support, but mostly because of the ease of finding packages made for it. So I happily downloaded 8.10 and burned it at 4x, loaded the live CD (which took longer than I remember it taking in 8.04) and installed onto partition 3, overwriting my old Ubuntu install. I then rebooted and was faced with my age old enemy: GRUB.

Problem being that GRUB does not want to boot most Linux distros at all. When I tried to boot Ubuntu it just hung at "Starting up..." No errors or anything, even with "quiet" taken off the boot lines. No matter how many times I try, it reliably won't boot it, being the stubborn thing it is.

This has happened before. A few years back, when Kanotix (an excellent but not well known distro) was my main distro, I had the same problem. I worked around the problem by using Super Grub Disk, selecting "Boot GNU/Linux" and then choosing the only option, which seemingly brought me back to my normal MBR GRUB but somehow made Linux bootable. Windows always booted fine. Every single distro I've installed to the hard drive has had this problem too, except for one...

Arch (which sits on partition 4) somehow boots fine through some kind of miracle, even without the Super Grub Disk. I've made no changes to its boot options, and it works fine everywhere: on my old Arch MBR-installed GRUB, through Super Grub Disk, and through my freshly-installed-to-MBR Ubuntu GRUB.

When trying to use Super Grub Disk, the normal "Boot GNU/Linux" option doesn't show Ubuntu, it only shows Arch; however, using the Disk's own "Show partitions" option, it correctly lists every partition on my hard drive, including Ubuntu. I've tried using the Ubuntu Live CD to install GRUB to root instead of to MBR and booting that, but it still gives the same "Starting up..." hang.

The two hard drives I've had (the first a Seagate, this one a Maxtor) both had this problem with GRUB. I used some hard drive copying CD that came with my Maxtor to automagically transfer all the contents of the old hard drive onto my new one. I booted my new hard drive and tried to load Ubuntu again to see if it was my old hard drive that was the problem, but alas, it's just the same.

I would appreciate any help I can get here.

My hard drive is SATA, and my partitions go as such:
    1. Windoze XP (ntfs)
    2. Swap for Linux
    3. Ubuntu (ext3)
    4. Arch (ext3)
I have no other hard drives in my computer. My Arch menu.lst is at [http://pastebin.com/f6cda8f38](http://pastebin.com/f6cda8f38) and my Ubuntu menu.lst is at [http://pastebin.com/f49a62051](http://pastebin.com/f49a62051) . If you need any other information just tell me.

Sorry for the long post and my stupid name. Thanks in advance.

---

### Post by caljohnsmith on 2009-01-10
In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your booting problem might be.

---

### Post by specificallygeneric on 2009-01-10
Done, results are at [http://pastebin.com/f818295a](http://pastebin.com/f818295a) .

```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTLDR /NTDETECT.COM /ntdetect.com

sda2: _________________________________________________________________________

    File system:       swap

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of /dev/sda3 
                       and looks at sector 773999125 of the same hard drive 
                       for the stage2 file and on partition #3 for 
                       /boot/grub/menu.lst .
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  [H[2J Arch Linux () ()
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x63af6124

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   739536209   369768073+   7  HPFS/NTFS
/dev/sda2       739536210   741640724     1052257+  82  Linux swap / Solaris
/dev/sda3   *   741640725   913857524    86108400   83  Linux
/dev/sda4       913857525   976768064    31455270   83  Linux

sfdisk -V /dev/sda:

/dev/sda: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="E6E84734E8470273" TYPE="ntfs" 
/dev/sda2: UUID="c7ce48db-61e3-4679-9df1-e0130ac6794c" TYPE="swap" 
/dev/sda3: UUID="ee37066b-d803-48e8-9b89-7b21bc10af91" TYPE="ext3" 
/dev/sda4: UUID="2e8e03e9-9a0d-4861-906d-1ea3dd3842d7" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda4 on / type ext3 (rw)
none on /dev type ramfs (rw)
none on /proc type proc (rw)
none on /sys type sysfs (rw)
none on /dev/pts type devpts (rw)
none on /dev/shm type tmpfs (rw)
/dev/sda3 on /media/disk type ext3 (rw,nosuid,nodev)

================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /SOS

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
# kopt=root=UUID=ee37066b-d803-48e8-9b89-7b21bc10af91 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ee37066b-d803-48e8-9b89-7b21bc10af91

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		ee37066b-d803-48e8-9b89-7b21bc10af91
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ee37066b-d803-48e8-9b89-7b21bc10af91 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		ee37066b-d803-48e8-9b89-7b21bc10af91
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ee37066b-d803-48e8-9b89-7b21bc10af91 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		ee37066b-d803-48e8-9b89-7b21bc10af91
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda4.
title		Arch Linux (on /dev/sda4)
root		(hd0,3)
kernel		/boot/vmlinuz26 root=/dev/disk/by-uuid/2e8e03e9-9a0d-4861-906d-1ea3dd3842d7 ro 
initrd		/boot/kernel26.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda4.
title		Arch Linux Fallback (on /dev/sda4)
root		(hd0,3)
kernel		/boot/vmlinuz26 root=/dev/disk/by-uuid/2e8e03e9-9a0d-4861-906d-1ea3dd3842d7 ro 
initrd		/boot/kernel26-fallback.img
savedefault
boot


=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=ee37066b-d803-48e8-9b89-7b21bc10af91 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=c7ce48db-61e3-4679-9df1-e0130ac6794c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sda3/boot: ==================================

total 11936
drwxr-xr-x  3 root root    4096 2009-01-10 18:41 .
drwxr-xr-x 20 root root    4096 2009-01-10 18:41 ..
-rw-r--r--  1 root root 1029585 2008-10-24 04:29 System.map-2.6.27-7-generic
-rw-r--r--  1 root root  507665 2008-10-24 04:29 abi-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-10-24 04:29 config-2.6.27-7-generic
drwxr-xr-x  2 root root    4096 2009-01-10 18:41 grub
-rw-r--r--  1 root root 8163493 2009-01-10 18:41 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 16:11 memtest86+.bin
-rw-r--r--  1 root root    1073 2008-10-24 04:31 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2244272 2008-10-24 04:29 vmlinuz-2.6.27-7-generic

=============================== sda3/boot/grub: ===============================

total 216
drwxr-xr-x 2 root root   4096 2009-01-10 18:41 .
drwxr-xr-x 3 root root   4096 2009-01-10 18:41 ..
-rw-r--r-- 1 root root    197 2009-01-10 18:41 default
-rw-r--r-- 1 root root     15 2009-01-10 18:41 device.map
-rw-r--r-- 1 root root   8108 2009-01-10 18:41 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-01-10 18:41 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-01-10 18:41 installed-version
-rw-r--r-- 1 root root   8712 2009-01-10 18:41 jfs_stage1_5
-rw-r--r-- 1 root root   5217 2009-01-10 18:41 menu.lst
-rw-r--r-- 1 root root   7352 2009-01-10 18:41 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-01-10 18:41 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-10 18:41 stage1
-rw-r--r-- 1 root root 121460 2009-01-10 18:41 stage2
-rw-r--r-- 1 root root   9556 2009-01-10 18:41 xfs_stage1_5

=========================== sda4/boot/grub/menu.lst: ===========================

# Config file for GRUB - The GNU GRand Unified Bootloader
# /boot/grub/menu.lst

# DEVICE NAME CONVERSIONS 
#
#  Linux           Grub
# -------------------------
#  /dev/fd0        (fd0)
#  /dev/hda        (hd0)
#  /dev/hdb2       (hd1,1)
#  /dev/hda3       (hd0,2)
#

#  FRAMEBUFFER RESOLUTION SETTINGS
#     +-------------------------------------------------+
#          | 640x480    800x600    1024x768   1280x1024
#      ----+--------------------------------------------
#      256 | 0x301=769  0x303=771  0x305=773   0x307=775
#      32K | 0x310=784  0x313=787  0x316=790   0x319=793
#      64K | 0x311=785  0x314=788  0x317=791   0x31A=794
#      16M | 0x312=786  0x315=789  0x318=792   0x31B=795
#     +-------------------------------------------------+

# general configuration:
timeout   9
default   0
color light-blue/black light-cyan/blue

# boot sections follow
# each is implicitly numbered from 0 in the order of appearance below
#
# TIP: If you want a 1024x768 framebuffer, add "vga=773" to your kernel line.
#
#-*

# (0) Arch Linux
title  Arch Linux
root   (hd0,3)
kernel /boot/vmlinuz26 root=/dev/disk/by-uuid/2e8e03e9-9a0d-4861-906d-1ea3dd3842d7 ro
initrd /boot/kernel26.img

# (1) Arch Linux
title  Arch Linux Fallback
root   (hd0,3)
kernel /boot/vmlinuz26 root=/dev/disk/by-uuid/2e8e03e9-9a0d-4861-906d-1ea3dd3842d7 ro
initrd /boot/kernel26-fallback.img

# (1) Windows
title Windows
rootnoverify (hd0,0)
makeactive
chainloader +1

=============================== sda4/etc/fstab: ===============================

# 
# /etc/fstab: static file system information
#
# <file system>        <dir>         <type>    <options>          <dump> <pass>
none                   /dev/pts      devpts    defaults            0      0
none                   /dev/shm      tmpfs     defaults            0      0


/dev/cdrom /media/cdrom   auto    ro,user,noauto,unhide   0      0
/dev/dvd /media/dvd   auto    ro,user,noauto,unhide   0      0
UUID=2e8e03e9-9a0d-4861-906d-1ea3dd3842d7 / ext3 defaults 0 1
UUID=c7ce48db-61e3-4679-9df1-e0130ac6794c swap swap defaults 0 0

================================== sda4/boot: ==================================

total 8148
drwxr-xr-x  3 root root    4096 2009-01-01 01:26 .
drwxr-xr-x 22 root root    4096 2008-10-23 01:57 ..
-rw-r--r--  1 root root  773329 2008-12-21 04:34 System.map26
drwxr-xr-x  2 root root    4096 2009-01-02 15:24 grub
-rw-r--r--  1 root root 5057324 2009-01-01 01:28 kernel26-fallback.img
-rw-r--r--  1 root root  778312 2009-01-01 01:27 kernel26.img
-rw-r--r--  1 root root 1688368 2008-12-21 04:34 vmlinuz26

=============================== sda4/boot/grub: ===============================

total 328
drwxr-xr-x 2 root root   4096 2009-01-02 15:24 .
drwxr-xr-x 3 root root   4096 2009-01-01 01:26 ..
-rw-r--r-- 1 root root   8072 2008-08-01 06:27 e2fs_stage1_5
-rw-r--r-- 1 root root   7816 2008-08-01 06:27 fat_stage1_5
-rw-r--r-- 1 root root   7096 2008-08-01 06:27 ffs_stage1_5
-rw-r--r-- 1 root root   7088 2008-08-01 06:27 iso9660_stage1_5
-rw-r--r-- 1 root root   8676 2008-08-01 06:27 jfs_stage1_5
-rw-r--r-- 1 root root   2042 2009-01-10 19:06 menu.lst
-rw-r--r-- 1 root root   1355 2008-11-12 05:37 menu.lst.pacnew
-rw-r--r-- 1 root root   7320 2008-08-01 06:27 minix_stage1_5
-rw-r--r-- 1 root root   9720 2008-08-01 06:27 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-08-01 06:27 stage1
-rw-r--r-- 1 root root 102614 2008-08-01 06:27 stage2
-rw-r--r-- 1 root root 102614 2008-08-01 06:27 stage2_eltorito
-rw-r--r-- 1 root root   7352 2008-08-01 06:27 ufs2_stage1_5
-rw-r--r-- 1 root root   6696 2008-08-01 06:27 vstafs_stage1_5
-rw-r--r-- 1 root root   9512 2008-08-01 06:27 xfs_stage1_5

=============================== StdErr Messages: ===============================

No errors were reported.

```

---

### Post by caljohnsmith on 2009-01-10
So just to clarify, you do get the Grub menu on start up, but when you select Ubuntu to boot, it immediately hangs? If so, can you boot the Ubuntu Live CD OK, or does that hang too?

---

### Post by specificallygeneric on 2009-01-10
Live CD works fine, but the GRUB I have on my hard drive doesn't boot it.

---

### Post by caljohnsmith on 2009-01-10
Have you by chance tried adding kernel options when booting Ubuntu? How about when you get the Grub menu on start up, select Ubuntu, press "e" to edit the entry, select the "kernel" line, press "e" to edit it, and at the end of the kernel line try adding different kernel options like:
```
noapic nolapic acpi=off pci=noacpi irqpoll ide=nodma nopcmcia all_generic_ide pci=nomsi
```
After adding the option to the kernel line, press enter to save the change, and finally "b" to boot. Let me know if any of those options makes any difference.

---

### Post by specificallygeneric on 2009-01-10
Tried a few of those by themselves, and even all of them at the same time. Didn't seem to do anything. I'll test more of them later on if you want.

NEXT DAY EDIT:
Dawn of the Second Day (48 hours remain)

I thought that maybe _purging everything on my drive_ might help it boot up, so I deleted every partition and made a new ext3 and swap. After I installed, no luck, same deal. I had nothing to boot into anymore (but memtest86+ worked great, woohoo.) so I fumbled around trying to get Super Grub Disk to boot it, but it couldn't find GRUB on my Ubuntu partition apparently (kept giving error 15). So I took my old Arch install CD and spent the rest of the night configuring my new system, which boots fine yet again and is what I have now.
I guess it all works out in the end. I don't have XP anymore, but that thing was so bogged down after me torturing it for two or three years that it started to become crippled so bad that it took 10 seconds for My Documents to appear. My father sure won't be happy with me having no XP, but I suppose it's my PC anyway. It's a good feeling though, having all this space freed from killing off my (mostly useless) games and things...I guess this is Happy End.

---

