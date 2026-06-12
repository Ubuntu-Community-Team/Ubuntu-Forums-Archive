---
title: "[SOLVED] Reinstalling Win XP after GRUB fails to recognize it on dual boot"
date: 2008-12-27
forum: Installation &amp; Upgrades
---

### Post by corvx on 2008-12-27
So, basically I have 2 Sata drives (both masters, just in case):
1. Ubuntu Intrepid (amd64) - 80gb
2. Windows Xp - 500gb

I installed windows xp before hand on the second drive, then installed intrepid on the first, and so the grub, ... grub did not recognize windows.

```

sudo fdisk -l
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4a504a50

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe96bbce9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       60801   488376000    f  W95 Ext'd (LBA)
/dev/sdb5               2       60801   488375968+   7  HPFS/NTFS

```

Also, I should note that when trying to boot directly on the 500gb drive I get a weird error message, the only thing I can recall was it said something like this:
```

Booting from CD/DVD:
Disk read failure, please insert system disk
(tried inserting windows installation disk and nothing happened)

```
something like that I might have it wrong, but you get the idea.

And last but not least:
```

/boot/grub/menu.lst
title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		6828aeda-46c3-42d2-887b-f13666f1dad3
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=6828aeda-46c3-42d2-887b-f13666f1dad3 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		6828aeda-46c3-42d2-887b-f13666f1dad3
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=6828aeda-46c3-42d2-887b-f13666f1dad3 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		6828aeda-46c3-42d2-887b-f13666f1dad3
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=6828aeda-46c3-42d2-887b-f13666f1dad3 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		6828aeda-46c3-42d2-887b-f13666f1dad3
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=6828aeda-46c3-42d2-887b-f13666f1dad3 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		6828aeda-46c3-42d2-887b-f13666f1dad3
kernel		/boot/memtest86+.bin
quiet

title Windows
map (hd0) (hd1)
map (hd1) (hd0)
chainloader (hd1,0)+1

```
I added the last one, didn't work, just a black screen that said, Starting up or something like that.

---

### Post by damis648 on 2008-12-27
Try this instead:
```
title		Windows XP
root		(hd1,0)
makeactive
chainloader	+1
```

(replace (hd1,0) with whatever Windows is.)

BTW, how can you have two masters? Is one primary and one secondary master?

---

### Post by caljohnsmith on 2008-12-27
You have Windows installed on sdb5, which is a logical partition; that means Windows would have put its boot files in some other primary NTFS/FAT partition, and since you don't seem to have one, the sdb5 Windows partition is probably missing its boot files. In order to get a clearer picture of your setup, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and what it might take to boot Windows from Grub in your present configuration.

---

### Post by corvx on 2008-12-27
> **damis648 said:**
> Try this instead:
```
title		Windows XP
root		(hd1,0)
makeactive
chainloader	+1
```

(replace (hd1,0) with whatever Windows is.)

BTW, how can you have two masters? Is one primary and one secondary master?
Got this when trying your code
```
Error12: Invalid device requested
Press any key to continue
```
then it takes me back to the Grub boot selector.
Well I have 2 SATA slots on my motherboard, each drive on each slot, both figure as Master on my BIOS (no primary no secondary) BUT, there is first and second slot. And I have intrepid installed on the first slot drive (namely the 80gb drive).

> **caljohnsmith said:**
> You have Windows installed on sdb5, which is a logical partition; that means Windows would have put its boot files in some other primary NTFS/FAT partition, and since you don't seem to have one, the sdb5 Windows partition is probably missing its boot files. In order to get a clearer picture of your setup, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and what it might take to boot Windows from Grub in your present configuration.
Yup, I thought something like this too. I should also note, I had previously XP installed on the 80gb drive, then had XP reinstalled on the 500gb drive (without formating the previously 80gb drive), and finally reformating the 80gb drive for the sake of linux. My guess is that the boot info was on the 80gb drive, and when reformatted for installing ubuntu, it got lost. Anyway here is the content of the "RESULTS.txt":
```

============================= Boot Info Summary: ==============================

Grub is installed in the MBR of /dev/sda and looks on the same drive in 
partition #1 for its boot files.
Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda2: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       swap

sdb1: _________________________________________________________________________

    File system:       Extended Partition

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4a504a50

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   149838254    74919096   83  Linux
/dev/sda2       149838255   156296384     3229065    5  Extended
/dev/sda5       149838318   156296384     3229033+  82  Linux swap / Solaris

sfdisk -V /dev/sda:

/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe96bbce9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1           16065   976768064   488376000    f  W95 Ext'd (LBA)
/dev/sdb5           16128   976768064   488375968+   7  HPFS/NTFS

sfdisk -V /dev/sdb:

/dev/sda: OK
Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
/dev/sdb: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="6828aeda-46c3-42d2-887b-f13666f1dad3" TYPE="ext3" 
/dev/sda5: UUID="aae2e797-05b5-4f3b-9d20-31fee659954e" TYPE="swap" 
/dev/sdb5: UUID="6EF4043FF4040C51" TYPE="ntfs" 

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
gvfs-fuse-daemon on /home/eric/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=eric)

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
# kopt=root=UUID=6828aeda-46c3-42d2-887b-f13666f1dad3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=6828aeda-46c3-42d2-887b-f13666f1dad3

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
uuid		6828aeda-46c3-42d2-887b-f13666f1dad3
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=6828aeda-46c3-42d2-887b-f13666f1dad3 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		6828aeda-46c3-42d2-887b-f13666f1dad3
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=6828aeda-46c3-42d2-887b-f13666f1dad3 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		6828aeda-46c3-42d2-887b-f13666f1dad3
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=6828aeda-46c3-42d2-887b-f13666f1dad3 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		6828aeda-46c3-42d2-887b-f13666f1dad3
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=6828aeda-46c3-42d2-887b-f13666f1dad3 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		6828aeda-46c3-42d2-887b-f13666f1dad3
kernel		/boot/memtest86+.bin
quiet

title		Windows XP
root		(hd1,0)
makeactive
chainloader	+1

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=6828aeda-46c3-42d2-887b-f13666f1dad3 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=aae2e797-05b5-4f3b-9d20-31fee659954e none            swap    sw              0       0

================================== sda1/boot: ==================================

total 25524
drwxr-xr-x  3 root root    4096 2008-12-25 22:00 .
drwxr-xr-x 20 root root    4096 2008-12-25 21:58 ..
-rw-r--r--  1 root root  503560 2008-11-04 15:53 abi-2.6.27-7-generic
-rw-r--r--  1 root root  503560 2008-11-20 18:30 abi-2.6.27-9-generic
-rw-r--r--  1 root root   85316 2008-11-04 15:53 config-2.6.27-7-generic
-rw-r--r--  1 root root   85316 2008-11-20 18:30 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2008-12-27 10:59 grub
-rw-r--r--  1 root root 8668545 2008-12-25 21:57 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8668296 2008-12-25 22:00 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 15:11 memtest86+.bin
-rw-r--r--  1 root root 1352144 2008-11-04 15:53 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1352144 2008-11-20 18:30 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1130 2008-11-04 15:57 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1130 2008-11-20 18:32 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2339552 2008-11-04 15:53 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2339712 2008-11-20 18:30 vmlinuz-2.6.27-9-generic

=============================== sda1/boot/grub: ===============================

total 224
drwxr-xr-x 2 root root   4096 2008-12-27 10:59 .
drwxr-xr-x 3 root root   4096 2008-12-25 22:00 ..
-rw-r--r-- 1 root root    197 2008-12-25 20:17 default
-rw-r--r-- 1 root root     45 2008-12-25 20:17 device.map
-rw-r--r-- 1 root root   8108 2008-12-25 20:17 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-25 20:17 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-25 20:17 installed-version
-rw-r--r-- 1 root root   8712 2008-12-25 20:17 jfs_stage1_5
-rw-r--r-- 1 root root   4851 2008-12-27 10:59 menu.lst
-rw-r--r-- 1 root root   4861 2008-12-26 22:12 menu.lst~
-rw-r--r-- 1 root root   7352 2008-12-25 20:17 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-25 20:17 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-25 20:17 stage1
-rw-r--r-- 1 root root 121460 2008-12-25 20:17 stage2
-rw-r--r-- 1 root root   9556 2008-12-25 20:17 xfs_stage1_5

=============================== StdErr Messages: ===============================

No errors were reported.

```
Thanks for the quick response.

---

### Post by caljohnsmith on 2008-12-27
OK, great, that clarifies your setup quite a bit. Unfortunately, you are indeed missing your Windows boot files though, so I've attached them to my post to save you the hassle of digging them off your Windows Install CD. Also, I've configure the "boot.ini" file so that it should work with your particular setup. So to start, go ahead and download the "WinXP_boot_files1.zip" file to your Ubuntu desktop, and then do:
```
sudo mount /dev/sdb5 /mnt
cd ~/Desktop
unzip WinXP_boot_files1.zip
sudo mv boot.ini ntldr NTDETECT.COM /mnt
```
Let me know if any of the above commands return an error. Next, you'll need to correct your Windows entry in the menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And change your Windows entry to:
```
title Windows XP
rootnoverify (hd1,4)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```
Next, the Windows XP boot sector needs fixing, because the partition info in the boot sector currently says your Windows partition starts at sector 63, when really it starts at sector 16128 according to fdisk. So to correct that, first make sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "no log", choose the correct HDD and "proceed", choose "intel", choose "advanced", select the Windows sdb5 partition, choose "boot", then choose "Rebuild BS"; if testdisk gives you a warning that the "sectors are not identical", then choose "write". After you are done doing the "rebuild BS" in testdisk, reboot and let me know exactly what happens when you boot Windows XP from the Grub menu. We can work from there.

---

### Post by corvx on 2008-12-27
> **caljohnsmith said:**
> 
Next, the Windows XP boot sector needs fixing, because the partition info in the boot sector currently says your Windows partition starts at sector 63, when really it starts at sector 16128 according to fdisk. So to correct that, first make sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "no log", choose the correct HDD and "proceed", choose "intel", choose "advanced", select the Windows sdb5 partition, choose "boot", then choose "Rebuild BS"; if testdisk gives you a warning that the "sectors are not identical", then choose "write". After you are done doing the "rebuild BS" in testdisk, reboot and let me know exactly what happens when you boot Windows XP from the Grub menu. We can work from there.
testdisk didn't gave me any warning about sector not being identical, just the opposite they were identical, so I proceeded to "rebuild BS" and rebooted. The outcome:
```
Starting up...
```
Don't know how much time should I have waited, but it didn't seem like it would take me anywhere, so I force reboot and now I'm here (on ubuntu).
Nevertheless I should note some things during test disk.
After selecting "boot", this appeared:
```

TestDisk 6.9, Data Recovery Utility, February 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sdb - 500 GB / 465 GiB - CHS 60801 255 63
     Partition                  Start        End    Size in sectors
 5 L HPFS - NTFS              1   1  1 60800 254 63  976751937

Boot sector
Status: OK

Backup boot sector
Status: OK

Sectors are identical.

A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.

[  Quit  ]  [  List  ]  [Rebuild BS]  [Repair MFT]  [  Dump  ]
                            Return to Advanced menu

```
Then, I chose "Rebuild BS", then I got this:
```

TestDisk 6.9, Data Recovery Utility, February 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sdb - 500 GB / 465 GiB - CHS 60801 255 63
     Partition                  Start        End    Size in sectors
 5 L HPFS - NTFS              1   1  1 60800 254 63  976751937

filesystem size           976751937 976751937
sectors_per_cluster       8 8
mft_lcn                   786432 786432
mftmirr_lcn               61046996 61046996
clusters_per_mft_record   -10 -10
clusters_per_index_record 1 1
Extrapolated boot sector and current boot sector are different.

[  Dump  ]  [  List  ]  [ Write  ]  [  Quit  ]

                           List directories and files

```

---

### Post by caljohnsmith on 2008-12-27
> **corvx said:**
> 
Then, I chose "Rebuild BS", then I got this:
```

TestDisk 6.9, Data Recovery Utility, February 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sdb - 500 GB / 465 GiB - CHS 60801 255 63
     Partition                  Start        End    Size in sectors
 5 L HPFS - NTFS              1   1  1 60800 254 63  976751937

filesystem size           976751937 976751937
sectors_per_cluster       8 8
mft_lcn                   786432 786432
mftmirr_lcn               61046996 61046996
clusters_per_mft_record   -10 -10
clusters_per_index_record 1 1
[COLOR="Red"]Extrapolated boot sector and current boot sector are different.[/COLOR]

[  Dump  ]  [  List  ]  [ Write  ]  [  Quit  ]

                           List directories and files

```
OK, testdisk says the two sectors are different, so go ahead and choose "write" above. Then reboot, and let me know how far you get booting Windows again.

---

### Post by corvx on 2008-12-27
> **caljohnsmith said:**
> OK, testdisk says the two sectors are different, so go ahead and choose "write" above. Then reboot, and let me know how far you get booting Windows again.

Good enough, thanks to you I finally manage to boot XP.
When I select XP the following appear:
```
Please select the operating system to start:
Microsoft Windows Xp
/NoExecute=OptIn 
```
I just have to select the first option and I'm in. I wonder what's up with that "/NoExecute=OptIn" entry, when I select it, it will just reboot. But this seems to me more like a windows related issue, don't know if you know anyway to boot Xp without this additional menu. As this entry seems useless to me.
In addition, I'm the only linux user in my home, probably going to remove the ubuntu hard drive sooner or later. As far as I can picture, by removing the ubuntu drive I won't be able to load XP. In this case, should I restore boot information with Windows xp restore tool (from CD drive)? or Will I have to reinstall the whole windows again?

This is the exact message I get when trying to boot the XP hard drive directly.
```
Boot from CD/DVD: (wait a few seconds, then)
DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER
```
I press enter and all happens over and over again.

EDIT: Don't know it this will help but GParted tells me I have about 7.84mb of unallocated space on the 500gb hard drive (the one with XP on).

BTW, Thanks a lot, I was about to reinstall the whole system again if it wasn't for you :shock:

---

### Post by caljohnsmith on 2008-12-27
Great, I'm glad to hear you can boot Windows from Grub now. But I found out your strange boot menu when you boot Windows is my mistake; somehow an extra line ending ended up in the boot.ini file where it shouldn't have, so sorry about that. To correct it, how about downloading the attached "boot.ini.txt" file to your desktop and do:
```
sudo mount /dev/sdb5 /mnt
sudo mv ~/Desktop/boot.ini.txt /mnt/boot.ini
```
And about booting the Windows drive, that will be quite tricky, because you have Windows on a logical partition and not a primary partition; a Windows MBR is only capable of booting a primary partition. You could try this trick and see if it works:
```
sudo sfdisk -A5 /dev/sdb
sudo lilo -M  /dev/sdb ext
```
And then try booting the Windows sdb drive. But if you have a BIOS that won't boot a drive that doesn't have a primary partition marked as active (bootable), the above method won't work. Let me know what happens though and we can work from there. :)

---

### Post by corvx on 2008-12-27
> **caljohnsmith said:**
> And about booting the Windows drive, that will be quite tricky, because you have Windows on a logical partition and not a primary partition; a Windows MBR is only capable of booting a primary partition. You could try this trick and see if it works:
```
sudo sfdisk -A5 /dev/sdb
sudo lilo -M  /dev/sdb ext
```
And then try booting the Windows sdb drive. But if you have a BIOS that won't boot a drive that doesn't have a primary partition marked as active (bootable), the above method won't work. Let me know what happens though and we can work from there. :)
The new boot.ini worked like charm.
And, yes, it did boot from sdb just as expected :cool:

Now, I know this is not a tutorial, but I like to learn from my mess ups, so finally, can you tell me what exactly those two last commands did (in order to be able to boot from sdb)?

---

### Post by caljohnsmith on 2008-12-27
> **corvx said:**
> The new boot.ini worked like charm.
And, yes, it did boot from sdb just as expected :cool:

Now, I know this is not a tutorial, but I like to learn from my mess ups, so finally, can you tell me what exactly those two last commands did (in order to be able to boot from sdb)?
Glad to hear it worked OK in your case. The first sfdisk command sets the boot flag on the 5th partition of /dev/sdb (your sdb5 Windows partition), and the second lilo command installs a special boot loader to the MBR (Master Boot Record) of the sdb drive that is capable of booting a logical partition which has the boot flag set. Cheers and have fun with Windows and Ubuntu. :)

---

### Post by 62chevy on 2008-12-27
> **caljohnsmith said:**
> 
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```


Thanks caljohnsmith now I can get grub working right. I'm triple booting Debian, Ubuntu and XP. Thinking of trying Slack 12. [http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)

---

### Post by corvx on 2008-12-27
> **caljohnsmith said:**
> Glad to hear it worked OK in your case. The first sfdisk command sets the boot flag on the 5th partition of /dev/sdb (your sdb5 Windows partition), and the second lilo command installs a special boot loader to the MBR (Master Boot Record) of the sdb drive that is capable of booting a logical partition which has the boot flag set. Cheers and have fun with Windows and Ubuntu. :)

Thanks a lot, thread marked as SOLVED :)

---

