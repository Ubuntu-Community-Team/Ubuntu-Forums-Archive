---
title: "GRUB not installed after ubuntu 9.04 installation"
date: 2009-07-06
forum: Installation &amp; Upgrades
---

### Post by jjmedem on 2009-07-06
Hello everyone,

since some time I'm having problems installing Ubuntu as the third system on my PC after WinXP and WinVista. I have been able to install Ubuntu just fine, but GRUB doesn't get installed or doesn't load. I'm certain that I did set it to install GRUB (last screen before installation, Advanced). After this failing for the millionth time I've kind of had it and I want it working. I tried searching the forum and google, nothing yet worked for me. I tried opening the terminal in the live cd, opened the grub > command (sudo fdisk -l), then I used the command. Before that I found out that hd (1,5) is the hd / partition where my linux install is located (not the swap partition), then I think I used setup (hd1,5) and another command, or the setup command, I don't exactly remember for hd (0). 

Basic question here is: Can anyone tell me what I need to do to get GRUB in front of windows bootloader so that I can boot into any of my 3 OS's?

---

### Post by JC Cheloven on 2009-07-06
1.- From your post, one would say that you have other hard disk, that grub would name as (hd0). Is that right?

2.- To answer your question in a quick'n'dirty way: SuperGrub disk. But you could try a smarter thing: 

3.- The commands you issued seem to be "more or less" the right approach, but the output of the folowing commands would be helpful if you need more precise help:```
sudo fdisk -l
sudo blkid
cat /boot/grub/menu.lst
```

---

### Post by presence1960 on 2009-07-06
Let's get a better view of your setup and boot process. Download the Boot Info Script to your Desktop (from Live CD if you can't boot Ubuntu) get it here: [http://sourceforge.net/projects/bootinfoscript/files/](http://sourceforge.net/projects/bootinfoscript/files/) ver 0.32 is what you want

Then once on Desktop open a terminal and run this command: ```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on your desktop. Paste the contents of that file back here, once pasted here highlight all text pasted and click # on the toolbar to place CODE tags around the text.

This will give us all pertinent info about your setup and boot process, including if and where GRUB is installed. It will include all 3 commands JC gave you and more. This script is a great tool in solving boot problems.

---

### Post by bondmatt on 2009-07-06
There is a program called EasyBCD that can add entries in the Vista bootloader for XP and GRUB.

Cheers,
- Matt Bondy

---

### Post by presence1960 on 2009-07-06
Personally I don't like Easy BCD, GRUB is more versatile and very easy to configure. But I ask this, if the OP doesn't know if or where GRUB is located how is he going to configure Easy BCD?

---

### Post by jjmedem on 2009-07-07
> **JC Cheloven said:**
> 1.- From your post, one would say that you have other hard disk, that grub would name as (hd0). Is that right?

2.- To answer your question in a quick'n'dirty way: SuperGrub disk. But you could try a smarter thing: 

3.- The commands you issued seem to be "more or less" the right approach, but the output of the folowing commands would be helpful if you need more precise help:```
sudo fdisk -l
sudo blkid
cat /boot/grub/menu.lst
```

1. Weirdly, yes I think my third drive is registered as hd(0) even though it was installed the latest in my PC and has no OS on it. (I forgot the command to check so if anyone can give it I can make sure.)

2. I read a lot about that in various GRUB problem solutions, but that would mean burning another CD, and if that isn't necessary I'd rather avoid that.

3.

**sudo fdisk -l:**
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf19ad901

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       36484   293054464    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xad0964b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30401   244193253    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2           30401       54275   191763456    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sdb3           54275       60802    52429530    5  Extended
Partition 3 does not end on cylinder boundary.
/dev/sdb5           54275       54524     1999863   82  Linux swap / Solaris
/dev/sdb6           54524       60802    50429633   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe2e1efe3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60802   488384160+   7  HPFS/NTFS
```

**sudo blkid:**
```
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="30981D9F981D651E" LABEL="Data 2" TYPE="ntfs" 
/dev/sdb1: UUID="D4FCB497FCB474F8" LABEL="Windows XP" TYPE="ntfs" 
/dev/sdb2: UUID="DC400276400257A2" LABEL="Windows Vista" TYPE="ntfs" 
/dev/sdb5: TYPE="swap" UUID="4900d05d-9d71-4ebb-be9f-777a5a361279" 
/dev/sdb6: UUID="1790f58c-5f84-41c9-8143-c4dc3504ce92" TYPE="ext4" 
/dev/sdc1: UUID="3660E2F260E2B82F" LABEL="Data" TYPE="ntfs" 

```

**cat /boot/grub/menu.lst**
```
ubuntu@ubuntu:~$ cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory
```

-----------

> **presence1960 said:**
> Let's get a better view of your setup and boot process. Download the Boot Info Script to your Desktop (from Live CD if you can't boot Ubuntu) get it here: [http://sourceforge.net/projects/bootinfoscript/files/](http://sourceforge.net/projects/bootinfoscript/files/) ver 0.32 is what you want

Then once on Desktop open a terminal and run this command: ```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on your desktop. Paste the contents of that file back here, once pasted here highlight all text pasted and click # on the toolbar to place CODE tags around the text.

This will give us all pertinent info about your setup and boot process, including if and where GRUB is installed. It will include all 3 commands JC gave you and more. This script is a great tool in solving boot problems.

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf19ad901

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   586,110,975   586,108,928   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xad0964b2

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             34   488,386,539   488,386,506   7 HPFS/NTFS
/dev/sdb2         488,386,560   871,913,471   383,526,912   7 HPFS/NTFS
/dev/sdb3         871,913,680   976,772,739   104,859,060   5 Extended
/dev/sdb5         871,913,714   875,913,439     3,999,726  82 Linux swap / Solaris
/dev/sdb6         875,913,474   976,772,739   100,859,266  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe2e1efe3

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   976,768,383   976,768,321   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="30981D9F981D651E" LABEL="Data 2" TYPE="ntfs" 
/dev/sdb1: UUID="D4FCB497FCB474F8" LABEL="Windows XP" TYPE="ntfs" 
/dev/sdb2: UUID="DC400276400257A2" LABEL="Windows Vista" TYPE="ntfs" 
/dev/sdb5: TYPE="swap" UUID="4900d05d-9d71-4ebb-be9f-777a5a361279" 
/dev/sdb6: UUID="1790f58c-5f84-41c9-8143-c4dc3504ce92" TYPE="ext4" 
/dev/sdc1: UUID="3660E2F260E2B82F" LABEL="Data" TYPE="ntfs" 

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


================================ sdb1/boot.ini: ================================

;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /NOEXECUTE=OPTIN /FASTDETECT


=========================== sdb6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=1790f58c-5f84-41c9-8143-c4dc3504ce92 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=1790f58c-5f84-41c9-8143-c4dc3504ce92

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
uuid		1790f58c-5f84-41c9-8143-c4dc3504ce92
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=1790f58c-5f84-41c9-8143-c4dc3504ce92 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		1790f58c-5f84-41c9-8143-c4dc3504ce92
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=1790f58c-5f84-41c9-8143-c4dc3504ce92 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		1790f58c-5f84-41c9-8143-c4dc3504ce92
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista (loader)
rootnoverify	(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb6 during installation
UUID=1790f58c-5f84-41c9-8143-c4dc3504ce92 /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=4900d05d-9d71-4ebb-be9f-777a5a361279 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb6: Location of files loaded by Grub: ===================


 452.8GB: boot/grub/menu.lst
 450.4GB: boot/grub/stage2
 450.4GB: boot/initrd.img-2.6.28-11-generic
 450.5GB: boot/vmlinuz-2.6.28-11-generic
 450.4GB: initrd.img
 450.5GB: vmlinuz
```

So, GRUB seems to be installed but probably not on the right drive or something? Since it doesn't load it.

---

### Post by presence1960 on 2009-07-07
GRUB is installed on the MBR of drive sda. Go into your BIOS and make sure that sda is the first HDD in the order of HDD booting. Once sda is set to boot first your GRUB should load when you boot. While you are in there set the order of all drives like this sda>sdb>sdc.

When you boot your machine the BIOS determines what devices boot in what order. A typical setup is CD > HDD > USB or Removable (I omitted floppies). If you have more than one HDD there is another setting which determines the order of the HDD booting. Looking at your info I would say you have sdb or sdc set to boot first. Whatever drive boots first if there is a bootloader on the MBR that bootloader will take over. sdb & sdc have windows bootloader on it. sda has GRUB. Make sda first boot.

After doing this you may have to change your windows entry in menu.lst, but that is a quick fix.

---

### Post by jjmedem on 2009-07-07
> **presence1960 said:**
> GRUB is installed on the MBR of drive sda. Go into your BIOS and make sure that sda is the first HDD in the order of HDD booting. Once sda is set to boot first your GRUB should load when you boot. While you are in there set the order of all drives like this sda>sdb>sdc.

When you boot your machine the BIOS determines what devices boot in what order. A typical setup is CD > HDD > USB or Removable (I omitted floppies). If you have more than one HDD there is another setting which determines the order of the HDD booting. Looking at your info I would say you have sdb or sdc set to boot first. Whatever drive boots first if there is a bootloader on the MBR that bootloader will take over. sdb & sdc have windows bootloader on it. sda has GRUB. Make sda first boot.

After doing this you may have to change your windows entry in menu.lst, but that is a quick fix.

Sadly, I cannot choose to boot sdX anything in BIOS, what I did try now was change the priority of HDD boot in the BIOS from my one 500GB drive to the other but the PC cannot boot from that drive so I changed it back. Now ofcourse it loads the Vista bootloader again. (quite what I expected since Ubuntu is installed on the same drive as XP and Vista, ofcourse on another partition.) 

Also, the sda etc are partitions, not physical drives if you ask me, which means I can't choose to boot from any of the partition. Weird thing is, like a year ago or  a bit longer I have had Ubuntu 8.04 installed no problem this same way. I have tried using that cd before to install ubuntu but that gave me the same problems.

I don't know but since we now maybe "know" where GRUB is, can't EasyBCD add an entry for it? I have used that prog before to change windows boot properties

---

### Post by presence1960 on 2009-07-07
change the boot order to the 300 GB drive that is where GRUB is. If that doesn't work you will have to restore GRUB to the Vista disk's MBR.
> Also, the sda etc are partitions, not physical drives if you ask me, which means I can't choose to boot from any of the partition. Weird thing is, like a year ago or a bit longer I have had Ubuntu 8.04 installed no problem this same way.

sda, sdb and sdc are not partitions. you have 3 separate HDDs in your rig. sda is 300 GB, sdb and sdc are 500 GB. They are separate hard disks (HDD)

> Sadly, I cannot choose to boot sdX anything in BIOS, what I did try now was change the priority of HDD boot in the BIOS from my one 500GB drive to the other sda is 300 GB so choose that in the HDD boot priority.

---

### Post by presence1960 on 2009-07-07
personally I stay away from Easy BCD. I had used it initially when I didn't know how to configure GRUB. GRUB is way more versatile and can do a lot of things. It really is easy to configure once you learn how to. It just happens in your case that you installed it to the wrong drive.

---

### Post by jjmedem on 2009-07-07
> **presence1960 said:**
> change the boot order to the 300 GB drive that is where GRUB is. If that doesn't work you will have to restore GRUB to the Vista disk's MBR.

Ok, then I need the second step, since I can only choose the 500GB drives in BIOS (I will double-check this after posting)

edit: Alright, the 2 500GB drives are the only ones I can boot from, and I can change priority on those which I tried after reading your previous post, that didn't work, so I guess I need GRUB "moved" to another drives' MBR.

[QUOTE=presence1960]sda, sdb and sdc are not partitions. you have 3 separate HDDs in your rig. sda is 300 GB, sdb and sdc are 500 GB. They are separate hard disks (HDD)[/QUOTE]

thx for clearing that up.

---

### Post by presence1960 on 2009-07-07
In BIOS set your 500 GB drive with Vista & Ubuntu as first boot. Then boot off the Ubuntu Live cd and do this:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

In #5 try root (hd1,5) or whatever #4 outputs.
In #6 use setup (hdx) where x is the hard drive # from #step #5 [i.e (hd1,5) is (hd1)] This will put GRUB to MBR of that 500 GB drive. Again make sure that HDD is set to boot first in BIOS and you should be good to go.

I am going to work now. Post back someone will be able to help if you need more help.

---

### Post by jjmedem on 2009-07-07
> **presence1960 said:**
> In BIOS set your 500 GB drive with Vista & Ubuntu as first boot. Then boot off the Ubuntu Live cd and do this:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

In #5 try root (hd1,5) or whatever #4 outputs.
In #6 use setup (hdx) where x is the hard drive # from #step #5 [i.e (hd1,5) is (hd1)] This will put GRUB to MBR of that 500 GB drive. Again make sure that HDD is set to boot first in BIOS and you should be good to go.

I am going to work now. Post back someone will be able to help if you need more help.

Did everything in that code bit, it was (hd1,5), did all following steps but still no grub to be seen, it still loads vista's bootloader, thx for the replies today, I hope eventually it will be solved :)

Just one thing, should I make it setup (hd1) or (hd1,5) to install GRUB to the MBR?

---

### Post by presence1960 on 2009-07-07
> **jjmedem said:**
> Did everything in that code bit, it was (hd1,5), did all following steps but still no grub to be seen, it still loads vista's bootloader, thx for the replies today, I hope eventually it will be solved :)

Just one thing, should I make it setup (hd1) or (hd1,5) to install GRUB to the MBR?

setup (hd1) to install to MBR. if you use setup (hd1,5) GRUB will be on the partition and will not boot.

---

### Post by JC Cheloven on 2009-07-07
> **jjmedem said:**
> 1.
**cat /boot/grub/menu.lst**
```
ubuntu@ubuntu:~$ cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory
```

-----------
Sorry for my absence since yesterday, and sorry to come back after so an extensive talk (which I admittedly didn't read in whole), but:

YOU HAVE NO menu.lst  !!

The first obvious thing you can do is to provide one. 
You can take as a model the menu.lst file of another ubuntu installation, changing the uuid for that of your sdb6 (as seen in blkid) wherever it appears, and replacing the entries at the end for new ones matching your ubuntu installation and your couple of windoze ones (these using chainloader +1). Ask here if yo need further help with this.

At the point you are (you just installed grub), perhaps this is all you need to get your system booting as desired. Let's hope so :-)

---

### Post by presence1960 on 2009-07-07
> **JC Cheloven said:**
> -----------
Sorry for my absence since yesterday, and sorry to come back after so an extensive talk (which I admittedly didn't read in whole), but:

YOU HAVE NO menu.lst  !!

The first obvious thing you can do is to provide one. 
You can take as a model the menu.lst file of another ubuntu installation, changing the uuid for that of your sdb6 (as seen in blkid) wherever it appears, and replacing the entries at the end for new ones matching your ubuntu installation and your couple of windoze ones (these using chainloader +1). Ask here if yo need further help with this.

At the point you are (you just installed grub), perhaps this is all you need to get your system booting as desired. Let's hope so :-)
He does have a menu.lst file. Here is a snippet from his output of the Boot Info script in post #6, note the top and scroll down to sdb6 in red:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

[COLOR="Red"]sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab[/COLOR]

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   



```

The reason the cat command returned no such file is he ran it from the Live CD. There is no menu.lst on the Live CD filesystem. He would have had to cd in terminal to the Ubuntu installation directory then run that command. otherwise it is looking in the Live CD directory structure.

---

### Post by jjmedem on 2009-07-08
> **presence1960 said:**
> setup (hd1) to install to MBR. if you use setup (hd1,5) GRUB will be on the partition and will not boot.

ok, that gave me grub, but, now there is a problem with the vista boot loader, it's saying: NTLDR missing. I know I have had this before and back then I fixed it with the vista DVD /fixmbr, but that writes over GRUB, any idea for this problem? I'm sorry to be such a nuisance and I want to thank you both for the help you've given me so far. Just one more thing to fix and then I should be good to go.

---

### Post by presence1960 on 2009-07-08
> **jjmedem said:**
> ok, that gave me grub, but, now there is a problem with the vista boot loader, it's saying: NTLDR missing. I know I have had this before and back then I fixed it with the vista DVD /fixmbr, but that writes over GRUB, any idea for this problem? I'm sorry to be such a nuisance and I want to thank you both for the help you've given me so far. Just one more thing to fix and then I should be good to go.

Ok want to confirm & recap before giving next suggestion. You have your sdb (500 GB) drive set as first boot in HDD boot oder in BIOS. You restored GRUB to MBR of that same HDD.

If this is correct edit your windows entry in menu.lst to either (hd0,0) or (hd0,1) like this:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista (loader)
rootnoverify	(hd0,0)
chainloader	+1
```

That should work if Vista is on sdb1, if it is on sdb2 then make it (hd0,1). You no longer should need the map lines because windows is on the drive booting first. The reason your windows entry is (hd0,0) even though it is sdb disk is BIOS and fdisk read order of drives differently. Since your sdb disk is set to boot first in actuality it is hd0.

---

### Post by presence1960 on 2009-07-08
I just noticed another potential problem. Your sdb1 has Windows XP home boot.ini on it? I thought you restored the vista bootloader. Take a look at this from your Boot Info Script Output:
```

================================ sdb1/boot.ini: ================================

;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /NOEXECUTE=OPTIN /FASTDETECT
```

How did that happen? Do you have 2 versions of Windows? XP on sdb1 and Vista on sdb2? If so make the windows entry (hd0,1) in menu.lst
It looks like Vista is on sdb2 so put in (hd0,1) That should boot Vista then in Vista you should have choice of Vista or XP

---

### Post by jjmedem on 2009-07-08
> **presence1960 said:**
> Ok want to confirm & recap before giving next suggestion. You have your sdb (500 GB) drive set as first boot in HDD boot oder in BIOS. You restored GRUB to MBR of that same HDD.

If this is correct edit your windows entry in menu.lst to either (hd0,0) or (hd0,1) like this:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista (loader)
rootnoverify	(hd0,0)
chainloader	+1
```

That should work if Vista is on sdb1, if it is on sdb2 then make it (hd0,1). You no longer should need the map lines because windows is on the drive booting first. The reason your windows entry is (hd0,0) even though it is sdb disk is BIOS and fdisk read order of drives differently. Since your sdb disk is set to boot first in actuality it is hd0.

Sorry, but what are the exact commands I need to do? I understand I should edit menu.lst but how to? I have indeed set the BIOS to boot from one of the 500GB drives, I suppose that is (hd1) because that's where GRUB now is in the MBR and that boots fine, I wonder if Vista bootloader isn't damaged now though.

Edit: GRUB boots Ubuntu from hd0,5 if I can believe the booting post message

---

### Post by presence1960 on 2009-07-08
> **jjmedem said:**
> Sorry, but what are the exact commands I need to do? I understand I should edit menu.lst but how to? I have indeed set the BIOS to boot from one of the 500GB drives, I suppose that is (hd1) because that's where GRUB now is in the MBR and that boots fine, I wonder if Vista bootloader isn't damaged now though.

Edit: GRUB boots Ubuntu from hd0,5 if I can believe the booting post message
 Ok boot into ubuntu, open a terminal and run this command ```
gksu gedit /boot/grub/menu.lst
``` That is a lowercase L :)

Edit your windows entry by following the instructions I posted in post #18. Try (hd0,1) first:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title		Windows Vista (loader)
rootnoverify	(hd0,1)
chainloader	+1

```

---

### Post by jjmedem on 2009-07-08
> **presence1960 said:**
> Ok boot into ubuntu, open a terminal and run this command ```
gksu gedit /boot/grub/menu.lst
``` That is a lowercase L :)

Edit your windows entry by following the instructions I posted in post #18. Try (hd0,1) first:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title		Windows Vista (loader)
rootnoverify	(hd0,1)
chainloader	+1

```

did that, and now I get "bootmgr missing" when I choose the Vista option in GRUB (and yes, I have XP and Vista installed, so to be able to boot all OS's all I need is to get Vista bootloader working, since that automatically has XP included.) So it's still not working and the message has now changed, should I try the other option now (hd0,0)?

---

### Post by presence1960 on 2009-07-08
> **jjmedem said:**
> did that, and now I get "bootmgr missing" when I choose the Vista option in GRUB (and yes, I have XP and Vista installed, so to be able to boot all OS's all I need is to get Vista bootloader working, since that automatically has XP included.) So it's still not working and the message has now changed, should I try the other option now (hd0,0)?

which partition is vista on? I would try (hd0,0) - if that doesn't work you have a problem with your windows bootloader. You will then have to reinstall the windows bootloader, then reinstall GRUB. But at least now you know how to do it.

---

### Post by jjmedem on 2009-07-08
> **presence1960 said:**
> which partition is vista on? I would try (hd0,0) - if that doesn't work you have a problem with your windows bootloader. You will then have to reinstall the windows bootloader, then reinstall GRUB. But at least now you know how to do it.

That got it working, trying the (hd0,0). Thanks a lot, now I finally have it running again, can't thank you enough. :D

---

### Post by presence1960 on 2009-07-08
> **jjmedem said:**
> That got it working, trying the (hd0,0). Thanks a lot, now I finally have it running again, can't thank you enough. :D

No problem, if the roles were reversed I am sure you would do the same for me. main thing to remember is BIOS and fdisk (Ubuntu) read the order of drives differently. I also use Sabayon and when installing you have the option of changing the drive order to match your BIOS setting. Maybe in time Ubuntu will get that.

Study that boot info script output file of yours. it has a wealth of info about your machine

---

### Post by jjmedem on 2009-07-08
> **presence1960 said:**
> No problem, if the roles were reversed I am sure you would do the same for me. main thing to remember is BIOS and fdisk (Ubuntu) read the order of drives differently. I also use Sabayon and when installing you have the option of changing the drive order to match your BIOS setting. Maybe in time Ubuntu will get that.

Study that boot info script output file of yours. it has a wealth of info about your machine

In time I hope to understand even a little more of some of the Linux stuff :D For now, I'm very happy to have it running again, thanks again.

---

