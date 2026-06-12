---
title: "ntfs problem after reinstall on vista dual boot machine"
date: 2009-05-10
forum: Installation &amp; Upgrades
---

### Post by DrGNU on 2009-05-10
GOOD EXAMPLE OF PEARL:
ALWAYS BACK UP YOUR FILES BEFORE DOING ANY PARTITION CHANGES!


Helping try to convert my parents computer use from Vista to GNU/Linux.

Background:
New HP Pavillion computer came with Vista, convinced my father to install Ubuntu. He naturally chose an Ubuntu for 64bit computer that unfortunately was buggy and turned him off. So he returned to using his Vista computer with it's inherent flaws.

I managed to convince him to try GNU/Linux again and to install a 32-bit version in place of the 64bit.  We should have done our homework first and backed up his Vista files once more!

In the partition editor he removed the old Ubuntu partitions to make the drive appear to have unallocated space.
The gparted told him he had 2 NTFS partitions one about 146 GiB with his active VISTA install and a second about 9 GiB with his factory restore partition (for VISTA).

We chose to install gNewSense 2.2 (built from Ubuntu).
During the installation he selected to use his hard drive and use the unused space (thinking the older partitions would now be overwritten) and that the GRUB would create a new boot-loader to enable booting into the new gNewSense and/or the VISTA or VISTA restore.

The installation got most of the way through but then had errors at the end saying something was wrong with the CDROM or the HDD.
I don't know what the errors were exactly because I was talking to my father by telephone when this happened and not physically present.

We were able to see the Vista partition using the Live CD... 
MISTAKE 1 AGAIN: ALWAYS BACK-UP YOUR FILES!!!

We burned a new gNewSense cdrom, and cleared the partitions again (or so I thought they did).  Tried to install once more the same way and had the same error and failure. 

The partitions went from the 2 ntfs to like 8 (with the linux ones added).

We deleted the extra partitions using gparted... 

The computer could not boot into anything including VISTA saying things about the boot loader etc and NTFS signature being bad or missing.

Searcing the net we found SUPER GRUB and tried to use that program to fix the boot so we could get into Windows.  Even when it said successful we ran into problems with Vista suggesting we use the Vista start-up disk.  My father only has restore disks.

He tried to repair the boot using this disk as well.
No success.

Now the partition with the Vista installed isn't even recognized as NTFS by gparted the system does not want to boot but wants to reinstall Vista instead.

We do not want to erase Vista yet... there are files (atleast one) that apparently had not been backed up on this computer before this installation process was begun.  We just want to be able to mount (force mount does not work due to not seeing the ntfs and signature problems).  We need to access the Vista filesystem to retrieve important files (back them up).

Ideally if we could be able to boot to Vista again that would be great... but may not be possible.

Anyhow here is the fdisk results at this point:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   286085519   143042728+   7  HPFS/NTFS
/dev/sda2   *   958212990   976768064     9277537+   c  W95 FAT32 (LBA)
/dev/sda3       286085520   958212989   336063735    5  Extended
/dev/sda5       286085583   937681919   325798168+  83  Linux
/dev/sda6       937681983   958212989    10265503+  82  Linux swap / Solaris

Partition table entries are not in disk order
```

The following is a USB drive plugged in under the Live CD GNU/Linux to permit output of terminal results to files for sharing with me (I'm in another city and doing this via telephone, chats, and e-mails).

```

Disk /dev/sdb: 4016 MB, 4016045568 bytes
255 heads, 63 sectors/track, 488 cylinders, total 7843839 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              38     7839719     3919841    b  W95 FAT32
```

I appreciate any help with diagnosing the problems we are having.

GOAL 1: Get access to the Vista files to retrieve any files not backed-up

GOAL 2: Make this computer dual boot with:
Vista
GNU/Linux

Right now I am having my parents install gNewSense to a USB HDD so they can work from that to communicate with me on the computer, diagnose the problem, fix the partitions, and drill down into the NTFS Vista partition to get their files again.
I need some help form the forum wizards to do that.

I'm thinking of having them wipe the entire HDD, (after they get their Vista files that are at high risk of loss right now) to then reinstall Vista fresh on the HDD.  

Should I then have them add GNU/Linux to the available space on that HDD, add another HDD internally for GNU/Linux, or just continue to use the external USB HDD with GNU/Linux.

I am not sure how the GRUB is going to do this so I'll need help with manipulating GRUB for whichever of these we end up doing once the files are recovered.

I think I have them convinced to move to GNU/Linux but I am at risk of losing files they were supposed to have backed-up but did not do so recently.  

Another thing that may be useful... I'd appreciate any links on this:  since I am out of town trying to help them remotely... what is the best way (if it is possible) to get remote access to their GNU/Linux desktop over the internet to help them?

Thank you,

DrGNU (Steve)

---

### Post by cariboo on 2009-05-10
Does it make sense to install this version? If you heed restricted drivers for any of the devices, you would be just as well off instaling a regular version of Ubuntu.

I would suggest using the LiveCD to copy any needed files to the usb device then reinstall Vista, the next time you visit your parents you can install Ubuntu yourself and not run into these problems.

---

### Post by DrGNU on 2009-05-12
> **cariboo907 said:**
> Does it make sense to install this version? If you heed restricted drivers for any of the devices, you would be just as well off instaling a regular version of Ubuntu.

I would suggest using the LiveCD to copy any needed files to the usb device then reinstall Vista, the next time you visit your parents you can install Ubuntu yourself and not run into these problems.

**Thank you for your reply.**
Your advice sounds reasonable for future consideration but unfortunately does not address the problems at hand.
 
> RE: gNewSense vs. Ubuntu if I had a concern about restricted drivers for devices then yes Ubuntu would be a better choice, but I philosophically and ethically do not endorse the use of any end-user restrictive software so I will only use and encourage use of completely Free Software GNU/Linux distributions and Free Software (e.g., GNU Public Licensed or compatible). Fortunately, hardware device restrictions is not a relevant issue to my current dilemma.

**Let me summarize since my post was too long:**
> The LiveCD is NOT able to view the files because of something that got broken during the attempted installation.  


**UPDATE:**
> Since my post we successfully installed gNewSense to an external USB HDD that runs well on my parent's computer.  

We are STILL NOT able to view and/or mount the internal HDD partition that contains Vista to access the files we would like to recover.

**fdisk output:**
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   286085519   143042728+   7  HPFS/NTFS
/dev/sda2   *   958212990   976768064     9277537+   c  W95 FAT32 (LBA)
/dev/sda3       286085520   958212989   336063735    5  Extended
/dev/sda5       286085583   937681919   325798168+  83  Linux
/dev/sda6       937681983   958212989    10265503+  82  Linux swap / Solaris

Partition table entries are not in disk order
```
> I note that the above fdisk output for some reason shows the sda2 partition (the Vista restore partition) as the "boot" partition if I am reading this output correctly.  I think the Vista repair CD must have made this change because I know I did not direct my parents to do make this change in gparted.


**GOALS:**
> I believe it is possible to use the CLI in GNU/Linux to further diagnose and fix whatever may be wrong with the internal HDD partitions and ultimately permit me to mount or force mount the Vista partition to recover the "at-risk" files.

Once the files are recovered... then the machine can be turned into a dual boot or straight GNU/Linux machine with whatever flavor(s)/distribution(s) we may desire.  


**gNewSense Is Ubuntu**
> I like Ubuntu, that is why I use and recommend gNewSense.
gNewSense IS Ubuntu - but it has been stripped of proprietary blobs of code, drivers and software.  

If something doesn't work because it has a restricted driver then we have several options:
1) Use restricted drivers (which is pragmatic enough I suppose)
2) Encourage the manufacturer to make their drivers Free (recommended but may be a frustrating and fruitless process)
3) Remove the offensive hardware and support manufacturers who already support end user freedom and GNU/Linux instead (highly recommended to the extent that such information is available to end users and people purchasing their hardware).


***An aside on choosing to support Freedom:***> 
Supporting end user freedom (Free Software) sometimes requires asking the right questions and accepting temporal inconveniences and sacrifices until more information and skills are learned and mastered.  The nice thing is that such journeys do not have to occur alone thanks to sites such as the Ubuntu forums.

This is an important decision node... what operating system to use and why it may be important.  There are ethical and philosophical differences with many camps of users of various opinions.  I mean no offense to any of them we share this journey together and are better for it than if we do it alone.

It is up to individual users to determine the choice that they will make.  My parents and I have made ours - we want to do our best to support our own and other individual's freedom and view supporting Free Software as being for us the best choice and most congruent with our own individual ethics and philosophies to the best that we can articulate them.  

Others may not share this same conviction and might coerce us into using proprietary and restrictive tools such as Microsoft Windows operating systems, Apple Macintosh operating systems... and related software tools that are not licensed to permit them to be Free Software. Many people do not know the difference and often act pragmatically taking the fastest and easiest short-cuts for their own convenience.  We've been down that road long enough and are looking forward to trying a "GNU" one.

I appreciate any and all help from our community.
I also do appreciate any comments on what I have apparently done wrong along the way. 
Hopefully learning from mistakes can help not only me but also others.

Best regards,

**DrGNU**
[http://drgnu.org](http://drgnu.org)
[http://identi.ca/drgnu/all](http://identi.ca/drgnu/all)

[I]Steven C. Morreale, M.D./M.P.H.
Free Software Foundation Member #6887
GNUPG PKI: [https://biglumber.com/x/web?pk=9C2E7C77D332B59E4403B2CE012F5DC71036DFBA;qh=599](https://biglumber.com/x/web?pk=9C2E7C77D332B59E4403B2CE012F5DC71036DFBA;qh=599)[/I]

---

### Post by Mark Phelps on 2009-05-13
Since you don't have a Vista DVD, you can go to the NeoSmart forums and use torrent to download a Vista Recovery CD.  Once you burn that and boot from it, you can go into Startup Repair and try to fix the Vista boot.

Suggest you check the NeoSmart forums about the details.  They deal with this kind of stuff every day.

---

### Post by DrGNU on 2009-05-13
> **Mark Phelps said:**
> Since you don't have a Vista DVD, you can go to the NeoSmart forums and use torrent to download a Vista Recovery CD.  Once you burn that and boot from it, you can go into Startup Repair and try to fix the Vista boot.

Suggest you check the NeoSmart forums about the details.  They deal with this kind of stuff every day.

Perhaps my first post was confusing?
Also I do not know what the difference is between a Vista DVD and a Recovery CD.  My parents DO have a "recovery cd" but I do not think they have any official Vista DVD (i.e. "install disc).

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download)
[http://www.ehow.com/how-does_4619396_vista-recovery-disk-work.html](http://www.ehow.com/how-does_4619396_vista-recovery-disk-work.html)

When we tried to use the Vista Recovery CD it was not successful with fixing and rebooting the computer.  I think it also marked the restore partition (sda2) as the "boot" mount to trigger reinstallation of Vista instead of fixing the MBR to point to sda1.  The last time we checked with gparted the sda1 had an "unknown filesystem" but in fdisk it shows the NTFS.

Are there terminal commands to figure out the paritions and to reassign them properly again?
What commands &/or programs are recommended to fix the MBR?  
We tried super grub with no luck.  I suspect that the partition settings are where the problem originates?

I think we should have defragmented the HDD before attempting the installation (gnewsense) that failed due to some issue with the HDD - which left us in this current state.

We are now able to run gNewSense from an external USB HDD to work on repairing and force-mounting the sda1 partition to recover files as needed.  We just can't mount that partition yet.

How does one try to force-mount a partition?

Thank you,

DrGNU

---

### Post by Mark Phelps on 2009-05-13
The differences between the Vista media are as follows:
1) Vista DVD -- retail or OEM DVD that can be used to install Vista from scratch.  Also has option to do repairs.
2) Recovery CD -- media either supplied by an OEM, or burned from an OEM-installed machine, that is used to completely restore the machine's Vista OS to its original form, not to repair a broken installation.  However, may include a repair option if the OEM included that on the CD.
3) Repair CD -- A Windows Recovery Environment CD that can be used to repair and restore a Vista OS (restore using System Restore only).  Can not be used to install or reinstall a Vista OS.

Also, if you are able to force-mount an NTFS partition, it's  likely that will corrupt the filesystem in the process -- which is why that is NOT the default option.

---

### Post by DrGNU on 2009-05-13
> **Mark Phelps said:**
> The differences between the Vista media are as follows:
1) Vista DVD -- retail or OEM DVD that can be used to install Vista from scratch.  Also has option to do repairs.
2) Recovery CD -- media either supplied by an OEM, or burned from an OEM-installed machine, that is used to completely restore the machine's Vista OS to its original form, not to repair a broken installation.  However, may include a repair option if the OEM included that on the CD.
3) Repair CD -- A Windows Recovery Environment CD that can be used to repair and restore a Vista OS (restore using System Restore only).  Can not be used to install or reinstall a Vista OS.

Thank you!  The machine did not come with any CD's however they paid for recovery CDs sent from the OEM (Hewlett Packard) which they have tried to use to repair the machine but did not execute any commands from those CDs.  Today they talked to the OEM HP by phone who recommended "taking out the HDD and connecting it to another computer to access the files, backing up the files they want to save, and then reinstalling the HDD back onto their machine to run the OEM's recovery CD to reinstall Vista."

Running the OEM's recovery CD will only erase and reinstall Vista to the factory OEM default set-up and will NOT recover any files.  

Thanks to GNU/Linux installed onto an external USB HDD that is running on their machine they do not need to remove the HDD in order to work on accessing their Vista partition to recover their files.  This is where we need help from those experienced with GNU/Linux and accessing (broken and/or inaccessible) partitions that are not recognized by LiveCDs or GNU/Linux without more advanced CLI/Terminal methods being employed.

> **Mark Phelps said:**
> Also, if you are able to force-mount an NTFS partition, it's  likely that will corrupt the filesystem in the process -- which is why that is NOT the default option.

Very important to know! Thank you!  We will not attempt to force-mount the NTFS partition again.

I'll search around the forums again, I know I saw some threads about using fdisk and other commands to help figure out problems with broken partitions, NTFS problems, and Vista.  

Does anyone reading this know What methods we should try to make the dev/sda1 (Vista) accessible again in order to retrieve the files stored there before we end up erasing the HDD?

We are NOT able to see this partition from GNU/Linux in order to mount it at this time.  What can we do to change this?

Thank you,

DrGNU (Steve)

---

### Post by DrGNU on 2009-05-13
> **DrGNU said:**
> 
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   286085519   143042728+   7  HPFS/NTFS
/dev/sda2   *   958212990   976768064     9277537+   c  W95 FAT32 (LBA)
/dev/sda3       286085520   958212989   336063735    5  Extended
/dev/sda5       286085583   937681919   325798168+  83  Linux
/dev/sda6       937681983   958212989    10265503+  82  Linux swap / Solaris

Partition table entries are not in disk order
```

The above was our fdisk output.
I'll look around for more information on the forums for what else can be tried to figure this out.

Any links are appreciated.
The * appears to indicate that somehow the /dev/sda2 (the recovery partition for Vista) has been tagged to be the boot mount point.  I am unsure if gparted or some other tool can change this successfully.  

The /dev/sda1 is the prior Vista where there are files we want to access.  This partition is currently NOT mountable for some reason.  The last time I had my parents check gparted was not identifying the filesystem type (it should be NTFS as fdisk has identified).

Thank you,

DrGNU (Steve)

---

### Post by DrGNU on 2009-05-13
> **DrGNU said:**
> Any links are appreciated.
**Search Terms:** *"ntfs fdisk vista partitions file recovery"*
**Found the following:**
*I was most impressed by the posts by user "**caljohnsmith**"*
[http://ubuntuforums.org/member.php?u=530779](http://ubuntuforums.org/member.php?u=530779)
[http://ubuntuforums.org/showpost.php?p=5660697&postcount=5](http://ubuntuforums.org/showpost.php?p=5660697&postcount=5)
[http://ubuntuforums.org/showpost.php?p=6510347&postcount=6](http://ubuntuforums.org/showpost.php?p=6510347&postcount=6)
[http://ubuntuforums.org/showpost.php?p=6511714&postcount=8](http://ubuntuforums.org/showpost.php?p=6511714&postcount=8)
[http://ubuntuforums.org/showpost.php?p=5876696&postcount=4](http://ubuntuforums.org/showpost.php?p=5876696&postcount=4)
[http://ubuntuforums.org/showpost.php?p=5889403&postcount=21](http://ubuntuforums.org/showpost.php?p=5889403&postcount=21)

We will try some of these diagnostics.
We will post the outputs to try to problem solve our HDD issues.

I noted that ***caljohnsmith*** mentioned in one of the above threads that **gparted** will mess up Vista partition tables and this is likely exactly what happened.

I look forward to working through this, learning and documenting the process along the way, so we can also help others.

~DrGNU (Steve)

---

### Post by DrGNU on 2009-05-14
Running caljohnsmith's posted script from here:
[http://ubuntuforums.org/showpost.php?p=6510347&postcount=6](http://ubuntuforums.org/showpost.php?p=6510347&postcount=6)

We got this RESULTS.txt:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No known boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  gNewSense deltah
    Boot files/dirs:   /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  gNewSense deltah
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1549f232

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   286,085,519   286,085,457   7 HPFS/NTFS
/dev/sda2    *    958,212,990   976,768,064    18,555,075   c W95 FAT32 (LBA)
/dev/sda3         286,085,520   958,212,989   672,127,470   5 Extended
/dev/sda5         286,085,583   937,681,919   651,596,337  83 Linux
/dev/sda6         937,681,983   958,212,989    20,531,007  82 Linux swap / Solaris


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0007e287

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   112,326,479   112,326,417  83 Linux
/dev/sdb2         112,326,480   117,210,239     4,883,760   5 Extended
/dev/sdb5         112,326,543   117,210,239     4,883,697  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda2: UUID="2C88743C8874071C" LABEL="FACTORY_IMAGE" TYPE="ntfs" 
/dev/sda5: UUID="394ba38c-e272-44e0-9768-40d5638acc16" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="d12b7741-ffb2-4f2b-aa80-c0778ab7f627" TYPE="swap" 
/dev/sdb1: UUID="d1234a7e-eef4-4723-871d-af544cc11f07" TYPE="ext3" 
/dev/sdb5: UUID="ec0bb3d6-b158-4ff2-a72e-9b3162e62295" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/chuck/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=chuck)

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=394ba38c-e272-44e0-9768-40d5638acc16 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=d12b7741-ffb2-4f2b-aa80-c0778ab7f627 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 398.8GB: boot/initrd.img-2.6.24-23-generic
 398.8GB: boot/initrd.img-2.6.24-23-generic.bak
 398.8GB: boot/vmlinuz-2.6.24-23-generic
 398.8GB: initrd.img
 398.8GB: vmlinuz

=========================== sdb1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=d1234a7e-eef4-4723-871d-af544cc11f07 ro

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

title		gNewSense GNU/Linux 2.2 (deltah), kernel 2.6.24-24-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=d1234a7e-eef4-4723-871d-af544cc11f07 ro quiet splash
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		gNewSense GNU/Linux 2.2 (deltah), kernel 2.6.24-24-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=d1234a7e-eef4-4723-871d-af544cc11f07 ro single
initrd		/boot/initrd.img-2.6.24-24-generic

title		gNewSense GNU/Linux 2.2 (deltah), kernel 2.6.24-23-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=d1234a7e-eef4-4723-871d-af544cc11f07 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		gNewSense GNU/Linux 2.2 (deltah), kernel 2.6.24-23-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=d1234a7e-eef4-4723-871d-af544cc11f07 ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		gNewSense GNU/Linux 2.2 (deltah), memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		gNewSense GNU/Linux 2.2 (deltah) (2.2) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-23-generic root=/dev/sda5 
initrd		/boot/initrd.img-2.6.24-23-generic
savedefault
boot


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=d1234a7e-eef4-4723-871d-af544cc11f07 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=ec0bb3d6-b158-4ff2-a72e-9b3162e62295 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd2       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  46.9GB: boot/grub/menu.lst
  46.9GB: boot/grub/stage2
  46.9GB: boot/initrd.img-2.6.24-23-generic
  46.9GB: boot/initrd.img-2.6.24-23-generic.bak
  46.9GB: boot/initrd.img-2.6.24-24-generic
  46.8GB: boot/initrd.img-2.6.24-24-generic.bak
  46.9GB: boot/vmlinuz-2.6.24-23-generic
  46.9GB: boot/vmlinuz-2.6.24-24-generic
  46.9GB: initrd.img
  46.9GB: initrd.img.old
  46.9GB: vmlinuz
  46.9GB: vmlinuz.old

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdb

00000000  50 29 15 00 00 00 00 00  00 00 00 00 00 00 00 00  |P)..............|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000030  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000070  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000100  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000130  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  87 e2 07 00 00 00 00 01  |................|
000001c0  01 00 83 fe ff ff 3f 00  00 00 11 f7 b1 06 00 fe  |......?.........|
000001d0  ff ff 05 fe ff ff 50 f7  b1 06 30 85 4a 00 00 00  |......P...0.J...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sda1

00000000  b2 0c 0c 70 b9 01 13 01  5b b0 9c bc 01 3b 01 6d  |...p....[....;.m|
00000010  01 39 01 80 01 42 b0 09  b8 01 0d b0 74 b8 01 95  |.9...B......t...|
00000020  40 09 0c 0f 0b df 0c 84  1c 97 68 b8 01 31 b2 0c  |@.........h..1..|
00000030  6d f9 b8 01 5b b1 00 96  2b 00 ff ff 00 00 ff cd  |m...[...+.......|
00000040  04 00 03 cd 00 23 01 c0  01 54 03 44 00 23 01 89  |.....#...T.D.#..|
00000050  00 5c 02 ac 00 23 01 22  00 94 02 b4 00 23 01 b8  |.\...#.".....#..|
00000060  00 a8 02 38 00 23 01 17  01 34 02 b0 00 23 01 10  |...8.#...4...#..|
00000070  01 c4 02 c4 00 23 01 94  00 a4 01 c8 00 23 01 6b  |.....#.......#.k|
00000080  00 f0 01 d0 00 23 01 93  00 f4 01 74 00 23 01 5d  |.....#.....t.#.]|
00000090  01 c8 01 e4 00 23 01 8e  01 c0 01 80 00 23 01 1b  |.....#.......#..|
000000a0  01 24 00 d8 01 03 01 e1  01 1c 00 b4 00 77 b4 0c  |.$...........w..|
000000b0  a5 2b ed 00 b9 01 5a 01  84 b1 f4 0b b8 01 a7 b0  |.+....Z.........|
000000c0  0c b9 01 04 01 8f b3 e1  0c ca 81 b8 01 54 b2 0a  |.............T..|
000000d0  bf bb b8 01 00 b2 28 e8  8c b8 01 23 b0 09 b8 01  |......(....#....|
000000e0  06 b0 88 b8 01 59 b4 09  80 23 94 bb b8 01 31 b2  |.....Y...#....1.|
000000f0  0a b1 7c b8 01 5a 40 0e  0a d7 7b d6 09 e9 6d dd  |..|..Z@...{...m.|
00000100  0d 0e cc a4 b1 6e b8 01  7e b1 0e 0e b8 01 92 b1  |.....n..~.......|
00000110  e8 0c b8 01 36 b0 ac b8  01 4f b2 11 72 f3 b8 01  |....6....O..r...|
00000120  86 b1 00 96 2b 00 ff ff  00 00 ff cd 04 00 03 cd  |....+...........|
00000130  00 23 01 0b 00 e8 03 2c  00 23 01 b2 00 d4 03 0c  |.#.....,.#......|
00000140  00 23 01 93 00 f0 02 a4  00 23 01 93 00 f4 02 48  |.#.......#.....H|
00000150  00 23 01 94 00 f0 01 e4  00 23 01 7a 00 60 02 1c  |.#.......#.z.`..|
00000160  00 23 01 90 00 08 00 bc  00 23 01 29 00 6c 00 d0  |.#.......#.).l..|
00000170  00 23 01 10 02 94 02 50  00 23 01 94 01 b0 01 64  |.#.....P.#.....d|
00000180  00 23 01 05 01 c4 01 8c  01 03 01 bb 01 bc 00 bc  |.#..............|
00000190  00 6e b2 0d e8 2a ba 01  68 01 6e 01 81 b1 0c db  |.n...*..h.n.....|
000001a0  b8 01 84 b1 cb 0c b8 01  3e b0 8f b8 01 5a b0 0c  |........>....Z..|
000001b0  b8 01 2f b3 b0 d6 0d 15  b8 01 90 b4 ef 0b 10 6a  |../............j|
000001c0  25 b8 01 56 b5 0d b5 ab  75 87 71 b9 01 74 01 40  |%..V....u.q..t.@|
000001d0  b0 0c b8 01 24 b0 d3 b8  01 5a b0 0b ba 01 27 01  |....$....Z....'.|
000001e0  0d 01 59 b2 0b 96 e3 b8  01 59 b1 0b 0e b9 01 05  |..Y......Y......|
000001f0  01 2d b1 e3 66 b8 01 78  b5 0a c6 d8 d1 00 95 2b  |.-..f..x.......+|
00000200


=============================== StdErr Messages: ===============================

boot_info_script.txt: line 1043: [: =: unary operator expected
```

Aside from seeing there are problems this is Greek to me.

We appreciate any help.

~DrGNU (Steve)

---

### Post by Mark Phelps on 2009-05-16
> **DrGNU said:**
> Running the OEM's recovery CD will only erase and reinstall Vista to the factory OEM default set-up and will NOT recover any files.  

That's what I suspected.  You can try booting from the first recovery CD and see if it provides you the option of doing a Startup  Repair.  But, I'm guessing it won't.

You can go to the NeoSmart forums and use torrent to download a Windows Vista Recovery CD, which can be used to repair the Vista installation.  You burn that, boot from it, select Startup Repair, run that at least three times, and when done, you should be able to boot into your Vista OS.

---

### Post by DrGNU on 2009-05-16
> **Mark Phelps said:**
> That's what I suspected.  You can try booting from the first recovery CD and see if it provides you the option of doing a Startup  Repair.  But, I'm guessing it won't.

You can go to the NeoSmart forums and use torrent to download a Windows Vista Recovery CD, which can be used to repair the Vista installation.  You burn that, boot from it, select Startup Repair, run that at least three times, and when done, you should be able to boot into your Vista OS.

Thank you Mark!
I'll task my Mom to downloading and burning this Vista Recovery CD right now.

Meanwhile let me post what we are seeing in our gparted.

---

### Post by DrGNU on 2009-05-16
We are downloading the torrent.
I don't have much experience with torrents but this appears to be working.
```
~$ aria2c -o vista-recover.iso -T ~/Documents/downloads/Vista_Recovery_Disc.iso.torrent
```

Note the errors on the gparted partitions sda1 and sda2

---

### Post by DrGNU on 2009-05-16
Is it possible to use this Vista Recovery CD to boot to the command line (recovery console) and do:

```
bootrec /fixboot
```

I guess we will try this: 
```
Windows Key+R
```


Right now I am trying to find out what the "lba" means for the sda2 partition, and considering removing these two flags from this partition.

---

### Post by DrGNU on 2009-05-16
> **DrGNU said:**
> Is it possible to use this Vista Recovery CD to boot to the command line (recovery console) and do:

```
bootrec /fixboot
```

I guess we will try this: 
```
Windows Key+R
```


Right now I am trying to find out what the "lba" means for the sda2 partition, and considering removing these two flags from this partition.

**Definition of: LBA** *(Logical Block Addressing)* 
> A method used to address hard disks by a single sector number rather than by cylinder, head and sector (CHS). LBA was introduced to support ATA/IDE drives as they reached 504MB, and Enhanced BIOSs in the PC translated CHS addressing into LBA addressing. Subsequent ATA specifications raised support to 8.4GB, 128GB and 128PB (petabytes), the latter capacity we hope never to reach on our home PC in many lifetimes.

**I think it is best to just leave that flag alone.**
[http://www.gnu.org/software/parted/manual/html_chapter/parted_3.html](http://www.gnu.org/software/parted/manual/html_chapter/parted_3.html)

[http://www.gnu.org/software/parted/manual/html_chapter/parted_2.html#SEC28](http://www.gnu.org/software/parted/manual/html_chapter/parted_2.html#SEC28)

---

### Post by DrGNU on 2009-05-16
**What I am considering doing next:**

1) remove the "boot" flag on sda2 but leave the "lba" flag
2) add the "boot" flag and the "lba flag" to sda1 (vista partition).

Attempt a mounting of the drive.
If fails...
reboot computer...
probably will fail due to grub being installed for GNU/Linux currently on sba (external usb hdd).

Will re-run the script from my yearlier post and will post the results.

Then if we are in the same predicament, unable to mount the drive... will try the Vista Recovery CD per Mark Phelp's advice (three times) - will try the Windows+R to get to the fix boot commands already mentioned.

**Sound good?**

---

### Post by DrGNU on 2009-05-16
> **DrGNU said:**
> **What I am considering doing next:**

1) remove the "boot" flag on sda2 but leave the "lba" flag
2) add the "boot" flag and the "lba flag" to sda1 (vista partition).

Attempt a mounting of the drive.
If fails...
reboot computer...
probably will fail due to grub being installed for GNU/Linux currently on sba (external usb hdd).

Will re-run the script from my yearlier post and will post the results.

Then if we are in the same predicament, unable to mount the drive... will try the Vista Recovery CD per Mark Phelp's advice (three times) - will try the Windows+R to get to the fix boot commands already mentioned.

**Sound good?**

Hopefully anyone reading along... can chime in on this reasoning. I'm putting this online to share with others, and for my parents to reference... where we are, where we are going, and any other information.

---

### Post by n3tbk on 2009-05-16
Thank you.  Appreciate the help.  We will try your suggestion of changing the boot after we search Ubuntu forums with the following search terms:  boot, gparted, partition and vista.

---

### Post by Mark Phelps on 2009-05-16
You can continue hacking and slashing, hoping that SOMETHING will work ... and most likely destroy any chance at all of recovering your Vista installation ... or you can calm down and do what I suggested:

Burn the ISO you downloaded to CD, boot from it, select Startup Repair, run that at least three times, and when done, you should be able to boot into your Vista OS.

Your choice.

---

### Post by DrGNU on 2009-05-18
> **Mark Phelps said:**
> You can continue hacking and slashing, hoping that SOMETHING will work ... and most likely destroy any chance at all of recovering your Vista installation ... or you can calm down and do what I suggested:

Burn the ISO you downloaded to CD, boot from it, select Startup Repair, run that at least three times, and when done, you should be able to boot into your Vista OS.

Your choice.

***"Beware how you take away hope from another human being."***
-- Oliver Wendell Holmes, Sr.
[http://en.wikipedia.org/wiki/Oliver_Wendell_Holmes,_Sr.](http://en.wikipedia.org/wiki/Oliver_Wendell_Holmes,_Sr.)

Unfortunately, the Start-Up repair did not work.
It turns out that we had tried that previously because this IS on our OEM CD RECOVERY DISKS.  We tried it again with the newly burned ISO recommended to us... and that failed to work.  We also tried it again with the OEM CD RECOVERY DISKS with no difference in outcome.

We finally also tried altering the boot flags which only resulted in the Start-Up recovery disk changing the flag back to dev/sda2 again.

We attempted to recover and this failed as well.
We have tried to reinstall to the factory Vista erasing the whole drive.  Vista appears to hang (with a graphic showing folders looking like they are exchanging files) that goes on for over a day.  

I'm going to just erase this HDD and just install gNewSense by itself.  If Microsoft ever has a presence on this computer again it will only be as a virtual machine running inside GNU/Linux.

Thank you for your patience and help while we checked out the options that may have been available for repairing the partitions.

---

### Post by Mark Phelps on 2009-05-18
Sorry to hear that nothing worked.  

Never seen a situation where BOTH the Startup Repair and Complete Restore failed.  

I had a restore on an older HP machine take over 8 hours to complete -- but at least it eventually worked.  My guess is that it was doing sector-by-sector expansion and copying, and very slowly at that. And, that was using XP -- which is a lot smaller than Vista.

So, there's the outside chance that a full restoration from the recovery CDs would work.  But, I can certainly understand your not wanting to have to suffer through that.

---

