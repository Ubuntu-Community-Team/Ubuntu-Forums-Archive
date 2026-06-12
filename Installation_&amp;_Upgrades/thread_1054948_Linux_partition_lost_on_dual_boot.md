---
title: "Linux partition lost on dual boot"
date: 2009-01-30
forum: Installation &amp; Upgrades
---

### Post by abicash on 2009-01-30
Hello

I have two IDE drives.
Hitachi 160Gb (Primary Master) and SAMSUNG 20Gb (Slave)

I was dual booting with Windows XP on Hitachi and Ubuntu on the Samsung disk on some 7Gb (2Gb swap).The rest of the space on the Slave is for my backup and other stuff.

I was happy all these days with GRUB asking me to select one of the OSes to boot from.
But I heard of installing Leopard OS on my computer and thought about trying that.
I cleared some 7Gb(FAT32) on the Slave for Leopard and booted with the Installation DVD.
After booting eventually I went to Disc Utility to partition the Leopard as 'Mac Os Extended Journaled' and it said something like "some error took place" (don't remember exactly).

So I rebooted to find that I am not able to boot since the screen is forever waiting to find Grub stage 1.5

I then popped in SuperGrub disk to fix the boot on Grub,but somehow it couldn't find it.

So i tried fixing the Windows boot..(basically I tried whichever option they have on Supergrub) to activate at least my Windows.

Now I can boot in windows to find that the 20Gb space shows as unformatted free space.
Is all my Data lost?Is my sweeet Ubuntu lost too?:(

Please help me guys with this one

---

### Post by Pumalite on 2009-01-30
Boot your Live CD and post:
```
sudo fdisk -lu
```

---

### Post by abicash on 2009-01-30
Hello Pumalite

Thanks for replying.Much appreciated!!!

Here's my fdisk -lu listing

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x27822781

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    43471889    21735913+   b  W95 FAT32
/dev/sda2        43471890   312576704   134552407+   f  W95 Ext'd (LBA)
/dev/sda5        43471953    57352049     6940048+   b  W95 FAT32
/dev/sda6        57352113   118784609    30716248+   7  HPFS/NTFS
/dev/sda7       118784673   180217169    30716248+   7  HPFS/NTFS
/dev/sda8       180217233   241649729    30716248+   7  HPFS/NTFS
/dev/sda9       241649793   312576704    35463456    7  HPFS/NTFS
Bad offset in primary extended partition

Disk /dev/sdb: 20.0 GB, 20060135424 bytes
255 heads, 63 sectors/track, 2438 cylinders, total 39179952 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc1e0c1e0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               0    39166469    19583235    5  Extended
```

What I can understand is that this sdb partition is still there with extended.but why isn't it showing in Places/Computer ?

Please help

Thanks and regards:)

---

### Post by Pumalite on 2009-01-30
The whole drive is an extended partition. It appears empty.

---

### Post by abicash on 2009-01-30
Hello again

Thanks for the prompt reply :)

So does it mean that there is no data there now?All has been erased?

Is there some way of getting it back?

Thanks and regards!!!:)

EDIT: Even if it is empty and is extended partition,why isn't ubuntu identifying it as an empty disk?

---

### Post by Pumalite on 2009-01-30
An extended partition allows you to place many logical partitions inside it. This one seems to have none. You could reinstall Ubuntu to it and could be ideal. As to your data; unless it is in sda; I doubt very much you'll find it in sdb.
Take a screenshot of sdb with gparted and you'll have a better idea.

---

### Post by abicash on 2009-01-30
:( it's showing as unallocated in GParted 

So I hope I damaged the data,isn't it?

Can I recover it some how? or I should forget it?

---

### Post by Pumalite on 2009-01-30
You can boot a Knoppix Live CD and see what you find, but if it's unallocated; I'd say; format it.

---

### Post by caljohnsmith on 2009-01-30
I would recommend seeing if testdisk can find your lost partitions; if you want to try that, first make sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
Make sure you are using testdisk version 6.9 or later, if not let me know. After starting testdisk with the above command, choose "No Log", select the sdb HDD and "Proceed", "Intel", "Analyze", "Quick search", Y/N depending on if you have any Vista partitions, hit enter to continue, and select "Deeper Search" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let me know exactly which partitions give you a directory listing and if you can identify them. We can work from there if you want.

---

### Post by abicash on 2009-01-31
Hello caljohnsmith

Thank you for replying :)

I tried to apt-get install testdisk in my ubuntu live-cd session but it could not get it anyhow i try.Enabling all repositories did not work :(.

So I found testdisk for windows and downloaded and run it in my windows.

It shows my /dev/sdb-20Gb /18Gb -Samsung disk.

But when I hit Proceed tab on this disk,the program doesn't go ahead,it just sits there doing nothing and up/down keys freeze.
It works good on my other disk.

What can I do next?

Awaiting help as usual :)

Thanks and regards!!

EDIT: Testdisk ver 6.10

---

### Post by abicash on 2009-01-31
Hello again

I downloaded version 6.11 of test disk and even though its beta release,it is detecting and proceeding further.
I am now analysing my 20Gb busted disk.

Will keep you updated once I go a bit ahead.

Thanks for mentioning this wonderful program  

Regards

---

### Post by abicash on 2009-01-31
Hello

I did a complete analysis with the testdisk and my drive F: is still there:D
I can identify eac and every folder and sub-folder and the files that they hold.

Now how do I recover these?

I can see also the Linux Swap and the Linux ext2 partition but cannot enter its folders as in Fat32.

Now can this whole drive be restructured as it was before?

Please help soon...quite excited for now

Thanks and regards!!!!!

EDIT: Recovered ALL my important data on F::D
Now I am checking if I am able to get the Linux partitions back.
:lolflag:
Thank you so much!!!

---

### Post by caljohnsmith on 2009-01-31
That's great news that testdisk 6.11 worked. Please post the results of the "deep search" from testdisk, and let me know which are the partitions that give directory listings and that you want to recover. We can work from there.

---

### Post by abicash on 2009-02-01
Hello caljohn

I have attached the screenshot of the testdisk after a deeper search of my drive.

Here you can see the Fat32 [F]in green which has been recovered totally.
I did this by activating the MBR for that drive and it just miraculously retained my F: with all its contents.

The 1st entry of Fat32is not really important.

The other two,Linux swap and Linux which show as 'Deleted' are 'Logical drives' and these are I want to recover.It is not as if I have any important data in these but I have my very nice Ubuntu with all these desktop effects and other programs which I frequently use.

Could these be recovered as-they-are by adding an entry in GRUB (which could be re-installed?) like I did for the Fat32 partition?

If that was not possible,that would be okay to the extent of me burying myself for a couple of hours to set it up again.But if this could be avoided:redface:

Thanks again and best regards :)

EDIT: I can find all directories and files in the Linux partition.I can also recover these (I recovered a small video in my /home/video folder)
I now am thinking that only the way to reach Ubuntu is lost.So how do I activate this partition...Please help!!!

---

### Post by caljohnsmith on 2009-02-01
First of all, I just want to check to make sure, but are the results you posted from the "deep search" and not the "quick search"? That's really important. If the results are from the deep search, it should be safe to recover your linux partition since it gave you a directory listing, so how about marking the swap partition as "L", the linux partition as "L", be sure to mark your FAT32 partition at the end with "*" (don't leave it as "D"), and the first FAT partition you can leave as "D". Once you are sure they are marked as described, hit enter to get to the next screen, and then write the new partition table. Then reboot, and from your Live CD please post the output of:
```
sudo fdisk -lu
```
And also for your FAT partition and linux partition try:
```
sudo mkdir /mnt/FAT /mnt/linux
sudo mount /dev/[COLOR="Blue"]sdb1[/COLOR] /mnt/FAT && ls -l /mnt/FAT
sudo mount /dev/[COLOR="Blue"]sdb6[/COLOR] /mnt/linux && ls -l /mnt/linux
```
I think the FAT partition will most likely be sdb1 and the linux partition sdb6, but if they are different, be sure to use whatever is correct in the above commands. Please post the output and we can work from there if you want.

---

### Post by abicash on 2009-02-02
Hello caljohn

Thanks for replying.Much appreciated :)

The results posted earlier were indeed Deep Search results.

Here is fdisk -lu listing

```
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x27822781

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    43471889    21735913+   b  W95 FAT32
/dev/sda2        43471890   312576704   134552407+   f  W95 Ext'd (LBA)
/dev/sda5        43471953    57352049     6940048+   b  W95 FAT32
/dev/sda6        57352113   118784609    30716248+   7  HPFS/NTFS
/dev/sda7       118784673   180217169    30716248+   7  HPFS/NTFS
/dev/sda8       180217233   241649729    30716248+   7  HPFS/NTFS
/dev/sda9       241649793   312576704    35463456    7  HPFS/NTFS

Disk /dev/sdb: 20.0 GB, 20060135424 bytes
255 heads, 63 sectors/track, 2438 cylinders, total 39179952 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1cc1b2a7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1           16065    39166469    19575202+   f  W95 Ext'd (LBA)
[COLOR="Red"]/dev/sdb5           16128     4080509     2032191   82  Linux swap / Solaris
/dev/sdb6         4080573    14105069     5012248+  83  Linux[/COLOR]
/dev/sdb7        30748473    39166469     4208998+   c  W95 FAT32 (LBA)
```

You are right.sdb6 is the linux partition and sdb5 is swap.
I am able to see all the files in this sdb6 in my /Places/5.1Gb Media (which happens to be sdb6) :)

The mounting sdb7 command gave me all the files of my Fat32 as expected.
```
ubuntu@ubuntu:~$ sudo mount /dev/sdb7 /mnt/FAT && ls -l /mnt/FAT
total 11944
  drwxr-xr-x  3 root root    4096 2009-01-20 16:08 Filename
 -rwxr-xr-x  1 root root   78476 2007-08-10 16:27 Filename
```
(this is small listing of all the files)

For Linux mount it gave
```
ubuntu@ubuntu:~$ sudo mount /dev/sdb6 /mnt/linux && ls -l /mnt/linux
total 128
drwxr-xr-x   2 root root    4096 2009-01-20 23:17 bin
drwxr-xr-x   3 root root    4096 2009-01-21 06:18 boot
lrwxrwxrwx   1 root ubuntu    11 2009-01-20 17:30 cdrom -> media/cdrom
drwxr-xr-x   4 root root    4096 2008-04-22 17:59 dev
drwxr-xr-x 123 root root    8192 2009-01-29 06:59 etc
drwxr-xr-x   3 root root    4096 2009-01-20 17:39 home
drwxr-xr-x   2 root root    4096 2008-04-22 17:48 initrd
lrwxrwxrwx   1 root ubuntu    33 2009-01-20 23:16 initrd.img -> boot/initrd.img-2.6.24-16-generic
drwxr-xr-x  16 root root    8192 2009-01-21 05:34 lib
drwxr-xr-x   2 root root   49152 2009-01-20 17:30 lost+found
drwxr-xr-x   8 root root    4096 2009-01-29 06:47 media
drwxr-xr-x   2 root root    4096 2008-04-15 05:53 mnt
drwxr-xr-x   2 root root    4096 2008-04-22 17:48 opt
drwxr-xr-x   2 root root    4096 2008-04-15 05:53 proc
drwxr-xr-x  13 root root    4096 2009-01-28 11:32 root
drwxr-xr-x   2 root root    4096 2009-01-21 05:34 sbin
drwxr-xr-x   2 root root    4096 2008-04-22 17:48 srv
drwxr-xr-x   2 root root    4096 2008-04-19 05:05 sys
drwxrwxrwt  13 root root    4096 2009-01-29 06:59 tmp
drwxr-xr-x  12 root root    4096 2009-01-20 12:26 usr
drwxr-xr-x  15 root root    4096 2008-04-22 18:07 var
lrwxrwxrwx   1 root ubuntu    30 2009-01-20 23:16 vmlinuz -> boot/vmlinuz-2.6.24-16-generic
```

I guess everything is there.
Please help as usual :)

Thanks and regards

[COLOR="Red"]**EDIT: Added Screenshot of Gparted on sdb**[/COLOR]

---

### Post by caljohnsmith on 2009-02-02
That's great, abicash, it looks like your linux partition and FAT partition are just fine. Can you set your BIOS to boot the Ubuntu sdb drive on start up? If so, here's how you can reinstall Grub to that drive to make it bootable:
```
sudo grub
grub> root (hd1,5)
grub> setup (hd1)
grub> quit
```
Then reboot, set your BIOS to boot the sdb Ubuntu drive, and let me know how far you get. We can work from there.

---

### Post by abicash on 2009-02-02
Hello again :)
I am not able to boot sdb by setting it in bios.

---

### Post by caljohnsmith on 2009-02-02
OK, if you can only boot your sda drive, how about trying:
```
sudo grub
grub> root (hd1,5)
grub> setup (hd0)
grub> quit
```
Then let me know exactly what happens when you boot the sda drive.

---

### Post by abicash on 2009-02-02
Hello caljohn

I setup grub for hd0 and when I boot I can find the grub menu on startup where I select both the OSes but when I select Ubuntu,
Grub gives out Error 15 File not found and then it reverts back to the selection screen.
EDIT: I can boot Windows normally though!

What could be wrong?

Thanks and awaiting your reply
:)

---

### Post by caljohnsmith on 2009-02-02
In order to figure out how we will need to reconfigure your Grub menu to boot Ubuntu, how about booting your Live CD, download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. The results of that script will help clarify your setup and help us figure out what we need to change in your Grub's menu.lst file so you can boot Ubuntu again.

---

### Post by abicash on 2009-02-03
Hello caljohn
Thanks for being there :)

Here is the Results.txt file after running bash

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTLDR /NTDETECT.COM /ntdetect.com

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda9 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x27822781

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    43,471,889    43,471,827   b W95 FAT32
/dev/sda2          43,471,890   312,576,704   269,104,815   f W95 Ext d (LBA)
/dev/sda5          43,471,953    57,352,049    13,880,097   b W95 FAT32
/dev/sda6          57,352,113   118,784,609    61,432,497   7 HPFS/NTFS
/dev/sda7         118,784,673   180,217,169    61,432,497   7 HPFS/NTFS
/dev/sda8         180,217,233   241,649,729    61,432,497   7 HPFS/NTFS
/dev/sda9         241,649,793   312,576,704    70,926,912   7 HPFS/NTFS


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 20.0 GB, 20060135424 bytes
255 heads, 63 sectors/track, 2438 cylinders, total 39179952 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1cc1b2a7

Partition  Boot         Start           End          Size  Id System

/dev/sdb1              16,065    39,166,469    39,150,405   f W95 Ext d (LBA)
/dev/sdb5              16,128     4,080,509     4,064,382  82 Linux swap / Solaris
/dev/sdb6           4,080,573    14,105,069    10,024,497  83 Linux
/dev/sdb7          30,748,473    39,166,469     8,417,997   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="SYSTEM" UUID="18CA-1952" TYPE="vfat" 
/dev/sda5: LABEL="EXTRAS" UUID="48D4-32A9" TYPE="vfat" 
/dev/sda6: UUID="96ECF413ECF3EAFF" LABEL="SONGS" TYPE="ntfs" 
/dev/sda7: UUID="E868040D6803D968" LABEL="MOVIES" TYPE="ntfs" 
/dev/sda8: UUID="B8400D34400CFB40" LABEL="SOFTWARES" TYPE="ntfs" 
/dev/sda9: UUID="A81018C510189BFE" LABEL="STUDY" TYPE="ntfs" 
/dev/sdb5: TYPE="swap" UUID="ffb57ebf-a695-472c-8690-83799784b08a" 
/dev/sdb6: UUID="ccdd337a-3508-4dcb-89ed-f46882426626" TYPE="ext2" 
/dev/sdb7: LABEL="F" UUID="13DB-2172" TYPE="vfat" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer /noexecute=optout


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
default		1

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		4

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

#A splash image for the menu
splashimage=(hd1,6)/boot/grub/splashimages/appleblack.xpm.gz

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=ccdd337a-3508-4dcb-89ed-f46882426626 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,6)

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

title		Ubuntu 8.04 Hardy Heron
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=ccdd337a-3508-4dcb-89ed-f46882426626 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

#title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
#root		(hd1,6)
#kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=ccdd337a-3508-4dcb-89ed-f46882426626 ro single
#initrd		/boot/initrd.img-2.6.24-16-generic

#title		Ubuntu 8.04, memtest86+
#root		(hd1,6)
#kernel		/boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title		Other operating systems:
#root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb7
UUID=ccdd337a-3508-4dcb-89ed-f46882426626 /               ext2    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=ffb57ebf-a695-472c-8690-83799784b08a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb6: Location of files loaded by Grub: ===================


   6.4GB: boot/grub/menu.lst
   6.4GB: boot/grub/stage2
   6.4GB: boot/initrd.img-2.6.24-16-generic
   6.4GB: boot/initrd.img-2.6.24-16-generic.bak
   6.4GB: boot/vmlinuz-2.6.24-16-generic
   6.4GB: initrd.img
   6.4GB: vmlinuz

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  e2 e6 e0 20 8a 68 6b e6  8a d8 1d 46 45 fc f6 e9  |... .hk....FE...|
00000010  a8 bc 7e de cc 15 71 d8  83 79 ad 8b 7e 79 ae 99  |..~...q..y..~y..|
00000020  2b 22 f5 39 7c 59 fe 34  c7 19 42 4d 30 3d 9c d0  |+".9|Y.4..BM0=..|
00000030  c6 13 cb 69 fd f2 93 f5  cb 4f 44 35 3d 53 de d1  |...i.....OD5=S..|
00000040  1d df 60 38 b8 f7 6d d1  9a 6d 8b f6 52 9a d7 13  |..`8..m..m..R...|
00000050  a9 7e f9 d8 8c ce 3e cf  75 74 ea ed 88 8e 7a b9  |.~....>.ut....z.|
00000060  8e 58 3b ba 30 43 ea 41  fc c9 25 05 b9 c7 1b e6  |.X;.0C.A..%.....|
00000070  51 5c 78 e8 61 58 99 b2  8f 96 df 06 8c b1 6f 39  |Q\x.aX........o9|
00000080  c9 56 3c b5 57 12 3c f0  54 a6 c9 63 64 df 49 18  |.V<.W.<.T..cd.I.|
00000090  74 b0 89 02 7d 93 29 f1  5b f5 c0 8c 6d be 6f 77  |t...}.).[...m.ow|
000000a0  24 ff 6f f3 fd eb 9e f3  a8 b9 f2 6d 51 ca 19 f3  |$.o........mQ...|
000000b0  0e df 20 bf ff 71 54 ce  1d d1 2f 6f 7e 07 35 77  |.. ..qT.../o~.5w|
000000c0  62 2f 4e 1c e8 a9 1d 48  71 ed 36 dd 9e 17 b5 1f  |b/N....Hq.6.....|
000000d0  9d c1 f6 db e1 fe 17 a5  e6 96 82 71 ab 05 bf 04  |...........q....|
000000e0  fd 74 11 2b 78 df 55 58  59 05 6b a7 dd 2a 24 15  |.t.+x.UXY.k..*$.|
000000f0  19 ab ea 97 30 0c a3 04  12 60 bb 5d 14 3c 56 ad  |....0....`.].<V.|
00000100  35 48 e3 3c 11 7f 75 27  6f 06 fa 5e 40 ce e7 db  |5H.<..u'o..^@...|
00000110  59 dd 56 d7 48 81 f2 cb  17 94 d4 a1 e6 7d de 8e  |Y.V.H........}..|
00000120  a7 ee 22 73 ff 9c 3d 91  b9 7f 98 e3 12 62 af cf  |.."s..=......b..|
00000130  2f ea b9 04 a7 b6 b4 fd  3f 74 43 bb 1b f6 e0 92  |/.......?tC.....|
00000140  40 ee 53 ba b5 86 30 5b  13 d8 bc e7 c2 73 5d 7c  |@.S...0[.....s]||
00000150  3f dc 35 81 74 c7 42 d7  aa 0a af e8 59 ab 2d 0a  |?.5.t.B.....Y.-.|
00000160  34 52 1d 7f 3a 48 5a e7  20 2c 6b 18 6b 02 4d 2d  |4R..:HZ. ,k.k.M-|
00000170  36 c3 dc 1d d1 0b 13 8b  d4 14 0b b1 d8 ba eb b3  |6...............|
00000180  74 65 92 f5 1a 2b 93 e9  90 02 bd 73 2c 94 49 e5  |te...+.....s,.I.|
00000190  56 2c 13 86 fb 57 77 5c  4c ac cd 5b e6 d3 76 a6  |V,...Ww\L..[..v.|
000001a0  fa 43 26 5f 6c 93 29 80  db d1 85 a6 98 60 86 3f  |.C&_l.)......`.?|
000001b0  24 80 27 36 98 e4 0f c5  82 47 08 c6 e4 b6 00 fe  |$.'6.....G......|
000001c0  ff ff 0b fe ff ff 3f 00  00 00 21 cb d3 00 00 fe  |......?...!.....|
000001d0  ff ff 05 fe ff ff 60 cb  d3 00 f0 62 a9 03 00 00  |......`....b....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

Thanks and regards!!

---

### Post by caljohnsmith on 2009-02-03
OK, I believe I see the problem; how about from your Live CD do:
```
sudo mount /dev/sdb6 /mnt
gksudo gedit /mnt/boot/grub/menu.lst
```
And change all your Ubuntu entries to use (hd1,5) instead of (hd1,6):
```
title		Ubuntu 8.04 Hardy Heron
root		[COLOR="Blue"](hd1,5)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=ccdd337a-3508-4dcb-89ed-f46882426626 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet
```
Also, change the "#groot=(hd1,6)" to use (hd0,5):
```
#groot=[COLOR="Blue"](hd1,5)[/COLOR]
```
Save, reboot, and let me know if you can boot Ubuntu OK. We can work from there.

---

### Post by abicash on 2009-02-03
Hello caljohn...you are the man...=D>
:guitar::lolflag:\\:D/

Its done!!!!!!!!!!!!!!!!!!!!!!!!!!!


Kudos to you.Friends like you have kept me on Linux for this long ...of course linux itself is the other reason:biggrin:

I am really not able to believe this yet...since once in the past a similar thing had occurred wherein I had to lose all my data and I was all sad...

What more can I say!!

Thanks and regards

---

### Post by caljohnsmith on 2009-02-03
Glad to hear that worked OK, abicash; cheers and enjoy your resurrected Ubuntu install. :)

---

