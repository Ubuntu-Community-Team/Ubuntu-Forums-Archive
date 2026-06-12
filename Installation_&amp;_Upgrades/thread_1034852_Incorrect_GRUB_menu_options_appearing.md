---
title: "Incorrect GRUB menu options appearing"
date: 2009-01-09
forum: Installation &amp; Upgrades
---

### Post by ajayvarrier on 2009-01-09
Hi,

I tried to install Ubuntu 8.10 from live CD. But the GRUB loader shows only 2 options to select.
1. ubuntu 8.10, memory86+...(something like this)
2. Other operating systems: windows XP

Windows boots fine when selected. But if I choose option 1, memory test runs. I don't know why selection 1 comes together like what I typed above.

I went and checked in /boot/GRUB folder after inserting live CD and couldnt find any menu file or config file. I am not able to get into super user mode also because no where in the install, I gave a root password.

I had an old ubuntu in which xserver was failing, thats why I tried to upgrade to 8.10. At that time also, I was not getting super user access. Later I got in when I entered in recovery mode. Here in this case, there is no linux to login to itsef?

Can anyone help me to rectify this?

---

### Post by Pumalite on 2009-01-09
Post:
```
cat /boot/grub/menu.lst
```
Boot a Live CDE and post after mounting corresponding partition.

---

### Post by ajayvarrier on 2009-01-09
There is no such folder like grub under /boot.

---

### Post by Pumalite on 2009-01-09
Have you installed yet?

---

### Post by caljohnsmith on 2009-01-09
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. If you don't have internet connectivity when using the Live CD, you can instead right-click [this link]("http://home.comcast.net/~ubuntu_grub/boot_info_script.txt") to the script in your web browser, choose "Save link as...", save the "boot_info_script.txt" file, transfer it to your Ubuntu desktop on the Live CD via USB stick, floppy, or however you want to do it, and then do the following in a terminal:
```
sudo bash ~/Desktop/boot_info_script.txt
```
The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by chdieawoy on 2009-01-09
Hi, I am new here. I view all posts. Good disscussion here.----------------------------------------------------------------------------------------------[Your Online Classic and Boutique from Guangzhou](http://www.towholesalejewelry.com/to/13.html), [Welcome to jewelry Fantasy](http://www.towholesalejewelry.com/to/14.html), [Welcome to China Jewelry Factory](http://www.towholesalejewelry.com/to/15.html), [Fashion can be high quality](http://www.towholesalejewelry.com/to/16.html)

---

### Post by ajayvarrier on 2009-01-10
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #8 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf208f208

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    92164904    46082421    7  HPFS/NTFS
/dev/sda2        92164905   312576704   110205900    f  W95 Ext'd (LBA)
/dev/sda5        92164968   194563214    51199123+   7  HPFS/NTFS
/dev/sda6       194563278   253168334    29302528+   7  HPFS/NTFS
/dev/sda7       253168398   256092164     1461883+  82  Linux swap / Solaris
/dev/sda8       256092228   312576704    28242238+  83  Linux

sfdisk -V /dev/sda:

/dev/sda: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="9CD8DE1CD8DDF48C" TYPE="ntfs" 
/dev/sda5: UUID="9814ADF214ADD392" TYPE="ntfs" 
/dev/sda6: UUID="8E68B7CB68B7B077" TYPE="ntfs" 
/dev/sda7: TYPE="swap" UUID="8a16cf03-e3c1-4d22-b941-979d95baf701" 
/dev/sda8: UUID="fd40f11c-d35e-4c9c-97e9-18432eaef8e6" SEC_TYPE="ext2" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda8/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=fd40f11c-d35e-4c9c-97e9-18432eaef8e6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=fd40f11c-d35e-4c9c-97e9-18432eaef8e6

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

title		Ubuntu 8.10, memtest86+
uuid		fd40f11c-d35e-4c9c-97e9-18432eaef8e6
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


=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=fd40f11c-d35e-4c9c-97e9-18432eaef8e6 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=8a16cf03-e3c1-4d22-b941-979d95baf701 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sda8/boot: ==================================

total 10060
drwxr-xr-x  3 root root    4096 2009-01-10 18:36 .
drwxr-xr-x 20 root root    4096 2009-01-10 18:36 ..
-rw-r--r--  1 root root  507665 2008-10-24 08:29 abi-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-10-24 08:29 config-2.6.27-7-generic
drwxr-xr-x  2 root root    4096 2009-01-10 18:36 grub
-rw-r--r--  1 root root 8488719 2009-01-10 18:36 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-10-24 08:29 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-10-24 08:31 vmcoreinfo-2.6.27-7-generic

=============================== sda8/boot/grub: ===============================

total 216
drwxr-xr-x 2 root root   4096 2009-01-10 18:36 .
drwxr-xr-x 3 root root   4096 2009-01-10 18:36 ..
-rw-r--r-- 1 root root    197 2009-01-10 18:36 default
-rw-r--r-- 1 root root     15 2009-01-10 18:36 device.map
-rw-r--r-- 1 root root   8108 2009-01-10 18:36 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-01-10 18:36 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-01-10 18:36 installed-version
-rw-r--r-- 1 root root   8712 2009-01-10 18:36 jfs_stage1_5
-rw-r--r-- 1 root root   4139 2009-01-10 18:36 menu.lst
-rw-r--r-- 1 root root   7352 2009-01-10 18:36 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-01-10 18:36 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-10 18:36 stage1
-rw-r--r-- 1 root root 121460 2009-01-10 18:36 stage2
-rw-r--r-- 1 root root   9556 2009-01-10 18:36 xfs_stage1_5

=============================== StdErr Messages: ===============================

No errors were reported.
```

---

### Post by caljohnsmith on 2009-01-10
For some reason the "vmlinuz-2.6.27-7-generic" kernel file is missing in your install, so that would explain why you don't have an option to boot it in your Grub menu. I would try reinstalling Ubuntu, and if you get any errors during the installation, how about letting us know exactly what they are. Otherwise hopefully reinstalling will do the trick. Good luck and let us know how it goes.

---

### Post by ajayvarrier on 2009-01-10
I actually tried to reinstall the same today morning after deleting the existing swap and ext3 partitions and recreating. This time again, I got the same grub menu as before. The statistics I pasted above is from the newly tried version. Can I replace the boot loader part to LILO or something else? Is it a problem with a boot loader or complete install itself?

---

### Post by caljohnsmith on 2009-01-10
Did you get any errors during/after the installation process? If not, maybe you should try the "check CD for defects" option when you boot the Live CD, and see if it turns up anything. I don't think that replacing Grub with Lilo during the install will correct the problem, but if the problem is a bug, then it's hard to say what might help circumvent it.

---

### Post by ajayvarrier on 2009-01-10
Last time I didn't get any error while install. 
I tried installing mythbundu... Now I am in more danger. My boot loader is all corrupted. I cant even boot windows.
When Grub loads, it says ERROR 15 and fails to load anything. I have lots of documents in windows? Can I make windows boot work? Can you help me quickly to restore that boot??

---

### Post by munim on 2009-01-10
Ajay, 
Since you are from India, I guess you are using the Ubuntu 8.10 multi-boot cd which was distributed in last month's issue of LinuxForYou magazine.
The installation image is corrupted in this cd. It doesn't copy the kernel file during install. I tried it myself and I have read about this from many other LFY users on the internet.
It's surprising no one complained or wrote to the editor in this month's issue.

---

### Post by ajayvarrier on 2009-01-10
ohh..Thanks for that update. Yes. I am using the same DVD which was distributed with LFY.

---

### Post by caljohnsmith on 2009-01-10
If you want to restore a Windows MBR to your HDD so you can boot directly into Windows, how about trying:
```
sudo apt-get install lilo
sudo lilo -M  /dev/sda mbr
```
Then reboot, and let me know how it goes.

---

### Post by ajayvarrier on 2009-01-10
Thanks Caljonsmith.I restored the windows boot part atleast. Thanks. Let me look for some new distribution CDs for Ubuntu.

---

### Post by ajayvarrier on 2009-01-14
I have installed the ubuntu succesfully. I downloaded the latest from ubuntu website and burned the CD and installed from it. This proved that the install CD I used earlier was corrupted. Now boot menu appears fine and I am impressed with the look and feel of Ubuntu. Thanks to everyone for the support. :D

---

