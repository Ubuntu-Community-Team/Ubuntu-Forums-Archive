---
title: "[SOLVED] Grub Error 22 -&amp;gt; NTLDR Missing"
date: 2008-12-18
forum: Installation &amp; Upgrades
---

### Post by Mouser58907 on 2008-12-18
Hey guys I'm brand new to linux. I installed ubuntu about 3 weeks ago and have spent less than 4 hours on here total. I'm in ubuntu now because I can't get into my windows.

I have 2 hard drives, SATA0 is 250gb with XP Pro. SATA1 is 1TB with 200GB to Ubuntu, rest open storage for XP. I've been able to restart fine since the install, but I woke up this morning to:

Grub Loading please wait...
Error 22.

I then googled around and found this article:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

I did it once using 
setup (hd0) (I was given hd(1,4))
then that didn't work so I used:
setup (hd1)

now I can get into ubuntu even and I can select XP from Grub, but when I get to it I have NTLDR Missing. I've seen this error before and I got worried and ran here.

-edit, I have Ubuntu and XP CD's handy.
 I tried booting up the XP repair console and it seems to have forgot my admin pw. 
 I tried leaving it blank too, no joy.

Thanks in advance,

mouser58907

---

### Post by Pumalite on 2008-12-18
Read this. It might help you:
[http://ubuntuforums.org/showthread.php?t=813628&highlight=meierfra](http://ubuntuforums.org/showthread.php?t=813628&highlight=meierfra)

---

### Post by Mouser58907 on 2008-12-18
Alright I tried this, didn't work. At the last step:
Step 5: Rebuild the Boot sector of the Windows partition.
It said they were identical. 

I think I may know why it screwed up to start with. I had an 80gb external usb drive plugged in that has never been in before. Unfortunately I just realized it so I can't just unplug it, It doesn't work with it unplugged either.

---

### Post by caljohnsmith on 2008-12-18
Chances are your Windows partition is fine if you were able to previously boot it, so you probably don't need to follow that tutorial to rebuild the XP boot sector. In order to get a clearer picture of your setup, how about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo sh boot_info_script.txt
```
That will create a "boot_info_results.txt" file on your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and what your problem might be.

---

### Post by Mouser58907 on 2008-12-18
Grub is installed in the MBR of /dev/sda and looks on boot drive #2 in partition #5 for its boot files.
Grub is installed in the MBR of /dev/sdb and looks on the same drive in partition #5 for its boot files.
No known boot loader is installed in the MBR of /dev/sdc
No known boot loader is installed in the MBR of /dev/sdd
No known boot loader is installed in the MBR of /dev/sde
No known boot loader is installed in the MBR of /dev/sdf

sda1:
    File system:  ntfs
    Boot sector  type:  XP
    Boot sector  info:  According to the info in the boot sector, sda1 starts at sector 63
    Operating System: XP
    Boot files/directories present:  /boot.ini /ntldr /NTLDR /NTDETECT.COM

sdb1:
    File system:  ntfs
    Boot sector  type:  XPa
    Boot sector  info:  According to the info in the boot sector, sdb1 starts at sector 63
    Operating System: 
    Boot files/directories present: 

sdb2:
    File system:  Extended Partition

sdb5:
    File system:  ext3
    Boot sector  type:  Unknown
    Boot sector  info:  
    Operating System: Linux
    Boot files/directories present:  /boot/grub/menu.lst /boot /boot/grub

sdb6:
    File system:  swap


Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcad0cad0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   490207409   245103673+   7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe4e2e5a6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63  1741670909   870835423+   7  HPFS/NTFS
/dev/sdb2      1741670910  1953520064   105924577+   5  Extended
/dev/sdb5      1741670973  1944812834   101570931   83  Linux
/dev/sdb6      1944812898  1953520064     4353583+  82  Linux swap / Solaris
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=490207347, Id= 7, bootable
/dev/sda2 : start=        0, size=        0, Id= 0
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=       63, size=1741670847, Id= 7, bootable
/dev/sdb2 : start=1741670910, size=211849155, Id= 5
/dev/sdb3 : start=        0, size=        0, Id= 0
/dev/sdb4 : start=        0, size=        0, Id= 0
/dev/sdb5 : start=1741670973, size=203141862, Id=83
/dev/sdb6 : start=1944812898, size=  8707167, Id=82

sda1/boot.ini

[Boot Loader]

timeout=30

Default=multi(0)disk(0)rdisk(0)partition(3)\Windows

[Operating Systems]

multi(0)disk(0)rdisk(0)partition(3)\Windows="Windows XP" /fastdetect




sdb5/boot/grub/menu.lst

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
# kopt=root=UUID=9355a1be-b2bb-4638-ad70-9d3f540ceb6d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9355a1be-b2bb-4638-ad70-9d3f540ceb6d

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
uuid		9355a1be-b2bb-4638-ad70-9d3f540ceb6d
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=9355a1be-b2bb-4638-ad70-9d3f540ceb6d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		9355a1be-b2bb-4638-ad70-9d3f540ceb6d
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=9355a1be-b2bb-4638-ad70-9d3f540ceb6d ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		9355a1be-b2bb-4638-ad70-9d3f540ceb6d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=9355a1be-b2bb-4638-ad70-9d3f540ceb6d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		9355a1be-b2bb-4638-ad70-9d3f540ceb6d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=9355a1be-b2bb-4638-ad70-9d3f540ceb6d ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		9355a1be-b2bb-4638-ad70-9d3f540ceb6d
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		XP
rootnoverify	(hd0,0)
chainloader	+1


sdb5/boot

total 25516
drwxr-xr-x  3 root root    4096 2008-12-18 14:00 .
drwxr-xr-x 22 root root    4096 2008-12-18 14:14 ..
-rw-r--r--  1 root root  503560 2008-11-04 14:53 abi-2.6.27-7-generic
-rw-r--r--  1 root root  503560 2008-11-20 17:30 abi-2.6.27-9-generic
-rw-r--r--  1 root root   85316 2008-11-04 14:53 config-2.6.27-7-generic
-rw-r--r--  1 root root   85316 2008-11-20 17:30 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2008-12-18 14:47 grub
-rw-r--r--  1 root root 8666256 2008-12-05 14:29 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8665340 2008-12-18 14:00 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 15:11 memtest86+.bin
-rw-r--r--  1 root root 1352144 2008-11-04 14:53 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1352144 2008-11-20 17:30 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1130 2008-11-04 14:57 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1130 2008-11-20 17:32 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2339552 2008-11-04 14:53 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2339712 2008-11-20 17:30 vmlinuz-2.6.27-9-generic

sdb5/boot/grub

total 224
drwxr-xr-x 2 root root   4096 2008-12-18 14:47 .
drwxr-xr-x 3 root root   4096 2008-12-18 14:00 ..
-rw-r--r-- 1 root root    197 2008-12-05 14:13 default
-rw-r--r-- 1 root root     30 2008-12-05 14:13 device.map
-rw-r--r-- 1 root root   8108 2008-12-05 14:13 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-05 14:13 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-05 14:13 installed-version
-rw-r--r-- 1 root root   8712 2008-12-05 14:13 jfs_stage1_5
-rw-r--r-- 1 root root   5056 2008-12-18 14:47 menu.lst
-rw-r--r-- 1 root root   5056 2008-12-18 14:40 menu.lst~
-rw-r--r-- 1 root root   7352 2008-12-05 14:13 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-05 14:13 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-05 14:13 stage1
-rw-r--r-- 1 root root 121460 2008-12-05 14:13 stage2
-rw-r--r-- 1 root root   9556 2008-12-05 14:13 xfs_stage1_5

StdErr Messages 

Unknown MBR on /dev/sdc


Unknown MBR on /dev/sdd


Unknown MBR on /dev/sde


Unknown MBR on /dev/sdf


xxd: /dev/sdc: No medium found
hexdump: /dev/sdc: No medium found
/dev/sdc: No medium found

sfdisk: cannot open /dev/sdc for reading
xxd: /dev/sdd: No medium found
hexdump: /dev/sdd: No medium found
/dev/sdd: No medium found

sfdisk: cannot open /dev/sdd for reading
xxd: /dev/sde: No medium found
hexdump: /dev/sde: No medium found
/dev/sde: No medium found

sfdisk: cannot open /dev/sde for reading
xxd: /dev/sdf: No medium found
hexdump: /dev/sdf: No medium found
/dev/sdf: No medium found

sfdisk: cannot open /dev/sdf for reading
/dev/sdb2: unknown volume type

---

### Post by caljohnsmith on 2008-12-18
OK, how about first opening your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And then change your Windows XP entry near the bottom to:
```
title       Windows XP (hd1)
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
Also, since you can now boot Ubuntu from your sdb drive, it would be good to restore a Windows MBR to your sda Windows drive; that way if anything happens to Ubuntu or the Ubuntu drive, you should still be able to boot into Windows OK. If that sounds good to you, then do:
```
sudo lilo -M  /dev/sda mbr
```
Then reboot, and let me know exactly what happens when you boot XP from your Grub menu. We can work from there. :)

---

### Post by Mouser58907 on 2008-12-18
alright so I selected Windows XP (hd1) and recieved the following:

Windows could not start because of a computer disk hardware configuration problem.
Could not read from the selected boot disk. Check boot path and disk hardware.
Please Check the Windows documentation about hardware disk configuration and your hardware reference manuals for additional information.

Appreciate the help so far.

---

### Post by caljohnsmith on 2008-12-18
OK, I believe I see the problem: your Windows XP boot.ini file is pointing to the wrong partition. How about doing the following:
```
sudo mount /dev/sda1 /mnt
gksudo gedit /mnt/boot.ini
```
And change the partition numbers to "1" as follows:
```
[Boot Loader]
timeout=30
Default=multi(0)disk(0)rdisk(0)partition[COLOR="Blue"](1)[/COLOR]\Windows
[Operating Systems]
multi(0)disk(0)rdisk(0)partition[COLOR="Blue"](1)[/COLOR]\Windows="Windows XP" /fastdetect
```
Save, reboot, and let me know what happens again when you try and boot Windows from Grub.

---

### Post by oliwek on 2008-12-18
mouser, for info, in case you really have lost your xp admin password (different from your personal account password with administrative rights), you can use several tools to reset it or to retrieve it : google a  bit (windows password recovery) or see [here]("http://www.petri.co.il/forgot_administrator_password.htm#20"). If you have already burned [Ultimate boot cd]("http://www.ultimatebootcd.com/")(see the "Offline NT Password & Registry Editor") or [Hirens boot cd]("http://www.hiren.info/pages/bootcd") ("Offline NT/2K/XP Password Changer" and "Active Password Changer"), you can use that : you'll find the right tool there too.  This last cd especially has also lots of usefull things to work on partitions/mbr/....

you can then reboot with  your xp cd, type "R" to get access to the recovery console, and use FIXBOOT + FIXMBR commands to solve your xp boot issue...

---

### Post by Mouser58907 on 2008-12-18
Got this error this time:

Windows could not start because the following file is missing or corrupt.
<WindowsRoot>\system32\ntoskrnl.exe.
Please Re-install a copy of the above file.

Ha that first tutorial has me change those to 3, I had a feeling that was wrong.

---

### Post by caljohnsmith on 2008-12-18
Since you now have a Windows MBR in your Windows sda drive, if you boot the drive directly on start by setting your BIOS to boot it, do you get the same error? You mentioned that the tutorial had you change the boot.ini file; did you change anything else in Windows? When was the last time you could successfully boot into Windows?

---

### Post by Mouser58907 on 2008-12-18
I'm sorry I'm not sure I know what you mean. My windows HDD is my primary drive in my bios. I restarted again and got the same error. I have not changed anything else in windows.

---

### Post by caljohnsmith on 2008-12-18
Do you have your Windows Install CD? It looks quite likely that you will need it to get Windows working again. How about also posting:
```
sudo mkdir /mnt/sda1 /mnt/sdb1
sudo mount /dev/sda1 /mnt/sda1
sudo mount /dev/sdb1 /mnt/sdb1
ls -l /mnt/sda1 /mnt/sdb1
```

---

### Post by Mouser58907 on 2008-12-18
Yes I do have the CD but either it forgot my admin password or I used a different one than I usually do for some reason. I'll try some more. Heres the results of the above code:

/mnt/sda1:
total 1589
-rwxrwxrwx 1 root root      0 2008-10-19 23:33 AUTOEXEC.BAT
-rwxrwxrwx 1 root root    173 2008-12-18 16:11 boot.ini
-rwxrwxrwx 1 root root    173 2008-12-18 14:46 boot.ini~
-rwxrwxrwx 1 root root      0 2008-12-18 14:34 boot.ini.save
-rwxrwxrwx 1 root root    213 2008-12-18 14:34 boot.ini.save.1
-rwxrwxrwx 1 root root    213 2008-12-18 14:35 boot.ini.save.2
-rwxrwxrwx 1 root root    213 2008-12-18 14:37 boot.ini.save.3
-rwxrwxrwx 1 root root      0 2008-10-24 14:04 check.eps
-rwxrwxrwx 1 root root      0 2008-10-24 14:04 check.max
-rwxrwxrwx 1 root root      0 2008-10-24 14:04 check.pdd
-rwxrwxrwx 1 root root      0 2008-10-24 14:04 check.psd
drwxrwxrwx 1 root root   4096 2008-12-14 16:53 Config.Msi
-rwxrwxrwx 1 root root      0 2008-10-19 23:33 CONFIG.SYS
drwxrwxrwx 1 root root      0 2008-11-13 19:52 CUDA
drwxrwxrwx 1 root root   4096 2008-10-22 09:50 Documents and Settings
-rwxrwxrwx 1 root root      0 2008-10-19 23:33 IO.SYS
-rwxrwxrwx 1 root root    374 2008-10-20 00:53 IPH.PH
drwxrwxrwx 1 root root   4096 2008-11-14 14:35 Movies
-rwxrwxrwx 1 root root 904704 2006-12-01 22:37 msdia80.dll
-rwxrwxrwx 1 root root      0 2008-10-19 23:33 MSDOS.SYS
drwxrwxrwx 1 root root      0 2008-10-20 19:44 MSOCache
drwxrwxrwx 1 root root   4096 2008-12-14 17:00 NETRENDER
-rwxrwxrwx 1 root root  47580 2002-09-16 00:50 NTDETECT.COM
-rwxrwxrwx 1 root root 297072 2008-10-20 00:22 ntldr
-rwxrwxrwx 1 root root 233632 2002-09-16 00:50 NTLDR
drwxrwxrwx 1 root root      0 2008-10-19 23:47 NVIDIA
drwxrwxrwx 1 root root      0 2008-11-30 21:40 OpenCandy
drwxrwxrwx 1 root root   8192 2008-11-11 01:06 Program Files
drwxrwxrwx 1 root root  24576 2008-12-14 00:21 Program Files (x86)
drwxrwxrwx 1 root root      0 2008-10-22 09:52 RECYCLER
-rwxrwxrwx 2 root root    268 2008-10-20 14:38 sqmdata00.sqm
-rwxrwxrwx 2 root root    232 2008-12-15 18:36 sqmdata01.sqm
-rwxrwxrwx 2 root root    244 2008-10-20 14:38 sqmnoopt00.sqm
-rwxrwxrwx 2 root root    244 2008-12-15 18:36 sqmnoopt01.sqm
drwxrwxrwx 1 root root   4096 2008-10-19 23:37 System Volume Information
drwxrwxrwx 1 root root  77824 2008-12-18 03:00 WINDOWS
drwxrwxrwx 1 root root      0 2008-10-20 14:56 XP_64

/mnt/sdb1:
total 96
drwxrwxrwx 1 root root  4096 2008-12-14 16:00 Alaska Cruise
drwxrwxrwx 1 root root 45056 2008-12-14 16:02 Argentina Good
drwxrwxrwx 1 root root  4096 2008-12-14 16:03 cis200
drwxrwxrwx 1 root root     0 2008-12-14 17:00 Downloads
drwxrwxrwx 1 root root 16384 2008-12-14 16:04 maps
drwxrwxrwx 1 root root 16384 2008-12-14 16:34 My Videos
drwxrwxrwx 1 root root  8192 2008-12-14 16:16 Presets
drwxrwxrwx 1 root root     0 2008-12-10 16:51 RECYCLER
drwxrwxrwx 1 root root  4096 2008-12-07 21:29 System Volume Information

seems I have a few too many boot.ini's?

---

### Post by caljohnsmith on 2008-12-18
OK, while you still have those partitions mounted, lets do a quick sanity check:
```
cat -A /mnt/sda1/boot.ini
ls -l /mnt/sda1/WINDOWS/system32/n*
```

---

### Post by Mouser58907 on 2008-12-18
wow thats a lot of mumbo jumbo.

-rwxrwxrwx 1 root root    65024 2007-02-16 23:39 /mnt/sda1/WINDOWS/system32/narrator.exe
-rwxrwxrwx 1 root root    55296 2005-03-25 06:00 /mnt/sda1/WINDOWS/system32/narrhook.dll
-rwxrwxrwx 1 root root    27136 2005-03-25 06:00 /mnt/sda1/WINDOWS/system32/nbtstat.exe
-rwxrwxrwx 1 root root    81920 2005-03-25 06:00 /mnt/sda1/WINDOWS/system32/ncobjapi.dll
-rwxrwxrwx 1 root root    59904 2007-02-16 23:39 /mnt/sda1/WINDOWS/system32/ncpa.cpl
-rwxrwxrwx 2 root root      749 2008-10-19 23:32 /mnt/sda1/WINDOWS/system32/ncpa.cpl.manifest
-rwxrwxrwx 1 root root    14848 2005-03-25 06:00 /mnt/sda1/WINDOWS/system32/ncxpnt.dll
-rwxrwxrwx 1 root root    25600 2005-03-25 06:00 /mnt/sda1/WINDOWS/system32/nddeapi.dll
-rwxrwxrwx 1 root root     4608 2005-03-25 06:00 /mnt/sda1/WINDOWS/system32/nddeapir.exe
-rwxrwxrwx 1 root root    25600 2007-02-16 23:39 /mnt/sda1/WINDOWS/system32/nddenb32.dll
-rwxrwxrwx 1 root root    77824 2005-03-25 06:00 /mnt/sda1/WINDOWS/system32/ndptsp.tsp
-rwxrwxrwx 1 root root   219648 2007-02-16 23:39 /mnt/sda1/WINDOWS/system32/net1.exe
-rwxrwxrwx 1 root root   603648 2008-10-17 07:53 /mnt/sda1/WINDOWS/system32/netapi32.dll
-rwxrwxrwx 1 root root  1354240 2005-03-25 06:00 /mnt/sda1/WINDOWS/system32/netcfgx.dll
-rwxrwxrwx 1 root root   160768 2007-02-16 23:40 /mnt/sda1/WINDOWS/system32/netdde.exe
-rwxrwxrwx 1 root root   230912 2005-03-25 06:00 /mnt/sda1/WINDOWS/system32/netevent.dll
-rwxrwxrwx 1 root root    74752 2005-03-25 06:00 /mnt/sda1/WINDOWS/system32/net.exe
-rwxrwxrwx 2 root root    13824 2008-07-25 10:13 /mnt/sda1/WINDOWS/system32/netfxperf.dll
-rwxrwxrwx 1 root root   254976 2005-03-25 06:00 /mnt/sda1/WINDOWS/system32/neth.dll
-rwxrwxrwx 1 root root   102434 2005-03-25 06:00 /mnt/sda1/WINDOWS/system32/net.hlp
-rwxrwxrwx 1 root root   244736 2007-02-16 23:40 /mnt/sda1/WINDOWS/system32/netid.dll
-rwxrwxrwx 1 root root   681984 2005-03-25 06:00 /mnt/sda1/WINDOWS/system32/netlogon.dll
-rwxrwxrwx 1 root root   467968 2005-03-25 06:00 /mnt/sda1/WINDOWS/system32/netman.dll
-rwxrwxrwx 1 root root   183296 2005-03-25 06:00 /mnt/sda1/WINDOWS/system32/netmsg.dll
-rwxrwxrwx 1 root root   961024 2007-02-16 23:40 /mnt/sda1/WINDOWS/system32/netplwiz.dll
-rwxrwxrwx 1 root root    26624 2005-03-25 06:00 /mnt/sda1/WINDOWS/system32/netrap.dll
-rwxrwxrwx 1 root root    69120 2007-02-16 23:40 /mnt/sda1/WINDOWS/system32/netset03.exe
-rwxrwxrwx 1 root root    30208 2005-03-25 06:00 /mnt/sda1/WINDOWS/system32/netsetup.cpl
-rwxrwxrwx 1 root root  2437120 2005-03-25 06:00 /mnt/sda1/WINDOWS/system32/netshell.dll
-rwxrwxrwx 1 root root   115200 2007-02-16 23:40 /mnt/sda1/WINDOWS/system32/netsh.exe
-rwxrwxrwx 1 root root    47616 2007-02-16 23:40 /mnt/sda1/WINDOWS/system32/netstat.exe
-rwxrwxrwx 1 root root   133120 2005-03-25 06:00 /mnt/sda1/WINDOWS/system32/netui0.dll
-rwxrwxrwx 1 root root   346624 2005-03-25 06:00 /mnt/sda1/WINDOWS/system32/netui1.dll
-rwxrwxrwx 1 root root   555008 2007-02-16 23:40 /mnt/sda1/WINDOWS/system32/netui2.dll
-rwxrwxrwx 1 root root   284160 2005-03-25 06:00 /mnt/sda1/WINDOWS/system32/newdev.dll
-rwxrwxrwx 1 root root   183296 2007-02-16 23:40 /mnt/sda1/WINDOWS/system32/nlhtml.dll
-rwxrwxrwx 1 root root    29184 2006-06-28 18:09 /mnt/sda1/WINDOWS/system32/nlsdl.dll
-rwxrwxrwx 1 root root     1696 2005-03-25 06:00 /mnt/sda1/WINDOWS/system32/noise.chs
-rwxrwxrwx 1 root root     1696 2005-03-25 06:00 /mnt/sda1/WINDOWS/system32/noise.cht
-rwxrwxrwx 1 root root      741 2005-03-25 06:00 /mnt/sda1/WINDOWS/system32/noise.dat
-rwxrwxrwx 1 root root   151578 2005-03-25 06:00 /mnt/sda1/WINDOWS/system32/noise.deu
-rwxrwxrwx 1 root root      751 2005-03-25 06:00 /mnt/sda1/WINDOWS/system32/noise.eng
-rwxrwxrwx 1 root root      751 2005-03-25 06:00 /mnt/sda1/WINDOWS/system32/noise.enu
-rwxrwxrwx 1 root root    20774 2005-03-25 06:00 /mnt/sda1/WINDOWS/system32/noise.esn
-rwxrwxrwx 1 root root    49906 2005-03-25 06:00 /mnt/sda1/WINDOWS/system32/noise.fra
-rwxrwxrwx 1 root root    20694 2005-03-25 06:00 /mnt/sda1/WINDOWS/system32/noise.ita
-rwxrwxrwx 1 root root    13256 2005-03-25 06:00 /mnt/sda1/WINDOWS/system32/noise.nld
-rwxrwxrwx 1 root root    14564 2005-03-25 06:00 /mnt/sda1/WINDOWS/system32/noise.sve
-rwxrwxrwx 1 root root      697 2005-03-25 06:00 /mnt/sda1/WINDOWS/system32/noise.tha
-rwxrwxrwx 1 root root    25088 2006-06-29 08:05 /mnt/sda1/WINDOWS/system32/normaliz.dll
-rwxrwxrwx 1 root root    59342 2006-06-08 12:06 /mnt/sda1/WINDOWS/system32/normidna.nls
-rwxrwxrwx 1 root root    45794 2006-06-08 12:06 /mnt/sda1/WINDOWS/system32/normnfc.nls
-rwxrwxrwx 1 root root    39284 2006-06-08 12:06 /mnt/sda1/WINDOWS/system32/normnfd.nls
-rwxrwxrwx 1 root root    66384 2006-06-08 12:06 /mnt/sda1/WINDOWS/system32/normnfkc.nls
-rwxrwxrwx 1 root root    60294 2006-06-08 12:06 /mnt/sda1/WINDOWS/system32/normnfkd.nls
-rwxrwxrwx 1 root root    88064 2005-03-25 06:00 /mnt/sda1/WINDOWS/system32/notepad.exe
-rwxrwxrwx 1 root root    83968 2005-03-25 06:00 /mnt/sda1/WINDOWS/system32/npptools.dll
-rwxrwxrwx 1 root root   587776 2007-02-16 23:40 /mnt/sda1/WINDOWS/system32/nshipsec.dll
-rwxrwxrwx 1 root root   113664 2007-02-16 23:40 /mnt/sda1/WINDOWS/system32/nslookup.exe
-rwxrwxrwx 1 root root  1966592 2007-02-16 23:40 /mnt/sda1/WINDOWS/system32/ntbackup.exe
-rwxrwxrwx 1 root root  1254400 2007-02-18 09:57 /mnt/sda1/WINDOWS/system32/ntdll.dll
-rwxrwxrwx 1 root root   130560 2005-03-25 06:00 /mnt/sda1/WINDOWS/system32/ntdsapi.dll
-rwxrwxrwx 1 root root    44544 2007-02-16 23:41 /mnt/sda1/WINDOWS/system32/ntdsbcli.dll
-rwxrwxrwx 1 root root  6307840 2007-02-16 23:40 /mnt/sda1/WINDOWS/system32/ntds.dit
-rwxrwxrwx 1 root root    48794 2005-03-25 06:00 /mnt/sda1/WINDOWS/system32/ntimage.gif
-rwxrwxrwx 1 root root    73216 2005-03-25 06:00 /mnt/sda1/WINDOWS/system32/ntlanman.dll
-rwxrwxrwx 1 root root    20480 2005-03-25 06:00 /mnt/sda1/WINDOWS/system32/ntlanui2.dll
-rwxrwxrwx 1 root root    87040 2005-03-25 06:00 /mnt/sda1/WINDOWS/system32/ntlanui.dll
-rwxrwxrwx 1 root root    11264 2005-03-25 06:00 /mnt/sda1/WINDOWS/system32/ntlsapi.dll
-rwxrwxrwx 1 root root   227840 2005-03-25 06:00 /mnt/sda1/WINDOWS/system32/ntmarta.dll
-rwxrwxrwx 1 root root    92672 2007-02-16 23:41 /mnt/sda1/WINDOWS/system32/ntmsapi.dll
-rwxrwxrwx 1 root root   358400 2007-02-16 23:41 /mnt/sda1/WINDOWS/system32/ntmsdba.dll
-rwxrwxrwx 1 root root    41984 2005-03-25 06:00 /mnt/sda1/WINDOWS/system32/ntmsevt.dll
-rwxrwxrwx 1 root root   934400 2007-02-16 23:41 /mnt/sda1/WINDOWS/system32/ntmsmgr.dll
-rwxrwxrwx 1 root root    26209 2005-03-25 06:00 /mnt/sda1/WINDOWS/system32/ntmsmgr.msc
-rwxrwxrwx 1 root root    32968 2005-03-25 06:00 /mnt/sda1/WINDOWS/system32/ntmsoprq.msc
-rwxrwxrwx 1 root root   794112 2007-02-16 23:41 /mnt/sda1/WINDOWS/system32/ntmssvc.dll
-rwxrwxrwx 1 root root  4587520 2008-08-14 07:57 /mnt/sda1/WINDOWS/system32/ntoskrnl.exe
-rwxrwxrwx 1 root root   158720 2007-02-16 23:41 /mnt/sda1/WINDOWS/system32/ntprint.dll
-rwxrwxrwx 1 root root    55296 2007-02-18 09:58 /mnt/sda1/WINDOWS/system32/ntsd.exe
-rwxrwxrwx 1 root root   188416 2005-03-25 06:00 /mnt/sda1/WINDOWS/system32/ntshrui.dll
-rwxrwxrwx 1 root root    16896 2005-03-25 06:00 /mnt/sda1/WINDOWS/system32/ntvdm64.dll
-rwxrwxrwx 1 root root   277504 2007-02-16 23:41 /mnt/sda1/WINDOWS/system32/nusrmgr.cpl
-rwxrwxrwx 1 root root  8763648 2008-10-07 13:33 /mnt/sda1/WINDOWS/system32/nv4_disp.dll
-rwxrwxrwx 1 root root   689664 2008-10-07 13:33 /mnt/sda1/WINDOWS/system32/nvapi64.dll
-rwxrwxrwx 1 root root   476160 2008-10-07 13:33 /mnt/sda1/WINDOWS/system32/nvappbar.exe
-rwxrwxrwx 1 root root   200910 2008-12-11 08:56 /mnt/sda1/WINDOWS/system32/nvapps.xml
-rwxrwxrwx 1 root root   135680 2008-10-07 13:33 /mnt/sda1/WINDOWS/system32/nvcod.dll
-rwxrwxrwx 1 root root   135680 2008-10-07 13:33 /mnt/sda1/WINDOWS/system32/nvcodins.dll
-rwxrwxrwx 1 root root   174592 2008-10-07 13:33 /mnt/sda1/WINDOWS/system32/nvcolor.exe
-rwxrwxrwx 1 root root    42496 2006-08-04 01:49 /mnt/sda1/WINDOWS/system32/nvconrm.dll
-rwxrwxrwx 1 root root    40960 2008-10-07 13:33 /mnt/sda1/WINDOWS/system32/nvcpl32.exe
-rwxrwxrwx 1 root root   410656 2008-10-07 13:33 /mnt/sda1/WINDOWS/system32/nvcpl.cpl
-rwxrwxrwx 1 root root 15929344 2008-10-07 13:33 /mnt/sda1/WINDOWS/system32/nvcpl.dll
-rwxrwxrwx 1 root root  2112544 2008-10-07 13:33 /mnt/sda1/WINDOWS/system32/nvcplui.exe
-rwxrwxrwx 1 root root  1003008 2006-09-06 11:48 /mnt/sda1/WINDOWS/system32/nvcplUIR.dll
-rwxrwxrwx 1 root root  2007040 2008-10-07 13:33 /mnt/sda1/WINDOWS/system32/nvcuda.dll
-rwxrwxrwx 1 root root    18477 2008-10-07 13:33 /mnt/sda1/WINDOWS/system32/nvdisp.nvu
-rwxrwxrwx 1 root root  4319232 2008-10-07 13:33 /mnt/sda1/WINDOWS/system32/nvdisps.dll
-rwxrwxrwx 1 root root   381952 2006-09-06 11:47 /mnt/sda1/WINDOWS/system32/nvexpBar.dll
-rwxrwxrwx 1 root root  5042176 2008-10-07 13:33 /mnt/sda1/WINDOWS/system32/nvgames.dll
-rwxrwxrwx 1 root root  1263616 2008-10-07 13:33 /mnt/sda1/WINDOWS/system32/nview64.dll
-rwxrwxrwx 1 root root   258560 2008-10-07 13:33 /mnt/sda1/WINDOWS/system32/nvmccs.dll
-rwxrwxrwx 1 root root    35328 2008-10-07 13:33 /mnt/sda1/WINDOWS/system32/nvmccsrs.dll
-rwxrwxrwx 1 root root   283136 2008-10-07 13:33 /mnt/sda1/WINDOWS/system32/nvmccss.dll
-rwxrwxrwx 1 root root    75776 2008-10-07 13:33 /mnt/sda1/WINDOWS/system32/nvmctray.dll
-rwxrwxrwx 1 root root  1612800 2008-10-07 13:33 /mnt/sda1/WINDOWS/system32/nvmobls.dll
-rwxrwxrwx 1 root root        8 2008-12-05 13:53 /mnt/sda1/WINDOWS/system32/nvModes.dat
-rwxrwxrwx 1 root root     3903 2006-06-01 17:32 /mnt/sda1/WINDOWS/system32/nvnrm.nvu
-rwxrwxrwx 1 root root   293376 2008-10-07 13:33 /mnt/sda1/WINDOWS/system32/nvnt4cpl.dll
-rwxrwxrwx 1 root root 13179904 2008-10-07 13:33 /mnt/sda1/WINDOWS/system32/nvoglnt.dll
-rwxrwxrwx 1 root root   395776 2008-10-07 13:33 /mnt/sda1/WINDOWS/system32/nvshell.dll
-rwxrwxrwx 1 root root   164352 2008-10-07 13:33 /mnt/sda1/WINDOWS/system32/nvsvc64.exe
-rwxrwxrwx 1 root root    59392 2008-10-07 13:33 /mnt/sda1/WINDOWS/system32/nvtuicpl.cpl
-rwxrwxrwx 1 root root   501280 2008-10-07 13:33 /mnt/sda1/WINDOWS/system32/nvudisp.exe
-rwxrwxrwx 1 root root   222720 2006-08-04 01:48 /mnt/sda1/WINDOWS/system32/nvunrm.exe
-rwxrwxrwx 1 root root  4274688 2008-10-07 13:33 /mnt/sda1/WINDOWS/system32/nvvitvs.dll
-rwxrwxrwx 1 root root    80384 2008-10-07 13:33 /mnt/sda1/WINDOWS/system32/nvwddi64.dll
-rwxrwxrwx 1 root root  1802240 2008-10-07 13:33 /mnt/sda1/WINDOWS/system32/nvwdmcpl.dll
-rwxrwxrwx 1 root root  1010176 2008-10-07 13:33 /mnt/sda1/WINDOWS/system32/nvwimg64.dll
-rwxrwxrwx 1 root root  3226112 2008-10-07 13:33 /mnt/sda1/WINDOWS/system32/nvwss.dll
-rwxrwxrwx 2 root root      749 2008-10-19 23:32 /mnt/sda1/WINDOWS/system32/nwc.cpl.manifest
-rwxrwxrwx 1 root root  1684992 2008-10-07 13:33 /mnt/sda1/WINDOWS/system32/nwiz.exe
-rwxrwxrwx 1 root root   191488 2007-02-16 23:41 /mnt/sda1/WINDOWS/system32/nwprovau.dll

/mnt/sda1/WINDOWS/system32/npp:
total 72
-rwxrwxrwx 1 root root 50176 2007-02-16 23:39 ndisnpp.dll
-rwxrwxrwx 1 root root 19456 2005-03-25 06:00 nppagent.exe

---

### Post by caljohnsmith on 2008-12-18
OK, so you aren't actually missing your "ntoskrnl.exe" file as indicated by that earlier error. Also please post:
```
cat -A /mnt/sda1/boot.ini
```

---

### Post by Mouser58907 on 2008-12-18
Bad news, maybe good, I got my admin pw to work, turns out I did use a different one. But then I managed to fixboot and fixmbr, now I don't get grub loading and I get NTLDR missing again!

---

### Post by caljohnsmith on 2008-12-18
I see I should have warned you not to follow that advice, because as you've found out the hard way, you replaced Grub with a Windows MBR by running that fixmbr command. How about doing:
```
sudo grub
grub> root (hd1,4)
grub> setup (hd1)
grub> quit
```

---

### Post by Mouser58907 on 2008-12-18
Man, you're a life saver.

[Boot Loader]^M$
timeout=30^M$
Default=multi(0)disk(0)rdisk(0)partition(1)\Windows^M$
[Operating Systems]^M$
multi(0)disk(0)rdisk(0)partition(1)\Windows="Windows XP" /fastdetect^M$
^M$

Also is there a shortcut to open terminal? I'm not a clicking kinda guy.

---

### Post by logos34 on 2008-12-18
> **Mouser58907 said:**
> Man, you're a life saver.

[Boot Loader]^M$
timeout=30^M$
Default=multi(0)disk(0)rdisk(0)partition(1)\Windows^M$
[Operating Systems]^M$
multi(0)disk(0)rdisk(0)partition(1)\Windows="Windows XP" /fastdetect^M$
^M$

Also is there a shortcut to open terminal? I'm not a clicking kinda guy.

If that's what boot.ini looks like after you edited it using gedit (or is it a paste error?), it wouldn't surprise me if that was the problem. It can make a mess of the formatting, you have to be real careful.

Try cleaning it up following caljohnsmith's post #8, but instead use **nano** cli editor:

> sudo nano /mnt/boot.ini

Backspace to take out any extraneous characters.  In fact, do that even if the lines appear ok (you know, backspace/drag lines up one, then hit enter to push it back down--then you know it's clear).

just a suggestion--problem might be something else

---

### Post by Mouser58907 on 2008-12-18
Ok logos, I did that, even backspaced/enter, still got this as a result.

craig@craig-desktop:~$ cat -A /mnt/sda1/boot.ini
[Boot Loader]^M$
timeout=30^M$
Default=multi(0)disk(0)rdisk(0)partition(1)\Windows^M$
[Operating Systems]^M$
multi(0)disk(0)rdisk(0)partition(1)\Windows="Windows XP" /fastdetect^M$
^M$

---

### Post by caljohnsmith on 2008-12-18
Wait--please don't edit the boot.ini. Logos34, I had him show the contents of boot.ini by doing "cat -A", which shows the line breaks. I did that on purpose to make sure the boot.ini file has DOS style line endings (carriage return + line feed), and not a Unix style line endings (line feed). That's important because if you aren't careful when editing boot.ini in Linux, you can lose the DOS style line endings, and boot.ini will look like one long line to Windows. Mouser58907, your boot.ini is fine the way it is. :)

How about booting your Windows Install CD, Mouser58907, and run:
```
chkdsk /r
```
And run that as many times as it takes until it reports no errors. I don't think that will solve your Windows booting problem, but it is one last thing to try. Also, can you set your BIOS to boot the Windows drive on start up to see whether you get the same error? You are currently still trying to boot Windows from the Grub menu, true?

---

### Post by logos34 on 2008-12-18
> **caljohnsmith said:**
> Wait--please don't edit the boot.ini. Logos34, I had him show the contents of boot.ini by doing "cat -A", which shows the line breaks.

oops...sorry about that.

---

### Post by Mouser58907 on 2008-12-19
So I ran one and a half chkdsk /r* 's before my roommate accidentally unplugged my computer. Still get the same error.

Yes I am still booting from grub, but I don't know how to not use it. Even if I unplug my 2nd hard drive it still loads grub.

*edit- I have a 7:30 am cst final exam tomorrow and then going back home from college so I wont be on for almost a day.

---

### Post by caljohnsmith on 2008-12-19
Did you run the "lilo" command from post #6? That should have restored a Windows type MBR to your sda drive so you can boot Windows directly even when your 2nd Ubuntu HDD is disconnected.

---

### Post by Mouser58907 on 2008-12-19
okay, I unplugged the Ubuntu hdd, and it gave me the same missing or corrupted file error as before, but now when I re-plug it in Grub doesn't load back up so I'm running of the CD again.

also ran chkdsk /r with no errors!

---

### Post by caljohnsmith on 2008-12-19
So what exactly happens when you try to boot the Ubuntu drive? Do you get a Grub error or do you at least get the Grub menu? And about your Windows drive, I don't know of any more hacks that might solve that missing/corrupt "<WindowsRoot>\system32\ntoskrnl.exe" error; to the best of my knowledge your boot.ini is configured just fine, and also you aren't actually missing that ntoskrnl.exe file in the system32 folder. The only other cause of that error according to Microsoft is "General hardware failure:"

[http://support.microsoft.com/kb/314477](http://support.microsoft.com/kb/314477)

The fact that you can't boot your Ubuntu drive now would also support the idea that you may have a hardware problem at this point. I think if I were in your shoes, I would boot your Windows CD, choose the "install Windows" option, and after that when the CD detects your current Windows installation, it should give you an option to do a "Windows Repair". I think doing the "Windows Repair" is about your only last option, but that won't fix your problem if you truly have a hardware issue. Let us know how it goes.

---

### Post by Mouser58907 on 2008-12-19
Grub menu never comes up, still tries to boot straight to windows. I'm backing everything up now and I'll try the Windows Repair. If that doesn't work I will just reformat my whole drive.

---

### Post by Mouser58907 on 2008-12-20
Well this sucks. The hard drive is done. Now I want to re-install XP64 and ubuntu on my 1TB but its where I backed up everything too. I plugged in my external and can't seem to mount it. Any last tips??? You have been so helpful so far.

---

### Post by caljohnsmith on 2008-12-20
> **Mouser58907 said:**
> Well this sucks. The hard drive is done. Now I want to re-install XP64 and ubuntu on my 1TB but its where I backed up everything too. I plugged in my external and can't seem to mount it. Any last tips??? You have been so helpful so far.
At least your HDD failure explains your Windows problems, but sorry to hear that was the cause. How about booting your Live CD and please post:
```
sudo fdisk -lu
```
And we can work from there.

---

### Post by Mouser58907 on 2008-12-20
***Its the 500gb at the bottom.

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcad0cad0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   490207409   245103673+   7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe4e2e5a6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63  1741670909   870835423+   7  HPFS/NTFS
/dev/sdb2      1741670910  1953520064   105924577+   5  Extended
/dev/sdb5      1741670973  1944812834   101570931   83  Linux
/dev/sdb6      1944812898  1953520064     4353583+  82  Linux swap / Solaris

Disk /dev/sdg: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x581cd74d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1              63   976768064   488384001    7  HPFS/NTFS

---

### Post by caljohnsmith on 2008-12-20
OK, how about trying:
```
sudo mkdir /media/sdg1
sudo mount /dev/sdg1 /media/sdg1
```
If that doesn't return any errors, then do:
```
nautilus /media/sdg1 &
```
And if all goes well, you should be able to read/write to your sdg1 partition (mounted on /media/sdg1). Let me know how that goes.

---

### Post by Mouser58907 on 2008-12-20
I ran the first two and it returned an error with two options saying it hadn't been shutdown properly so I took it to a windows PC and safely removed it. Now its working fine! I'll be starting to back it up and reformatting now. I still plan on installing leaving ubuntu on here though so I may be back afterwords if I can't get grub to load. Which I most likely won't be able to.

Thanks a ton CalJohnSmith

---

### Post by Mouser58907 on 2008-12-21
Well I got everything working, didn't lose much data. Monday I will be installing beryl if the wiki page is back up. 

I'd really like to thank everyone that helped obviously john smith.

---

### Post by caljohnsmith on 2008-12-21
I'm really glad to hear you have Windows working again and didn't lose much data. Cheers and hope you don't run into any more major problems with Windows or Ubuntu. :)

---

