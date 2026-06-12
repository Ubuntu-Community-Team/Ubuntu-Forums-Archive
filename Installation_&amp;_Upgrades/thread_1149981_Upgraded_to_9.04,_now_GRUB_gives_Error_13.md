---
title: "Upgraded to 9.04, now GRUB gives Error 13"
date: 2009-05-05
forum: Installation &amp; Upgrades
---

### Post by thunderd on 2009-05-05
I updated to 9.04 a few days ago and everything was just peachy.  However, only today did I need to log into Windows XP for something, and I got a GRUB Error 13.  Here's my GRUB menu.lst:
> title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		17df6909-23b2-4262-aa3e-5187cba4df89
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=17df6909-23b2-4262-aa3e-5187cba4df89 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		17df6909-23b2-4262-aa3e-5187cba4df89
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=17df6909-23b2-4262-aa3e-5187cba4df89 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		17df6909-23b2-4262-aa3e-5187cba4df89
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
root		(hd2,0)
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

Any suggestions?

---

### Post by Bartender on 2009-05-05
You have three HDD's, and Windows is on the third one??

title Microsoft Windows XP Professional
root (hd2,0)

---

### Post by thunderd on 2009-05-05
That's correct; I have Ubuntu on hd0, media on hd1, and Windows on hd2.

---

### Post by caljohnsmith on 2009-05-05
Grub on start up sees the order of your drives the same as your BIOS boot order, not as they are ordered once you boot into linux. That means Windows may be on (hd1) and not (hd2) depending on how your BIOS boot order is set up. So with that in mind, how about first trying:
```
title Microsoft Windows XP Professional
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1 
```
If for some reason that doesn't work, it would help to get a clearer picture of your setup, so how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

John

---

### Post by thunderd on 2009-05-06
Thanks for the assistance, John.  I tried changing the grub menu, to no avail.  It tried to boot from hd1, and just did nothing.  Here's the result from the boot infor script:
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on boot drive #3 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
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
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0191372c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   300,511,889   300,511,827  83 Linux
/dev/sda2         300,511,890   312,576,704    12,064,815   5 Extended
/dev/sda5         300,511,953   312,576,704    12,064,752  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
16 heads, 63 sectors/track, 969021 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc981f3c6

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   976,770,143   976,770,081   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0140013f

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   488,375,999   488,375,937   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="17df6909-23b2-4262-aa3e-5187cba4df89" TYPE="ext3" 
/dev/sda5: UUID="14f320ba-4b29-4ad4-982d-a189cd17da6d" TYPE="swap" 
/dev/sdb1: UUID="F4DCC016DCBFD15A" LABEL="Media" TYPE="ntfs" 
/dev/sdc1: UUID="0054E5EE54E5E5FE" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/dan/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dan)


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
# kopt=root=UUID=17df6909-23b2-4262-aa3e-5187cba4df89 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=17df6909-23b2-4262-aa3e-5187cba4df89

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		17df6909-23b2-4262-aa3e-5187cba4df89
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=17df6909-23b2-4262-aa3e-5187cba4df89 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		17df6909-23b2-4262-aa3e-5187cba4df89
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=17df6909-23b2-4262-aa3e-5187cba4df89 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		17df6909-23b2-4262-aa3e-5187cba4df89
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
rootnoverify	(hd2,0)
map		(hd0) (hd2)
map		(hd2) (hd0)
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
UUID=17df6909-23b2-4262-aa3e-5187cba4df89 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=14f320ba-4b29-4ad4-982d-a189cd17da6d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


 121.3GB: boot/grub/menu.lst
 121.3GB: boot/grub/stage2
 121.4GB: boot/initrd.img-2.6.28-11-generic
 121.4GB: boot/vmlinuz-2.6.28-11-generic
 121.4GB: initrd.img
 121.4GB: vmlinuz

================================ sdc1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

```

Again, thank you for your help.

---

### Post by caljohnsmith on 2009-05-06
> **thunderd said:**
> Thanks for the assistance, John.  I tried changing the grub menu, to no avail.  It tried to boot from hd1, and just did nothing.  
So when you tried the Windows entry I gave in my previous post on start up, did the computer hang on "starting up..." or what exactly happened? Also, have you tried setting your Windows 250 GB drive first in your BIOS boot order and try booting directly into Windows? That would let us know whether you truly have a Grub problem or if maybe you have a Windows problem at this point instead. Let me know what you come up with, and we can work from there.

John

---

### Post by thunderd on 2009-05-06
> **caljohnsmith said:**
> So when you tried the Windows entry I gave in my previous post on start up, did the computer hang on "starting up..." or what exactly happened? Also, have you tried setting your Windows 250 GB drive first in your BIOS boot order and try booting directly into Windows? That would let us know whether you truly have a Grub problem or if maybe you have a Windows problem at this point instead. Let me know what you come up with, and we can work from there.

John

To answer your first question, yes, the computer displayed "starting up..." and then did nothing.  When I checked the BIOS order for the hard drvies, it was interesting.  The order was:

1. 250GB XP drive
2. 500GB media drive
3. 160GB Ubuntu Drive

I tried changing the order, going Ubuntu->XP->Media, but got the "starting up" result when I tried booting to (hd1,0).  I'll keep trying to find a way to boot directly to XP and will post the results when I am successful.  However, I think in the boot_info_script report, it said there were no errors found in the boot parameters, so hopefully the problems isn't with my XP installation.  Thanks!

---

### Post by caljohnsmith on 2009-05-06
OK, I see part of the problem that I missed earlier; you have Grub installed to the MBR of your Windows sdc drive, so booting that drive directly on start up will either give you the Grub menu or possibly a Grub error (it depends on how the other drives are ordered in your BIOS boot order). How about doing the following to restore a Windows MBR to your sdc drive:
```
sudo apt-get install lilo
sudo lilo -M /dev/sdc mbr
```
Then reboot, set your 250 GB Windows drive to be first in the BIOS boot order, and let me know what happens. We can work from there.

John

---

### Post by thunderd on 2009-05-06
I installed lilo, and it works!  When I set my BIOS to boot to the Windows hard drive first, XP starts up automatically.  Unfortunately, in order to log into Ubuntu, I have to reorder my BIOS so my Ubuntu hard drive comes first.  This is something I can live with, but would prefer not to.  I did try using GRUB to log into XP after this fix, and it's the same error 13 as before.

---

### Post by caljohnsmith on 2009-05-07
That's good news that XP will at least boot when it is first in your BIOS boot order, but sorry we couldn't make it boot from Ubuntu's Grub. Instead of trying to boot Ubuntu and Windows from Ubuntu's Grub menu, another option would be to install Grub4DOS inside of Windows, and then use Grub4DOS in Windows to boot both XP and Ubuntu; that way you wouldn't have to change your BIOS every time you wanted to boot either Ubuntu or Windows. If you are interested in giving that a shot, let me know. 

John

---

