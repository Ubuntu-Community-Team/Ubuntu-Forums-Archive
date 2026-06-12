---
title: "Help with installing Ubuntu 8.10 on ext. usb hdd for dual boot w/winxp"
date: 2008-12-17
forum: Installation &amp; Upgrades
---

### Post by brookie on 2008-12-17
Hello, 

I've been going in circles looking at all the posts on how to install ubuntu on an external hdd for dual boot with windows xp, and I can't find a solution. 

I would really appreciate some help or point me in the right direction please. What I want is to install ubuntu 8.10 on my ext. usb hdd, winxp pro on internal hdd, and have dual boot option into either os. 

What I have done:

I downloaded the iso, did the graphical install to my external hdd, grub, ubuntu, and all were installed on the external drive aok as confirmed by swapping out my drives and rebooting into ubuntu, however, no dual boot option when ubuntu drive is in external usb enclosure. 

I read lots of posts and tried to follow directions but have not been successful yet. 

Here are the links i followed: 

[http://ubuntuforums.org/showthread.php?p=4205536&mode=linear#post4205536](http://ubuntuforums.org/showthread.php?p=4205536&mode=linear#post4205536) 

[http://ubuntuforums.org/showthread.php?p=6230518&mode=linear&highlight=external+hard+drive#post6230518](http://ubuntuforums.org/showthread.php?p=6230518&mode=linear&highlight=external+hard+drive#post6230518) 

When I swapped out my drives and rebooted with the ubuntu drive as internal, I started mucking around with system files as posted in the first link above.

I would like to do a fresh install to this little external hard drive and start from scratch. 

The main problem with the graphical install approach was that at the end of the install, a restart message pops up, requiring a reboot, so that system files cannot be accessed, and configured for the dual boot process. 

After reboot, windows xp boots up but cannot see the ubuntu drive. 

Any and all help will be greatly appreciated. :confused:

Cheers, 
brookie

---

### Post by pastalavista on 2008-12-17
I would set the bios to boot from USB before the internal HD and just unplug the drive when I wanted to boot Windows. There are free programs for Windows that let you read ext3 filesystems. I'm sure there's a way to do what you want, but I don't know it. I'm a relative noob, but I manage with Ubuntu better than I ever could Windows. Vista is gone for me.

---

### Post by caljohnsmith on 2008-12-17
In order to get a clearer picture of your setup, how about booting into Ubuntu, download the attached "boot_info9.txt" file to your desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo sh ~/Desktop/boot_info9.txt
```
That will create a "BootInfo.txt" file on your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup in order to know how to best configure your dual boot.

---

### Post by brookie on 2008-12-17
caljohn, 
the command fails:
fontinalis@i600m:~$ sudo sh ~/Desktop/boot_info9.txt
sh: Can't open /home/fontinalis/Desktop/boot_info9.txt

update to situation:
I plugged the external hdd direeectly into my inspiron 600m rather than a hub and I can hit F12 to bring up a one time boot option, at bootup. I chose USB HDD and ubuntu booted from the external. 

I still want to get the automated dual boot option setup rather than hitting a key.

Should I undo these changes I made from that obsolete install guide I was following? 

***
8. type "nano /etc/initramfs-tools/modules"
and add the following lines to the end:
sd_mod
ehci-hcd
usb-storage
scsi_mod
sd_mod

Exit (Ctrl +x) then save (Y) then press Enter

This adds the support needed (but not initially available) to mount and run a USB hard drive in the initial ram disk,

9. I edit /etc/initramfs-tools/initramfs.conf ("nano /etc/initramfs-tools/initramfs.conf")to include a line at the top that reads:
"WAIT=4" in the front of the file.
close and save this file.
then I made the initial ramfs:

10. "mkinitramfs -o /boot/initrd-img."<hit tab and enter> /lib/modules/"<hit tab and enter>"

11. type &#8220;nano /boot/grub/menu.lst"
change all the hd1,0 to hd0,0 and vise versa.
***

The only thing I did no do above edit is /bot/grub/menu.lst. I think all we have to do is edit this list to allow a dual boot option but I cannot get the command to work.

Note: from one of your other posts ([http://ubuntuforums.org/showthread.php?t=946707&highlight=fdisk+list+hard+drives](http://ubuntuforums.org/showthread.php?t=946707&highlight=fdisk+list+hard+drives)) I got this: 

fontinalis@i600m:/boot/grub$ sudo fdisk -lu

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xab7ba465

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    52596809    26298373+   7  HPFS/NTFS
/dev/sda2        52596810   195366464    71384827+   5  Extended
/dev/sda5        52596873   195366464    71384796    7  HPFS/NTFS

Disk /dev/sdb: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00d47562

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   112326479    56163208+  83  Linux
/dev/sdb2       112326480   117210239     2441880    5  Extended
/dev/sdb5       112326543   117210239     2441848+  82  Linux swap / Solaris
fontinalis@i600m:/boot/grub$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=0c0b39fa-7625-44bd-a504-91c9cbe6d309 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=0c0b39fa-7625-44bd-a504-91c9cbe6d309

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		0c0b39fa-7625-44bd-a504-91c9cbe6d309
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=0c0b39fa-7625-44bd-a504-91c9cbe6d309 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		0c0b39fa-7625-44bd-a504-91c9cbe6d309
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=0c0b39fa-7625-44bd-a504-91c9cbe6d309 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		0c0b39fa-7625-44bd-a504-91c9cbe6d309
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0c0b39fa-7625-44bd-a504-91c9cbe6d309 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		0c0b39fa-7625-44bd-a504-91c9cbe6d309
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0c0b39fa-7625-44bd-a504-91c9cbe6d309 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		0c0b39fa-7625-44bd-a504-91c9cbe6d309
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
chainloader	+1

---

### Post by caljohnsmith on 2008-12-17
I don't think you need to manually add all those modules to your /etc/initramfs-tools/modules file order to get your USB drive booting OK; most people I've seen in the forums who have installed Ubuntu to a USB drive get it booting OK without having to add those modules. 

Did you download that attached "boot_info9.txt" file in my last post to your desktop and then run the command I gave? You have to download the attachment first.

---

### Post by brookie on 2008-12-17
caljohn, the command fails every time like this:

fontinalis@i600m:~$ sudo sh ~/Desktop/boot_info9.txt
[sudo] password for fontinalis: 
sh: Can't open /home/fontinalis/Desktop/boot_info9.txt

i'm stumped?!:(

---

### Post by caljohnsmith on 2008-12-17
> **brookie said:**
> caljohn, the command fails every time like this:

fontinalis@i600m:~$ sudo sh ~/Desktop/boot_info9.txt
[sudo] password for fontinalis: 
sh: Can't open /home/fontinalis/Desktop/boot_info9.txt

i'm stumped?!:(
Yes, but did you download the attachment in my post to your desktop? How about posting the output of:
```
cd ~/Desktop
ls -l
sudo sh ./boot_info9.txt
```
Note "-l" is a lowercase L, not a one. Also, that second command above should show the "boot_info9.txt" file on your desktop. If it doesn't, you still need to download that file to your desktop.

---

### Post by brookie on 2008-12-17
Ok, thanks for being patient. You were right and I need to follow directions better. 
Here is the BootInfo.txt:
No known boot loader is installed in the MBR of /dev/sda
Grub is installed in the MBR of /dev/sdb and looks on the same drive in partition #1 for its boot files.

sda1:
    File system:  ntfs
    Boot sector  type:  XP
    Boot sector  info:  According to the info in the boot sector, sda1 starts at sector 63
    Operating System: XP
    Boot files/directories present:  /boot.ini /ntldr /NTDETECT.COM

sda2:
    File system:  
    Boot sector  type:  Unknown
    Boot sector  info:  
    Operating System: 
    Boot files/directories present: 

sda5:
    File system:  ntfs
    Boot sector  type:  XP
    Boot sector  info:  According to the info in the boot sector, sda5 starts at sector 63
    Operating System: 
    Boot files/directories present: 

sdb1:
    File system:  ext3
    Boot sector  type:  Unknown
    Boot sector  info:  
    Operating System: Linux
    Boot files/directories present:  /boot/grub/menu.lst /boot /boot/grub

sdb2:
    File system:  
    Boot sector  type:  Unknown
    Boot sector  info:  
    Operating System: 
    Boot files/directories present: 

sdb5:
    File system:  swap
    Boot sector  type:  Unknown
    Boot sector  info:  
    Operating System: 
    Boot files/directories present: 


Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xab7ba465

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    52596809    26298373+   7  HPFS/NTFS
/dev/sda2        52596810   195366464    71384827+   5  Extended
/dev/sda5        52596873   195366464    71384796    7  HPFS/NTFS

Disk /dev/sdb: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00d47562

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   112326479    56163208+  83  Linux
/dev/sdb2       112326480   117210239     2441880    5  Extended
/dev/sdb5       112326543   117210239     2441848+  82  Linux swap / Solaris
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 52596747, Id= 7, bootable
/dev/sda2 : start= 52596810, size=142769655, Id= 5
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start= 52596873, size=142769592, Id= 7
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=       63, size=112326417, Id=83, bootable
/dev/sdb2 : start=112326480, size=  4883760, Id= 5
/dev/sdb3 : start=        0, size=        0, Id= 0
/dev/sdb4 : start=        0, size=        0, Id= 0
/dev/sdb5 : start=112326543, size=  4883697, Id=82

sda1/boot.ini

[boot loader]

timeout=3

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


sdb1/boot/grub/menu.lst

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
# kopt=root=UUID=0c0b39fa-7625-44bd-a504-91c9cbe6d309 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=0c0b39fa-7625-44bd-a504-91c9cbe6d309

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		0c0b39fa-7625-44bd-a504-91c9cbe6d309
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=0c0b39fa-7625-44bd-a504-91c9cbe6d309 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		0c0b39fa-7625-44bd-a504-91c9cbe6d309
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=0c0b39fa-7625-44bd-a504-91c9cbe6d309 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		0c0b39fa-7625-44bd-a504-91c9cbe6d309
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0c0b39fa-7625-44bd-a504-91c9cbe6d309 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		0c0b39fa-7625-44bd-a504-91c9cbe6d309
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0c0b39fa-7625-44bd-a504-91c9cbe6d309 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		0c0b39fa-7625-44bd-a504-91c9cbe6d309
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
chainloader	+1


sdb1/boot

total 31768
drwxr-xr-x  3 root root    4096 2008-12-16 23:21 .
drwxr-xr-x 20 root root    4096 2008-12-16 20:05 ..
-rw-r--r--  1 root root  507665 2008-11-04 14:00 abi-2.6.27-7-generic
-rw-r--r--  1 root root  507665 2008-11-20 16:46 abi-2.6.27-9-generic
-rw-r--r--  1 root root   91364 2008-11-04 14:00 config-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-11-20 16:46 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2008-12-16 20:05 grub
-rw-r--r--  1 root root 8183618 2008-12-16 23:22 initrd-img.
-rw-r--r--  1 root root 8182702 2008-12-16 20:04 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8183653 2008-12-16 20:06 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 14:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-11-04 14:00 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1029585 2008-11-20 16:46 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1073 2008-11-04 14:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-11-20 16:48 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2244464 2008-11-04 14:00 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2244304 2008-11-20 16:46 vmlinuz-2.6.27-9-generic

sdb1/boot/grub

total 224
drwxr-xr-x 2 root root   4096 2008-12-16 20:05 .
drwxr-xr-x 3 root root   4096 2008-12-16 23:21 ..
-rw-r--r-- 1 root root    197 2008-12-16 09:10 default
-rw-r--r-- 1 root root     30 2008-12-16 09:10 device.map
-rw-r--r-- 1 root root   8108 2008-12-16 09:10 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-16 09:10 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-16 09:10 installed-version
-rw-r--r-- 1 root root   8712 2008-12-16 09:10 jfs_stage1_5
-rw-r--r-- 1 root root   5092 2008-12-16 20:05 menu.lst
-rw-r--r-- 1 root root   5008 2008-12-16 20:05 menu.lst~
-rw-r--r-- 1 root root   7352 2008-12-16 09:10 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-16 09:10 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-16 09:10 stage1
-rw-r--r-- 1 root root 121460 2008-12-16 09:10 stage2
-rw-r--r-- 1 root root   9556 2008-12-16 09:10 xfs_stage1_5

StdErr Messages 

ls: cannot access /dev/hd?: No such file or directory
ls: cannot access /dev/hd??*: No such file or directory
mount: you must specify the filesystem type
/dev/sda2: unknown volume type
umount: sda2: not mounted
mount: you must specify the filesystem type
/dev/sdb2: unknown volume type
umount: sdb2: not mounted
/dev/sdb5 looks like swapspace - not mounted
mount: you must specify the filesystem type
umount: sdb5: not mounted

---

### Post by caljohnsmith on 2008-12-17
OK, while you are in Ubuntu, how about opening your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And then replace your current Windows entry at the bottom with the following two entries:
```
title Microsoft Windows XP Professional (hd1)
rootnoverify     (hd1)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title Microsoft Windows XP Professional (hd1,0)
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
Then reboot, and when you get the Grub menu on start up, let me know exactly what happens when you try each entry above. Your Windows sda drive does not have recognized boot code in its MBR (Master Boot Record), so I'll be greatly interested if the first entry above works. Let me know how it goes. :)

---

### Post by xjcannonx on 2008-12-17
You'll have to excuse me because i'm a bit of a noob to, but should grub be on the MBR of sda1?, I dual boot ubuntu and xp but also have an ubuntu distro on an ext harddrive and it shows up when grub asks what OS to load

---

### Post by brookie on 2008-12-17
removed dbl post

---

### Post by brookie on 2008-12-17
Caljohn,

It's working, it's working!!! :) 

Total weirdness though beccccause this hapened without making the above changes to menu.lst. 

I have the ubuntu disk in the external enclosure, and I plugged it directly into the pc usb rather than a usb 7-port hub, and voila, when I reboot grub starts up and I can choose WinXP or Ubuntu. 

Now the question is, should I still make the changes you recommended to meu.lst? If you want, I'll still give it a quick try as I would like to learn more about those statements and how they are pointing grub to the diffenent hds (hd0,0) and (hd0,1), etc... 

Thanks.

---

### Post by caljohnsmith on 2008-12-17
> **brookie said:**
> Caljohn,

It's working, it's working!!! :) 

Total weirdness though beccccause this hapened without making the above changes to menu.lst. 

I have the ubuntu disk in the external enclosure, and I plugged it directly into the pc usb rather than a usb 7-port hub, and voila, when I reboot grub starts up and I can choose WinXP or Ubuntu. 

Now the question is, should I still make the changes you recommended to meu.lst? If you want, I'll still give it a try. ;)
Can you boot into Windows OK? I wouldn't think you could with the current Windows entry you have in your Grub menu.lst. If you can't boot Windows from Grub, then go ahead and modify your menu.lst with my previous suggestions, and let me know how it goes.

---

### Post by caljohnsmith on 2008-12-17
> **xjcannonx said:**
> You'll have to excuse me because i'm a bit of a noob to, but should grub be on the MBR of sda1?, I dual boot ubuntu and xp but also have an ubuntu distro on an ext harddrive and it shows up when grub asks what OS to load
If you install Grub to the boot sector of the sda1 Windows partition, that will unfortunately corrupt the Windows NTFS boot sector, and you won't be able to boot Windows after that nor mount the Windows partition. But if you mean install Grub to the MBR of drive sda, yes, that could work, but that's not as ideal because then the sda and sdb drives are dependent on each other for booting. If Brookie were to do that, and if he disconnects his sdb drive at any time, he won't be able to boot his sda Windows drive. :)

---

### Post by brookie on 2008-12-17
Right again Caljohn! 
I could not boot into windows as it was so I made the changes and it works again. Now I can boot into either os, however, there are two entries on grub's boot screen for WinXP Pro. 

WinXP...(hd1)
WinXp...(hd1,0)

Both work but can we get rid of one. No need to see both on the screen is there? 

And, thank you so much for helping me today. I may become an ubuntu switchover if i can keep learning about this stuff. 

Cheers, brook

---

### Post by caljohnsmith on 2008-12-17
I'm glad to hear those entries both worked to boot Windows. You don't have to keep both of course, so you can delete either one. Cheers and have fun with Windows and Ubuntu. :)

---

### Post by brookie on 2008-12-17
don't know how to mark this thread as solved but i read somewhere that its the proper thing to do and its all working now, so i'll try putting solved in the title. 

recap:
1. installed ubnt 8.10 onto external usb hdd using graphical install. made sure to point the install of grub to that external hdd

2. install completed, restarted computer but no boot logon, only windows xp

3. swapped out the external hdd with the internal hdd and ubuntu booted straight away

4. did not know which files to edit for dual boot so found some great help here and many thanks to caljohnsmith! 

5. once the boot file was correctly edited I can now dual boot my computer to either the internal hdd with winxp pro or external hdd with ubuntu 8.10

Thanks again caljohn! 

Cheers, 
brookie

---

