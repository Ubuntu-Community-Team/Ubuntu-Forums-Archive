---
title: "Help recover dual boot"
date: 2009-08-09
forum: Installation &amp; Upgrades
---

### Post by emeraldgirl08 on 2009-08-09
```
Disk /dev/sda: 40.0 GB, 40007761920 bytes

255 heads, 63 sectors/track, 4864 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x000dae8d



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1            4573        4789     1743052+  1c  Hidden W95 FAT32 (LBA)

/dev/sda2               1        3420    27471118+   5  Extended

/dev/sda3            4471        4572      819315   82  Linux swap / Solaris

/dev/sda4   *        3421        4470     8434125   83  Linux

/dev/sda5               1        2611    20972794+   7  HPFS/NTFS



Partition table entries are not in disk order
```

I need help recovering Grub to include XP in this. I can boot into Jaunty if I mess with the Grub menu but am not sure what to put in!

I open Terminal>>type sudo grub>> hd.... I can't remember the rest of it. I found this here in the forums. It did work but only Jaunty booted with no Grub menu. I repaired the MBR with the Xp disk but nothing works now!

I logged in courtesy of SuperGrub Disk.

Could anyone assist me?

---

### Post by merlinus on 2009-08-09
The order and numbering of your partitions i incorrect.  You can fix it this way, from a terminal:

```
sudo fdisk /dev/sda
x
f
w
```

Then post results of

```
sudo fdisk -l
```

---

### Post by emeraldgirl08 on 2009-08-09
```
The number of cylinders for this disk is set to 4864.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): 


```

This is what I got with the fdisk dev/sda command.

This is a bigger picture of my sitch!

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #4 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /BOOT.INI /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   


=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000dae8d

Partition  Boot         Start           End          Size  Id System

/dev/sda1          73,449,180    76,935,284     3,486,105  1c Hidden W95 FAT32 (LBA)
/dev/sda2                  63    54,942,299    54,942,237   5 Extended
/dev/sda5                 126    41,945,714    41,945,589   7 HPFS/NTFS
/dev/sda3          71,810,550    73,449,179     1,638,630  82 Linux swap / Solaris
/dev/sda4    *     54,942,300    71,810,549    16,868,250  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 3999 MB, 3999793152 bytes
98 heads, 33 sectors/track, 2415 cylinders, total 7812096 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               8,192     7,812,095     7,803,904   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="IBM_SERVICE" UUID="3D4F-15F0" TYPE="vfat" 
/dev/sda3: UUID="d64f1869-f103-4811-beda-f8adc4e99f0b" TYPE="swap" 
/dev/sda4: UUID="b3be3f5f-6bca-4e6e-b7ef-dd8fd0613e99" TYPE="ext3" 
/dev/sda5: UUID="6EEC6FDAEC6F9ADB" LABEL="IBM_PRELOAD" TYPE="ntfs" 
/dev/sdb1: UUID="FC30-3DA9" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sda4 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-14-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/tbanks/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=tbanks)
/dev/sr0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=tbanks)


================================ sda5/BOOT.INI: ================================

;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /FASTDETECT /NOEXECUTE=OPTIN



## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		b3be3f5f-6bca-4e6e-b7ef-dd8fd0613e99
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=b3be3f5f-6bca-4e6e-b7ef-dd8fd0613e99 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		b3be3f5f-6bca-4e6e-b7ef-dd8fd0613e99
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=b3be3f5f-6bca-4e6e-b7ef-dd8fd0613e99 ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		b3be3f5f-6bca-4e6e-b7ef-dd8fd0613e99
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=b3be3f5f-6bca-4e6e-b7ef-dd8fd0613e99 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		b3be3f5f-6bca-4e6e-b7ef-dd8fd0613e99
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=b3be3f5f-6bca-4e6e-b7ef-dd8fd0613e99 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		b3be3f5f-6bca-4e6e-b7ef-dd8fd0613e99
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=b3be3f5f-6bca-4e6e-b7ef-dd8fd0613e99 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		b3be3f5f-6bca-4e6e-b7ef-dd8fd0613e99
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=b3be3f5f-6bca-4e6e-b7ef-dd8fd0613e99 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		b3be3f5f-6bca-4e6e-b7ef-dd8fd0613e99
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=b3be3f5f-6bca-4e6e-b7ef-dd8fd0613e99 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=e1cd9d15-8570-44f3-87de-2587526527bf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda4: Location of files loaded by Grub: ===================


  28.4GB: boot/grub/menu.lst
  28.3GB: boot/grub/stage2
  28.3GB: boot/initrd.img-2.6.28-11-generic
  30.0GB: boot/initrd.img-2.6.28-13-generic
  28.5GB: boot/initrd.img-2.6.28-14-generic
  28.3GB: boot/vmlinuz-2.6.28-11-generic
  28.4GB: boot/vmlinuz-2.6.28-13-generic
  28.7GB: boot/vmlinuz-2.6.28-14-generic
  28.5GB: initrd.img
  30.0GB: initrd.img.old
  28.7GB: vmlinuz
  28.4GB: vmlinuz.old
```

---

### Post by merlinus on 2009-08-09
Each if those is a separate command.

So 

sudo fdisk /dev/sda

then

x  

then 

f  

then 

w

Press Enter after each one.

---

### Post by emeraldgirl08 on 2009-08-09
This is the fdisk results:

```
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000dae8d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3420    27471118+   5  Extended
/dev/sda2   *        3421        4470     8434125   83  Linux
/dev/sda3            4471        4572      819315   82  Linux swap / Solaris
/dev/sda4            4573        4789     1743052+  1c  Hidden W95 FAT32 (LBA)
/dev/sda5               1        2611    20972794+   7  HPFS/NTFS

```

---

### Post by merlinus on 2009-08-09
Try adding this at the end of menu.lst

title Windows XP
rootnoverify (hd0,4)
makeactive
savedefault
chainloader +1

and restart.

You also may need to remove the bootflag on sda2 using gparted, and place one on sda5.

---

### Post by emeraldgirl08 on 2009-08-09
I got a Grub error 17.

and does it really matter where I put this at?

 ```
title Windows XP
rootnoverify (hd0,4)
makeactive
savedefault
chainloader +1
```

b/c I put it two space lines under the memtest scripts.

---

### Post by merlinus on 2009-08-09
It needs to go below this line:

### END DEBIAN AUTOMAGIC KERNELS LIST

Try this to reinstall grub:

```
sudo grub
root (hd0,1)
setup (hd0)
quit
```

Also you may need to check the UUID for sda2 in menu.lst, as it may have changed.

```
sudo blkid
```

---

### Post by emeraldgirl08 on 2009-08-09
Merlin. I had saved my an original menu.lst txt from when I was doing a triple boot on the lappy I'm working on. 

FYI I figured that was wrong so I corrected it but no go. I also removed and placed the bootable flag on sda5.

This is what I placed under the end of the menu.lst


```


##END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,4)
savedefault
makeactive
chainloader	+1

```

still a no go :(

---

### Post by merlinus on 2009-08-09
I do believe it is because windows is installed in a logical rather than primary partition.  It will almost always not work that way.

It may be possible for you to change sda1 from extended to primary, but if not, then you will have to delete it and create a primary partition that is first on your hdd, and reinstall windows.

Then you can restore grub using the commands I gave, and change (hd0,4) to (hd0,0) in the menu.lst entry for windows.

---

### Post by emeraldgirl08 on 2009-08-09
Geez!

I had XP setup the way I want it!

If I have to reinstall it I'm waiting for another day to do it! 

Hmmm... would Supergrub disc be able to boot my XP partition?

---

### Post by merlinus on 2009-08-09
Certainly worth trying supergrub to boot xp, but I don't imagine you would want to do this every time.

---

### Post by presence1960 on 2009-08-09
hey Emerald, I see you have XP in a logical partition. There is an outside chance you can get it to boot from GRUB. See [here]("https://www.linuxquestions.org/questions/linux-software-2/grub-windows-on-logical-partition-607114/")

---

### Post by emeraldgirl08 on 2009-08-09
Wait a minute... I'm looking at my fdisk and it tells me that my xp part is on sda5. The menu.lst I entered in is (hd0,4). 

Shouldn't my my root be (hd0,1)???

---

### Post by Sef on 2009-08-09
> I do believe it is because windows is installed in a logical rather than primary partition. It will almost always not work that way.

Windows should be on the first primary partition.

---

### Post by presence1960 on 2009-08-09
> **merlinus said:**
> Certainly worth trying supergrub to boot xp, but I don't imagine you would want to do this every time.

hey merlin check out that link I gave Emerald. I found that googling the other day. I have not tried it yet though and don't intend to  as I don't have XP on a logical partition. Maybe one day when I am bored I can redo my machine and try it out.

---

### Post by emeraldgirl08 on 2009-08-09
Off topic:
 
Sorry guys. I've been wanting to get that Xp part off my R52 HDD for a long time. I didn't have anywhere to put it. I wanted to use Partimage to compress it and put it on a DVD but the instructions are very vague for me!

It was a long process b/c I had to move partitions around and copy and paste from one HD to the other. 

I'm hardly a comp whiz yet but I have a basic understanding of the process.

So thanks!

I'm going to post another txt of the new menu.lst and the boot info script b/c of all the tinkering I've done so far- so bear with me!

---

### Post by emeraldgirl08 on 2009-08-09
> **Sef said:**
> Windows should be on the first primary partition.

Sef.

When I moved stuff around on the drive I'm working on I placed the NTFS part first. Then the ext3, swap, and the hidden FAT32 rescue and recovery part.

---

### Post by presence1960 on 2009-08-09
> **Sef said:**
> Windows should be on the first primary partition.

Generally Windows should be on any primary partition. I have it on sda4. it is Windows 7 RC now but it was formerly XP Professional. See screenshot below. My sdb is 160GB HDD with sdb1 as ext 3 data partition and sdb2 sabayon 4.1

---

### Post by merlinus on 2009-08-09
@ presence

Tres interessant!  I can't test it either, as I do not run windows, but perhaps Emeraldgirl can get it to work.

@ Emeraldgirl

Numbering for grub sorts of things begins at 0 (zero), so sda5 translates to hd0,4 -- first hdd, fifth partition.

---

### Post by presence1960 on 2009-08-09
> **emeraldgirl08 said:**
> Sef.

When I moved stuff around on the drive I'm working on I placed the NTFS part first. Then the ext3, swap, and the hidden FAT32 rescue and recovery part. That should work as long as the NTFS is a primary partition.

---

### Post by emeraldgirl08 on 2009-08-09
OMG!

This is horrible! So on the Gparted screenshot the first partition is on the furthest right side of the graph???

If so I'm at a loss!!!

:lolflag:

---

### Post by presence1960 on 2009-08-09
> **emeraldgirl08 said:**
> OMG!

This is horrible! So on the Gparted screenshot the first partition is on the furthest right side of the graph???

If so I'm at a loss!!!

:lolflag:

if you are talking about my screenshot then hold on a second. I posted that to show windows does not have to be on the 1st primary partition. it is on the 3rd primary partition of sda on my machine. Windows can be on any primary partition, whether it is the 1st or the 4th primary partition! All that matters is that it is a primary partition. sda1 is an extended partition, sda2, sda3 & sda4 are primary partitions.

There seem to be some misconceptions about dual booting windows that are mentioned frequently in these forums. The first misconception is that you must install windows before Ubuntu. The second misconception is that windows **_MUST_** be the first primary partition. neither is correct. Sorry Sef, not personal.

---

### Post by merlinus on 2009-08-09
Yes indeed.  Gatesville wants to be a primary, but not necessarily first, or not even on the first hdd, thanks to map statements.

But unfortunately, for some reason, emeraldgirl's ntfs partition is a logical inside an extended one, which seems to have been created first.

---

### Post by emeraldgirl08 on 2009-08-09
It seems the partition is an extended one.

Is there a way I can change that to primary???

---

### Post by presence1960 on 2009-08-09
> **emeraldgirl08 said:**
> It seems the partition is an extended one.

Is there a way I can change that to primary???

if you are going to reinstall then delete the partitions inside the extended partition. When all space in the extended partition is unallocated, then go ahead and delete the extended partition. You will have all that unallocated space at the beginning of your HDD.

---

### Post by emeraldgirl08 on 2009-08-09
Presence. 

That's what I was thinking. Since I still have both partitions (xp and recovery) on my other comps HDD I was going to delete the extended and repaste the xp back into the newly created unallocated space.

Is that what you were getting at?

---

### Post by presence1960 on 2009-08-09
> **merlinus said:**
> Yes indeed.  Gatesville wants to be a primary, but not necessarily first, or not even on the first hdd, thanks to map statements.

But unfortunately, for some reason, emeraldgirl's ntfs partition is a logical inside an extended one, which seems to have been created first.

I think I remember the reason why it is a logical partition. I believe Emerald had Win 7 installed as well at one time. When you install 2 windows doesn't one of them become a logical partition? Is this the same machine Emerald or was that your other machine that had XP, Win 7 & Ubuntu?

---

### Post by presence1960 on 2009-08-09
> **emeraldgirl08 said:**
> Presence. 

That's what I was thinking. Since I still have both partitions (xp and recovery) on my other comps HDD I was going to delete the extended and repaste the xp back into the newly created unallocated space.

Is that what you were getting at?
Yes if you have an image of your XP you can do that or if that fails you can always reinstall XP.

---

### Post by emeraldgirl08 on 2009-08-09
Presence.

Bear with me. 

**My R52:**

no problems on it. Has W7 and Jaunty. Both are running fine :)
It also has the two partitions (xp and recovery) stored on it since it's got room.

**My T30:**

The one I'm working on now. Never had W7. Had Xp and Jaunty. I moved Xp for other reasons. Now want Xp partition off my R52 and back into the T30 HDD and functional.

---

### Post by presence1960 on 2009-08-09
> **emeraldgirl08 said:**
> Presence.

Bear with me. 

**My R52:**

no problems on it. Has W7 and Jaunty. Both are running fine :)
It also has the two partitions (xp and recovery) stored on it since it's got room.

**My T30:**

The one I'm working on now. Never had W7. Had Xp and Jaunty. I moved Xp for other reasons. Now want Xp partition off my R52 and back into the T30 HDD and functional.

OK, I know you had 2 puters and we were tinkering with one previously.

---

### Post by emeraldgirl08 on 2009-08-09
Deleted the Xp part and extended part off the HDD.

Have a nice clean gray Unallocated space :)

Am now prepping for transfer.

I'll be back in about 1/2 hr.

---

### Post by emeraldgirl08 on 2009-08-09
[SIZE="4"]Okay got the new fdisk and here it is![/SIZE]

```
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000dae8d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2611    20972826    7  HPFS/NTFS
/dev/sda2            3421        4470     8434125   83  Linux
/dev/sda3            4471        4572      819315   82  Linux swap / Solaris
/dev/sda4            4573        4789     1743052+  1c  Hidden W95 FAT32 (LBA)

```

*It seems cleaner than that last one. *
[B]
And the menu.lst[/B]

```
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
# kopt=root=UUID=b3be3f5f-6bca-4e6e-b7ef-dd8fd0613e99 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b3be3f5f-6bca-4e6e-b7ef-dd8fd0613e99

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

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		b3be3f5f-6bca-4e6e-b7ef-dd8fd0613e99
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=b3be3f5f-6bca-4e6e-b7ef-dd8fd0613e99 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		b3be3f5f-6bca-4e6e-b7ef-dd8fd0613e99
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=b3be3f5f-6bca-4e6e-b7ef-dd8fd0613e99 ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		b3be3f5f-6bca-4e6e-b7ef-dd8fd0613e99
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=b3be3f5f-6bca-4e6e-b7ef-dd8fd0613e99 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		b3be3f5f-6bca-4e6e-b7ef-dd8fd0613e99
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=b3be3f5f-6bca-4e6e-b7ef-dd8fd0613e99 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		b3be3f5f-6bca-4e6e-b7ef-dd8fd0613e99
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=b3be3f5f-6bca-4e6e-b7ef-dd8fd0613e99 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		b3be3f5f-6bca-4e6e-b7ef-dd8fd0613e99
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=b3be3f5f-6bca-4e6e-b7ef-dd8fd0613e99 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		b3be3f5f-6bca-4e6e-b7ef-dd8fd0613e99
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,4)
makeactive
savedefault
chainloader	+1



```

---

### Post by presence1960 on 2009-08-09
change the windows entry of menu.lst to :

> title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
chainloader	+1

---

### Post by emeraldgirl08 on 2009-08-09
Okay done.

Do I need to go back to Gparted and mark the Winxp partition as boot?

---

### Post by merlinus on 2009-08-10
Only if xp will not run from grub.

You could also add

makeactive

to its entry in menu.lst.

---

### Post by emeraldgirl08 on 2009-08-10
oh boy. 

Hi Merlin! It's been an allday affair w/ this!

I've added the boot flag and added this to the menu.lst

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

as you can probably guess. I'm tired. I'm not giving up on this yet though! I did that and rebooted and don't get a Grub menu. I see the countdown from three and it boots right from to Jaunty.

---

### Post by merlinus on 2009-08-10
Find this in menu.lst

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

and place a hashmark (#) in front ot the last line (hiddenmenu).

Also, you can increase the timeout to 10 (it is now 3):

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

---

### Post by emeraldgirl08 on 2009-08-10
I actually saved the previous menu.lst and erased the timeout, hidden menu scripts, and the old kernal choices on the current /boot/grub/menu.lst.

I don't need a timer telling me to *"Hurry Hurry!!!"*

I've rebooted and now the Grub menu comes up and I don't have no timer on it :)

I also have a strange sitch with Xp. The Windows boot comes up- however there are two entries:

older Windows version
Windows 7 (recovery)

:confused:

Time to hit the threads again!

---

### Post by merlinus on 2009-08-10
You might look for a boot.ini file in xp that may have the two menu entries.

[http://support.microsoft.com/kb/289022](http://support.microsoft.com/kb/289022)

---

### Post by emeraldgirl08 on 2009-08-10
Fixed with [EasyBCD!]("http://neosmart.net/dl.php?id=1")

Only thing is you gotta have an external drive and a second comp with a MS OS on it for the program.

I'm very lucky to have a second Lappy here!

Now I have those two images off my HDD :)

---

### Post by merlinus on 2009-08-10
Glad to hear you got it working to your satisfaction.  Now what are you going to do with all that unallocated space?

---

### Post by emeraldgirl08 on 2009-08-10
@@###!!!

Hold on a second.

Looks like I traded in one problem for another one!

I've got the dual-boot going on the T30 finally...but the R52 can only boot Jaunty!

When I try and boot W7 it says NTLDR is missing!

Quickly did a search and found this [thread.]("http://ubuntuforums.org/showthread.php?t=1014708")

**The new Boot info Script for my current problem machine (R52):**

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa266a266

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    42,026,039    42,025,977   7 HPFS/NTFS
/dev/sda4          42,026,040    61,561,079    19,535,040   5 Extended
/dev/sda5          42,026,103    57,657,284    15,631,182  83 Linux
/dev/sda6          57,657,348    61,561,079     3,903,732  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="0C0C0F830C0F6754" TYPE="ntfs" 
/dev/sda5: UUID="531e9b96-1d73-4735-a9a4-1bc810f58ff1" TYPE="ext3" 
/dev/sda6: UUID="b0e34ba2-19de-4109-9a14-f2086b41ede9" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-14-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/tyrene/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=tyrene)


=========================== sda5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=531e9b96-1d73-4735-a9a4-1bc810f58ff1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=531e9b96-1d73-4735-a9a4-1bc810f58ff1

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

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		531e9b96-1d73-4735-a9a4-1bc810f58ff1
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=531e9b96-1d73-4735-a9a4-1bc810f58ff1 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		531e9b96-1d73-4735-a9a4-1bc810f58ff1
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=531e9b96-1d73-4735-a9a4-1bc810f58ff1 ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, memtest86+
uuid		531e9b96-1d73-4735-a9a4-1bc810f58ff1
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows 7 (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1



=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=531e9b96-1d73-4735-a9a4-1bc810f58ff1 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=b0e34ba2-19de-4109-9a14-f2086b41ede9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  29.5GB: boot/grub/menu.lst
  29.4GB: boot/grub/stage2
  29.4GB: boot/initrd.img-2.6.28-11-generic
  29.3GB: boot/initrd.img-2.6.28-14-generic
  29.4GB: boot/vmlinuz-2.6.28-11-generic
  29.4GB: boot/vmlinuz-2.6.28-14-generic
  29.3GB: initrd.img
  29.4GB: initrd.img.old
  29.4GB: vmlinuz
  29.4GB: vmlinuz.old
```

**and the fdisk results for the R52:**

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa266a266

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2616    21012988+   7  HPFS/NTFS
/dev/sda4            2617        3832     9767520    5  Extended
/dev/sda5            2617        3589     7815591   83  Linux
/dev/sda6            3590        3832     1951866   82  Linux swap / Solaris

```

T30 fixed. 

Now R52. No boot W7 only Jaunty.

[SIZE="4"]Can this day get any stranger??!!![/SIZE]

---

### Post by merlinus on 2009-08-10
ntldr is used by xp, but bootmgr is for vista and 7.  You might try reinstalling 7 to the mbr via recovery mode (/fixmbr and/or /fixboot, or something like that), and then fix grub.

But first try changing this:

title        Windows 7 (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1

to this:

title        Windows 7 (loader)
rootnoverify    (hd0,0)
savedefault
chainloader    +1

---

### Post by talsemgeest on 2009-08-10
Yes, after you have tried merlinus's suggestion, you should reinstall the windows bootloader, before reinstalling grub. Run through the instructions (the ones for vista should work on win7) [here]("http://ubuntuforums.org/showthread.php?t=1014708"), then the ones for Ubuntu on the same post.

---

### Post by emeraldgirl08 on 2009-08-10
Merlin. I'm only 45 mins from New Mex!

Meet me in Gallup!

:lolflag:

jp. This whole deal is trying my patience!

I loaded my W7 disk and had it automatically fix my W7 boot.

It fixed it but there wasn't any Linux.

I added it with EasyBCD but it asked me insert system disk. I edited and upon reboot. I get grub>. Is there a way to modify the part from this prompt???

So far the Lappy is booting with Windows version of Grub. I have the screen like this when boot menu comes up:

Windows 7
Ubuntu Jaunty 9.04

From grub> I'm able to type HELP and a whole list of commands come up. I don't know if I would be able to set this up so I could just use that Windows bootloader and be able to enter into Linux.

---

### Post by talsemgeest on 2009-08-10
> **emeraldgirl08 said:**
> Merlin. I'm only 45 mins from New Mex!

Meet me in Gallup!

:lolflag:

jp. This whole deal is trying my patience!

I loaded my W7 disk and had it automatically fix my W7 boot.

It fixed it but there wasn't any Linux.

I added it with EasyBCD but it asked me insert system disk. I edited and upon reboot. I get grub>. Is there a way to modify the part from this prompt???

So far the Lappy is booting with Windows version of Grub. I have the screen like this when boot menu comes up:

Windows 7
Ubuntu Jaunty 9.04

From grub> I'm able to type HELP and a whole list of commands come up. I don't know if I would be able to set this up so I could just use that Windows bootloader and be able to enter into Linux.
Now all you have to do is reinstall the grub to the mbr. Just follow the instructions in [my tutorial](http://ubuntuforums.org/showthread.php?t=1014708) and you should be fine.

---

### Post by emeraldgirl08 on 2009-08-10
> Now all you have to do is reinstall the grub to the mbr. Just follow the instructions in my tutorial and you should be fine.

Should I delete the Linux entry off the easybcd first? Or is it a moot point?

---

### Post by talsemgeest on 2009-08-10
> **emeraldgirl08 said:**
> Should I delete the Linux entry off the easybcd first? Or is it a moot point?
You could if you don't want the win7 boot menu coming up every time you want to boot into windows, but it is not entirely necessary.

---

### Post by merlinus on 2009-08-10
If still stuck, try this:

```
sudo grub 
root (hd0,4)
setup (hd0)
quit
```and restart.

I live a bit east of Santa Fe, so Gallup is several hours away.  Someday, though...

---

### Post by emeraldgirl08 on 2009-08-10
:popcorn:

I'm SO glad!!!!

It's working nicely through GRUB now!

I tried both OS' and they work :)

Since I have that weird menu listing on my T30 I think I might be able to fix it with all the knowledge I've accumulated now!

Group hug guys!

{{{{{{{{{hugs}}}}}}}}}}}

bye bye.

	:grin:

---

### Post by merlinus on 2009-08-10
Great news!  The day is better already...

Hugs back attya...

---

### Post by presence1960 on 2009-08-10
Emerald, I know you worked really hard at getting this working, a lot of people would have given up blasting Linux in the process. And the result would be no knowledge gained and back to windows. But you stuck it out and when it all settles in you will have a lot of knowledge about booting you didn't have prior.

Enjoy your Ubuntu dual boot!

---

### Post by talsemgeest on 2009-08-11
> **emeraldgirl08 said:**
> :popcorn:

I'm SO glad!!!!

It's working nicely through GRUB now!

I tried both OS' and they work :)

Since I have that weird menu listing on my T30 I think I might be able to fix it with all the knowledge I've accumulated now!

Group hug guys!

{{{{{{{{{hugs}}}}}}}}}}}

bye bye.

	:grin:
Haha, glad you got it working :)

---

