---
title: "WIndows XPSP2 &amp; Ubuntu 8.10 DUal boot -&gt; Disk Mistake before Grub"
date: 2009-02-11
forum: Installation &amp; Upgrades
---

### Post by sun0id on 2009-02-11
Hi guys!

At first, take my apologise for my english pls :)

I have a very big problem with XPSP2 and Ubuntu 8.10!

The problem is that I installed Windows XP SP2. I did it right. It's okay. 

After I installed Ubuntu to another partition with ext3 file system.
 
**But when the installation was finished (after the reboot) i got a screen that told me : "Disk Mistake" with natural black background** and nothing is happened.

BUT! I wanted to grow up and I tried that I put on my Ubuntu CD then I choosed "Boot from the primary HDD". And WOALA.. Grub is loaded, everything is okay....

So my question is.. What can I do for that I boot normally, without the CD's help?

Thank you for your answers!

Best regards

---

### Post by cariboo on 2009-02-11
It sounds like you may installed grub on the drive you installed Ubuntu on. To resolve the problem boot from the LiveCD and once at the desktop open an Applications-->Accessoires-->Terminal and type:

```
sudo grub
```

at the grub prompt type:

```
find /boot/grub/stage1
```

the result should be something like this:

```
(hd0,0 or (hd1,0)
```

Next at the prompt type:

```
root (hd0,0)
```

replace (hd0,0) with the result of the find command.
Next type:

```
setuo (hd0)
```

Use the result of the find command without the partition number. THe final step type:

```
quit
```

at the prompt and reboot.

Jim

---

### Post by sun0id on 2009-02-12
Hi Jim!

Thank you for your help!

I did it that you said, but it doesn't works for me!

If i wrote "find /boot/grub/stage1" i get "hd(0,4)" and i configured things by 0,4. may its a problem, i mean it must be 0,1 at basically?

By the way the reason is still: 

"Disk Mistake 
Press a button"

---

### Post by caljohnsmith on 2009-02-12
Sun0id, in order to get a clearer picture of your setup, how about booting your Ubuntu Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to the Live CD desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by sun0id on 2009-02-12
Ok, I put all!

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd4d3e54f

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   102,398,309   102,398,247   7 HPFS/NTFS
/dev/sda2         102,398,310   312,576,704   210,178,395   f W95 Ext d (LBA)
/dev/sda5         102,398,373   308,464,064   206,065,692  83 Linux
/dev/sda6         308,464,128   312,576,704     4,112,577  82 Linux swap / Solaris


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 2031 MB, 2031091712 bytes
255 heads, 63 sectors/track, 246 cylinders, total 3966976 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0217934c

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     3,966,975     3,966,913   6 FAT16

/dev/sdb1 ends after the last cylinder of /dev/sdb

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="C8D85EB3D85E9F8C" TYPE="ntfs" 
/dev/sda5: UUID="fff5e0a5-f94b-46ad-8fb4-37256166875c" TYPE="ext3" 
/dev/sda6: UUID="101e5ecd-4d82-4cf8-abd8-a034521a70bd" TYPE="swap" 
/dev/sdb1: SEC_TYPE="msdos" LABEL="KINGSTON2GB" UUID="84A7-0625" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
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
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/sinkovicz/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=sinkovicz)
/dev/sdb1 on /media/KINGSTON2GB type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=sinkovicz)

================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional - magyar" /noexecute=optin /fastdetect


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
# kopt=root=UUID=fff5e0a5-f94b-46ad-8fb4-37256166875c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=fff5e0a5-f94b-46ad-8fb4-37256166875c

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
uuid		fff5e0a5-f94b-46ad-8fb4-37256166875c
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=fff5e0a5-f94b-46ad-8fb4-37256166875c ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		fff5e0a5-f94b-46ad-8fb4-37256166875c
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=fff5e0a5-f94b-46ad-8fb4-37256166875c ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		fff5e0a5-f94b-46ad-8fb4-37256166875c
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=fff5e0a5-f94b-46ad-8fb4-37256166875c ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		fff5e0a5-f94b-46ad-8fb4-37256166875c
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=fff5e0a5-f94b-46ad-8fb4-37256166875c ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		fff5e0a5-f94b-46ad-8fb4-37256166875c
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional - magyar
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=fff5e0a5-f94b-46ad-8fb4-37256166875c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=101e5ecd-4d82-4cf8-abd8-a034521a70bd none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  71.0GB: boot/grub/menu.lst
  71.0GB: boot/grub/stage2
  70.9GB: boot/initrd.img-2.6.27-11-generic
  71.0GB: boot/initrd.img-2.6.27-7-generic
  71.0GB: boot/vmlinuz-2.6.27-11-generic
  71.0GB: boot/vmlinuz-2.6.27-7-generic
  70.9GB: initrd.img
  71.0GB: initrd.img.old
  71.0GB: vmlinuz
  71.0GB: vmlinuz.old

```

---

### Post by caljohnsmith on 2009-02-12
It looks like you have Grub correctly installed to your sda drive, and that's also supported by the fact that you can at least boot your sda drive using the Live CD. So I think your problem is most likely with how your HDD is set up in BIOS, or maybe even with your BIOS boot order. The first thing to check would be to make sure the sda drive is before your sdb drive in your BIOS boot order, so that the sda drive will be booted on start up. If that's not the issue, how about checking your BIOS settings and let me know what HDD-related settings you have available for your sda drive. Look for settings like "auto-detect", LBA, CHS, RAID, AHCI/HCI/EHCI vs. IDE, IDE-emulation, ACPI, DMA, etc. Also, is your sda drive IDE or SATA?

---

### Post by sun0id on 2009-02-12
Ohh man we shot the problem down :):):)

So the mistake was in the BIOS settings, where is The SATA Controller mode!

There are four option: 
1. Native IDE
2. RAID
3. Legacy IDE
4. SATA->AHCI

It was on the Native IDE option... but after I changed it to Legacy IDE then everything is gonna be okay :):)

Thank you so much  ;)
Also thanks to cariboo907

---

### Post by caljohnsmith on 2009-02-12
That's great news that simply changing your BIOS setting to "Legacy IDE" fixed the problem. Cheers and enjoy your Ubuntu install. :)

---

### Post by sun0id on 2009-02-12
Yes, it's great :) I enjoying ubuntu so... the other one operation system what name is "we dont say it because don't want to hurt anyone" is not enemy to Ubuntu :):) I had so much problem with Intel HD Audio too on linux, but this forum was gave a big help and we know nothing is impossible :)

---

