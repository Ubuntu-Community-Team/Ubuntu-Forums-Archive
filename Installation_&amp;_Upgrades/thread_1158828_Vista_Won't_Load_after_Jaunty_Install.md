---
title: "Vista Won't Load after Jaunty Install"
date: 2009-05-14
forum: Installation &amp; Upgrades
---

### Post by madestro on 2009-05-14
Hi all. I tried to install Ubuntu 9.04 today and even though the install went perfect it messed up my Vista loader (I think), now I have used Super Grub to reload the Vista boot loader but that didn't work. I also tried the Vista Installation DVD but it cannot find the Vista installation on this drive.
Once I got into Ubuntu (after using Super Grub again) I can mount and unmount the windows partition and see all the files in it.
What I need now is a way to fix my Vista MBR or boot or whatever got screwed up so I can log back into my Vista partition as well as I log into Ubuntu. 
I haave tried the bootrec /fixmbr and /rebuilbcd but that hasn't worked either. The Vista startup gets to a point where it tells me the previous startup didn't work and choose but it won't let me into either of the safe modes or even the last known good configuration.
So to summarize I log in fine into Ubuntu and even have access to all my NTFS partitions but my main Vista partition won't boot at all.
Any help for this newbie will be gladly appreciated ):P
Thanks in advance :D

---

### Post by lisati on 2009-05-14
Some of the gurus might find the output of the following helpful:
```
sudo fdisk -l
```
(That's a little "ell", not a number one)

---

### Post by Gidskid on 2009-05-14
Is that such a bad thing?

---

### Post by moster on 2009-05-14
Do you maybe have two hard disks?

---

### Post by madestro on 2009-05-14
*@lisati* Here's my fdisk

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc1d800be

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       25942   208379083+   7  HPFS/NTFS
/dev/sda3           25943       72585   374659897+   f  W95 Ext'd (LBA)
/dev/sda4           77810       77825      128520   82  Linux swap / Solaris
/dev/sda5           25943       51468   205037563+   7  HPFS/NTFS
/dev/sda6           57184       72585   123716533+   7  HPFS/NTFS
/dev/sda7           51469       57183    45905706   83  Linux

Partition table entries are not in disk order

*@gidskid* well I do need vista right now since I haven't migrated fully to ubuntu plus I just love my wintendo and wine can't load the games I play on vista.
*@moster* no I only have one hard drive but do you think it will be better to install vista in one drive then have another one for ubuntu ??
**And thank you all for replying and for taking the time to read my post.**
What I want to avoid at all costs is to erase my vista partition, what worries me though is the part that says "Partition table entries are not in disk order" maybe that is why vista won't load up ?

---

### Post by rhmeyer50 on 2009-05-14
I just went through this with another distro, obviously Ubuntu is next. EasyBCD 1.7.2, free down load, will restore your Vista boot loader literally with one click, after selecting the correct menu item of course. However you will have to redo the boot loader to dual boot. Please read the instructions for easy BCD, it takes you through several levels of boot loader repairs. HTH
Best,
Rob

---

### Post by madestro on 2009-05-14
> **rhmeyer50 said:**
> I just went through this with another distro, obviously Ubuntu is next. EasyBCD 1.7.2, free down load, will restore your Vista boot loader literally with one click, after selecting the correct menu item of course. However you will have to redo the boot loader to dual boot. Please read the instructions for easy BCD, it takes you through several levels of boot loader repairs. HTH
Best,
Rob
The problem is that I can not get into the vista partition so how am I going to be able to install this EasyBCD ? Can I create a bootable cd like Super Grub ? Because I only see an exe on the download page.
Seems like an awesome tool wish I knew of it before installing Ubuntu.
Thanks for your reply though.

---

### Post by madestro on 2009-05-14
After some digging around on the forums I found this post [http://ubuntuforums.org/showthread.php?t=1033152&highlight=vista+boot]("http://ubuntuforums.org/showthread.php?t=1033152&highlight=vista+boot") where there's a similar problem to my own post so I followed and the script gave me this output
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
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

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc1d800be

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   416,758,229   416,758,167   7 HPFS/NTFS
/dev/sda3         416,758,230 1,166,078,024   749,319,795   f W95 Ext d (LBA)
/dev/sda5         416,758,293   826,833,419   410,075,127   7 HPFS/NTFS
/dev/sda6         918,644,958 1,166,078,024   247,433,067   7 HPFS/NTFS
/dev/sda7         826,833,483   918,644,894    91,811,412  83 Linux
/dev/sda4       1,250,001,585 1,250,258,624       257,040  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="54CE2DE1CE2DBBDC" TYPE="ntfs" 
/dev/sda4: UUID="c42d18f7-898f-4f6a-8e59-24bb01d879cf" TYPE="swap" 
/dev/sda5: UUID="01C9AB49D652E950" LABEL="Downloads" TYPE="ntfs" 
/dev/sda6: UUID="01C9AB49D73C37E0" LABEL="Multimedia" TYPE="ntfs" 
/dev/sda7: UUID="4dfd024f-341e-4e71-ab5b-c5a9d56ad761" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda7 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/jsn/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jsn)
/dev/sr0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=jsn)
/dev/sda1 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5 on /media/Downloads type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

=========================== sda7/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=4dfd024f-341e-4e71-ab5b-c5a9d56ad761 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=4dfd024f-341e-4e71-ab5b-c5a9d56ad761

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
```

I did use my Vista DVD to try to restore the mbr and now I can get as far as the little loading screen from Vista but after a few seconds the PC reboots, I'm assuming there has to be something corrupted IN the vista filesystem itself and that is why I can go no further. Is there any way to repair the Vista filesystem from a working Ubuntu partition on the same HD ?

---

### Post by moster on 2009-05-15
> **madestro said:**
> 
*@moster* no I only have one hard drive but do you think it will be better to install vista in one drive then have another one for ubuntu ??


I am sorry, I cannot help you :(   May I just suggest that if you again do your repartition and stuff like that, maybe you want to make it more simple. And if you have to have another OS you have it in in some of virtual machine like VirtualBox. 
     I have 1 disk for ubuntu and 1 disk for windows. I just think that having 2 separate disk there is less chance that something bad can happend. In meaning of mess with boot and similar stuff...
    Hope you will resolve this problem of yours :)

---

### Post by Sef on 2009-05-15
Have you tried [Super GRUB Disk]("http://www.supergrubdisk.org/")?

---

### Post by madestro on 2009-05-15
> **Sef said:**
> Have you tried [Super GRUB Disk]("http://www.supergrubdisk.org/")?
Yeah I did use Super Grub at first because when I installed Ubuntu at first and then trying to repair vista, the vista dvd wrote over Ubuntu's grub so Super Grub helped me get the Ubuntu partition up and running again but I think the problem is somewhere "inside" the vista partition since I get to the loading part of vista but I can't go further than that
Thanks anyway for trying to help.

---

