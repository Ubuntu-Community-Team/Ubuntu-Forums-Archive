---
title: "[SOLVED] Ubuntu/Windows XP dual boot disaster"
date: 2008-12-28
forum: Installation &amp; Upgrades
---

### Post by impalerau on 2008-12-28
I've had a Windows-free household since the release of Gutsy, with all computers in the house running Hardy (till yesterday).  Then my daughter got a new iPod for Xmas.  After several days of struggling with Rhythmbox & Hipo and still no solution to pictures and videos in sight, I finally relented and agreed to make her laptop dual boot so she could run iTunes.  The laptop only had a 20 Gig drive but I had a 30 Gig available so the idea was a fresh install of Intrepid, a shared NTFS multi-media partition and Windows XP.

Here's what I did:

1. Standard guided install of Intrepid using the whole disk.

2. Used Gparted Live CD to shrink the Intrepid partition (to the left) and move the swap partition next to it leaving 2/3 of the disk free.

3. Used Gparted Live CD to create 2 10 Gig NTFS partitions on the remaining 2/3 of the disk.

4. Copied all the data off the original 20 Gig disk onto the new one with all multi-media going into the middle NTFS partition.

5. Replacede Music, Pictures & Videos directories in the home directory with links to the multi-media disk.

6. Installed all additional software (aMSN, LimeWire, Wine, Ares) and configured to point to the multi=media disk as appropriate.

7. Installed XP in the remaining (right most) NTFS partition.

When I was installing XP I got a warning about it detecting a partition with an unknown operating system and that it would "mark it inactive" (whatever that means).  I figured I would get it installed and sort that out later.  Once XP was installed, the machine would only boot up in XP.  On the plus side, the multi-media partition was available from XP and looking good.  I then fired up the Gparted Live CD again to see if I could "activate" the Intrepid partition.  I saw that the XP partition was flagged as "boot" so I switched the boot flag on in the Intrepid partition.  Now I got an "Invalid boot disk" message when trying to reboot.  After going back and setting the boot flag back on the XP partition, I now just get a blank, black screen with a flashing cursor in the top left corner.  

Could someone please help me get out of this mess.  Ideally, I'd like to avoid having to go through the whole installation process again.  If that's not possible, could someone pleas point me to some instructions on how to do it right.

Thanks in advance,
Vlad.

PS A little knowledge can be a very dangerous thing :)

---

### Post by gettinoriginal on 2008-12-28
Hope this can help you   :P

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by impalerau on 2008-12-28
Thanks gettinoriginal.  Probably shouild have read that first :)

So now that I've very cleverly destroyed both boot sectors, is there any option other than reinstalling both Ubuntu and XP?  Can I create a boot sector some other way?

Also in the Installing Windows after Ubuntu section of the doco, the last step simply says, "Setup grub to boot windows".  How? 

Thanks in advance

---

### Post by gettinoriginal on 2008-12-28
Personally, since mistakes have already been made in the attempt, I would format the HD, install windows first, then with the live CD install Ubuntu.  That way, you get the correct installation including grub, and you are in control all the way.  The live CD has a partitioner on it, so after the installation of Windows, you can set up the HD any way you want.  Good Luck.  :P  But if you do decide to start from scratch, you may want to print out the tutorial so you have it as a guide while you are working on it.

---

### Post by caljohnsmith on 2008-12-28
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by impalerau on 2009-01-01
Oh dear.  Another shortcut gone wrong... and it was looking so good too :)  

The disk was partitioned just how I wanted so I decided to reinstall without reformatting the disk and avoid having to rebuild the multi-media partition.  So I reinstalled XP on the right-most partition.  What a hassle.  Best part of 24 hours and god knows how much wasted download to get it installed and apply all the updates and patches.  And that's with a fast ADSL2+ connection!

Then another day of coming to grips with iTunes.  I used to hate iPods.  Now I loathe them with a passion, but I digress.

So finally, I deleted the the Ubuntu and linux swap partitions and installed Intrepid in the remaining free space.  Got it all up to date and set up just right.  Totally pain free experience btw.  Very impressive.

The boot options come up as expected except that there are 2 Windows XP entries.  Problem is neither of them work.  Both come up with the same message saying can't boot due to missing or corrupt file:

    <windows root>\system32\hal.dll

Boot script details are pasted below.  Please help.  And apologies to gettinoriginal for not taking what was probably very good advice :)

```
============================= Boot Info Summary: ==============================

 => Grub is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for its boot files.

sda1: _________________________________________________________________________

    File system:       Extended Partition

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda3 starts 
                       at sector 19792080.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda4 starts 
                       at sector 39198600.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda6: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders, total 58605120 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    19792079     9896008+   5  Extended
/dev/sda3   *    19792080    39198599     9703260    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sda4        39198600    58605119     9703260    7  HPFS/NTFS
Partition 4 does not end on cylinder boundary.
/dev/sda5             126    18844244     9422059+  83  Linux
/dev/sda6        18844308    19792079      473886   82  Linux swap / Solaris

sfdisk -V /dev/sda:

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
partition 3: start: (c,h,s) expected (1023,254,63) found (1023,0,1)
partition 3: end: (c,h,s) expected (1023,254,63) found (1023,119,63)
partition 4: start: (c,h,s) expected (1023,254,63) found (1023,120,1)
partition 4: end: (c,h,s) expected (1023,254,63) found (1023,239,63)
/dev/sda: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda3: UUID="1A28CD963839F886" LABEL="Documents Disk" TYPE="ntfs" 
/dev/sda4: UUID="023C3A6D6F8B7B8D" TYPE="ntfs" 
/dev/sda5: UUID="0ef79874-0f15-45ea-89c6-f10e3a8eadc5" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="724bd17a-e0d9-4b6b-a628-4a40d733ace6" 

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
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
/dev/sda3 on /media/sda3 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/zoya/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=zoya)
/dev/sda4 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

================================ sda3/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /fastdetect


================================ sda4/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn


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
# kopt=root=UUID=0ef79874-0f15-45ea-89c6-f10e3a8eadc5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=0ef79874-0f15-45ea-89c6-f10e3a8eadc5

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
uuid		0ef79874-0f15-45ea-89c6-f10e3a8eadc5
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=0ef79874-0f15-45ea-89c6-f10e3a8eadc5 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		0ef79874-0f15-45ea-89c6-f10e3a8eadc5
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=0ef79874-0f15-45ea-89c6-f10e3a8eadc5 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		0ef79874-0f15-45ea-89c6-f10e3a8eadc5
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0ef79874-0f15-45ea-89c6-f10e3a8eadc5 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		0ef79874-0f15-45ea-89c6-f10e3a8eadc5
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0ef79874-0f15-45ea-89c6-f10e3a8eadc5 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		0ef79874-0f15-45ea-89c6-f10e3a8eadc5
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Microsoft Windows XP Professional
root		(hd0,2)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title		Microsoft Windows XP Professional
root		(hd0,3)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/sda5
UUID=0ef79874-0f15-45ea-89c6-f10e3a8eadc5  /              ext3         relatime,errors=remount-ro  0  1  
# /dev/sda6
UUID=724bd17a-e0d9-4b6b-a628-4a40d733ace6  none           swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/sda3                                  /media/sda3    ntfs-3g      defaults                    0  0  

================================== sda5/boot: ==================================

total 23812
drwxr-xr-x  3 root root    4096 2008-12-31 04:13 .
drwxr-xr-x 20 root root    4096 2008-12-31 04:11 ..
-rw-r--r--  1 root root  507665 2008-11-05 08:00 abi-2.6.27-7-generic
-rw-r--r--  1 root root  507665 2008-11-21 10:46 abi-2.6.27-9-generic
-rw-r--r--  1 root root   91364 2008-11-05 08:00 config-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-11-21 10:46 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2008-12-31 04:11 grub
-rw-r--r--  1 root root 8207325 2008-12-31 04:10 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8207320 2008-12-31 04:13 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-12 06:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-11-05 08:00 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1029585 2008-11-21 10:46 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1073 2008-11-05 08:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-11-21 10:48 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2244464 2008-11-05 08:00 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2244304 2008-11-21 10:46 vmlinuz-2.6.27-9-generic

=============================== sda5/boot/grub: ===============================

total 224
drwxr-xr-x 2 root root   4096 2008-12-31 04:11 .
drwxr-xr-x 3 root root   4096 2008-12-31 04:13 ..
-rw-r--r-- 1 root root    197 2008-12-31 00:47 default
-rw-r--r-- 1 root root     15 2008-12-31 00:47 device.map
-rw-r--r-- 1 root root   8108 2008-12-31 00:47 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-31 00:47 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-31 00:47 installed-version
-rw-r--r-- 1 root root   8712 2008-12-31 00:47 jfs_stage1_5
-rw-r--r-- 1 root root   5289 2008-12-31 04:11 menu.lst
-rw-r--r-- 1 root root   5205 2008-12-31 04:11 menu.lst~
-rw-r--r-- 1 root root   7352 2008-12-31 00:47 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-31 00:47 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-31 00:47 stage1
-rw-r--r-- 1 root root 121460 2008-12-31 00:47 stage2
-rw-r--r-- 1 root root   9556 2008-12-31 00:47 xfs_stage1_5

=============================== StdErr Messages: ===============================

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.


```

---

### Post by caljohnsmith on 2009-01-01
OK, I believe I see at least part of the problem: your Windows boot.ini file points to the wrong partition. To fix it, first do:
```
gksudo gedit /media/disk/boot.ini
```
And modify the partition numbers as highlighted in red:
```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition[COLOR="Red"](2)[/COLOR]\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition[COLOR="Red"](2)[/COLOR]\WINDOWS="Microsoft Windows XP Professional" /fastdetect
```
Next pull up your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And you can delete the Windows entry at the bottom that uses (hd0,2), but keep the Windows entry that uses (hd0,3). Next reboot, select Windows XP from the Grub menu, and let me know exactly what happens. Most likely it should work since your Windows is a fresh install, but if it doesn't, we can go from there if you want.

---

### Post by impalerau on 2009-01-01
Thanks so much, caljohnsmith.  That seemed to be the whole problem.  Dual boot is working just as it should.  I can now got to bed and look forward to a happy daughter when she wakes up tomorrow.

---

### Post by caljohnsmith on 2009-01-01
Glad that did the trick; cheers and Happy New Year. :)

---

### Post by grandsatrap on 2009-01-01
You may want to look into a program called "BootIt Ng" It is excellent and handles every possible type of multiple boot as well as moving, resizing, and copying partitions around.

---

