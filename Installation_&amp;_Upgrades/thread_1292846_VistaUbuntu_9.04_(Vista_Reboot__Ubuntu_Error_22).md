---
title: "Vista/Ubuntu 9.04 (Vista Reboot / Ubuntu Error 22)"
date: 2009-10-16
forum: Installation &amp; Upgrades
---

### Post by kblair on 2009-10-16
So there's dozens of threads similar to this but I can't find a solution through any of them (I've been searching and trying things for days before posting).

Situation.. First drive in system (sda) with two partitions.

1. Shrink 2nd partition on drive to make room for Ubuntu
2. Let Ubuntu installer use that free space and set up its install/swap partitions
3. Ubuntu installs fine, reboots and shows Grub and goes into Ubuntu fine.

Easy enough, right?


Reboot and choose Vista from the Grub menu and *poof* the PC reboots before I ever see the Windows screen or anything related to Windows. Every time I choose Windows on the Grub menu, it reboots the PC as it tries to load. Choosing Ubuntu works fine.

So.. I load up the windows recovery disk, fix the MBR and it boots into windows no problem. Install EasyBCD and follow the online instructions I found for adding NeoGrub to the windows up.. reboot, the windows boot menu comes up, can boot into windows fine. Reboot and choose NeoGrub and I get the error 17 about files not found. I doube, triple, quadruple check and set the proper settings from menu.lst and they're fine.

I go and do the whole boot (hd0,4) , setup (hd0) thing with the CD instance of Ubuntu.. great. Now I can boot into Ubuntu again but choosing Windows makes the computer reboot.

So in summary.. I can either fix the windows MBR and boot into Vista but not able to find Ubuntu, or I can set the Ubuntu MBR and the computer reboots when choosing Vista.

(btw: I've tried the supergrub disk, found no fixes there either unless I just didnt know enough of what I was doing)


Here's my menu.lst from Ubuntu that I used in EasyBCD / NeoGrub:

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        aba1882c-50cc-424e-bea7-5319c49d1c33
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=aba1882c-50cc-424e-bea7-5319c49d1c33 ro xforcevesa quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        aba1882c-50cc-424e-bea7-5319c49d1c33
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=aba1882c-50cc-424e-bea7-5319c49d1c33 ro xforcevesa  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        aba1882c-50cc-424e-bea7-5319c49d1c33
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=aba1882c-50cc-424e-bea7-5319c49d1c33 ro xforcevesa quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        aba1882c-50cc-424e-bea7-5319c49d1c33
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=aba1882c-50cc-424e-bea7-5319c49d1c33 ro xforcevesa  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        aba1882c-50cc-424e-bea7-5319c49d1c33
kernel        /boot/memtest86+.bin
quiet


==============================================
And here's the entry for Windows when I'm booting up to Ubuntu.. which as I said, choosing makes my computer reboot.


# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1



===============
Here's some output of info:

grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd0,4)
grub> root (hd0,4)
root (hd0,4)
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,4)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.
grub> quit

root@ubuntu:~# fdisk -l
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa05ca05c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6386    51295513+   7  HPFS/NTFS
/dev/sda2            6387       56977   406368486    7  HPFS/NTFS
/dev/sda3           56978       60801    30716280    5  Extended
/dev/sda5           56978       60638    29406951   83  Linux
/dev/sda6           60639       60801     1309266   82  Linux swap / Solaris


Here's the error message I receive when using Windows bootloader trying to launch NeoGrub/Ubuntu:

  Booting 'Ubuntu 9.04, kernel 2.6.28-15-generic'
kernel   /boot/vmlinuz-2.6.28-15-generic root=UUID=aba1882c-50cc-424e-bea7-5319c49d1c33 ro xforcevesa quiet splash

Error 17: File not found

Press any key to continue...

---

### Post by kblair on 2009-10-16
Anyone have any ideas?

---

### Post by phillw on 2009-10-16
> **kblair said:**
> Anyone have any ideas?

Hi, looks like it may be me, then !!

I'm called Phill & have a Vista / 9.04 system running happily.

A couple of questions ... ( I apologise if you've already answered them)

Computer Spec, CPU-type (32 / 64 bit), RAM ?

How is you hard-drive partitioned ? Scrub that - i'm looking at your partiton table !!!



Bear with me !!

Phillw

---

### Post by Zimmer on 2009-10-16
Did you install GRUB to the Ubuntu partition?  If not, then that is the problem. You should reinstall GRUB to the Ubuntu partition and point EasyBCD to it ... 
On BOOT you will get a Choice of Vista or Ubuntu and the Ubuntu choice will take you to GRUB....

---

### Post by kblair on 2009-10-16
PC specs.. 4 gig memory, running Vista 32bit and Ubuntu 64 bit 9.04...

Here's how the drive in question (first drive of system) is partitioned:

root@ubuntu:~# fdisk -l
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa05ca05c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6386    51295513+   7  HPFS/NTFS
/dev/sda2            6387       56977   406368486    7  HPFS/NTFS
/dev/sda3           56978       60801    30716280    5  Extended
/dev/sda5           56978       60638    29406951   83  Linux
/dev/sda6           60639       60801     1309266   82  Linux swap / Solaris

Looking at it from a 'Microsoft Storage Management' point of view, there's 

DriveC (50g) / DriveI (400g) / Free Space (30g)

I shrunk Drive I to make the free space at the end of the drive and installed Ubuntu there. I let Ubuntu do the partitioning of the install by choosing 'use largest free space' at install.

---

### Post by phillw on 2009-10-16
hmmm...

okies, 

your fdisk -l is saying you have two partitions for vista (the HPFS/NTFS ones)

these being sda1 (the boot one) and sda2

So, do U have dive C: and drive D: in vista on your hard-drive ?

Phill.

---

### Post by kblair on 2009-10-16
> **Zimmer said:**
> Did you install GRUB to the Ubuntu partition?  If not, then that is the problem. You should reinstall GRUB to the Ubuntu partition and point EasyBCD to it ... 
On BOOT you will get a Choice of Vista or Ubuntu and the Ubuntu choice will take you to GRUB....

Ubuntu and Windows are on the same drive, so basically.. yes.

I did try at one point putting Ubuntu on my second drive, choosing advanced options during install and choosing to put the bootloader on the Ubuntu drive. When I rebooted with that it went directly into Windows. When I tried adding it to Windows boot up with EasyBCD I got error 17 with the file not found just like I have now.

I can't seem to win. :(

---

### Post by phillw on 2009-10-16
okies, drive I, in your case ...

---

### Post by kblair on 2009-10-16
> **phillw said:**
> your fdisk -l is saying you have two partitions for vista (the HPFS/NTFS ones)

these being sda1 (the boot one) and sda2

So, do U have dive C: and drive D: in vista on your hard-drive ?

See above, on the first drive I've got C and I, but yes - two windows partitions.

Here's a full fdisk -l of all drives if you're interested..



root@ubuntu:~# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
Disk identifier: 0xa05ca05c

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6386    51295513+   7  HPFS/NTFS
/dev/sda2            6387       56977   406368486    7  HPFS/NTFS
/dev/sda3           56978       60801    30716280    5  Extended
/dev/sda5           56978       60638    29406951   83  Linux
/dev/sda6           60639       60801     1309266   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
Disk identifier: 0xec3b975c

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
Disk identifier: 0xf37a6e81

Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdd: 300.0 GB, 300069052416 bytes
Disk identifier: 0xb7458fd7

Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       36481   293033601    7  HPFS/NTFS

root@ubuntu:~#

---

### Post by phillw on 2009-10-16
before we proceed, with what I'm thinking - 

1) can you get vista back working okay
2) can we do a completely new install for ubuntu ? - JUST of ubuntu !!!!

Phill.

---

### Post by kblair on 2009-10-16
> **phillw said:**
> 1) can you get vista back working okay
2) can we do a completely new install for ubuntu ? - JUST of ubuntu !!!!


Sure thing.. I'm in windows now (just saved all that above info while I had Ubuntu up). I can certainly do a reinstall of Ubuntu.

---

### Post by phillw on 2009-10-16
The bit that bothers me in this list 

> 
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6386    51295513+   7  HPFS/NTFS
/dev/sda2            6387       56977   406368486    7  HPFS/NTFS
/dev/sda3           56978       60801    30716280    5  Extended
/dev/sda5           56978       60638    29406951   83  Linux
/dev/sda6           60639       60801     1309266   82  Linux swap / Solaris


is sda3

It's starting at the beginning of sda5, all the way thru' sda5 - then goes onto include the whole of sda6

This just seems wrong to me !!!

Phill.

---

### Post by phillw on 2009-10-16
Can you go  'kill' / 'nuke' / 'napalm' / 'erase' .... lol

sda3, sda5 and sda6 - go make them 'unallocated' space.

Phill.

btw - do u have AIM  instant messaging ?

---

### Post by kblair on 2009-10-16
> **phillw said:**
> The bit that bothers me in this list 
is sda3
 It's starting at the beginning of sda5, all the way thru' sda5 - then goes onto include the whole of sda6
 This just seems wrong to me !!!



While looking at it, I wondered why it would skip sda4 - but I'm not that knowledgeable about partitions to question it. SDA3 is where Ubuntu is located - also (as noted in first post) it comes up as hd0,4 in grub.

In an extreme measure, if necessary, I can kill the I partition also if necessary. But I'm not going to wipe out my main windows partition.

---

### Post by phillw on 2009-10-16
just 'nuke'   sda3, sda5 and sda6

---

### Post by phillw on 2009-10-16
and, who knows the secret of how partitions work .. i have little 1-5 kb 'bits' hanging around after my many re-slicing and shrinking and growing of partitions - one thing I do NOT have, is over-lapping ones !!

---

### Post by Zimmer on 2009-10-16
> **kblair said:**
> Ubuntu and Windows are on the same drive, so basically.. yes.

I did try at one point putting Ubuntu on my second drive, choosing advanced options during install and choosing to put the bootloader on the Ubuntu drive. When I rebooted with that it went directly into Windows. When I tried adding it to Windows boot up with EasyBCD I got error 17 with the file not found just like I have now.

I can't seem to win. :(

Erm, NO. You need to install GRUB to the Ubuntu partition, which appears to be sda5 (or in GRUBspeak hd0,4) . Yes, it is on the same physical drive, but not the same partition as Vista. My guess is that if you did install GRUB to the same partition as Ubuntu you got the naming wrong in EasyBCD.

---

### Post by phillw on 2009-10-16
>  
Erm, NO. You need to install GRUB to the Ubuntu partition, which appears to be sda5 (or in GRUBspeak hd0,4) . Yes, it is on the same physical drive, but not the same partition as Vista. My guess is that if you did install GRUB to the same partition as Ubuntu you got the naming wrong in EasyBCD.

As the OP has an overlapping partition - I'm getting the 3 of them removed & a fresh, clean start.

---

### Post by kblair on 2009-10-16
> **Zimmer said:**
> Erm, NO. You need to install GRUB to the Ubuntu partition, which appears to be sda5 (or in GRUBspeak hd0,4) . Yes, it is on the same physical drive, but not the same partition as Vista. My guess is that if you did install GRUB to the same partition as Ubuntu you got the naming wrong in EasyBCD.

I installed grub at the same spot that the install was installing Ubuntu. What I was saying there, was at another time I tried putting Ubuntu on a whole different drive (sdb) because I wasn't able to get it working on the same drive that Windows is on (sda).

---

### Post by kblair on 2009-10-16
So I wiped out the partitions requested.. and am going through the install now and Ubuntu is setting them up exactly as they were before:
 
The partition tables of the following devices are changed:
SCSI3 (0,0,0) (sda)
 
The following partitions are going to be formatted:
partition #5 of SCSI3 (0,0,0) (sda) as ext3
partition #6 of SCSI3 (0,0,0) sda) as swap
 
Advanced options shows installing boot loader to (hd0).

---

### Post by Zimmer on 2009-10-16
To enlighten you on the partition naming..

You can have 4 primary partitions on a disk. They will be numbered 1-4.
You have created partition 3 as an 'extended' partition, allowing more LOGICAL partitions within it (numbers 5 and 6). Number 4 is reserved for the final primary partition you could (if you had room) create.


[http://members.iinet.net.au/~herman546/p17.html#help_on_partitioning](http://members.iinet.net.au/~herman546/p17.html#help_on_partitioning)

---

### Post by kblair on 2009-10-16
So after the new installation I have the same problem still.
 
Using grub, if I choose Ubuntu it loads fine. If I choose Vista, it reboots the computer.
 
Using the windows recovery to allow me to get back into windows, I then configure EasyBCD and add the menu.lst entries to the NeoGrub add.. this lets me boot to windows and see NeoGrub as a chioce. I choose the NeoGrub option and again, get Error 17..
 
Booting 'Ubuntu 9.04, kernel 2.6.28-11-generic'
 
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=af477790-25a5-41df-9015-5b7037e30411 ro quiet splash
 
Error 17: File not found

---

### Post by phillw on 2009-10-16
i'm sorry I could not help :-(

Hopefully, as the  Tech guys come on, they can shed some light on it - It's the 1st time I've known that set of instructions not to work - So, I will keep an eye on this thread

Phill.

---

### Post by oldfred on 2009-10-16
What is your drive configuration? Are you running raid since I see SCSI?
Normal Sata drives are (x,y) not (0,0,0)?

The partition tables of the following devices are changed:
SCSI3 (0,0,0) (sda)

---

### Post by Zimmer on 2009-10-16
SCSI or no SCSI, I still reckon you have installed GRUB to the MBR...
> Installing GRUB to MBR:
'setup (hd0)' is the command to install Grub's stage1 to MBR in the first hard disk.
Stage1_5 will also be installed to the 15 sectors following the MBR in the first track of the hard disk.
Installing GRUB to a partition: 
To install GRUB to a partition, you would use a command like, 'setup (hd0,1), or 'setup (hd0,3)', where (hd0,1) and (hd0,3) are Linux partitions. If you do that, you'll be able to boot your operating system using the 'chainloader' command.

---

### Post by kblair on 2009-10-16
No SCSI drives and no RAID configured. I believe there's 3 SATA drives and 1 eIDE in this box. Why Ubuntu believes or calls anything SCSI3 I have no idea.

Abit AB9 Pro MB and e6600 chip, 4 gb memory, etc..

Funny nobody mentions how odd it is that the computer resets when I choose Windows from the grub menu. :P

---

### Post by phillw on 2009-10-16
Ahh.... now I'm on a different track ... let me see how far I get down it

This is puzzling me

Phill.

---

### Post by phillw on 2009-10-16
Is this thread any where near what you're looking for ?


[http://ubuntuforums.org/showthread.php?t=1277789](http://ubuntuforums.org/showthread.php?t=1277789)

Phill.

---

### Post by kblair on 2009-10-16
So I wiped out all partitions on the drive minus the main windows one. Then I went and installed ubuntu on a primary partition that I made after the windows primary partition. Created the swap partition, left the rest of the disk unpartitioned for the moment.
 
Same all around results.
 
It's getting silly at this point.

---

### Post by oldfred on 2009-10-16
We are guessing what your entire system configuration is please post the results of this script that documents your system and how it is configured to boot.

Boot Info Script 0.32 courtesy of forum member meierfra
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
Instructions
[http://ubuntuforums.org/showpost.php?p=6725571&postcount=3](http://ubuntuforums.org/showpost.php?p=6725571&postcount=3)
cd to directory saved to:
chmod 755 boot_info_script032.sh
sudo ./boot_info_script032.sh
or  as example if on desktop
sudo bash ~/Desktop/boot_info_script*.sh
This will create a RESULTS.txt file in the same directory. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by kblair on 2009-10-17
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /NST/menu.lst /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /grldr

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda2 and 
                       looks at sector 124824178 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #2 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /menu.lst

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa05ca05c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   102,591,089   102,591,027   7 HPFS/NTFS
/dev/sda2         102,591,090   161,180,144    58,589,055  83 Linux
/dev/sda3         161,180,145   165,083,939     3,903,795   5 Extended
/dev/sda5         161,180,208   165,083,939     3,903,732  82 Linux swap / Solaris
/dev/sda4         165,085,184   976,769,023   811,683,840   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xec3b975c

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   976,768,064   976,768,002   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf37a6e81

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   976,768,064   976,768,002   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb7458fd7

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63   586,067,264   586,067,202   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="40CC47E8CC47D6B6" TYPE="ntfs" 
/dev/sda2: UUID="8223483e-db4c-48ba-88d7-ce537fdc2be0" TYPE="ext3" 
/dev/sda4: UUID="E8142D03142CD5FA" TYPE="ntfs" 
/dev/sda5: UUID="ea888376-18bf-463f-9999-215028c3c0cb" TYPE="swap" 
/dev/sdb1: UUID="18C0E6D0C0E6B2E4" TYPE="ntfs" 
/dev/sdc1: UUID="FA9429189428D941" TYPE="ntfs" 
/dev/sdd1: UUID="A820498520495C06" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/kblair/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=kblair)
/dev/sdd1 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


============================== sda1/NST/menu.lst: ==============================

# NeoSmart NeoGrub Bootloader Configuration File 
# 
# This is the NeoGrub configuration file, and should be located at C:\NST\menu.lst 
# Please see the EasyBCD Documentation for information on how to create/modify entries: 
# http://neosmart.net/wiki/display/EBCD 
 
title        Ubuntu 9.04, kernel 2.6.28-11-generic 
uuid        8223483e-db4c-48ba-88d7-ce537fdc2be0 
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=8223483e-db4c-48ba-88d7-ce537fdc2be0 ro quiet splash  
initrd        /boot/initrd.img-2.6.28-11-generic 
quiet 
 
title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) 
uuid        8223483e-db4c-48ba-88d7-ce537fdc2be0 
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=8223483e-db4c-48ba-88d7-ce537fdc2be0 ro  single 
initrd        /boot/initrd.img-2.6.28-11-generic 
 
title        Ubuntu 9.04, memtest86+ 
uuid        8223483e-db4c-48ba-88d7-ce537fdc2be0 
kernel        /boot/memtest86+.bin 
quiet 

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
# kopt=root=UUID=8223483e-db4c-48ba-88d7-ce537fdc2be0 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=8223483e-db4c-48ba-88d7-ce537fdc2be0

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        8223483e-db4c-48ba-88d7-ce537fdc2be0
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=8223483e-db4c-48ba-88d7-ce537fdc2be0 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        8223483e-db4c-48ba-88d7-ce537fdc2be0
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=8223483e-db4c-48ba-88d7-ce537fdc2be0 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        8223483e-db4c-48ba-88d7-ce537fdc2be0
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=8223483e-db4c-48ba-88d7-ce537fdc2be0 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ea888376-18bf-463f-9999-215028c3c0cb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


  63.9GB: boot/grub/menu.lst
  63.9GB: boot/grub/stage2
  63.7GB: boot/initrd.img-2.6.28-11-generic
  63.7GB: boot/vmlinuz-2.6.28-11-generic
  63.7GB: initrd.img
  63.7GB: vmlinuz

================================ sdd1/menu.lst: ================================

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        aba1882c-50cc-424e-bea7-5319c49d1c33
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=aba1882c-50cc-424e-bea7-5319c49d1c33 ro xforcevesa quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        aba1882c-50cc-424e-bea7-5319c49d1c33
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=aba1882c-50cc-424e-bea7-5319c49d1c33 ro xforcevesa  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        aba1882c-50cc-424e-bea7-5319c49d1c33
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=aba1882c-50cc-424e-bea7-5319c49d1c33 ro xforcevesa quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        aba1882c-50cc-424e-bea7-5319c49d1c33
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=aba1882c-50cc-424e-bea7-5319c49d1c33 ro xforcevesa  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        aba1882c-50cc-424e-bea7-5319c49d1c33
kernel        /boot/memtest86+.bin
quiet


=================== sdd1: Location of files loaded by Grub: ===================


  42.9GB: menu.lst

```

---

### Post by oldfred on 2009-10-17
I do not see anything wrong with your system? I do not know neogrub, does it give you choices for going to Ubuntu, but not windows?

I have heard of the makeactive line causing issues with Vista boots. As long as the Vista partition is flagged as boot which it is, the makeactive command is not required, but should not cause a problem. Try deleting it just to see.

If you were not able to boot Vista I would say there was some issue with the Vista loader that is in the Vista partition (PBR not MBR). Grub has to link to the Vista partition loader to boot as it does with any chainboot. It knows nothing about windows and does not really know NTFS, it just redirects booting to the windows partition PBR. When you put Vista in the MBR it should be doing the same thing. It links to the  same PBR loader in the partition which then reads the actual files. 

Someone else may see something that I do not see.

---

### Post by kblair on 2009-10-17
> **oldfred said:**
> I do not see anything wrong with your system? I do not know neogrub, does it give you choices for going to Ubuntu, but not windows?

I have heard of the makeactive line causing issues with Vista boots. As long as the Vista partition is flagged as boot which it is, the makeactive command is not required, but should not cause a problem. Try deleting it just to see.

If you were not able to boot Vista I would say there was some issue with the Vista loader that is in the Vista partition (PBR not MBR). Grub has to link to the Vista partition loader to boot as it does with any chainboot. It knows nothing about windows and does not really know NTFS, it just redirects booting to the windows partition PBR. When you put Vista in the MBR it should be doing the same thing. It links to the  same PBR loader in the partition which then reads the actual files. 

Well, I'm not able to boot Vista when using Grub. As I've mentioned, it restarts my computer completely when choosing Vista from the grub menu. The ONLY way I can boot back into Windows is by repairing the mbr with the recovery disk.

NeoGrub is just EasyBCD's thing for putting you into Grub while using windows mbr. That gets me to grub just fine. It's just once I'm at grub and choose to boot Ubuntu, I get the error 17 problem. (I'm using the menu.lst from Ubuntu in NeoGrub - so it matches).

I'll try removing the makeactive thing and seeing if my computer still resets when choosing windows from grub.

---

### Post by oldfred on 2009-10-17
I always have prefered grub, but in your case i don not know. I understand that the UUID is something Ubuntu did as an upgrade to grub to avoid the issue of hd & partitions getting renumbered. Does Neogrub support UUID or do you need to modify the neogrub entries to the older style root (hd0,1) style like my very old entry with your version (please check if correct):

title        Ubuntu 9.04, kernel 2.6.28-11-generic
[COLOR=DarkRed]root        (hd0,1)[/COLOR]
kernel       /boot/vmlinuz-2.6.28-11-generic[COLOR=DarkRed] root=/dev/sda2[/COLOR] ro quiet splash
initrd        /boot/initrd.img-2.6.28-11-generic
quiet
savedefault
boot


Your also have grub in your PBR partition boot record so you should be able to chainboot with an entry like this:

title       Ubuntu 9.04 Jaunty 32 bit @ sda2
root        (hd0,1)
chainloader +1

I would add both of these style enties and see if either works.

---

### Post by Zimmer on 2009-10-17
According to the info you posted above you still have GRUB installed in the MBR of sda. Fortunately you have also loaded it to the Ubuntu partition.

I believe you will need to use EasyBCD (if you can boot to VISTA) 
to reinstall the Vista bootloader (Write MBR) 
see the screenshots @ halfway down the page... (do not read too much of the other stuff it may add to confusion..)

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=4](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=4)

Use EasyBCD to Uninstall NEoGrub (if it still installed.)

Then choose the ADD/Remove entries  button . Choose the Linux tab and a list of your partitons will be in a drop down list. Select the Ubuntu partition. Give it a name in the box below (Ubuntu looks good ;)  )
Add it.....

What should happen on restart..
The Windows Boot Manager in glorious monochrome will /should display a Vista option and an Ubuntu option.
Selecting the Ubuntu option should take you to GRUB on the Ubuntu partition with all the options from your GRUB menu.lst file.
The first option should be the latest of the kernels... select... Ubuntu ..

A bit of reference reading...
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

---

### Post by kblair on 2009-10-18
> **oldfred said:**
> Your also have grub in your PBR partition boot record so you should be able to chainboot with an entry like this:

title       Ubuntu 9.04 Jaunty 32 bit @ sda2
root        (hd0,1)
chainloader +1

THIS worked. (The suggestion just above it did not.) Using the windows recovery disk to get back into windows, then using EasyBCD to install NeoGrub and making the above be the ONLY entry in the menu.lst it boots up and let's me choose successfully..

Thank you!

PS: I'd try your second suggestion, but I'm afraid I'd end up breaking it again and then not getting it to work..

PSS: Someone with ability should change the subject line to say Error 17 instead of 22. That was a mistake on my part. Correct subject would help googlers..

---

### Post by Zimmer on 2009-10-18
> PSS: Someone with ability should change the subject line to say Error 17 instead of 22. That was a mistake on my part. Correct subject would help googlers..
That's you, the OP.
Look under  Thread Tools.. Glad you are sorted.
BTW, I have been dual booting Vista and Ubuntu for over 12 months using the method I outlined, but I am a great advocate of 'if it aint broke, don't fix it(until you have to ) '  :)

---

### Post by kblair on 2009-10-18
I don't see any options to change the original subject title unfortunately. Just the subject titles of replies.

---

### Post by phillw on 2009-10-18
> THIS worked. (The suggestion just above it did not.) Using the windows recovery disk to get back into windows, then using EasyBCD to install NeoGrub and making the above be the ONLY entry in the menu.lst it boots up and let's me choose successfully..

Thank you!


I'm really glad it was resolved, as I initially said ... patience is a virtue & some one will have an answer for you.

Like several others, I've had no problem with my vista / ubuntu installation - It just 'works out of the box' 

Now, you can get down to enjoying ubuntu, and teaching it to go 'tip-toe' over your vista partitions to be able to access any data on them.

Regards,

Phill.

---

### Post by phillw on 2009-10-18
> I don't see any options to change the original subject title unfortunately. Just the subject titles of replies.


from memory, you need to go into edit mode, then go to 'advanced' - you can then both correct the error number ans add [SOLVED] at the start of it.

Phill.

---

