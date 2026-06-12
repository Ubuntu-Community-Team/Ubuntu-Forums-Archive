---
title: "External HDD not Booting Ubuntu"
date: 2009-10-04
forum: Installation &amp; Upgrades
---

### Post by Habboblob on 2009-10-04
I have an external HDD which I have installed Ubuntu recently today.
The HDD has 2 partitions,
1, A partition where I store all my files
2, The Ubuntu partition

The problem is, partition 1 is infront of partition 2, so there is nothing to boot it from.

Here is a picture to help describe:
[img]http://victorystreet.net/uploader/filestore/fb/-12r-63uXB.Screenshot.png._[/img]


Is there anyway which I can move partition 2 infront of partition 1, so that it can boot partition 2? Because I think it's trying to boot off partition 1 because it is infront of partition 2.

---

### Post by Habboblob on 2009-10-04
Anyone please?

I am currently only running Ubuntu off the LiveCD.

---

### Post by presence1960 on 2009-10-04
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD with the external disk plugged in. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Habboblob on 2009-10-04
> **presence1960 said:**
> Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD with the external disk plugged in. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

Tried that didn't work.
Results:
```
ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot_info_script*.sh
bash: /home/ubuntu/Desktop/boot_info_script*.sh: No such file or directory
ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot_info_script.sh
bash: /home/ubuntu/Desktop/boot_info_script.sh: No such file or directory

```

So I downloaded the bootinfoscript off your signature and ran that.
That created a results file.

Here is the contents of the results file:
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #3 in 
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /grldr /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x41ab2316

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   312,480,314   312,480,252   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000975db

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   547,013,249   547,013,187   7 HPFS/NTFS
/dev/sdb2         547,013,250   625,137,344    78,124,095   5 Extended
/dev/sdb5         547,013,313   625,137,344    78,124,032  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="1E1035BA103599AB" TYPE="ntfs" 
/dev/sdb1: UUID="AEAA814CAA8111CF" LABEL="Stephan Roberto / Roflology HD" TYPE="ntfs" 
/dev/sdb5: UUID="be51b98f-b7a0-4900-84d6-d8e0b02491cc" TYPE="ext3" 

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
/dev/sdb1 on /media/Stephan Roberto % Roflology HD type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb5 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)


=========================== sdb5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=be51b98f-b7a0-4900-84d6-d8e0b02491cc ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=be51b98f-b7a0-4900-84d6-d8e0b02491cc

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
uuid		be51b98f-b7a0-4900-84d6-d8e0b02491cc
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=be51b98f-b7a0-4900-84d6-d8e0b02491cc ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		be51b98f-b7a0-4900-84d6-d8e0b02491cc
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=be51b98f-b7a0-4900-84d6-d8e0b02491cc ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		be51b98f-b7a0-4900-84d6-d8e0b02491cc
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc5 during installation
UUID=be51b98f-b7a0-4900-84d6-d8e0b02491cc /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 285.8GB: boot/grub/menu.lst
 285.7GB: boot/grub/stage2
 285.8GB: boot/initrd.img-2.6.28-11-generic
 285.7GB: boot/vmlinuz-2.6.28-11-generic
 285.8GB: initrd.img
 285.7GB: vmlinuz
```

Thanks for your help again.

---

### Post by presence1960 on 2009-10-04
Can your machine boot from USB? If so this is what I would do. I would restore Vista to MBR of your internal disk using your Vista DVD. Unplug the external disk now. If you don't have a Vista DVD you can download a Vista recovery console CD from [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/"). Burn that as an image to CD. Using that or the Vista DVD follow the instructions for Vista [here]("http://ubuntuforums.org/showthread.php?t=1014708").

Reboot and make sure you boot right into Vista.

Now you want to put GRUB on MBR of your external disk by doing this with the external disk plugged in:
```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd1,4)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd1,4)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd1)", to install GRUB to MBR
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

When you reboot go into BIOS and set your USB to boot before your internal disk. Save changes to CMOS and continue booting. You should get a GRUB menu and boot into Ubuntu. Open a terminal and run this command ```
gksu gedit /boot/grub/menu.lst
``` That is a lowercase L in .lst

scroll down to your windows entry and change it to this:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
rootnoverify	(hd1,0)
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader	+1
```

you should be good to go. if you boot without the external plugged in you boot into Vista. If you boot with the the external plugged in you get GRUB.

---

### Post by Habboblob on 2009-10-04
> **presence1960 said:**
> Can your machine boot from USB? If so this is what I would do. I would restore Vista to MBR of your internal disk using your Vista DVD. Unplug the external disk now. If you don't have a Vista DVD you can download a Vista recovery console CD from [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/"). Burn that as an image to CD. Using that or the Vista DVD follow the instructions for Vista [here]("http://ubuntuforums.org/showthread.php?t=1014708").

Reboot and make sure you boot right into Vista.

Now you want to put GRUB on MBR of your external disk by doing this with the external disk plugged in:
```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd1,4)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd1,4)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd1)", to install GRUB to MBR
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

When you reboot go into BIOS and set your USB to boot before your internal disk. Save changes to CMOS and continue booting. You should get a GRUB menu and boot into Ubuntu. Open a terminal and run this command ```
gksu gedit /boot/grub/menu.lst
``` That is a lowercase L in .lst

scroll down to your windows entry and change it to this:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
rootnoverify	(hd1,0)
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader	+1
```

you should be good to go. if you boot without the external plugged in you boot into Vista. If you boot with the the external plugged in you get GRUB.

Thanks mate.
That worked like a charm.

Also, when I booted up to Ubuntu, I had a hardware icon near the Time, so I clicked on it and it opened as Window Labeled Hardware Drivers.
It said something about restricted drivers.

Here is 2 screenies of the windows:
[[img]http://victorystreet.net/uploader/thumbstore/73/ILoFVnj73Z.Screenshot-Hardware_Drivers1_thumb.png[/img]](http://victorystreet.net/uploader/index.php/image/show/ILoFVnj73Z/screenshot-hardware-drivers1.png)

[[IMG]http://victorystreet.net/uploader/thumbstore/4f/8IrQC6LY8X.Screenshot-Hardware_Drivers2_thumb.png[/IMG]](http://victorystreet.net/uploader/index.php/image/show/8IrQC6LY8X/screenshot-hardware-drivers2.png)

---

### Post by Habboblob on 2009-10-04
Fixed my problem with the drivers.

Just installed EnvyNG

[http://albertomilone.com/index.html](http://albertomilone.com/index.html)

and it made everything work easy.

I didn't even need to do anything beside install it, the rest was easy.

---

### Post by presence1960 on 2009-10-05
Glad you got it working! Enjoy Ubuntu.

---

### Post by Bartender on 2009-10-05
presence1960!

Thanks for the link to the Vista MBR fixer.  I'm bookmarking that one

---

### Post by presence1960 on 2009-10-05
> **Habboblob said:**
> Fixed my problem with the drivers.

Just installed EnvyNG

[http://albertomilone.com/index.html](http://albertomilone.com/index.html)

and it made everything work easy.

I didn't even need to do anything beside install it, the rest was easy.

I know envyng is in the jaunty repositories. You can install it through synaptic package manager by selecting envyng -core & envng -qt or running these commands in terminal ```
sudo apt-get install envyng -core
```
& ```
sudo apt-get install envyng -qt
```

---

### Post by Habboblob on 2009-10-06
> **presence1960 said:**
> I know envyng is in the jaunty repositories. You can install it through synaptic package manager by selecting envyng -core & envng -qt or running these commands in terminal ```
sudo apt-get install envyng -core
```
& ```
sudo apt-get install envyng -qt
```

Once again thankyou for all your help.

But I still have one question, can run Ubuntu via my Harddrive from another computer?

Like can another computer boot off my harddrive? Or will it not work due to the hardware configurations it has already made.

---

