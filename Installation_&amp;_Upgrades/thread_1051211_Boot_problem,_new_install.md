---
title: "Boot problem, new install"
date: 2009-01-26
forum: Installation &amp; Upgrades
---

### Post by tommy1987 on 2009-01-26
Hi,

I've installed jaunty (development branch).

My setup is as follows:

/dev/hdd
  /dev/hdd1 (ntfs) (Windows XP) (boot flag)
  /dev/hdd2 (linux-swap)
  /dev/hdd3 (ext3) (empty at present)

/dev/sda      (ext4) (Ubuntu Jaunty) (boot flag)
  /dev/sda2   (extended)
    /dev/sda5 (linux-swap)

When I booted I got error 17 with grub. I had FreeBSD and ArchLinux installed before on the hard drive which Ubuntu has now been installed to. I let the installer have the whole drive and set it up accordingly. How can I get grub booting from my linux install, I've tried using the live CD and setting up the hard drive again but to no avail. I've also used super grub CD and that doesn't work either to restore grub. Odd.

Please help,

Thanks a lot.

---

### Post by Pumalite on 2009-01-26
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

---

### Post by caljohnsmith on 2009-01-26
In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu Live CD desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by tommy1987 on 2009-01-26
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Boot file info:     
    Operating System:  Ubuntu jaunty (development branch)
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

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
    Boot file info:     
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Boot file info:     
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8f8000b1

Partition  Boot        Start          End         Size  Id System

/dev/sda1    *            63  964,687,184  964,687,122  83 Linux
/dev/sda2        964,687,185  976,768,064   12,080,880   5 Extended
/dev/sda5        964,687,248  976,768,064   12,080,817  82 Linux swap / Solaris


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders, total 120103200 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf67ce581

Partition  Boot        Start          End         Size  Id System

/dev/sdb1    *         2,048   71,682,047   71,680,000   7 HPFS/NTFS
/dev/sdb2         71,682,048   73,658,024    1,975,977  82 Linux swap / Solaris
/dev/sdb3         73,658,025  120,101,939   46,443,915  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="f95ebb3f-9d5c-4bf7-9817-fff8daf303e4" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="8b0086cf-f4a4-45e8-9a14-5d319d5433cd" TYPE="swap" 
/dev/sdb1: UUID="FE58195758190FCF" TYPE="ntfs" 
/dev/sdb2: UUID="602913a8-762d-493d-8c93-b19e0a0a115f" TYPE="swap" 
/dev/sdb3: UUID="3b561682-030e-4c49-9e6b-428cb5fb6d29" SEC_TYPE="ext2" TYPE="ext3" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-4-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-4-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

=========================== sda1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=f95ebb3f-9d5c-4bf7-9817-fff8daf303e4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f95ebb3f-9d5c-4bf7-9817-fff8daf303e4

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

title		Ubuntu jaunty (development branch), kernel 2.6.28-4-generic
uuid		f95ebb3f-9d5c-4bf7-9817-fff8daf303e4
kernel		/boot/vmlinuz-2.6.28-4-generic root=UUID=f95ebb3f-9d5c-4bf7-9817-fff8daf303e4 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-4-generic
quiet

title		Ubuntu jaunty (development branch), kernel 2.6.28-4-generic (recovery mode)
uuid		f95ebb3f-9d5c-4bf7-9817-fff8daf303e4
kernel		/boot/vmlinuz-2.6.28-4-generic root=UUID=f95ebb3f-9d5c-4bf7-9817-fff8daf303e4 ro  single
initrd		/boot/initrd.img-2.6.28-4-generic

title		Ubuntu jaunty (development branch), memtest86+
uuid		f95ebb3f-9d5c-4bf7-9817-fff8daf303e4
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
rootnoverify	(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=f95ebb3f-9d5c-4bf7-9817-fff8daf303e4 /               ext3    relatime,errors=remount-ro 0       1
# none was on /dev/sda5 during installation
UUID=8b0086cf-f4a4-45e8-9a14-5d319d5433cd none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location  of files loaded by Grub: ===================


  41.3GB: boot/grub/menu.lst
  41.2GB: boot/grub/stage2
  41.3GB: boot/initrd.img-2.6.28-4-generic
  41.2GB: boot/vmlinuz-2.6.28-4-generic
  41.3GB: initrd.img
  41.2GB: vmlinuz

================================ sdb1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=============================== StdErr Messages: ===============================

No errors were reported.
```

---

### Post by caljohnsmith on 2009-01-26
It looks like Grub is correctly installed to the MBR of your Ubuntu drive, so to get a Grub error 17 in your situation sometimes can be because of the way you have your Ubuntu HDD set up in BIOS. Can you let me know what HDD-related settings you have in your BIOS for the Ubuntu drive? Look for settings like "auto-detect", LBA, CHS, RAID, AHCI/HCI/EHCI vs. IDE, IDE-emulation, ACPI, DMA, etc.

If you boot your Live CD and choose "boot from first HDD", what happens? Also, in some rare cases you can circumvent illogical Grub errors (like yours) by installing Grub to the MBR without its stage1.5 file, so that the Grub stage1 file in the MBR points directly to the stage2 file in the Ubuntu partition. It would only take a minute to try, so if you want to give it a shot:
```
sudo grub
grub> root (hd0,0)
grub> install /boot/grub/stage1 (hd0) /boot/grub/stage2 p /boot/grub/menu.lst
grub> quit
```
Let me know if that makes any difference; if it doesn't work, you will probably get something like just the words "GRUB" on your screen, but no error.

---

### Post by tommy1987 on 2009-01-26
Hi, 

That seems to make no difference, Windows boots in the case that I make those changes.

It also boots when I select boot from first hard drive.

Arrrrggggggh!

Thanks,

---

### Post by caljohnsmith on 2009-01-26
So what happens when you set the Ubuntu drive to boot first? Do you still get the error 17? Did you try installing Grub using the commands from my previous post? If so, what happens when you boot the Ubuntu drive after that?

---

### Post by tommy1987 on 2009-01-26
I have found that I now have a 'press F12 for boot menu' appearing. In this menu it appears that I can select my hdd with Ubuntu on it and everything boots fine. How can I make this permanent? I'm guessing it is a bios problem from that.

Thanks

---

### Post by caljohnsmith on 2009-01-26
You could go into your BIOS and change the "boot order" so that the Ubuntu drive is first to boot, that way you won't have to choose to boot the Ubuntu drive via F12 every time on start up.

---

### Post by tommy1987 on 2009-01-27
Thanks for your help.

---

