---
title: "Change boot/Grub to previous state."
date: 2009-01-18
forum: Installation &amp; Upgrades
---

### Post by breakerr on 2009-01-18
Hello community.

I know this subject/topic must be somewhere else in the forums but maybe the technical specs are not the same so thats why I write this.

The reason of my post here is because I just installed Ubuntu 64bits on my 40Gb Seagate IDE but during installation I forgot to locate the GRUB in the same hard disk/drive I have Ubuntu, so instead I got it in the SATA with no jumpers (no jumpers,I guess thats slave) were my XP is....the problem is that I want all like before..........before means I had the 32bits installed completely alone and no grub to select anything...I could choose what to boot up from my **F11** option on my motherboard and by default was XP to boot up except if I press F11. 

I want GRUB to load/boot only from my IDE Ubuntu drive, only if I choose to boot from the IDE/ubuntu drive like it was before. I dont want GRUB to interfere to load/boot both operating systems. ( I don't know if Im explaining myself clearly) before GRUB wasn't needed to start Windows Xp which was the default boot option set from my BIOS/motherboard.

How can I make it boot like before without uninstalling Ubuntu ?????

Thanks in advance and anxious for the help. Thanks a lot.

---

### Post by caljohnsmith on 2009-01-18
In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your booting problem might be.

---

### Post by breakerr on 2009-01-18
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

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

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       Extended Partition

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9ae25047

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    74862899    37431418+  83  Linux
/dev/sda2        74862900    78156224     1646662+   5  Extended
/dev/sda5        74862963    78156224     1646631   82  Linux swap / Solaris

sfdisk -V /dev/sda:

/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xef0cef0c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   268414019   134206978+   7  HPFS/NTFS
/dev/sdb2       268414020   488392064   109989022+   f  W95 Ext'd (LBA)
/dev/sdb5       268414083   488392064   109988991    7  HPFS/NTFS

sfdisk -V /dev/sdb:

/dev/sdb: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="2c9d8468-93ee-4852-a6f1-bce629a83517" TYPE="ext3" 
/dev/sda5: UUID="dfbfe6ad-946c-4592-bbf8-9c621cf306e8" TYPE="swap" 
/dev/sdb1: UUID="E8F421C8F4219A38" TYPE="ntfs" 
/dev/sdb5: UUID="2E44552D4454F8D3" TYPE="ntfs" 

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
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/breaker/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=breaker)

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
timeout		1

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

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

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
# kopt=root=UUID=2c9d8468-93ee-4852-a6f1-bce629a83517 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=2c9d8468-93ee-4852-a6f1-bce629a83517

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
uuid		2c9d8468-93ee-4852-a6f1-bce629a83517
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=2c9d8468-93ee-4852-a6f1-bce629a83517 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		2c9d8468-93ee-4852-a6f1-bce629a83517
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=2c9d8468-93ee-4852-a6f1-bce629a83517 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		2c9d8468-93ee-4852-a6f1-bce629a83517
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2c9d8468-93ee-4852-a6f1-bce629a83517 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		2c9d8468-93ee-4852-a6f1-bce629a83517
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2c9d8468-93ee-4852-a6f1-bce629a83517 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		2c9d8468-93ee-4852-a6f1-bce629a83517
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=2c9d8468-93ee-4852-a6f1-bce629a83517 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=dfbfe6ad-946c-4592-bbf8-9c621cf306e8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sda1/boot: ==================================

total 25528
drwxr-xr-x  3 root root    4096 2009-01-14 16:07 .
drwxr-xr-x 21 root root    4096 2009-01-14 18:04 ..
-rw-r--r--  1 root root  503560 2008-11-04 16:53 abi-2.6.27-7-generic
-rw-r--r--  1 root root  503560 2008-11-20 19:30 abi-2.6.27-9-generic
-rw-r--r--  1 root root   85316 2008-11-04 16:53 config-2.6.27-7-generic
-rw-r--r--  1 root root   85316 2008-11-20 19:30 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2009-01-16 09:38 grub
-rw-r--r--  1 root root 8670513 2009-01-14 16:05 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8671712 2009-01-14 16:07 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 16:11 memtest86+.bin
-rw-r--r--  1 root root 1352144 2008-11-04 16:53 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1352144 2008-11-20 19:30 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1130 2008-11-04 16:57 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1130 2008-11-20 19:32 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2339552 2008-11-04 16:53 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2339712 2008-11-20 19:30 vmlinuz-2.6.27-9-generic

=============================== sda1/boot/grub: ===============================

total 232
drwxr-xr-x 2 root root   4096 2009-01-16 09:38 .
drwxr-xr-x 3 root root   4096 2009-01-14 16:07 ..
-rw-r--r-- 1 root root    197 2009-01-14 13:44 default
-rw-r--r-- 1 root root     30 2009-01-14 13:44 device.map
-rw-r--r-- 1 root root   8108 2009-01-14 13:44 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-01-14 13:44 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-01-14 13:44 installed-version
-rw-r--r-- 1 root root   8712 2009-01-14 13:44 jfs_stage1_5
-rw-r--r-- 1 root root   5429 2009-01-16 09:38 menu.lst
-rw-r--r-- 1 root root   5429 2009-01-16 09:37 menu.lst~
-rw------- 1 root root   5309 2009-01-15 03:43 menu.lst.save
-rw-r--r-- 1 root root   7352 2009-01-14 13:44 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-01-14 13:44 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-14 13:44 stage1
-rw-r--r-- 1 root root 121460 2009-01-14 13:44 stage2
-rw-r--r-- 1 root root   9556 2009-01-14 13:44 xfs_stage1_5

================================ sdb1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn


=============================== StdErr Messages: ===============================

No errors were reported.

---

### Post by caljohnsmith on 2009-01-18
OK, to install Grub to your Ubuntu drive, how about trying:
```
sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```
And then to restore a Windows MBR to your Windows drive, try:
```
sudo apt-get install lilo
sudo lilo -M  /dev/sdb mbr
```
Reboot, and if you set your BIOS to boot the Ubuntu drive, you should be able to boot into Ubuntu or Windows OK from your Grub menu. If you boot your Windows drive instead, you should be able to boot straight into Windows. Let me know how it goes or if you run into problems.

---

### Post by breakerr on 2009-01-18
**[COLOR="Indigo"]FROM FIRST CODE GOT THIS> [/COLOR]**

breaker@breaker-desktop:~$ sudo grub
[sudo] password for breaker: 
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> root (hd0,0)
root (hd0,0)
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,0)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.
grub> quit
quit
breaker@breaker-desktop:~$ 

**[COLOR="Indigo"]FROM SECOND CODE GOT THIS> [/COLOR]**

breaker@breaker-desktop:~$ sudo apt-get install lilo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lilo is already the newest version.
lilo set to manually installed.
The following packages were automatically installed and are no longer required:
  libboost-python1.34.1 python-mmkeys python-mpd python-xml python-zsi
  python-tagpy
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
breaker@breaker-desktop:~$ sudo lilo -M  /dev/sdb mbr
Backup copy of /dev/sdb in /boot/boot.0810
The Master Boot Record of  /dev/sdb  has been updated.
breaker@breaker-desktop:~$ 
[B][COLOR="DarkRed"]
GOING TO RESTART NOW TO CHECK IF ALL IS OK.[/COLOR][/B]

---

### Post by breakerr on 2009-01-18
_[COLOR="Navy"]THANKS A LOT[/COLOR]_ **caljohnsmith** deeply truely appreciated....worked like a charm and now trying to learn from it because I get all mess up with ***sda sdb hd0 hd1*** thanks aaaa LOOOOOOTT!!!!!!  if you ever need something please let me know at [http://www.breakerr.blogspot.com/](http://www.breakerr.blogspot.com/) I never received a quickest and righteous to the point answer from this forum, THANKSSSSSSS x 100.

---

### Post by caljohnsmith on 2009-01-18
You're certainly welcome, breakerr, I'm glad that worked OK. I took a look at your website, and I'm really impressed with your abstract artwork; looks like you have a really promising future as a professional artist. Cheers and have fun with Windows and Ubuntu. :)

---

