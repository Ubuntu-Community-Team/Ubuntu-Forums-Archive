---
title: "Stuck with 2.6.27-7-generic"
date: 2009-02-15
forum: Installation &amp; Upgrades
---

### Post by rattlehead on 2009-02-15
I've had a dual boot Ubuntu/XP for a couple of years, and only recently had a problem. Sometime ago, I upgraded from 2.6.27-7-generic and it broke the GRUB bootloader. Now, I get a list of kernels in the bootloader list, but only 2.6.27-7-generic works. The older kernels work fine, too, but all of the newer kernels yield this error:

Error 2: bad file or directory type

I waited through another upgrade to see if that took care of itself, but it did not. So much for the lazy way out! Any ideas what could be wrong?

For reference, here is optionlist from my menus.lst (note the first option I was just playing around with troubleshooting. It didn't work.)

```
title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-11-generic root=/dev/sda2 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=6fe1d554-b870-4f3d-a52a-3b475f13a034 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=6fe1d554-b870-4f3d-a52a-3b475f13a034 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=6fe1d554-b870-4f3d-a52a-3b475f13a034 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=6fe1d554-b870-4f3d-a52a-3b475f13a034 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=6fe1d554-b870-4f3d-a52a-3b475f13a034 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-4-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-4-generic root=UUID=6fe1d554-b870-4f3d-a52a-3b475f13a034 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-4-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-4-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-4-generic root=UUID=6fe1d554-b870-4f3d-a52a-3b475f13a034 ro  single
initrd		/boot/initrd.img-2.6.27-4-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet
 
```

---

### Post by caljohnsmith on 2009-02-16
In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your Grub error 2 might be.

---

### Post by rattlehead on 2009-02-17
Alright, sorry this took a bit... I was stuck working on another project today.I ran the bootinfo script (very handy), and here are the results (minus the password/account info):

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

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

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x09a309a2

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   153,597,464   153,597,402   7 HPFS/NTFS
/dev/sda2         153,597,465   310,327,604   156,730,140  83 Linux
/dev/sda3         310,327,605   312,576,704     2,249,100   5 Extended
/dev/sda5         310,327,668   312,576,704     2,249,037  82 Linux swap / Solaris


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7cbc4774

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   398,283,479   398,283,417   7 HPFS/NTFS


Drive sdc: _____________________________________________________________________

Disk /dev/sdc: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9d415d79

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   586,067,264   586,067,202   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="C8C426B9C426A9A0" TYPE="ntfs" 
/dev/sda2: UUID="6fe1d554-b870-4f3d-a52a-3b475f13a034" TYPE="ext3" 
/dev/sda5: UUID="bab64baa-abed-41e6-8728-5af7debf6a94" TYPE="swap" 
/dev/sdb1: UUID="4A8C862F8C86159B" LABEL="X1" TYPE="ntfs" 
/dev/sdc1: LABEL="backup01" UUID="699b5525-6057-42c3-88a9-38b1732bce07" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
//192.168.1.98/media2/audio on /media/morticia-audio type cifs (rw,mand)
//192.168.1.99/editing on /media/gomez-editing type cifs (rw,mand)
//192.168.1.99/library on /media/gomez-library type cifs (rw,mand)
gvfs-fuse-daemon on /home/sean/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=sean)
/dev/sdc1 on /media/backup01 type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sdb1 on /media/X1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader]

redirect=usebiossettings

redirectbaudrate=

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 


=========================== sda2/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=6fe1d554-b870-4f3d-a52a-3b475f13a034 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-11-generic root=/dev/sda2 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=6fe1d554-b870-4f3d-a52a-3b475f13a034 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=6fe1d554-b870-4f3d-a52a-3b475f13a034 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=6fe1d554-b870-4f3d-a52a-3b475f13a034 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=6fe1d554-b870-4f3d-a52a-3b475f13a034 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=6fe1d554-b870-4f3d-a52a-3b475f13a034 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-4-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-4-generic root=UUID=6fe1d554-b870-4f3d-a52a-3b475f13a034 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-4-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-4-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-4-generic root=UUID=6fe1d554-b870-4f3d-a52a-3b475f13a034 ro  single
initrd		/boot/initrd.img-2.6.27-4-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,1)
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


=============================== sda2/etc/fstab: ===============================

proc            /proc           proc    defaults        0       0
UUID=6fe1d554-b870-4f3d-a52a-3b475f13a034 /               ext3    relatime,errors=remount-ro 0       1
UUID=bab64baa-abed-41e6-8728-5af7debf6a94 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
//192.168.1.98/media2/audio	/media/morticia-audio/	smbfs	username=[*],password=[*]	0	0
//192.168.1.99/editing	/media/gomez-editing/	smbfs	username=[*],password=[*]	0	0
//192.168.1.99/library	/media/gomez-library/	smbfs	username=[*],password=[*]	0	0

=================== sda2: Location of files loaded by Grub: ===================


 124.1GB: boot/grub/menu.lst
 124.1GB: boot/grub/stage2
 145.2GB: boot/initrd.img-2.6.27-11-generic
 124.0GB: boot/initrd.img-2.6.27-4-generic
 124.0GB: boot/initrd.img-2.6.27-7-generic
 135.8GB: boot/initrd.img-2.6.27-9-generic
 141.3GB: boot/vmlinuz-2.6.27-11-generic
 124.1GB: boot/vmlinuz-2.6.27-4-generic
 124.0GB: boot/vmlinuz-2.6.27-7-generic
 145.2GB: boot/vmlinuz-2.6.27-9-generic
 145.2GB: initrd.img
 135.8GB: initrd.img.old
 141.3GB: vmlinuz
 145.2GB: vmlinuz.old
```

---

### Post by caljohnsmith on 2009-02-17
I don't see anything obviously wrong based on the script results, so how about posting:
```
ls -l /boot
```
And we can work from there.

---

### Post by rattlehead on 2009-02-18
Here's what i got:

```
total 47472
-rw-r--r-- 1 root root  508385 2009-01-29 16:11 abi-2.6.27-11-generic
-rw-r--r-- 1 root root  504774 2008-09-23 23:15 abi-2.6.27-4-generic
-rw-r--r-- 1 root root  507665 2008-11-04 16:00 abi-2.6.27-7-generic
-rw-r--r-- 1 root root  507665 2008-11-20 18:46 abi-2.6.27-9-generic
-rw-r--r-- 1 root root   91358 2009-01-29 16:11 config-2.6.27-11-generic
-rw-r--r-- 1 root root   95910 2008-09-23 23:15 config-2.6.27-4-generic
-rw-r--r-- 1 root root   91364 2008-11-04 16:00 config-2.6.27-7-generic
-rw-r--r-- 1 root root   91364 2008-11-20 18:46 config-2.6.27-9-generic
drwxr-xr-x 2 root root    4096 2009-02-15 19:42 grub
-rw-r--r-- 1 root root 8139170 2009-02-15 12:17 initrd.img-2.6.27-11-generic
-rw-r--r-- 1 root root 8344159 2008-10-22 05:15 initrd.img-2.6.27-4-generic
-rw-r--r-- 1 root root 8113494 2008-11-16 23:44 initrd.img-2.6.27-7-generic
-rw-r--r-- 1 root root 8134523 2009-01-11 01:22 initrd.img-2.6.27-9-generic
-rw-r--r-- 1 root root  124152 2008-09-11 16:11 memtest86+.bin
-rw-r--r-- 1 root root 1031799 2009-01-29 16:11 System.map-2.6.27-11-generic
-rw-r--r-- 1 root root 1041452 2008-09-23 23:15 System.map-2.6.27-4-generic
-rw-r--r-- 1 root root 1029585 2008-11-04 16:00 System.map-2.6.27-7-generic
-rw-r--r-- 1 root root 1029585 2008-11-20 18:46 System.map-2.6.27-9-generic
-rw-r--r-- 1 root root    1074 2009-01-29 16:12 vmcoreinfo-2.6.27-11-generic
-rw-r--r-- 1 root root    1073 2008-09-23 23:17 vmcoreinfo-2.6.27-4-generic
-rw-r--r-- 1 root root    1073 2008-11-04 16:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r-- 1 root root    1073 2008-11-20 18:48 vmcoreinfo-2.6.27-9-generic
-rw-r--r-- 1 root root 2248912 2009-01-29 16:11 vmlinuz-2.6.27-11-generic
-rw-r--r-- 1 root root 2305072 2008-10-22 05:12 vmlinuz-2.6.27-4-generic
-rw-r--r-- 1 root root 2244464 2008-11-04 16:00 vmlinuz-2.6.27-7-generic
-rw-r--r-- 1 root root 2244304 2008-11-20 18:46 vmlinuz-2.6.27-9-generic
```

---

### Post by caljohnsmith on 2009-02-18
So vmlinuz-2.6.27-11-generic is one of the kernels you can't boot right now, true? If so, how about posting the output of the following:
```
sudo dd if=/boot/vmlinuz-2.6.27-11-generic of=/dev/null
sudo dd if=/boot/initrd.img-2.6.27-11-generic of=/dev/null
```
If neither of those commands return an error, how about booting Ubuntu into recovery mode, and when it gives you the menu to choose what you want to do, choose to do a file system check (fsck) on the Ubuntu partition. Let me know if that returns any errors.

---

### Post by rattlehead on 2009-02-18
Here's what both those commands gives me:

```
4392+1 records in
4392+1 records out
2248912 bytes (2.2 MB) copied, 0.177439 s, 12.7 MB/s
```

then:

```
15896+1 records in
15896+1 records out
8139170 bytes (8.1 MB) copied, 0.27647 s, 29.4 MB/s
```

No errors, I guess; I'll try the recovery thing next...

Rebooted, went inot recovery mode and ran the fsck utility. It completed without errors, but to no avail: it still won't boot into any of the other kernels.

---

### Post by caljohnsmith on 2009-02-18
OK, how about trying:
```
sudo rm /boot/initrd.img-2.6.27-11-generic /boot/vmlinuz-2.6.27-11-generic
sudo apt-get purge linux-headers-2.6.27-11-generic linux-image-2.6.27-11-generic linux-restricted-modules-2.6.27-11-generic
sudo apt-get install linux-headers-2.6.27-11-generic linux-image-2.6.27-11-generic linux-restricted-modules-2.6.27-11-generic
```
Then reboot and try the 2.6.27-11 kernel from your Grub menu, and let me know what happens.

---

### Post by rattlehead on 2009-02-20
Believe it or not, it appears to work fine! It booted up without issue. Thank you so much... now is there anything I should do to remove the other entries or does it matter?

---

### Post by caljohnsmith on 2009-02-20
I'm really glad to hear that did the trick, rattlehead. So you can boot into either the 2.6.27-11 or 2.6.27-7 kernel now? If you want you can remove the other older kernels that you don't want by doing the apt-get "purge" command for each kernel, for instance:
```
sudo apt-get purge linux-headers-2.6.27-4-generic linux-image-2.6.27-4-generic linux-restricted-modules-2.6.27-4-generic
```
It's always a good idea to have at least one "backup" kernel that works in addition to the latest kernel (2.6.27-11), so I wouldn't recommend removing *all* the other kernels. When you uninstall a kernel, I think it gives you the option to update your Grub's menu.lst and remove the kernel from that file, but if for some reason you need to clean up your menu.lst of the old kernels, you can manually edit your menu.lst with:
```
gksudo gedit /boot/grub/menu.lst
```
Anyway, cheers and hope you don't have any more kernel problems. :)

---

