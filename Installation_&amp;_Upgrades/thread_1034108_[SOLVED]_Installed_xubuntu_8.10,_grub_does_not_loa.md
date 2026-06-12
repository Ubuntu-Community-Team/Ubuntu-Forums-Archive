---
title: "[SOLVED] Installed xubuntu 8.10, grub does not load after reboot"
date: 2009-01-08
forum: Installation &amp; Upgrades
---

### Post by SoloTSi97 on 2009-01-08
I'm not brand new to ubuntu, but I'm no guru either.  This one has me pulling my hair out.  Newly-built machine, I've installed xubuntu 8.10 amd64 a dozen different ways (or so it seems), with no errors except that in every case grub does not load after rebooting.  I get a blank screen with a blinking cursor in the top left corner which, after a few seconds, drops a couple of lines down on the screen and continues to blink endlessly.

*Interestingly, if I boot the Live CD and select "Boot First Hard Disk", all runs perfectly.  But, I can not boot directly to the hard drive.*

Hardware specs:
Motherboard: Foxconn A7GM-S (AM2+ 780G chipset), Athlon 64 X2 5200+
Video: On-board ATI Radeon HD 3200
4GB RAM, 4 hard drives (details below)

Hard drive info:
2 PATA drives (/dev/sdc, /dev/sdd)
2 SATA drives (/dev/sda, /dev/sdb)

I've tried various combinations of primary drives.  Originally, I tried using an SATA drive for the /boot partition.  At this point, I've fallen back to using an IDE drive for the /boot partition.  The root partition is on an SATA drive, however.  In the BIOS, the primary and secondary IDE drives are configured and detected to be the two PATA drives.

Boot order is defined as:
Floppy
DVD-RW
Primary IDE drive (/dev/sdc, which contains my /boot partition)

Dump from 'sudo fdisk -lu':
```

Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x070dccf8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       96389       48163+  83  Linux
/dev/sda2   *   163842336   321671951    78914808   83  Linux
Partition 2 does not end on cylinder boundary.
/dev/sda3           96390   163830869    81867240   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x11331133

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   976768064   488384001    f  W95 Ext'd (LBA)
/dev/sdb5        39070080   976768064   468848992+  83  Linux
/dev/sdb6             189    39063023    19531417+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc98df6cf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63       96389       48163+  83  Linux
/dev/sdc2           96390   390716864   195310237+  83  Linux

Disk /dev/sdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf5b55079

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          63   156264254    78132096    7  HPFS/NTFS
/dev/sdd2       156264255   312576704    78156225   83  Linux

```

I know that this is difficult to sort out given the plethora of drives/partitions.  Most of these are simply for storage, but are partitioned as was appropriate for the OS installed at a certain point in time.

Right now, the important ones (per my fstab) are:
/dev/sdc1 (my /boot partition)
/dev/sda2 (my / partition)
/dev/sdb6 (my swap partition)

Considering that everything boots up perfectly when I boot the 1st hard drive via the Live CD, I am inclined to believe that my menu.lst and device.map files are configured properly.  I have been playing around with various drive ordering in my BIOS thinking maybe that's the problem, but have had no luck.

I have used grub-install to install grub onto the MBR of /dev/sdc (at least I believe that's what 'sudo grub-install /dev/sdc' does).

Sorry if this is too little, too much, or just not the right information.  I'd be happy to paste more info about my grub configuration or whatever else may help.

Thanks in advance for any assistance!

-Bob

---

### Post by Tim Sharitt on 2009-01-08
Since it boots fine when you select "boot from first hard disk" on the live cd, I am led to believe that grub is installed on the MBR of the first hard disk. You could try to move the first hd up in the boot order to confirm this. If that is the case you may be able to fix it with grub. 

Fire up a terminal and do:
```
sudo grub
setup (hd2)
quit
```

Edit: Be careful though, grub *might* overwrite the start of the partition table instead of moving it. But the version in Ubuntu should be fine

---

### Post by SoloTSi97 on 2009-01-08
Thanks for the reply.  I guess that does make sense, doesn't it?  The picture in my head tends to get a little fuzzy when talking about "the first hard drive" when dealing with grub vs. what's listed in the bios vs. what you see in Linux.

Note that my current install is the result of several reinstalls, playing around with drive ordering, etc.  The first install that I did was with SATA #1 as the first boot device in the BIOS, and /boot and / partitions on that drive (/dev/sda1 and /dev/sda2, respectively).  After reading some things online about possible problems booting to an SATA device, I moved the /boot partition to an IDE device (and moved that IDE device to the top of the boot order in my BIOS).  So, I believe I've already tried the "moving the first hd up in the boot order", but think that an SATA vs. IDE problem may be preventing that from working properly.  So, I've gone ahead with your other suggestion, since what you point out does make sense. :-)

I ran the commands you listed (with the addition of a root (hd2,0) to get around an error) and grub claims to have installed itself properly.  When I get home from work tonight, I'll give a reboot a shot (I ran these commands remotely to provide output).

```

grub> find /grub/stage1
find /grub/stage1
 (hd0,0)
 (hd2,0)
grub> root (hd2,0)
root (hd2,0)
grub> setup (hd2)
setup (hd2)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... yes
 Checking if "/grub/stage2" exists... yes
 Checking if "/grub/e2fs_stage1_5" exists... yes
 Running "embed /grub/e2fs_stage1_5 (hd2)"...  16 sectors are embedded.
succeeded
 Running "install /grub/stage1 (hd2) (hd2)1+16 p (hd2,0)/grub/stage2 /grub/menu.lst"... succeeded
Done.
grub> quit

```

I'll report back after the reboot.  Thanks again for your time.

-Bob

---

### Post by jimbo007be on 2009-01-08
same problem with ubuntu server 8.10 64bits installed on a brand new IBM x3650 server ... 
1 logical raid volume (8 physical disks drives in Raid 10 configuration using a Serve-Raid 8K controller)
same configuration is OK with 8.04.1 version

any idea of what i can try ? 
(i'm really not a linux guru)

thanks in advance

---

### Post by caljohnsmith on 2009-01-08
Hi SoloTSi97, the fact that you can boot the Xubuntu drive just fine from the Live CD, and yet not directly on start up, means that you most likely have Grub installed just fine to that drive; in my experience, that type of strange behavior is sometimes caused by how the HDD is set up in BIOS, or in more rare cases, not having the HDD's properly jumpered. Do you have the Xubuntu drive in a master/slave configuration with one of your other drives? If so, I would check how you have the jumpers set on the drives just to make sure that's not the issue. Also, what HDD-related settings do you have in your BIOS? Do you have anything like "auto-detect", LBA, CHS, RAID, AHCI/HCI/EHCI vs. IDE, IDE-emulation, ACPI, DMA, etc? Also, sometimes with illogical Grub problems like you are experiencing, it sometimes helps to use a slightly different version of Grub, so have you by chance tried using the [Super Grub Disk]("http://www.supergrubdisk.org") yet to install Grub to the MBR of your Xubuntu drive? I would give that a shot if you haven't all ready to see if it makes any difference. 

Also, it would help to get a more complete picture of your setup to make sure there isn't some other issue at play, so how about opening a terminal and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by SoloTSi97 on 2009-01-08
caljohnsmith, thank you very much for taking the time to help!

I have not tried the Super GRUB disk, and didn't realize it was any different than the grub I am trying to install.  Pending further discussion in this thread before I get home and really start tinkering, I will definitely keep that in mind.

Having just built this system a week ago, I still have clear memory of how the hardware is configured.  The two IDE hard drives both are jumpered as "Cable Select".  My motherboard only has one IDE connector, so one acts as master and the other as slave.

The BIOS options you mention are exactly what I've been playing with for the past couple of days.  My motherboard has several options with regard to configuring the IDE/SATA controllers (listed below, with selected option bolded):

[LIST]
[*]IDE Enabled (**true**, false)
[*]SATA Enabled (**true**, false)
[*]SATA Controller Mode (Native IDE, RAID, **AHCI**, Legacy IDE)
[*]SATA IDE Combined Mode (true, **false**)
[*]SATA As Primary (only able to be set if combined mode = true)
[/LIST]

From what I understand, the SATA Controller Mode, SATA IDE Combined Mode, and SATA As Primary options all work together to control how the SATA drives are exposed through the BIOS (they can show up as pseudo-IDE drives in the BIOS configuration or not, and in varying orders).  See the attached chart if this doesn't make any sense, I find it to be much more helpful than plain text.  As currently set, these options prevent the SATA devices from being listed in the IDE device list at bootup.

If you do refer to the attached chart, you'll want to note that my SATA drives are attached to connectors SATA1 and SATA2.

I am not terribly clear on the difference between the various SATA Controller Mode options ... AHCI is the only one I have used.

Now, for the command you asked me to run:
```

============================= Boot Info Summary: ==============================

 => Drive sde does not have a valid partition table.
 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /grub/stage2 and /grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #1 for /grub/stage2 and /grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdd and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdf

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst /grub

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /etc/fstab /boot

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /etc/fstab /boot

sdb1: _________________________________________________________________________

    File system:       Extended Partition

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       swap

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst /grub

sdc2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdd2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 7.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdf1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x070dccf8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       96389       48163+  83  Linux
/dev/sda2   *   163842336   321671951    78914808   83  Linux
Partition 2 does not end on cylinder boundary.
/dev/sda3           96390   163830869    81867240   83  Linux

Partition table entries are not in disk order

sfdisk -V /dev/sda:

Warning: partition 2 extends past end of disk

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x11331133

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   976768064   488384001    f  W95 Ext'd (LBA)
/dev/sdb5        39070080   976768064   468848992+  83  Linux
/dev/sdb6             189    39063023    19531417+  82  Linux swap / Solaris

Partition table entries are not in disk order

sfdisk -V /dev/sdb:

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: partition [6] does not end at a cylinder boundary

Drive sdc: _____________________________________________________________________

fdisk -lu /dev/sdc:

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc98df6cf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63       96389       48163+  83  Linux
/dev/sdc2           96390   390716864   195310237+  83  Linux

sfdisk -V /dev/sdc:

/dev/sdc: OK

Drive sdd: _____________________________________________________________________

fdisk -lu /dev/sdd:

Disk /dev/sdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf5b55079

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          63   156264254    78132096    7  HPFS/NTFS
/dev/sdd2       156264255   312576704    78156225   83  Linux

sfdisk -V /dev/sdd:

/dev/sdd: OK

Drive sde: _____________________________________________________________________

fdisk -lu /dev/sde:

sfdisk -V /dev/sde:

/dev/sde: No medium found

sfdisk: cannot open /dev/sde for reading

Drive sdf: _____________________________________________________________________

fdisk -lu /dev/sdf:

Disk /dev/sdf: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd75efdab

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1            2048   320169983   160083968    7  HPFS/NTFS

sfdisk -V /dev/sdf:

Warning: partition 1 extends past end of disk

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="441b7982-6f99-4e06-9c12-0f1eb8c68138" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: UUID="d253edfc-266f-4bf2-b3bc-f4d69185c419" TYPE="ext3" 
/dev/sda3: UUID="c0265d88-e577-45fb-b9e2-bd1d290ab0a3" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="01f270f1-735a-4540-b10d-e24e38af1fee" TYPE="ext3" 
/dev/sdb6: UUID="59d0b1af-a6d0-452d-a124-837489593e68" TYPE="swap" 
/dev/sdc1: LABEL="boot" UUID="3f3ad0d7-fcf9-4de1-9928-dc5fb1b489f3" TYPE="ext3" 
/dev/sdc2: UUID="09a4602b-2b10-43ed-ac84-92f28689a1d4" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdd1: UUID="4808619D08618AB0" TYPE="ntfs" 
/dev/sdd2: UUID="2960a6cc-26e1-42e3-a83e-66d24a303028" TYPE="ext3" 
/dev/sdf1: UUID="92F65CC9F65CAF6B" LABEL="External HD" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
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
/dev/sdc1 on /boot type ext3 (rw)
/dev/sdb5 on /media/sdb5 type ext3 (rw)
/dev/sdd2 on /media/sdd2 type ext3 (rw)
/dev/sdd1 on /media/sdd1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdf1 on /media/External HD type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

============================= sda1/grub/menu.lst: =============================

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
# kopt=root=UUID=d253edfc-266f-4bf2-b3bc-f4d69185c419 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d253edfc-266f-4bf2-b3bc-f4d69185c419

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
howmany=2

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
uuid		441b7982-6f99-4e06-9c12-0f1eb8c68138
kernel		/vmlinuz-2.6.27-9-generic root=UUID=d253edfc-266f-4bf2-b3bc-f4d69185c419 ro quiet splash 
initrd		/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		441b7982-6f99-4e06-9c12-0f1eb8c68138
kernel		/vmlinuz-2.6.27-9-generic root=UUID=d253edfc-266f-4bf2-b3bc-f4d69185c419 ro  single
initrd		/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		441b7982-6f99-4e06-9c12-0f1eb8c68138
kernel		/vmlinuz-2.6.27-7-generic root=UUID=d253edfc-266f-4bf2-b3bc-f4d69185c419 ro quiet splash 
initrd		/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		441b7982-6f99-4e06-9c12-0f1eb8c68138
kernel		/vmlinuz-2.6.27-7-generic root=UUID=d253edfc-266f-4bf2-b3bc-f4d69185c419 ro  single
initrd		/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		441b7982-6f99-4e06-9c12-0f1eb8c68138
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdd1
title		Microsoft Windows XP Professional
root		(hd3,0)
savedefault
map		(hd0) (hd3)
map		(hd3) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdd2.
title		Ubuntu 7.10, kernel 2.6.22-16-generic (on /dev/sdd2)
root		(hd3,1)
kernel		/boot/vmlinuz-2.6.22-16-generic root=UUID=2960a6cc-26e1-42e3-a83e-66d24a303028 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdd2.
title		Ubuntu 7.10, kernel 2.6.22-16-generic (recovery mode) (on /dev/sdd2)
root		(hd3,1)
kernel		/boot/vmlinuz-2.6.22-16-generic root=UUID=2960a6cc-26e1-42e3-a83e-66d24a303028 ro single 
initrd		/boot/initrd.img-2.6.22-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdd2.
title		Ubuntu 7.10, kernel 2.6.22-15-generic (on /dev/sdd2)
root		(hd3,1)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=2960a6cc-26e1-42e3-a83e-66d24a303028 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdd2.
title		Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode) (on /dev/sdd2)
root		(hd3,1)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=2960a6cc-26e1-42e3-a83e-66d24a303028 ro single 
initrd		/boot/initrd.img-2.6.22-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdd2.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sdd2)
root		(hd3,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2960a6cc-26e1-42e3-a83e-66d24a303028 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdd2.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sdd2)
root		(hd3,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2960a6cc-26e1-42e3-a83e-66d24a303028 ro single 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdd2.
title		Ubuntu 7.10, memtest86+ (on /dev/sdd2)
root		(hd3,1)
kernel		/boot/memtest86+.bin  
savedefault
boot


================================== sda1/grub: ==================================

total 192
drwxr-xr-x 2 root root   1024 2009-01-07 23:31 .
drwxr-xr-x 4 root root   1024 2009-01-07 21:20 ..
-rw-r--r-- 1 root root    197 2009-01-07 23:21 default
-rw-r--r-- 1 root root     60 2009-01-07 23:21 device.map
-rw-r--r-- 1 root root   8108 2009-01-07 23:21 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-01-07 23:21 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-01-07 23:21 installed-version
-rw-r--r-- 1 root root   8712 2009-01-07 23:21 jfs_stage1_5
-rw-r--r-- 1 root root   7586 2009-01-07 21:20 menu.lst
-rw-r--r-- 1 root root   4287 2009-01-07 20:37 menu.lst.bak
-rw-r--r-- 1 root root   7352 2009-01-07 23:21 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-01-07 23:21 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-07 23:21 stage1
-rw-r--r-- 1 root root 121460 2009-01-07 23:21 stage2
-rw-r--r-- 1 root root   9556 2009-01-07 23:21 xfs_stage1_5

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
#UUID=441b7982-6f99-4e06-9c12-0f1eb8c68138 /boot	ext3	defaults	0	0
UUID=3f3ad0d7-fcf9-4de1-9928-dc5fb1b489f3 /boot	ext3	defaults	0	0

# /dev/sda2
UUID=d253edfc-266f-4bf2-b3bc-f4d69185c419 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb6
UUID=59d0b1af-a6d0-452d-a124-837489593e68 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

# /dev/sdb5
UUID=01f270f1-735a-4540-b10d-e24e38af1fee	/media/sdb5	ext3	defaults	0	0

# /dev/sdd2
UUID=2960a6cc-26e1-42e3-a83e-66d24a303028	/media/sdd2	ext3	defaults	0	0

# /dev/sdc1
UUID=1EBC1226BC11F8CB	/media/sdc1	ntfs	defaults	0	0

# /dev/sdd1
UUID=4808619D08618AB0	/media/sdd1	ntfs	defaults	0	0

# BuckeyeFans.net web disk
https://box229.bluehost.com:2078 /home/bob/buckeyefans davfs uid=1000,gid=1000,rw,user 0 0

================================== sda2/boot: ==================================

total 8
drwxr-xr-x  2 root root 4096 2009-01-07 11:01 .
drwxr-xr-x 22 root root 4096 2009-01-07 11:01 ..

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=c0265d88-e577-45fb-b9e2-bd1d290ab0a3 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=441b7982-6f99-4e06-9c12-0f1eb8c68138 /boot           ext3    relatime        0       2
# /dev/sdb6
UUID=59d0b1af-a6d0-452d-a124-837489593e68 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sda3/boot: ==================================

total 8
drwxr-xr-x  2 root root 4096 2009-01-07 20:29 .
drwxr-xr-x 20 root root 4096 2009-01-07 20:37 ..

============================= sdc1/grub/menu.lst: =============================

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
# kopt=root=UUID=d253edfc-266f-4bf2-b3bc-f4d69185c419 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d253edfc-266f-4bf2-b3bc-f4d69185c419

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
howmany=2

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
uuid		3f3ad0d7-fcf9-4de1-9928-dc5fb1b489f3
kernel		/vmlinuz-2.6.27-9-generic root=UUID=d253edfc-266f-4bf2-b3bc-f4d69185c419 ro quiet splash 
initrd		/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		3f3ad0d7-fcf9-4de1-9928-dc5fb1b489f3
kernel		/vmlinuz-2.6.27-9-generic root=UUID=d253edfc-266f-4bf2-b3bc-f4d69185c419 ro  single
initrd		/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		3f3ad0d7-fcf9-4de1-9928-dc5fb1b489f3
kernel		/vmlinuz-2.6.27-7-generic root=UUID=d253edfc-266f-4bf2-b3bc-f4d69185c419 ro quiet splash 
initrd		/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		3f3ad0d7-fcf9-4de1-9928-dc5fb1b489f3
kernel		/vmlinuz-2.6.27-7-generic root=UUID=d253edfc-266f-4bf2-b3bc-f4d69185c419 ro  single
initrd		/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		3f3ad0d7-fcf9-4de1-9928-dc5fb1b489f3
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdd1
title		Microsoft Windows XP Professional
root		(hd3,0)
savedefault
map		(hd0) (hd3)
map		(hd3) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdd2.
title		Ubuntu 7.10, kernel 2.6.22-16-generic (on /dev/sdd2)
root		(hd3,1)
kernel		/boot/vmlinuz-2.6.22-16-generic root=UUID=2960a6cc-26e1-42e3-a83e-66d24a303028 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdd2.
title		Ubuntu 7.10, kernel 2.6.22-16-generic (recovery mode) (on /dev/sdd2)
root		(hd3,1)
kernel		/boot/vmlinuz-2.6.22-16-generic root=UUID=2960a6cc-26e1-42e3-a83e-66d24a303028 ro single 
initrd		/boot/initrd.img-2.6.22-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdd2.
title		Ubuntu 7.10, kernel 2.6.22-15-generic (on /dev/sdd2)
root		(hd3,1)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=2960a6cc-26e1-42e3-a83e-66d24a303028 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdd2.
title		Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode) (on /dev/sdd2)
root		(hd3,1)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=2960a6cc-26e1-42e3-a83e-66d24a303028 ro single 
initrd		/boot/initrd.img-2.6.22-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdd2.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sdd2)
root		(hd3,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2960a6cc-26e1-42e3-a83e-66d24a303028 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdd2.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sdd2)
root		(hd3,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2960a6cc-26e1-42e3-a83e-66d24a303028 ro single 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdd2.
title		Ubuntu 7.10, memtest86+ (on /dev/sdd2)
root		(hd3,1)
kernel		/boot/memtest86+.bin  
savedefault
boot


================================== sdc1/grub: ==================================

total 195
drwxr-xr-x 2 root root   1024 2009-01-07 23:39 .
drwxr-xr-x 4 root root   1024 2009-01-07 23:37 ..
-rw-r--r-- 1 root root    197 2009-01-07 23:37 default
-rw-r--r-- 1 root root     60 2009-01-07 23:37 device.map
-rw-r--r-- 1 root root   8108 2009-01-07 23:37 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-01-07 23:37 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-01-07 23:37 installed-version
-rw-r--r-- 1 root root   8712 2009-01-07 23:37 jfs_stage1_5
-rw-r--r-- 1 root root   7586 2009-01-07 23:39 menu.lst
-rw-r--r-- 1 root root   7586 2009-01-07 21:20 menu.lst.bak
-rw-r--r-- 1 root root   7352 2009-01-07 23:37 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-01-07 23:37 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-07 23:37 stage1
-rw-r--r-- 1 root root 121460 2009-01-07 23:37 stage2
-rw-r--r-- 1 root root   9556 2009-01-07 23:37 xfs_stage1_5

================================ sdd1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

=========================== sdd2/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=2960a6cc-26e1-42e3-a83e-66d24a303028 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title		Ubuntu 7.10, kernel 2.6.22-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-16-generic root=UUID=2960a6cc-26e1-42e3-a83e-66d24a303028 ro quiet splash
initrd		/boot/initrd.img-2.6.22-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-16-generic root=UUID=2960a6cc-26e1-42e3-a83e-66d24a303028 ro single
initrd		/boot/initrd.img-2.6.22-16-generic

title		Ubuntu 7.10, kernel 2.6.22-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=2960a6cc-26e1-42e3-a83e-66d24a303028 ro quiet splash
initrd		/boot/initrd.img-2.6.22-15-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=2960a6cc-26e1-42e3-a83e-66d24a303028 ro single
initrd		/boot/initrd.img-2.6.22-15-generic

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2960a6cc-26e1-42e3-a83e-66d24a303028 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2960a6cc-26e1-42e3-a83e-66d24a303028 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sdd2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=2960a6cc-26e1-42e3-a83e-66d24a303028 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=4808619D08618AB0 /media/hda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda1
UUID=1EBC1226BC11F8CB /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb5
UUID=01f270f1-735a-4540-b10d-e24e38af1fee /media/sdb5     ext3    defaults 0       1
# /dev/sdc1
UUID=6EF4878AF48752EF /media/sdc1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb6
UUID=59d0b1af-a6d0-452d-a124-837489593e68 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

================================== sdd2/boot: ==================================

total 51700
drwxr-xr-x  3 root root    4096 2008-12-18 20:35 .
drwxr-xr-x 22 root root    4096 2009-01-03 11:42 ..
-rw-r--r--  1 root root  424317 2008-02-12 05:39 abi-2.6.22-14-generic
-rw-r--r--  1 root root  424374 2008-10-21 23:04 abi-2.6.22-15-generic
-rw-r--r--  1 root root  424374 2008-11-24 16:46 abi-2.6.22-16-generic
-rw-r--r--  1 root root   75311 2008-02-12 05:39 config-2.6.22-14-generic
-rw-r--r--  1 root root   75300 2008-10-21 23:04 config-2.6.22-15-generic
-rw-r--r--  1 root root   75300 2008-11-24 16:46 config-2.6.22-16-generic
drwxr-xr-x  2 root root    4096 2008-12-05 09:34 grub
-rw-r--r--  1 root root 7230399 2008-05-27 21:50 initrd.img-2.6.22-14-generic
-rw-r--r--  1 root root 7230222 2008-02-29 16:58 initrd.img-2.6.22-14-generic.bak
-rw-r--r--  1 root root 7229670 2008-11-11 17:11 initrd.img-2.6.22-15-generic
-rw-r--r--  1 root root 7229637 2008-11-05 22:37 initrd.img-2.6.22-15-generic.bak
-rw-r--r--  1 root root 7230506 2008-12-18 20:35 initrd.img-2.6.22-16-generic
-rw-r--r--  1 root root 7229716 2008-12-05 09:34 initrd.img-2.6.22-16-generic.bak
-rw-r--r--  1 root root  103204 2007-09-28 06:06 memtest86+.bin
-rw-r--r--  1 root root  823535 2008-02-12 05:39 System.map-2.6.22-14-generic
-rw-r--r--  1 root root  823860 2008-10-21 23:04 System.map-2.6.22-15-generic
-rw-r--r--  1 root root  823860 2008-11-24 16:46 System.map-2.6.22-16-generic
-rw-r--r--  1 root root 1764536 2008-02-12 05:39 vmlinuz-2.6.22-14-generic
-rw-r--r--  1 root root 1765144 2008-10-21 23:04 vmlinuz-2.6.22-15-generic
-rw-r--r--  1 root root 1765592 2008-11-24 16:46 vmlinuz-2.6.22-16-generic

=============================== sdd2/boot/grub: ===============================

total 220
drwxr-xr-x 2 root root   4096 2008-12-05 09:34 .
drwxr-xr-x 3 root root   4096 2008-12-18 20:35 ..
-rw-r--r-- 1 root root    197 2008-01-26 17:06 default
-rw-r--r-- 1 root root     60 2008-01-26 17:06 device.map
-rw-r--r-- 1 root root   8660 2008-01-26 17:06 e2fs_stage1_5
-rw-r--r-- 1 root root   8452 2008-01-26 17:06 fat_stage1_5
-rw-r--r-- 1 root root     15 2008-01-26 17:06 installed-version
-rw-r--r-- 1 root root   9152 2008-01-26 17:06 jfs_stage1_5
-rw-r--r-- 1 root root   5432 2008-12-05 09:34 menu.lst
-rw-r--r-- 1 root root   5004 2008-12-05 09:34 menu.lst~
-rw-r--r-- 1 root root   7860 2008-01-26 17:06 minix_stage1_5
-rw-r--r-- 1 root root  10132 2008-01-26 17:06 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-01-26 17:06 stage1
-rw-r--r-- 1 root root 110292 2008-01-26 17:06 stage2
-rw-r--r-- 1 root root   9980 2008-01-26 17:06 xfs_stage1_5

=============================== StdErr Messages: ===============================

/dev/sde: No medium found

sfdisk: cannot open /dev/sde for reading
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

```
(that's a LOT of output, very cool script!  FYI, I have no idea what /dev/sde is referring to.  /dev/sdf is my external USB hard drive, which happens to be powered on right now.)

Thanks again,
-Bob

---

### Post by caljohnsmith on 2009-01-08
Thanks for posting the output of the script and all the info about your BIOS, that definitely helps give me a clearer picture of your situation. As expected, it looks like Grub is installed and configured correctly in your sdc drive's MBR. In your first post you mentioned that you put your boot partition on one of your SATA drives; what happened when you tried to boot that drive? Did you get any Grub errors, or did Grub hang similar to what you are experiencing with your boot partition on your PATA drive?

---

### Post by SoloTSi97 on 2009-01-08
I had the same result with the boot partition on an SATA drive.

My first attempt was with an SATA 160GB drive:
/dev/sda1 (80GB) -> Vista partition
/dev/sda2 (80GB) -> Xubuntu partition (mounted as /, no separate /boot partition)

Next, still using the same single-drive approach, I wiped the Vista partition and used:
/dev/sda1 (50MB) -> /boot
/dev/sda2 (80GB) -> /
<~80GB free space>

This is when I read some posts elsewhere about possible issues with booting SATA drives.  Most of these posts were ~2 years old, though, so I didn't know if it was a current issue or not.  Decided it couldn't hurt and installed the /boot partition on a PATA drive.

All of the above have resulted in this same "blinking cursor" problem.

Thanks!

-Bob

---

### Post by SoloTSi97 on 2009-01-10
WOOHOO!  I've managed to get the machine to boot (finally).  Bad news is, I'm going to need to buy a new DVD-RW drive.  Here's what the problem was.

My new motherboard has only one IDE connector.  I have two IDE hard drives, plus an IDE DVD-RW drive.  So, I pulled an old Silicon Image 0680 PCI IDE controller off the shelf and threw it into the machine so I had a controller for the DVD drive.  While it appears to work fine in general (xubuntu installed fine from the drive, and booting from CD works, etc.), there must be some kind of conflict that is preventing GRUB from loading from ANY hard drive.

Last night, I played around with having a single drive connected (first SATA, which had the same blinking cursor result ... then PATA, which also had the same blinking cursor result).  In the process of connecting/disconnecting drives, it dawned on me that the PCI controller could be causing a conflict.  I unplugged the card, machine booted right up.  I then plugged all the hard drives in, changed around the boot order the way I wanted it originally, and it still booted right up.

So, problem solved.  It was a conflict between the Silicon Image 0680 PCI IDE controller and my Foxconn A7GM-S motherboard.  Guess I need to look into SATA DVD-RW drives. :-)

Thanks so much to caljohnsmith and Tim Sharitt for taking the time to help me out.  It is *much* appreciated.

-Bob

---

