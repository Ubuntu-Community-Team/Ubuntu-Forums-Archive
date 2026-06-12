---
title: "Errors abound"
date: 2009-05-06
forum: Installation &amp; Upgrades
---

### Post by ooolongT on 2009-05-06
A couple of weeks ago, I was using the Windows on a dual boot machine. I have two hard drives.  The bigger one is for my Windows XP install, and the smaller one is for Ubuntu.  I had finished working in Windows and shut down the computer- or so I thought.  The next morning I came into my study only to find that during shutdown, the computer had frozen and was hanging there. "Stupid Windows" I thought.  So I just powered it down manually, and restarted the computer, and that is when the problems started. Before GRUB came up I got Error 15.

Here is what I get when I run fdisk -l
```

ubuntu@ubuntu:~$ fdisk -l

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13f84d83

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14592   117210208+   7  HPFS/NTFS

Disk /dev/hdb: 17.0 GB, 17016717312 bytes
255 heads, 63 sectors/track, 2068 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb59db59d

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1976    15872188+  83  Linux
/dev/hdb2            1977        2068      738990    5  Extended
/dev/hdb5            1977        2068      738958+  82  Linux swap / Solaris

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x36ace502

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14593   117218241    7  HPFS/NTFS


```

It is only showing one hard disk, and not the one that Ubuntu is on. 

So then I downloaded and ran boot_info_script032.sh and got this:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/hda and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/hdb
 => No boot loader is installed in the MBR of /dev/hdc
 => Windows is installed in the MBR of /dev/sda

hda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /ntdetect.com /NTBOOTDD.SYS

hdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 7.10
    Boot files/dirs:   /etc/fstab

hdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

hdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: hda ___________________ _____________________________________________________

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x13f84d83

Partition  Boot         Start           End          Size  Id System

/dev/hda1    *             63   234,420,479   234,420,417   7 HPFS/NTFS


Drive: hdb ___________________ _____________________________________________________

Disk /dev/hdb: 17.0 GB, 17016717312 bytes
255 heads, 63 sectors/track, 2068 cylinders, total 33235776 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb59db59d

Partition  Boot         Start           End          Size  Id System

/dev/hdb1    *             63    31,744,439    31,744,377  83 Linux
/dev/hdb2          31,744,440    33,222,419     1,477,980   5 Extended
/dev/hdb5          31,744,503    33,222,419     1,477,917  82 Linux swap / Solaris


Drive: hdc ___________________ _____________________________________________________
Note: sector size is 2048 (not 512)

Disk /dev/hdc: 729 MB, 729608192 bytes
255 heads, 63 sectors/track, 22 cylinders, total 356254 sectors
Units = sectors of 1 * 2048 = 2048 bytes

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found


Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x36ace502

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   234,436,544   234,436,482   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/hda1: UUID="B458C5A458C565A8" LABEL="Local Disk" TYPE="ntfs" 
/dev/hdb1: UUID="f825681e-335f-4724-95a3-50947642f5b9" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hdb5: TYPE="swap" UUID="64e70d65-513d-420f-9671-c95758795571" 
/dev/sda1: UUID="523469C53469AD23" LABEL="Misfortune" TYPE="ntfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
/dev/sda1 on /media/Misfortune type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/hdb1 on /media/disk type ext3 (rw,nosuid,nodev)
/dev/hda1 on /media/Local Disk type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)


================================ hda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /noexecute=optin


=============================== hdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=f825681e-335f-4724-95a3-50947642f5b9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=64e70d65-513d-420f-9671-c95758795571 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

=================== hdb1: Location of files loaded by Grub: ===================


   5.0GB: boot/initrd.img-2.6.22-14-generic.bak
   5.0GB: boot/vmlinuz-2.6.22-14-generic
   5.0GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

hdd 
```

Ah!  There is my Ubuntu drive!

So then I tried to follow the steps described at the bottom of the first post in this thread: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) And I did fairly well with that, but when I got to the part where it says


```
grub> find /boot/grub/stage1 
```

I get:
```

Error 15: File not found
```

What is going on here?  Any suggestions?

---

### Post by sahabcse on 2009-05-06
Hi Follow below url for fixing the grub

[http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html](http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html)

---

### Post by ooolongT on 2009-05-06
Sahabcse, thank you for the link.  Those are some of the same instructions that I followed before. My problem is that I can get no further than this:

```

grub> find /grub/stage1

Error 15: File not found

grub> find /grub/boot/stage1

Error 15: File not found

```

I am not sure how to create/move the proper file into that directory.

---

### Post by caljohnsmith on 2009-05-06
The Boot Info Script was not able to find Grub's boot files in your hdb1 Ubuntu 7.10 partition. How about posting the output of the following so we can see what you have in your Ubuntu boot directory:
```
sudo mount /dev/hdb1 /mnt && ls -lR /mnt/boot
```

John

---

### Post by ooolongT on 2009-05-06
Here is what I got:

```

ubuntu@ubuntu:~$ sudo mount /dev/hdb1 /mnt && ls -lR /mnt/boot
/mnt/boot:
total 10120
-rw-r--r-- 1 root root  424317 2007-10-15 01:39 abi-2.6.22-14-generic
-rw-r--r-- 1 root root   75311 2007-10-15 01:39 config-2.6.22-14-generic
-rw-r--r-- 1 root root 7124250 2007-10-15 23:26 initrd.img-2.6.22-14-generic.bak
-rw-r--r-- 1 root root  103204 2007-09-28 10:06 memtest86+.bin
-rw-r--r-- 1 root root  823535 2007-10-15 01:39 System.map-2.6.22-14-generic
-rw-r--r-- 1 root root 1764280 2007-10-15 01:39 vmlinuz-2.6.22-14-generic

```

---

### Post by caljohnsmith on 2009-05-06
Well that certainly explains your Grub error 15 then--your /boot/grub directory no longer exists. Or did you have a boot partition somewhere that had Grub in it? It doesn't look like it, so do you have any idea how you might have unintentionally deleted the /boot/grub directory in your Ubuntu 7.10 partition? In other words, having to do a hard shutdown after being booted into Windows would not have caused your /boot/grub directory to disappear, so I'm wondering how you might have lost your Grub directory.

But anyway, to reinstall Grub, how about doing the following from your Live CD:
```
sudo mount /dev/hdb1 /mnt
sudo grub-install --root-directory=/mnt --recheck /dev/hda
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo chroot /mnt /bin/bash
update-grub      [COLOR="Blue"][note: say "y" when it asks if you want to create a new menu.lst][/COLOR]
cat /boot/grub/menu.lst
exit
```
And please post the output of all the above commands; we can work from there.

John

---

### Post by ooolongT on 2009-05-06
Ok, it looks like that worked.  Here is everything I got:

```
 ubuntu@ubuntu:~$ sudo mount /dev/hdb1 /mnt
mount: /dev/hdb1 already mounted or /mnt busy
mount: according to mtab, /dev/hdb1 is already mounted on /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt --recheck /dev/hda
Probing devices to guess BIOS drives. This may take a long time.
Due to a bug in xfs_freeze, the following command might produce a segmentation
fault when /mnt/boot/grub is not in an XFS filesystem. This error is harmless and
can be ignored.
xfs_freeze: specified file ["/mnt/boot/grub"] is not on an XFS filesystem
Installation finished. No error reported.
This is the contents of the device map /mnt/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)   /dev/fd0
(hd0)   /dev/hda
(hd1)   /dev/hdb
(hd2)   /dev/sda
ubuntu@ubuntu:~$ do mount --bind /dev /mnt/dev
bash: syntax error near unexpected token `do'
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc

ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo chroot /mnt /bin/bash
root@ubuntu:/# update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... 

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) y
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.22-14-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

root@ubuntu:/# cat /boot/grub/menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=f825681e-335f-4724-95a3-50947642f5b9 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=f825681e-335f-4724-95a3-50947642f5b9 ro quiet splash
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=f825681e-335f-4724-95a3-50947642f5b9 ro single

title           Ubuntu 7.10, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

To answer your question, no, I do not know what could have caused the directory to disappear.  I think, however that that drive was filling up so  that might have something to do with it.

---

### Post by caljohnsmith on 2009-05-06
OK, while you still have hdb1 mounted on /mnt, how about doing the following:
```
gksudo gedit /mnt/boot/grub/menu.lst
```
And add the following entry at the bottom of the menu.lst file:
```
title Windows XP
rootnoverify (hd0,0)
chainloader +1

```
Also, comment-out the "hiddenmenu" line near the top of the menu.lst:
```
#hiddenmenu
```
Save the menu.lst file and quit gedit, and lastly please post:
```
df -h
```
After that, reboot, and let me know if you get the Grub menu OK on start up, and if so, if you can boot your OSes. We can work from there.

John

---

### Post by ooolongT on 2009-05-06
Here are the results:

```
ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 474M   16M  459M   4% /lib/modules/2.6.22-14-generic/volatile
tmpfs                 474M   16M  459M   4% /lib/modules/2.6.22-14-generic/volatile
varrun                474M   92K  474M   1% /var/run
varlock               474M     0  474M   0% /var/lock
udev                  474M   92K  474M   1% /dev
devshm                474M     0  474M   0% /dev/shm
tmpfs                 474M   12K  474M   1% /tmp
/dev/sda1             112G   76G   36G  68% /media/Misfortune
/dev/hdb1              15G  1.7G   13G  12% /mnt

```

(Misfortune is a USB drive)

---

### Post by ooolongT on 2009-05-06
I restarted the computer and where it usually says "Error 15" it now says (retyped):

Boot from CD:
Boot from CD:
Error Loading Operating System 

and then it is frozen again. 

I think it might have something to do with the windows boot because I replaced the ntldr and ntdetect.com files.  It may be that I need to edit Windows boot.ini file?  Anyway, shouldn't I still get the Grub loader so I can boot into Ubuntu?

---

### Post by unutbu on 2009-05-06
caljohnsmith doesn't appear to be online right now, so I will take a stab at this one.

According to boot_info_script,
GRUB has been install on your 120 GB drive, /dev/hda.
The Windows bootloader is installed on the 17 GB drive, /dev/hdb.
(Kind of ironic, since hda holds Windows and hdb holds Ubuntu. This is not a problem, by the way, as long as we get GRUB on hda to control the boot process, and not the Windows bootloader on hdb.)
The Windows bootloader is also installed on the 120 GB USB drive, /dev/sda.

I don't recognize the boot error you are getting, but it suggests that GRUB is not handling the boot process. So the BIOS is probably not booting hda. Maybe it is booting hdb or sda.

Try booting again and press whatever magic key is required to enter your BIOS menu. (possibly some function key like F2 or F10?) Try changing the boot order so that the 120 GB drive, hda comes before hdb and sda.

If this does not work, please run and post the output of boot_info_script again, so we can see the current state of your boot setup.

---

### Post by caljohnsmith on 2009-05-06
I agree with Ubutbu, if you are getting an "Error Loading Operating System" on start up, your hda drive does not seem to be set to boot first on start up. First see if you can change your BIOS boot order so that your hda drive is first, and let us know if you get the Grub menu or at least a Grub error. And actually if you can change your BIOS boot order, it might be worth it to just install Grub to the MBR of the Ubuntu hdb drive, so that way your drives will be independent of each other as far as booting is concerned. My directions had you reinstall Grub to the MBR of the hda drive because I noticed from the Boot Info Script that hda is where Grub was installed before, so I thought I would just leave it as is. Anyway, let us know what happens if you set the hda drive first in your BIOS boot order, and we can work from there.

John

---

### Post by ooolongT on 2009-05-07
First of all, I can not thank you guys enough for all the help you have provided me.  This is awesome!

So, I read what unutbu wrote, and if I understand correctly, GRUB is on the Windows disk (120 GB drive), and the Windows boot loader is on the Ubuntu disk (17 GB drive) as well as the 120 GB drive. Do I need two Windows boot loaders?  If not, I would like to remove one, this seems like its jsut more things to break.  

I followed unutbu's instructions and made sure that the 120 GB drive was both the second boot device and the priority hard drive and... I got the GRUB loader!  Woo hoo!!  So then I tried to go into Ubuntu and got an error. Booooo... 

I re-typed this:
```

[24.448907] Kernel panic - not syncing: VFS: unable to mount root fs on unknown-block (0,0)

```

and it hangs there and needs to be manually restarted.


So then I booted into safe mode and got this (again typed my me):
```
[24.771342] VFS: can not open root device "UUID=f825681e-335f-4724-95a3-50947642f5b9" or unknown-block (0,0)
[24.771408] Please append a correct "root=" boot option; here are the available partitions: [COLOR="RoyalBlue"] *nothing else on this line*[/COLOR]
[24.771473] Kernel panic - not syncing: VFS: unable to mount root fs on unknown-block (0,0)
```



John, 

For some reason I am having trouble running the boot info script:
```
ubuntu@ubuntu:~/Desktop$ sudo boot_info_script032.sh
sudo: boot_info_script032.sh: command not foun
```

I just downloaded a new copy of it too, checked the permissions, and even did:
```
sudo ./boot*.sh
```

to no avail.  Not sure why it is not working.

---

### Post by unutbu on 2009-05-07
ooolongT, I believe the problem is due to GRUB not being able to find the proper initrd file. Notice in the output of boot_info_script that you have 
```

   5.0GB: boot/initrd.img-2.6.22-14-generic.bak

```
but no
```

   5.0GB: boot/initrd.img-2.6.22-14-generic
```

Fortunately, from post #5 it appears the initrd.img-2.6.22-14-generic.bak is not empty:
```

ubuntu@ubuntu:~$ sudo mount /dev/hdb1 /mnt && ls -lR /mnt/boot
/mnt/boot:
total 10120
-rw-r--r-- 1 root root 7124250 2007-10-15 23:26 initrd.img-2.6.22-14-generic.bak
```


So how about try this: 

Boot from the LiveCD.
Open a terminal (Applications>Accessories>Terminal), and type
```

sudo mount /dev/hdb1 /mnt
cd /mnt/boot/
sudo cp initrd.img-2.6.22-14-generic{.bak,}

```
Just in case this doesn't solve the problem, it would still be helpful to see the output of boot_info_script. Perhaps it is located in ~/Desktop? In that case, try
```

cd ~/Desktop
sudo bash ./boot_info_script*.sh
```

---

### Post by ooolongT on 2009-05-07
Ah, that did it.  Here is the info from the boot info script:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/hda and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/hdb
 => No boot loader is installed in the MBR of /dev/hdc
 => No boot loader is installed in the MBR of /dev/hdd
 => Windows is installed in the MBR of /dev/sda

hda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /ntdetect.com /NTBOOTDD.SYS

hdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 7.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

hdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

hdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: hda ___________________ _____________________________________________________

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x13f84d83

Partition  Boot         Start           End          Size  Id System

/dev/hda1    *             63   234,420,479   234,420,417   7 HPFS/NTFS


Drive: hdb ___________________ _____________________________________________________

Disk /dev/hdb: 17.0 GB, 17016717312 bytes
255 heads, 63 sectors/track, 2068 cylinders, total 33235776 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb59db59d

Partition  Boot         Start           End          Size  Id System

/dev/hdb1    *             63    31,744,439    31,744,377  83 Linux
/dev/hdb2          31,744,440    33,222,419     1,477,980   5 Extended
/dev/hdb5          31,744,503    33,222,419     1,477,917  82 Linux swap / Solaris


Drive: hdc ___________________ _____________________________________________________
Note: sector size is 2048 (not 512)

Disk /dev/hdc: 729 MB, 729608192 bytes
255 heads, 63 sectors/track, 22 cylinders, total 356254 sectors
Units = sectors of 1 * 2048 = 2048 bytes

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found


Drive: hdd ___________________ _____________________________________________________
Note: sector size is 2048 (not 512)

Disk /dev/hdd: 551 MB, 551448576 bytes
255 heads, 63 sectors/track, 16 cylinders, total 269262 sectors
Units = sectors of 1 * 2048 = 2048 bytes

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found


Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x36ace502

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   234,436,544   234,436,482   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/hda1: UUID="B458C5A458C565A8" LABEL="Local Disk" TYPE="ntfs" 
/dev/hdb1: UUID="f825681e-335f-4724-95a3-50947642f5b9" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hdb5: TYPE="swap" UUID="64e70d65-513d-420f-9671-c95758795571" 
/dev/sda1: UUID="523469C53469AD23" LABEL="Misfortune" TYPE="ntfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
/dev/sda1 on /media/Misfortune type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/hdd on /media/XP2_PER_ENG type iso9660 (ro,nosuid,nodev,uid=999,utf8)
/dev/hdb1 on /mnt type ext3 (rw)


================================ hda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /noexecute=optin


=========================== hdb1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=f825681e-335f-4724-95a3-50947642f5b9 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=f825681e-335f-4724-95a3-50947642f5b9 ro quiet splash
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=f825681e-335f-4724-95a3-50947642f5b9 ro single

title		Ubuntu 7.10, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Windows XP
rootnoverify (hd0,0)
chainloader +1


=============================== hdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=f825681e-335f-4724-95a3-50947642f5b9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=64e70d65-513d-420f-9671-c95758795571 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

=================== hdb1: Location of files loaded by Grub: ===================


   5.0GB: boot/grub/menu.lst
   5.0GB: boot/grub/stage2
   4.9GB: boot/initrd.img-2.6.22-14-generic
   5.0GB: boot/initrd.img-2.6.22-14-generic.bak
   5.0GB: boot/vmlinuz-2.6.22-14-generic
   4.9GB: initrd.img
   5.0GB: vmlinuz
```

I followed your instructions, and am going to reboot now and see if it is fixed, back in a few minutes.

---

### Post by ooolongT on 2009-05-07
Sadly, I got the same error when I restarted:

```
[24.448XXX] Kernel panic - not syncing: VFS: unable to mount root fs on unknown-block (0,0)
```

(the X's are there because I didn't write down the number this time)

---

### Post by caljohnsmith on 2009-05-07
> **ooolongT said:**
> ```

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=f825681e-335f-4724-95a3-50947642f5b9 ro quiet splash
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=f825681e-335f-4724-95a3-50947642f5b9 ro single

title		Ubuntu 7.10, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

```

It looks like Unutbu and I overlooked the fact that your current menu.lst doesn't have any "initrd" lines for the Ubuntu entries; that makes sense since you ran "grub-install" before you copied the backup initrd image file back to its original name as per Unutbu's instructions. So to fix your menu.lst, how about doing the following from the Live CD:
```
sudo mount /dev/hdb1 /mnt
gksudu gedit /mnt/boot/grub/menu.lst
```
Then add the following initrd lines to your Ubuntu entries:
```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=f825681e-335f-4724-95a3-50947642f5b9 ro quiet splash
[COLOR="Blue"]initrd          /boot/initrd.img-2.6.22-14-generic[/COLOR]
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=f825681e-335f-4724-95a3-50947642f5b9 ro single
[COLOR="Blue"]initrd          /boot/initrd.img-2.6.22-14-generic[/COLOR]
```
Reboot, and hopefully you'll be able to boot into Ubuntu this time; if not, let us know exactly what happens.

John

---

### Post by ooolongT on 2009-05-07
So close!!

I got to where it says "Starting up..." and goes to another screen and starts checking things - this is much further than I have gotten before. Then a blue screen came up that said:

```
Server Authorization Directory  (daemon/ServerAuthDir) is set to /var/libGDM but this does not exist.  Please correct the GDM configuration and restart GDM.

```

I hit ok, and then it took me to a screen that looked like: 
```
Starting up...
Loading please wait...
usplash: No usable theme found for 640x180
screen init failed
Ubuntu 7.10 terranova tty1
terranova login:[COLOR="Blue"]ubuntu[/COLOR]
password:[COLOR="Blue"]passwd[/COLOR]
```

I also tried my login and password for this machine and that did not work either.  Because I was not able ot login, I was stuck, so I restarted.

---

### Post by caljohnsmith on 2009-05-07
It seems to me like your Ubuntu installation has a lot more that needs to be fixed than just the missing Grub directory and boot files that we all ready reinstalled. According to the Boot Info Script, your Ubuntu installation is version 7.10; is there a particular reason why you have stayed with 7.10 all this time and decided not to upgrade to the latest 9.04 release? I think now would be a good time to consider saving all your important documents in Ubuntu, and then installing the latest 9.04 release. Since there seems to be a lot more wrong with your Ubuntu install than just a simple problem with Grub, I don't think it is worth trying to fix at this point, but it is up to you if you want to keep trying. If Unutbu wants to continue trying to help you troubleshoot the problems, that's great, I will respectfully step back and let him continue. But otherwise I think it is time to install a newer version of Ubuntu. 

John

---

### Post by ooolongT on 2009-05-07
John, 

I appreciate all of the help you and Unutbu have gien me.  This is one of the strange things about the info we have been getting.  My latest install was not 7.10, it was 8.04.  I am using a 7.10 live disk right now however, and that is probably what I upgraded from.  Not sure why everything is saying 7.10 though.  

There are two main reasons why I have not upgraded yet: 

1. I have had to do some fairly extensive reworking of the system to make it work with my computer, and I am afraid that my note taking was not great while I did it.  Therefore, I am not looking forward to figuring it all out again.

2. I usually like to wait a while before after a release comes out so that when run into the inevitable problems/questions, someone has already asked that question and I can try working through it myself for a while before I ask for help.  

However, I will do what I can to back up the important files, and try a fresh install.  I think I will give Kubuntu a try this time, and maybe I will not have to do so much reconfiguring [-o<

A last question though: I would love to avoid a problem like this in the future, do you have any idea what happened here?  Unutbu?

---

### Post by ooolongT on 2009-05-07
I also can't seem to get into my old Desktop Directory?  Shouldn't

```
sudo cd /media/disk/home

```
get me in there?  Sorry if this sounds clueless. When I use the File Browser, it looks like the home folder on that drive is completely empty.

---

### Post by unutbu on 2009-05-07
Edit: It depends on where hdb1 is mounted. To find that out, type

```
mount
```
or```

df /dev/hdb1
```
The commands we've been posting, have been mounting hdb1 at /mnt,
so perhaps try ```
cd /mnt/home
```

(Also, sudo never works with "cd" because cd is a shell command and not an executable).
------------------------------------------------------------
I think caljohnsmith is right -- you would probably be best off using the LiveCD to mount hdb1 and copy all your personal data, then reinstall. 

I am far from sure that your system is fully recoverable. 
Pieces are missing -- /boot/grub/menu.lst, the initrd file, and now /var/lib/gdm.
Whatever caused this is a mystery to me.

Nevertheless, here's one more thing you could try:

I googled "daemon/ServerAuthDir) is set to /var/libGDM but this does not exist"
and came up with this: [http://ubuntuforums.org/showthread.php?p=7152989](http://ubuntuforums.org/showthread.php?p=7152989).

So maybe we can get to a GDM login window by doing this:

Boot from the LiveCD.
```

sudo mount /dev/hdb1 /mnt
sudo mkdir /mnt/var/lib/gdm
sudo chmod 01770 /mnt/var/lib/gdm
```

Then reboot.

---

### Post by ooolongT on 2009-05-08
Unutbu, I followed your instructions and here is what I got:

```
ubuntu@ubuntu:~$  sudo mount /dev/hdb1 /mnt
ubuntu@ubuntu:~$ sudo mkdir /mnt/var/lib/gdm
mkdir: cannot create directory `/mnt/var/lib/gdm': No such file or directory

```

Which I thought was weird.  So then I used the file browser and went to that location on the disk, and the /var/ directory only has four folders in it.  

```
ubuntu@ubuntu:/mnt/var$ ls
crash  lock  log  run

```

So I made both directories.  

I am wondering what else may be missing from there though.  Should I copy the files that are on the live CD filesystem into those directories? 

I am going to restart now.  Wish me luck!

---

### Post by ooolongT on 2009-05-08
As Lewis Carroll would say, curiouser and curiouser.  I am now at the Ubuntu login screen but my name and password do not work.  However, in the bottom righthand corner it says terranova // (date and time).  That is weird, no?

---

### Post by unutbu on 2009-05-08
ooolongT, you are missing a lot of files. /mnt/var should have had all these directories

```
  drwxr-xr-x  2 root root  4096 2009-05-05 08:58 backups
  drwxr-xr-x 19 root root  4096 2009-04-10 21:16 cache
  drwxr-xr-x  2 root root  4096 2008-10-24 01:57 crash
  drwxr-xr-x  2 root root  4096 2009-04-10 07:45 games
  drwxr-xr-x 62 root root  4096 2009-04-22 08:18 lib
  drwxrwsr-x  2 root staff 4096 2008-10-20 08:27 local
  drwxrwxrwt  4 root root   100 2009-05-08 13:24 lock
  drwxr-xr-x 16 root root  4096 2009-05-08 13:24 log
  drwxrwsr-x  2 root mail  4096 2009-05-08 14:10 mail
  drwxr-xr-x  2 root root  4096 2009-04-10 07:21 opt
  drwxr-xr-x 18 root root   700 2009-05-08 13:24 run
  drwxr-xr-x  7 root root  4096 2009-04-13 18:29 spool
  drwxrwxrwt  2 root root  4096 2009-05-08 13:25 tmp
  drwxr-xr-x  2 root root  4096 2009-04-10 16:43 www
```

/mnt/var/lib should have contained all these directories

```
  total used in directory 248 available 14167128
  drwxr-xr-x 62 root          root          4096 2009-04-22 08:18 .
  drwxr-xr-x 16 root          root          4096 2009-04-10 16:43 ..
  drwxr-xr-x  2 root          root          4096 2009-04-10 08:56 acpi-support
  drwxr-xr-x  2 root          root          4096 2009-04-10 09:22 alsa
  drwxr-xr-x  2 root          root          4096 2009-04-21 14:50 apparmor
  drwxr-xr-x  6 root          root          4096 2009-05-07 12:48 apt
  drwxr-xr-x  2 root          root          4096 2008-09-02 08:50 aptitude
  drwxr-xr-x  3 root          root          4096 2009-05-08 07:44 apt-xapian-index
  drwxr-xr-x  2 root          root          4096 2009-04-10 07:34 aspell
  drwxr-xr-x  2 avahi-autoipd avahi-autoipd 4096 2009-04-10 07:41 avahi-autoipd
  drwxr-xr-x  2 root          root          4096 2009-04-10 16:34 belocs
  drwxr-xr-x  2 root          root          4096 2009-04-10 22:46 binfmts
  drwxr-xr-x  2 root          root          4096 2009-04-10 08:56 dbus
  drwxr-xr-x  9 root          root          4096 2009-04-20 21:27 defoma
  drwxr-xr-x  2 root          root          4096 2009-04-10 07:21 dhcp3
  drwxr-xr-x  4 root          root          4096 2009-04-10 07:47 dictionaries-common
  drwxr-xr-x  3 root          root          4096 2009-04-10 17:29 dkms
  drwxr-xr-x  5 root          root          4096 2009-04-10 07:34 doc-base
  drwxr-xr-x  7 root          root          4096 2009-05-04 11:49 dpkg
  drwxr-xr-x  2 root          root          4096 2009-04-10 09:54 emacsen-common
  drwxr-xr-x  3 root          root          4096 2009-04-10 09:54 emacs-snapshot
  drwxr-xr-x  2 root          root          4096 2009-05-08 13:24 exim4
  drwx------  2 fetchmail     nogroup       4096 2009-04-17 19:39 fetchmail
  drwxr-xr-x  2 root          root          4096 2009-04-10 21:09 flashplugin-nonfree
  drwxr-xr-x  4 root          root          4096 2009-04-10 07:32 gconf
  drwxrwx--T  3 root          gdm           4096 2009-05-08 13:24 gdm
  drwxr-xr-x  2 root          root          4096 2008-10-26 04:56 hal
  drwxr-xr-x  2 root          root          4096 2009-04-10 17:23 initramfs-tools
  drwxr-xr-x  2 root          root          4096 2008-10-14 09:02 initscripts
  drwxrwsr-x  2 libuuid       libuuid       4096 2009-04-10 07:21 libuuid
  drwxr-xr-x  3 root          root          4096 2009-04-10 07:34 libxml-sax-perl
  drwxr-xr-x  3 root          root          4096 2009-04-10 07:21 locales
  drwxr-xr-x  2 root          root          4096 2009-04-11 08:25 logrotate
  drwxr-xr-x  2 root          root          4096 2009-04-10 07:32 misc
  drwxr-xr-x  2 root          root          4096 2009-05-08 07:42 mlocate
  drwxr-xr-x  2 root          root          4096 2009-04-10 22:45 msttcorefonts
  drwxr-xr-x  2 mysql         mysql         4096 2009-05-08 13:24 mysql
  drwxr-xr-x  2 root          root          4096 2008-09-19 09:23 mysql-cluster
  drwxr-xr-x  2 root          root          4096 2008-10-20 23:17 NetworkManager
  drwxr-xr-x  2 root          root          4096 2009-04-22 08:19 os-prober
  drwxr-xr-x  2 root          root          4096 2009-04-10 16:33 pam
  drwx-wx-wt  2 root          root          4096 2009-05-08 09:39 php5
  drwxr-xr-x  2 root          root          4096 2009-04-10 16:46 phpmyadmin
  drwxrwx---  2 root          polkituser    4096 2009-04-10 07:42 PolicyKit
  drwxr-xr-x  2 polkituser    root          4096 2008-10-08 03:03 PolicyKit-public
  drwxr-xr-x  3 root          root          4096 2009-04-13 22:13 python-support
  drwxr-xr-x  2 root          root          4096 2008-10-10 10:12 samba
  drwxr-xr-x  2 root          root          4096 2009-04-10 07:32 sgml-base
  drwxr-xr-x  2 root          root          4096 2008-09-22 14:37 snmp
  drwxr-xr-x  2 root          root          4096 2008-10-21 14:13 synaptic
  drwxr-xr-x  5 root          root          4096 2009-04-10 14:59 tex-common
  drwxr-xr-x  5 root          root          4096 2009-04-10 15:00 texmf
  drwxr-xr-x  3 root          root          4096 2009-04-10 07:47 thunderbird
  drwxr-xr-x  3 root          root          4096 2009-04-17 23:47 ucf
  drwxr-xr-x  3 root          root          4096 2009-04-10 07:40 ufw
  drwxr-xr-x  2 root          root          4096 2008-10-24 18:02 update-manager
  drwxr-xr-x  3 root          root          4096 2009-04-10 07:46 update-notifier
  drwxr-xr-x  2 root          root          4096 2009-05-08 13:24 urandom
  drwxr-xr-x  3 root          root          4096 2009-04-10 07:21 vim
  drwxr-xr-x  2 root          root          4096 2009-04-10 07:28 x11
  drwxr-xr-x  2 root          root          4096 2009-05-08 13:24 xkb
  drwxr-xr-x  2 root          root          4096 2009-04-10 07:38 xml-core
```

Since your name and password do not work, you are probably missing files in /etc too.

Trying to restore all these directories manually would be very tough and slow. The fixes that you had to make to your system may be among the files that you are missing, so you would have to redo that anyway. 

Unfortunately, I'm pretty sure backing up and reinstalling is your best option at this point. :(

---

### Post by ooolongT on 2009-05-11
:shock: 8-[ It seems that my home directory is now empty.  Must have been among the files that were lost. 

```

ubuntu@ubuntu:~$ sudo mount /dev/hdb1 /mnt
ubuntu@ubuntu:~$ cd /mnt/
ubuntu@ubuntu:/mnt$ ls
bin   cdrom  etc   initrd      lib         media  opt   root  srv  tmp  var
boot  dev    home  initrd.img  lost+found  mnt    proc  sbin  sys  usr  vmlinuz
ubuntu@ubuntu:/mnt$ cd home
ubuntu@ubuntu:/mnt/home$ ls
ubuntu@ubuntu:/mnt/home$ 

```

I checked the lost+found too, nothing there either. 

So much for all my files.  

I will wait a while and see if anyone has any idea how to get back the things that were in my Home folder, and especially on my Desktop, but I am going to install Kubuntu EOD unless I hear otherwise. 

Once again, I REALLY appreciate all the help you guys!  Even if I lost my files, I have learned a ton in the process (not least about BACKING UP REGULARLY!!!) "...and knowing is half the battle."

---

