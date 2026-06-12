---
title: "boot up error"
date: 2009-01-28
forum: Installation &amp; Upgrades
---

### Post by hatmancan on 2009-01-28
i have a slight problem with the following.
i have windows xp and ubuntu on comp.
when i boot into Kbuntu i get the following error
Booting ubuntu 8.10
filesystem type is ntfs.partition type 0x07
The current working directory(I.E.,The relative path is /ubuntu/disks
[Linux-bzimage,setup=0x3000,size=0x221ed0]
[Linux-initrd 0x7d7c6000,0x814359 bytes]
loading please wait
Gave up waiting for boot device.Common problems
-Boot ARGS(CAT/PROC/CMDLINE)
-CHECK BOOTDELAY=(DID THE SYSTEM WAIT LONG ENOUGH?)
-CHECK ROOT=(DID THE SYSTEM WAIT FOR THE RIGHT DEVICE?)
-MISSING MODULES(CAT/PROC/MODULES;1S/DEV)

ALERT! /DEV/BY-UUID 16E7802FF7802C635 DOES NOT EXIST DROPPING INTO SHELL
BUSY BOX V1.10.2 (UBUNTU1:1.10.2-1UBUNTU6)BUILT-IN SHELL

ENTER HELP FOR LIST OF BUILT IN COMMANDS
(INITRAMFS)

What does all this mean?
How do i fix this?
if i enter EXIT after (initramfs)i can log into kbuntu.
all help greatly appreciated
hat

---

### Post by jonno on 2009-01-28
I have the same problem. There is a thread [here]("http://ubuntuforums.org/showthread.php?t=1027432&highlight=gave+waiting") which seems to have the most information.

---

### Post by caljohnsmith on 2009-01-28
How about on start up when you get the Grub menu, select the first Kubuntu entry, press "e" to edit it, select the line that says "kernel", press "e" to edit it, and at the end of the kernel line add:
```
rootdelay=120
```
Press return to save the change, then press "b" to boot. Let me know if you still get the same errors after trying the above kernel parameter.

---

### Post by hatmancan on 2009-01-28
i addec the rootdelay=120
still same thing.

maybe i do not have my linux set up right?
is there a way to wipe everything and do a fresh install?
i have all windows disks and have ubuntu 8.10
kbuntu 8.10
and mepis 7

is there a program i can download to windows system and use to partition the drive the way its supposed to be?

one other thing i had 2 40gig hd's but only have 1 now
hat

---

### Post by caljohnsmith on 2009-01-28
You could just boot your Ubuntu Live CD, run the installer, and then choose "manual" for the partitioning method; then you can select to have Ubuntu installed over your current partitions by setting the mount point for each partition and clicking the "format" checkbox. So whichever is your main partition where you want Ubuntu, you would set the mount point to root or "/". That way you should be able to install Ubuntu over your current installation. If you need to do any repartitioning, you can use gparted under System > Admin > Partition Editor. Good luck and let me know how it goes.

---

### Post by hatmancan on 2009-01-28
ok i found this link in another forum.
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt

i went here and ran and attached is what came back..Can you make heads or tails of this and what should i do..i have no idea what this means.
thanks again
hat
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /ubuntu/disks/boot/grub/menu.lst /boot.ini /ntldr 
                       /NTDETECT.COM /wubildr.mbr /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/disks /ubuntu/disks/boot/ 
                       /ubuntu/disks/boot/grub /ubuntu/disks/boot/grub

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd7ddd7dd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    78108029    39053983+   7  HPFS/NTFS

sfdisk -V /dev/sda:

/dev/sda: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="6E7802FF7802C635" TYPE="ntfs" 
/dev/loop0: UUID="5056e0da-dc39-498d-9f1b-6ab42b06888b" TYPE="ext3" 

=============================== "mount" output: ===============================

/host/ubuntu/disks/root.disk on / type ext3 (rw,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/sda1 on /host type fuseblk (rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
/host/ubuntu/disks/boot on /boot type none (rw,bind)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

==================== sda1/ubuntu/disks/boot/grub/menu.lst: ====================

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=6E7802FF7802C635 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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

title        Ubuntu 8.10, kernel 2.6.27-11-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=6E7802FF7802C635 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd        /boot/initrd.img-2.6.27-11-generic

title        Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=6E7802FF7802C635 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd        /boot/initrd.img-2.6.27-11-generic

title        Ubuntu 8.10, kernel 2.6.27-9-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=6E7802FF7802C635 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd        /boot/initrd.img-2.6.27-9-generic

title        Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=6E7802FF7802C635 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd        /boot/initrd.img-2.6.27-9-generic

title        Ubuntu 8.10, kernel 2.6.27-7-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=6E7802FF7802C635 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=6E7802FF7802C635 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, memtest86+
root        ()/ubuntu/disks
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
chainloader    +1


================================ sda1/boot.ini: ================================

[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn
c:\wubildr.mbr="Kubuntu"

============================== sda1/ubuntu/disks: ==============================

total 14648448
drwxrwxrwx 1 root root           0 2009-01-25 20:56 .
drwxrwxrwx 1 root root        4096 2009-01-25 20:51 ..
drwxrwxrwx 1 root root        4096 2009-01-28 12:26 boot
-rwxrwxrwx 2 root root 14000000000 2009-01-28 16:11 root.disk
drwxrwxrwx 1 root root           0 2009-01-25 20:51 shared
-rwxrwxrwx 2 root root  1000000000 2009-01-25 21:04 swap.disk

=========================== sda1/ubuntu/disks/boot/: ===========================

total 36336
drwxrwxrwx 1 root root    4096 2009-01-28 12:26 .
drwxrwxrwx 1 root root       0 2009-01-25 20:56 ..
-rwxrwxrwx 1 root root  508385 2009-01-22 15:09 abi-2.6.27-11-generic
-rwxrwxrwx 1 root root  507665 2008-11-04 17:00 abi-2.6.27-7-generic
-rwxrwxrwx 1 root root  507665 2008-11-20 19:46 abi-2.6.27-9-generic
-rwxrwxrwx 1 root root   91358 2009-01-22 15:09 config-2.6.27-11-generic
-rwxrwxrwx 1 root root   91364 2008-11-04 17:00 config-2.6.27-7-generic
-rwxrwxrwx 1 root root   91364 2008-11-20 19:46 config-2.6.27-9-generic
drwxrwxrwx 1 root root       0 2009-01-28 12:23 grub
-rwxrwxrwx 1 root root 8471385 2009-01-28 12:26 initrd.img-2.6.27-11-generic
-rwxrwxrwx 1 root root 8467991 2009-01-25 23:07 initrd.img-2.6.27-7-generic
-rwxrwxrwx 1 root root 8468247 2009-01-25 23:14 initrd.img-2.6.27-9-generic
-rwxrwxrwx 1 root root  124152 2008-09-11 17:11 memtest86+.bin
-rwxrwxrwx 1 root root 1031799 2009-01-22 15:09 System.map-2.6.27-11-generic
-rwxrwxrwx 1 root root 1029585 2008-11-04 17:00 System.map-2.6.27-7-generic
-rwxrwxrwx 1 root root 1029585 2008-11-20 19:46 System.map-2.6.27-9-generic
-rwxrwxrwx 1 root root    1074 2009-01-22 15:11 vmcoreinfo-2.6.27-11-generic
-rwxrwxrwx 1 root root    1073 2008-11-04 17:02 vmcoreinfo-2.6.27-7-generic
-rwxrwxrwx 1 root root    1073 2008-11-20 19:48 vmcoreinfo-2.6.27-9-generic
-rwxrwxrwx 1 root root 2248912 2009-01-22 15:09 vmlinuz-2.6.27-11-generic
-rwxrwxrwx 1 root root 2244464 2008-11-04 17:00 vmlinuz-2.6.27-7-generic
-rwxrwxrwx 1 root root 2244304 2008-11-20 19:46 vmlinuz-2.6.27-9-generic

========================= sda1/ubuntu/disks/boot/grub: =========================

total 21
drwxrwxrwx 1 root root    0 2009-01-28 12:23 .
drwxrwxrwx 1 root root 4096 2009-01-28 12:26 ..
-rwxrwxrwx 1 root root  191 2009-01-25 21:51 default
-rwxrwxrwx 1 root root   30 2009-01-25 21:50 device.map
-rwxrwxrwx 1 root root 5570 2009-01-28 12:23 menu.lst
-rwxrwxrwx 1 root root 5078 2009-01-28 12:23 menu.lst~

========================= sda1/ubuntu/disks/boot/grub: =========================

total 21
drwxrwxrwx 1 root root    0 2009-01-28 12:23 .
drwxrwxrwx 1 root root 4096 2009-01-28 12:26 ..
-rwxrwxrwx 1 root root  191 2009-01-25 21:51 default
-rwxrwxrwx 1 root root   30 2009-01-25 21:50 device.map
-rwxrwxrwx 1 root root 5570 2009-01-28 12:23 menu.lst
-rwxrwxrwx 1 root root 5078 2009-01-28 12:23 menu.lst~

=============================== StdErr Messages: ===============================

No errors were reported.

---

### Post by caljohnsmith on 2009-01-28
OK, I see the issue now, you have a Wubi Kubuntu install (Kubuntu installed inside of Windows) rather than a standard install. If you want to do a standard install and give Ubuntu its own partition, how about booting your Live CD, choose the "try Ubuntu without making changes" option, open the partition editor (System > Admin > Partition Editor), shrink your current Windows sda1 partition from the end to make room for Ubuntu, and then create an "extended" partition with that space. Inside of the extended partition, create a logical partition for your main Ubuntu install (you can use ext3 as the file system), and then create a swap partition for swap space. Be sure to first back up anything important in Windows before shrinking the Windows partition. After you're done amaking the partitions, run the Ubuntu installer on the Ubuntu desktop, and you should be able to install Ubuntu. If you would like a tutorial for some additional help, you might find this useful:

[http://www.herman.linuxmaniac.net/p22.html](http://www.herman.linuxmaniac.net/p22.html)

Good luck and let us know how it goes.

---

### Post by hatmancan on 2009-01-28
will not let me boot to live cd
is there a way of deleting everything and starting over?

how do uninstall all ubuntu and kubuntu from windows?
then i can reinstall everything
hat

---

### Post by caljohnsmith on 2009-01-28
When you are in Windows, if you go to Control Panel > Add/Remove Programs, you should be able to remove Kubuntu there. If you are not able to boot a Live CD, how do you plan on installing Ubuntu?

---

### Post by hatmancan on 2009-02-02
ok i got kbuntu to boot and installed off cd..
i ran another boot report and here is what i get now???
i think i did something wrong..i think i may be better off to wipe whole thing..tried and now cannot reloaad windows..
is there a way i can boot into strictly a linux system without windows???
maybe this is better for me..this is a second comp so does not matter to me if i lose windows in all honesty..i like the different themes and others for free(lol)
look forward to a reply
hat
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda2: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd7ddd7dd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    74862899    37431418+  83  Linux
/dev/sda2        74862900    78156224     1646662+   5  Extended
/dev/sda5        74862963    78156224     1646631   82  Linux swap / Solaris

sfdisk -V /dev/sda:

/dev/sda: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="b7588746-8ff5-4573-bb06-a177041e3dc6" TYPE="ext3" 
/dev/sda5: UUID="8307b3f5-1d15-4ba6-b3b7-36d3b6a764ef" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/dave/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dave)

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
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=b7588746-8ff5-4573-bb06-a177041e3dc6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b7588746-8ff5-4573-bb06-a177041e3dc6

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

title		Ubuntu 8.10, kernel 2.6.27-11-server
uuid		b7588746-8ff5-4573-bb06-a177041e3dc6
kernel		/boot/vmlinuz-2.6.27-11-server root=UUID=b7588746-8ff5-4573-bb06-a177041e3dc6 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-server
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-server (recovery mode)
uuid		b7588746-8ff5-4573-bb06-a177041e3dc6
kernel		/boot/vmlinuz-2.6.27-11-server root=UUID=b7588746-8ff5-4573-bb06-a177041e3dc6 ro  single
initrd		/boot/initrd.img-2.6.27-11-server

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		b7588746-8ff5-4573-bb06-a177041e3dc6
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=b7588746-8ff5-4573-bb06-a177041e3dc6 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		b7588746-8ff5-4573-bb06-a177041e3dc6
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=b7588746-8ff5-4573-bb06-a177041e3dc6 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		b7588746-8ff5-4573-bb06-a177041e3dc6
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=b7588746-8ff5-4573-bb06-a177041e3dc6 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		b7588746-8ff5-4573-bb06-a177041e3dc6
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=b7588746-8ff5-4573-bb06-a177041e3dc6 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.25-2-386
uuid		b7588746-8ff5-4573-bb06-a177041e3dc6
kernel		/boot/vmlinuz-2.6.25-2-386 root=UUID=b7588746-8ff5-4573-bb06-a177041e3dc6 ro quiet splash 
initrd		/boot/initrd.img-2.6.25-2-386
quiet

title		Ubuntu 8.10, kernel 2.6.25-2-386 (recovery mode)
uuid		b7588746-8ff5-4573-bb06-a177041e3dc6
kernel		/boot/vmlinuz-2.6.25-2-386 root=UUID=b7588746-8ff5-4573-bb06-a177041e3dc6 ro  single
initrd		/boot/initrd.img-2.6.25-2-386

title		Ubuntu 8.10, memtest86+
uuid		b7588746-8ff5-4573-bb06-a177041e3dc6
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b7588746-8ff5-4573-bb06-a177041e3dc6 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=8307b3f5-1d15-4ba6-b3b7-36d3b6a764ef none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sda1/boot: ==================================

total 46848
drwxr-xr-x  3 root root    4096 2009-02-01 21:02 .
drwxr-xr-x 20 root root    4096 2009-02-01 21:02 ..
-rw-r--r--  1 root root  426118 2008-09-30 12:26 abi-2.6.25-2-386
-rw-r--r--  1 root root  508385 2009-01-29 17:11 abi-2.6.27-11-generic
-rw-r--r--  1 root root  510401 2009-01-29 17:26 abi-2.6.27-11-server
-rw-r--r--  1 root root  507665 2008-11-04 17:00 abi-2.6.27-7-generic
-rw-r--r--  1 root root   82153 2008-09-30 12:26 config-2.6.25-2-386
-rw-r--r--  1 root root   91358 2009-01-29 17:11 config-2.6.27-11-generic
-rw-r--r--  1 root root   91522 2009-01-29 17:26 config-2.6.27-11-server
-rw-r--r--  1 root root   91364 2008-11-04 17:00 config-2.6.27-7-generic
drwxr-xr-x  2 root root    4096 2009-02-01 21:02 grub
-rw-r--r--  1 root root 8015556 2009-02-01 17:19 initrd.img-2.6.25-2-386
-rw-r--r--  1 root root 8209368 2009-02-01 10:37 initrd.img-2.6.27-11-generic
-rw-r--r--  1 root root 8239813 2009-02-01 21:02 initrd.img-2.6.27-11-server
-rw-r--r--  1 root root 8208237 2009-02-01 00:37 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 17:11 memtest86+.bin
-rw-r--r--  1 root root  878789 2008-09-30 12:26 System.map-2.6.25-2-386
-rw-r--r--  1 root root 1031799 2009-01-29 17:11 System.map-2.6.27-11-generic
-rw-r--r--  1 root root 1052790 2009-01-29 17:26 System.map-2.6.27-11-server
-rw-r--r--  1 root root 1029585 2008-11-04 17:00 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1074 2009-01-29 17:12 vmcoreinfo-2.6.27-11-generic
-rw-r--r--  1 root root    1073 2009-01-29 17:28 vmcoreinfo-2.6.27-11-server
-rw-r--r--  1 root root    1073 2008-11-04 17:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 1895424 2008-09-30 12:26 vmlinuz-2.6.25-2-386
-rw-r--r--  1 root root 2248912 2009-01-29 17:11 vmlinuz-2.6.27-11-generic
-rw-r--r--  1 root root 2297776 2009-01-29 17:26 vmlinuz-2.6.27-11-server
-rw-r--r--  1 root root 2244464 2008-11-04 17:00 vmlinuz-2.6.27-7-generic

=============================== sda1/boot/grub: ===============================

total 224
drwxr-xr-x 2 root root   4096 2009-02-01 21:02 .
drwxr-xr-x 3 root root   4096 2009-02-01 21:02 ..
-rw-r--r-- 1 root root    197 2009-01-31 19:03 default
-rw-r--r-- 1 root root     15 2009-01-31 19:03 device.map
-rw-r--r-- 1 root root   8108 2009-01-31 19:03 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-01-31 19:03 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-01-31 19:03 installed-version
-rw-r--r-- 1 root root   8712 2009-01-31 19:03 jfs_stage1_5
-rw-r--r-- 1 root root   5738 2009-02-01 21:02 menu.lst
-rw-r--r-- 1 root root   5654 2009-02-01 21:02 menu.lst~
-rw-r--r-- 1 root root   7352 2009-01-31 19:03 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-01-31 19:03 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-31 19:03 stage1
-rw-r--r-- 1 root root 121460 2009-01-31 19:03 stage2
-rw-r--r-- 1 root root   9556 2009-01-31 19:03 xfs_stage1_5

=============================== StdErr Messages: ===============================

No errors were reported.

---

### Post by caljohnsmith on 2009-02-02
I don't understand what you are saying about Windows, because there's no NTFS/FAT partition at all on your sda drive; thus there is no Windows on that drive. Can you boot into the Ubuntu install on that drive, or do you get an error again? According to the script results, everything is configured OK for you to boot into Ubuntu. What exactly happens on start up?

---

### Post by hatmancan on 2009-02-02
i get a message similar to the below...
i have to enter exit 5 times after initfrms to get into eithe edbuntu,kbuntu 
gave up waiting for root device. common problems:
-boot args (cat /proc/cmdline)
-check rootdelay=(did the system wait long enough?)
-check root=(did the system wait for the right device?) 
-missing modules (cat /proc/modules; is dev)

ALERT! /dev/disk/by-uuid/07cdf0c-25f1-4db1-a213-d44bcd3efbdd does not exist. dropping to shell!

the above alert for the dev is not mine but wanted to show the error without having to restart
does this help?
hat

---

