---
title: "Install problem with dual boot"
date: 2009-02-05
forum: Installation &amp; Upgrades
---

### Post by emb on 2009-02-05
Hi Guys,

I have been having some problems after installing Ubuntu 8.10 on a machine with an exsisting XP install.

I can install Ubuntu ok, everything completes fine.

I then reboot the PC removing the setup disk. Here is where the problem starts.

I cannot get the system to present me with an option to choose either Winodws or Ubuntu.

The system loads right into XP.

Any ideas on how to resolve ?

Thanks in advance.

Emb.

---

### Post by feelshift on 2009-02-05
From what you say, the Grub boot-loader isn't installed. Did you disabled "Install Grub boot-loader" some point during installation?

---

### Post by caljohnsmith on 2009-02-05
Do you have more than one HDD? If so, that's most likely the issue. How about going into your BIOS and change the "boot order" to boot a different drive than the Windows drive that you are currently booting first, and see if that helps. If not, how about booting your Ubuntu Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to the Live CD desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by emb on 2009-02-05
Thanks for the swift response.

I have also tried to remove all but the one boot disk and the results are the same, there is no option to boot Ubuntu.

I did as suggested.

Thanks again.

Emb

```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   

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
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4df24df1

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   398,267,414   398,267,352   7 HPFS/NTFS


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa1774fab

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   488,392,064   488,392,002   7 HPFS/NTFS


Drive sdc: _____________________________________________________________________

Disk /dev/sdc: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6c42cc84

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   127,475,774   127,475,712   7 HPFS/NTFS
/dev/sdc2         127,475,775   160,071,659    32,595,885   5 Extended
/dev/sdc5         127,475,838   158,609,744    31,133,907  83 Linux
/dev/sdc6         158,609,808   160,071,659     1,461,852  82 Linux swap / Solaris


Drive sdd: _____________________________________________________________________

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa029fd02

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63   488,392,064   488,392,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________


/dev/sda1: UUID="10448CFA448CE3B6" LABEL="Lucie Storage" TYPE="ntfs" 
/dev/sdb1: UUID="D48C869E8C867B2E" LABEL="Media" TYPE="ntfs" 
/dev/sdc1: UUID="D084F6B984F6A160" TYPE="ntfs" 
/dev/sdc5: UUID="b0079912-4117-4cf0-8ce7-9c63899752b2" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc6: TYPE="swap" UUID="6ddb3612-0cf0-4250-97e1-c0d88d09e99c" 
/dev/sdd1: UUID="BA085EA2085E5E07" LABEL="Store" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

================================ sdc1/boot.ini: ================================

[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sdc5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=b0079912-4117-4cf0-8ce7-9c63899752b2 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,4)

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b0079912-4117-4cf0-8ce7-9c63899752b2 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b0079912-4117-4cf0-8ce7-9c63899752b2 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdd1
title		Windows NT/2000/XP
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1


=============================== sdc5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc5
UUID=b0079912-4117-4cf0-8ce7-9c63899752b2 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc6
UUID=6ddb3612-0cf0-4250-97e1-c0d88d09e99c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc5: Location of files loaded by Grub: ===================


  79.3GB: boot/grub/menu.lst
  79.4GB: boot/grub/stage2
  79.3GB: boot/initrd.img-2.6.24-19-generic
  79.3GB: boot/vmlinuz-2.6.24-19-generic
  79.3GB: initrd.img
  79.3GB: vmlinuz

================================ sdd1/boot.ini: ================================

[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Windows Server 2003, Standard" /noexecute=optout /fastdetect



```

---

### Post by caljohnsmith on 2009-02-05
So can you make your 82 GB Ubuntu sdc drive first in the BIOS boot order? If so, how about trying:
```
sudo grub
grub> root (hd2,4)
grub> setup (hd2)
grub> quit
```
Also, you'll need to modify your menu.lst a little, so how about doing:
```
sudo mount /dev/sdc5 /mnt
gksudo gedit /mnt/boot/grub/menu.lst
```
And change all the Ubuntu entries to use (hd0,4) rather than (hd1,4) similar to:
```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		[COLOR="Blue"](hd0,4)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b0079912-4117-4cf0-8ce7-9c63899752b2 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
```
Also change the "#groot=(hd1,4)" line to use (hd0,4):
```
# groot=[COLOR="Blue"](hd0,4)[/COLOR]
```
Then reboot, set your BIOS to boot the Ubuntu sdc drive, and let me know how far you get. We can work from there.

---

