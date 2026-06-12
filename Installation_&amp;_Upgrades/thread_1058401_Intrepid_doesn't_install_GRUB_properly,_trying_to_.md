---
title: "Intrepid doesn't install GRUB properly, trying to Triple Boot"
date: 2009-02-02
forum: Installation &amp; Upgrades
---

### Post by Antioch on 2009-02-02
Hi all. I'm trying to install Intrepid on my desktop into a Triple-Boot configuration. I currently have Vista and 7 installed, and I'd like Intrepid. I have Intrepid on my laptop, which I installed using the same live CD so it shouldn't be the problem.

My disk configuration as the live CD sees it is:
sda2   NTFS data partition
sdb1/2 Vista/7 partitions respectively
sdc1   NTFS data partition

sda1 is strange, it's a block of ~140MB before sda2 with the flag msft--- (not sure the exact name, not booted into Ubuntu now and this partition does NOT show up in the Vista disk manager).

Anyways, I originally installed Intrepid onto a new partition I made called sda3 behind sda2. Install worked fine and the installer said it would setup grub on hd(0). When I rebooted I simply went to the Windows boot manager (to choose between Vista and 7). 

So I tried again, this time making sda3 the /boot partition and sda4 the / partition. No effect. So I googled directions to add Ubuntu to the Windows boot manager. Something along the lines of making a raw copy of the first 512 bytes of the /boot partition and adding it to the Windows boot manager. This didn't work. When I tried to launch Ubuntu from WinBootMgr it displayed "GRUB geom error."

So -- I tried reinstalling again. This time I told the last step of the install to setup grub on /dev/sdb (not sdb1 or sdb2, just 'sdb'). After I rebooted it simply displayed "GRUB" and nothing happened.

Oh, and the Ubuntu installer did detect that I had Vista and offered to let me transfer files and settings from it - I picked no. Also, I've since repaired the MBR to launch WinBootMgr again.

So, I'm not sure how to get this install to work properly. I have Dual boot working perfectly on my laptop, but I can't get my desktop to work.

I don't care what disk I install it on, but I had more free space on sda so I tried to stick it there.

Please help. Thank you! :)

---

### Post by caljohnsmith on 2009-02-02
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by Antioch on 2009-02-02
CalJohnSmith, just the man I was hoping for! :)

Actually, I'm following your other directions for partition recovery as I managed to hose one of my NTFS data partitions. TestData found the partition fine and is chugging along. Once it's finished I will post that RESULT.txt file for you.

Thanks for the help, I look forward to getting Ubuntu on this machine. Ubuntu inside VMware isn't cutting it anymore. ;)

---

### Post by Antioch on 2009-02-02
The results of that boot info script are further down, but I will begin with the following.

SDA's contents are a little strange at the moment due to the partition issues I mentioned in the previous post. GParted doesn't display the same information as that script does.

I have copied "fdisk -l" output below:
```

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x379dd06a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              17       76551   614759440+   f  W95 Ext'd (LBA)
/dev/sda2           76551       77766     9755856   83  Linux
/dev/sda5              17       76551   614759424    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x947f947f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       26256   210900296    7  HPFS/NTFS
/dev/sdb2           26257       30402    33294336    7  HPFS/NTFS

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x20b520b4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       38914   312569665    7  HPFS/NTFS

```



Again, this drive got messed up, using TestDisk I recovered the hosed NTFS partition on windows and I can access the data, but the disk's structure is still a bit strange. Perhaps that is why Gparted gives the following message when launched from a terminal:



```
/dev/sda contains GPT signatures, indicating that it has a GPT table.  However, it does not have a valid fake msdos partition table, as it should.  Perhaps it was corrupted -- possibly by a program that doesn't understand GPT partition tables.  Or perhaps you deleted the GPT table, and are now using an msdos partition table.  Is this a GPT partition table?
```



The only reason I bring this us is because when I was originally trying to install Ubuntu, I installed it to a new partition following the NTFS data partition on SDA. While doing so I noticed a strange 128MB partition preceding that NTFS partition with the flag "msftres" -- perhaps this is the "fake valid msdos partition table" that gparted is referring to above?

In any case, because this mysterious partition existed I was hesitant to install GRUB to sda and attempt to boot the machine from SDA. (I am current booting off of SDB).

Anyways, here are the results of that boot info script. As I tried to install GRUB in many locations it looks like they are still visible.

It seems to have found sda2 as the old partition which I mounted as my /boot partition. At that time, before the partitions got messed up, it was sda3 and the NTFS partition was sda2. I will likely copy the data off of that disk and completely format it in the coming days.


```
============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     Grub in the file /linux.bin looks at sector 1229970434 
                       of the same hard drive for the stage2 file, but no 
                       stage2 files can be found at this location.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     Grub in the file /linux.bin looks at sector 1229970434 
                       of the same hard drive for the stage2 file, but no 
                       stage2 files can be found at this location.
    Operating System:  Windows Vista
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x379dd06a

Partition  Boot         Start           End          Size  Id System

/dev/sda1             264,159 1,229,783,039 1,229,518,881   f W95 Ext d (LBA)
/dev/sda5             264,192 1,229,783,039 1,229,518,848   7 HPFS/NTFS
/dev/sda2       1,229,783,040 1,249,294,751    19,511,712  83 Linux


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x947f947f

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   421,802,639   421,800,592   7 HPFS/NTFS
/dev/sdb2         421,804,032   488,392,703    66,588,672   7 HPFS/NTFS

/dev/sdb2 ends after the last cylinder of /dev/sdb

Drive sdc: _____________________________________________________________________

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x20b520b4

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   625,139,392   625,139,330   7 HPFS/NTFS

/dev/sdc1 ends after the last cylinder of /dev/sdc

blkid -c /dev/null: ____________________________________________________________

/dev/sda2: UUID="0598ec4c-4294-4bfb-84a5-49c8fffc9e85" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="C68CBE6C8CBE56A1" LABEL="Storage" TYPE="ntfs" 
/dev/sdb1: UUID="DAA026BFA026A24D" LABEL="Windows" TYPE="ntfs" 
/dev/sdb2: UUID="B0667002666FC7A4" LABEL="Windows7" TYPE="ntfs" 
/dev/sdc1: UUID="F6049D86049D4B0F" LABEL="Data" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

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
# kopt=root=UUID=0598ec4c-4294-4bfb-84a5-49c8fffc9e85 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=0598ec4c-4294-4bfb-84a5-49c8fffc9e85

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		0598ec4c-4294-4bfb-84a5-49c8fffc9e85
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0598ec4c-4294-4bfb-84a5-49c8fffc9e85 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		0598ec4c-4294-4bfb-84a5-49c8fffc9e85
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0598ec4c-4294-4bfb-84a5-49c8fffc9e85 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		0598ec4c-4294-4bfb-84a5-49c8fffc9e85
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1


=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=0598ec4c-4294-4bfb-84a5-49c8fffc9e85 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=e8a7d28b-ac0b-4a89-86be-eaea741d10f1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


 635.7GB: boot/grub/menu.lst
 635.6GB: boot/grub/stage2
 635.7GB: boot/initrd.img-2.6.27-7-generic
 635.7GB: boot/vmlinuz-2.6.27-7-generic
 635.7GB: initrd.img
 635.7GB: vmlinuz

================================ sdc1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

```

In case I haven't mentioned it before, the linux partitions (/boot and /) were among those hosed, and no valid partition of those currently exist.

---

### Post by caljohnsmith on 2009-02-03
It looks like at some point you mistakenly chose to set up a GUID Partition Table (GPT) on your sda drive; fdisk obviously found remnants of the GPT and complained that sda still has a GPT. I think it would be good to fix that, but it would be best if I can first look at the sectors on your HDD that contain the GPT info to make sure it is safe to delete them. So how about doing:
```
sudo dd if=/dev/sda count=100 | gzip -c > ~/Desktop/sda.MBR.gz
```
And please post the the "sda.MBR.gz" file on your desktop to your next post so I can take a look at it. But in the meantime, it should be perfectly safe to install Grub to the MBR of sda, so how about doing:
```
sudo grub
grub> root (hd0,1)
grub> makeactive
grub> setup (hd0)
grub> quit
```
And if the commands complete successfully, go ahead and reboot, set your BIOS to boot the sda drive, and let me know how far you get. We can work from there. :)

---

### Post by Antioch on 2009-02-03
A la Wikipedia, it seems that Windows created that GPT partition when it formatted my disk.

[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

I'm not sure, but what I also read in regards to GPT is that it is the new standard. So why is it a mistake to have this table?

Also, that wikipedia entry about MSFTRES said that the GPT replaces the MBR - but the GPT still contains MBR at LBA0, so am I just misinterpreting that statement?

I will reboot onto the Live CD again in a few minutes and preform the requested operations.

Again, thank you! :)

---

### Post by caljohnsmith on 2009-02-03
You're absolutely right, the GPT fortunately leaves the MBR intact; the GPT comes in the sectors immediately following the MBR, and that is done for legacy purposes. But unless your BIOS supports GPT HDDs, it is of no use to have a GPT. So does your BIOS support GPT drives? Also, your only NTFS partition on that drive (sda5) does not appear to have Windows installed according to the script, so is there any reason why you would want to keep the GPT?

---

### Post by Antioch on 2009-02-03
No, that partition is purely a data storage partition, as is the sdc disk. I only attempted to install Ubuntu on sda because Vista and Win7 had taken up a lot of space on sdb while sda was still relatively empty.

As I don't know what advantages GPTs offer and why sda (and not sdc) has a GPT on it, I can't really say that I want or need to keep it. Perhaps I mistakenly told Windows to add that GPT while formatting sda a few months ago (it is a much newer drive than sdc, which could explain why only it has the GPT).

Anyways, moving to Live CD.

---

### Post by Antioch on 2009-02-03
I've attached the first 100 (blocks, I'm assuming) of the SDA. I'm curious how you're going to read this data. Reading raw HEX numbers?

sda2 is merely the /boot partition, the / partition is gone, so it would be a bit meaningless to attempt to boot linux at the moment. However, after you've looked at that GPT information I will re-structure the disk and attempt, once more, to install Ubuntu.

An interesting note: I've never used the makeactive command in grub before. What does that command do, and is it necessary? I'm going to guess that it marks the specified partition as the active boot partition.

---

### Post by caljohnsmith on 2009-02-03
Are you sure sda2 is only a boot partition? The script found Grub's boot files in /boot/grub on that partition, not /grub, and also the script found the /etc/fstab file on that partition. But if you are going to delete it anyway then obviously it is a moot point. I looked at your sda.MBR file in a hex editor, and it is clear Microsoft is indeed the culprit for putting the GPT on that drive; in the third sector is the ascii text "Microsoft reserved partition". Anyway, how about doing the following to erase the GPT remnants:
```
sudo dd if=/dev/zero of=/dev/sda seek=1 count=2
```
And then run:
```
sudo fdisk -lu
```
And hopefully fdisk won't complain about sda having a GPT any more. And by the way, you're exactly right about the "makeactive" Grub command; it sets the boot flag on whichever partition is first defined by "root (hdX,Y)", but the partition can't be a logical partition, only primary. I noticed none of the partitions on the sda drive had the boot flag set on, and some BIOSes will refuse to boot a drive that doesn't have the boot flag set on one primary partition; thus it is usually a good practice to make sure the boot flag is set on one primary partition if you want to boot the drive. Anyway, let me know how it goes or if you run into more problems. :)

---

### Post by Antioch on 2009-02-03
Okay, thanks.

You may be right, as I mentioned earlier I tried many configurations in the hopes that something would work, so perhaps I mistook what the last configuration I tried was.

That command will zero out the specified sectors, and effectively erase that partition, and the resulting space will appear as partitioned, correct?

I also took a look into that hex file, there wasn't much data at all. Am I safe in guessing that deleting the GPT will *not* jeopardize the data in the NTFS partition it was supposed to be associated with?

---

### Post by caljohnsmith on 2009-02-03
> **Antioch said:**
> 
That command will zero out the specified sectors, and effectively erase that partition, and the resulting space will appear as partitioned, correct?

I also took a look into that hex file, there wasn't much data at all. Am I safe in guessing that deleting the GPT will *not* jeopardize the data in the NTFS partition it was supposed to be associated with?
Yes to both of your questions. :) There should be no harm in zeroing out those GPT sectors at this point, and you can feel secure because we have a perfect online backup of those sectors since you posted the sda.MBR.gz file.

---

### Post by Antioch on 2009-02-03
Zeroed that section, but fdisk still complains:

```
ubuntu@ubuntu:~$ sudo dd if=/dev/zero of=/dev/sda seek=1 count=2
2+0 records in
2+0 records out
1024 bytes (1.0 kB) copied, 0.0225176 s, 45.5 kB/s
ubuntu@ubuntu:~$ sudo fdisk -lu

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x379dd06a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1          264159  1229783039   614759440+   f  W95 Ext'd (LBA)
/dev/sda2      1229783040  1249294751     9755856   83  Linux
/dev/sda3      1249310790  1250258624      473917+  82  Linux swap / Solaris
/dev/sda5          264192  1229783039   614759424    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x947f947f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   421802639   210900296    7  HPFS/NTFS
/dev/sdb2       421804032   488392703    33294336    7  HPFS/NTFS

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x20b520b4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   625139392   312569665    7  HPFS/NTFS
```

However, launching GParted from console does not, and it now accurately shows the extended and logical NTFS partition (It didn't before, only showed unknown regions). The swap space wasn't originally there, I added it after zeroing. However, for some reason it inserts a 7MB buffer of empty space before it - is it possible to get rid of this? I tried and it seems to want to add a buffer there. Also, using Gparted I tried to resize the Extended partition to encompass the 120MB at the beginning of the disk, but it doesn't want to let me. Is there any way to do so?

A screenshot for a better visual:
[IMG]http://img16.imageshack.us/img16/5544/sdaparttablefm4.jpg[/IMG]

Oh - reinstalling GRUB worked, and it booted the linux partition, so I guess the install was still intact. Now I have to figure out how to login to configure my bluetooth keyboard without having a keyboard to log in with! Hahaha. Using the live cd is nice because I simply click on the BT icon and connect the keyboard.

---

### Post by caljohnsmith on 2009-02-03
I think there must be significant remnants of the Microsoft Reserved Partition in that 128 MB of free space, and somehow fdisk is seeing that as a sign of still having a GPT. I think if you can get gparted to resize your sda1 extended partition to use that space, that will cure the GPT problem. How about when you are in gparted, first right-click your swap partition and select "swapoff" if that option is enabled, then click the sda1 extended partition, click resize, and then in the dialog box that comes up, *uncheck* the "**round to cylinders option**". Then try to resize sda1 so it takes up the 129 MB of free space at the beginning of the drive. Also, unless you want to manually partition your HDD, I don't think gparted is going to let you reclaim that 7.8 MB of free space before the swap partition. But if gparted won't let you resize sda1 to use the 129 MB of space, we could easily manually partition your drive so it will. Also, since your swap partition all ready starts on a cylinder boundary, we could resize your sda2 linux partition to use the 7.8 MB of space, but it probably isn't worth the trouble. It's up to you though.

---

### Post by meierfra. on 2009-02-03
> I think there must be significant remnants of the Microsoft Reserved Partition in that 128 MB of free space, and somehow fdisk is seeing that as a sign of still having a GPT. I think if you can get gparted to resize your sda1 extended partition to use that space, that will cure the GPT problem.

This won't work.  GPT keeps a backup of the partition table in the last few sectors of the hard drive. To cure the GPT problem  you need to  zero the last sector of the hard drive.  

Type

```
sudo dd  if=/dev/sda skip=1250263727  count=1 |hexdump -C
```

If the first line of the output starts with "EFI PART", then write zeroes to  the last sector with

```
sudo dd  if=/dev/zero of=/dev/sda seek=1250263727  count=1 
```

---

### Post by caljohnsmith on 2009-02-03
> **meierfra. said:**
> This won't work.  GPT keeps a backup of the partition table in the last few sectors of the hard drive. To cure the GPT problem  you need to  zero the last sector of the hard drive.  

So that's what I was missing. Thanks for sharing the info, meierfra.

---

### Post by Antioch on 2009-02-04
meierfra, thank you. You were right!

I still can't move the Extended partition down to absorb the new space released from the GPT with Gparted. I guess I'll try in windows.

---

