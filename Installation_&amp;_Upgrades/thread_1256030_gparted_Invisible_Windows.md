---
title: "gparted: Invisible Windows"
date: 2009-09-02
forum: Installation &amp; Upgrades
---

### Post by tombacker on 2009-09-02
I have (what was) a dual boot boot laptop (a Dell Latitude D430) with Windows XP and Jaunty installed on a logical drive (sda5).

Since XP had become terribly slow I had XP reinstalled, which of course made the grub loader vanish.  From here on I thought I had two alternatives, (a) reinstall Ubuntu in the same logical drive as before (somewhat time-consuming, but not really a big problem), or (b) somehow reinstall grub in order to get the initial menu for a dual boot.

The problem with the first one is that I am told by the gparted part of the installation (I have both a live DVD and a normal installation CD) that there are no other operating systems on the machine.  In other words, gparted does not see see the first two NFTS partitions (sda1 and sda2) with Windows XP. It seems to assume that there is only one partition.

The second alternative would be preferred (I am lazy), but I am not able to find any directions to do so.

Any suggestions?

Tom

---

### Post by tommcd on 2009-09-02
A quick search of the ubuntu forums would find many threads on how to reinstall grub to the MBR from the Ubuntu live CD after reinstalling Windows. Here is one:
[http://ubuntuforums.org/showthread.php?t=224351&highlight=fsck](http://ubuntuforums.org/showthread.php?t=224351&highlight=fsck)
Write back if you need more help.

---

### Post by presence1960 on 2009-09-02
> **tommcd said:**
> A quick search of the ubuntu forums would find many threads on how to reinstall grub to the MBR from the Ubuntu live CD after reinstalling Windows. Here is one:
[http://ubuntuforums.org/showthread.php?t=224351&highlight=fsck](http://ubuntuforums.org/showthread.php?t=224351&highlight=fsck)
Write back if you need more help.

+1

No more than a 45 second process.

---

### Post by tombacker on 2009-09-02
Thank you, that link looked useful.  I started grub and managed to locate stage1 with the find command (in this case hd0,5).  However, when I entered the setup (hd0) I get 

 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,5)/boot/grub/stage2
/boot/grub/menu.lst"... failed

Error 22: No such partition

A little scary, no?

Anyhow, when I tried a new boot, no menu appeared.  Right into Windows.

Tom

---

### Post by presence1960 on 2009-09-02
No not scary We need more info.

Let's get a better look at your setup. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by stinger30au on 2009-09-02
what a pitty you ran these commands already and did not backup the config file

i bet it could have been easily repaired with super grub disc


[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by tombacker on 2009-09-02
Here are the results from the script:

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x95919591

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    51,215,219    51,215,157   7 HPFS/NTFS
/dev/sda2          51,215,220   179,815,544   128,600,325   7 HPFS/NTFS
/dev/sda3         179,815,545   234,436,544    54,621,000   5 Extended
/dev/sda5         179,815,671   234,034,919    54,219,249  83 Linux
/dev/sda4         234,050,985   234,436,544       385,560  82 Linux swap / Solaris

/dev/sda3 overlaps with /dev/sda4

blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="BC505B92505B51EE" TYPE="ntfs" 
/dev/sda2: UUID="20C4FBC1C4FB976E" LABEL="Data" TYPE="ntfs" 
/dev/sda4: TYPE="swap" UUID="6e296bbb-350b-4457-a11b-7bdde9f36c84" 
/dev/sda5: UUID="09cb76b0-84c0-48ae-98f8-ee068218c42a" TYPE="ext4" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-13-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-13-generic/volatile type tmpfs (rw,mode=0755)
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


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


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
default		4
#default		0

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
# kopt=root=UUID=09cb76b0-84c0-48ae-98f8-ee068218c42a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=09cb76b0-84c0-48ae-98f8-ee068218c42a

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

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		09cb76b0-84c0-48ae-98f8-ee068218c42a
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=09cb76b0-84c0-48ae-98f8-ee068218c42a ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		09cb76b0-84c0-48ae-98f8-ee068218c42a
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=09cb76b0-84c0-48ae-98f8-ee068218c42a ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, memtest86+
uuid		09cb76b0-84c0-48ae-98f8-ee068218c42a
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
# / was on /dev/sda6 during installation
UUID=09cb76b0-84c0-48ae-98f8-ee068218c42a /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=6e296bbb-350b-4457-a11b-7bdde9f36c84 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  97.5GB: boot/grub/menu.lst
  92.1GB: boot/grub/stage2
  93.6GB: boot/initrd.img-2.6.28-11-generic
  95.5GB: boot/initrd.img-2.6.28-14-generic
  96.9GB: boot/initrd.img-2.6.28-15-generic
 100.7GB: boot/vmlinuz-2.6.28-11-generic
  92.6GB: boot/vmlinuz-2.6.28-14-generic
  96.6GB: boot/vmlinuz-2.6.28-15-generic
  92.3GB: grub/stage2
  96.9GB: initrd.img
  95.5GB: initrd.img.old
  96.6GB: vmlinuz
  92.6GB: vmlinuz.old

Tom

---

### Post by springer_a on 2009-09-02
> **tombacker said:**
> Here are the results from the script:

(...)

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x95919591

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    51,215,219    51,215,157   7 HPFS/NTFS
/dev/sda2          51,215,220   179,815,544   128,600,325   7 HPFS/NTFS
/dev/sda3         179,815,545   234,436,544    54,621,000   5 Extended
/dev/sda5         179,815,671   234,034,919    54,219,249  83 Linux
/dev/sda4         234,050,985   234,436,544       385,560  82 Linux swap / Solaris
[COLOR=Red]
**[SIZE=2]/dev/sda3 overlaps with /dev/sda4[/SIZE]**[/COLOR]

(...)

Tom

Here is your problem. The overlapping partitions render your partition table invalid. That is why gparted and grub assume that the disk is not partitioned. But the fdisk utility which is used to produce the output above doesn't care. So it should be possible to delete the swap partition using fdisk. Then the partition table would be valid again and you could use gparted to create a new swap partition without the overlap. And with a valid partition table you should be able to set up grub again.

To use fdisk, run
```
fdisk /dev/sda
```in the terminal. But be careful as this tool works on quite a low level. So it might be a good idea to backup partition table and MBR first.

---

### Post by tombacker on 2009-09-02
I must admit that that is somewhat strange, Ubuntu ran just fine before I reinstalled Windows.  Anyhow, you say: "So it might be a good idea to backup partition table and MBR first." 

Now how do I do that?

---

### Post by presence1960 on 2009-09-02
Don't install yet. You used the wrong partition when you ran those commands. Do this:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,4)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,4)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

In # 6 use setup (hd0)

```
Ubuntu is on sda5 which is (hd0,4) **not (hd0,5)**that is why it was not found. Your ubuntu install is intact you just need to put GRUB on MBR.

See here:
Checking if "/boot/grub/stage1" exists... yes
Checking if "/boot/grub/stage2" exists... yes
Checking if "/boot/grub/e2fs_stage1_5" exists... yes
Running "embed /boot/grub/e2fs_stage1_5 (hd0)"... 17 sectors are embedded.
succeeded
Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p [COLOR="Red"](hd0,5)[/COLOR]/boot/grub/stage2
/boot/grub/menu.lst"... failed

Remember in GRUB numbering for disks and partitions starts with the number 0. sda1 = (hd0,0), sda2 = (hd0,1), sda3 = (hd0,2), etc

---

### Post by springer_a on 2009-09-02
> **tombacker said:**
> I must admit that that is somewhat strange, Ubuntu ran just fine before I reinstalled Windows. 
Indeed that's strange, so far the only time I saw overlapping partitions was with the vista partitioning tool and some weird OEM setup. But it is quite possible that your ubuntu ran just fine even with that error.

About backing up the MBR, had to use google as a reminder but here you go:

To backup both, boot a live cd and run:
```
dd if=/dev/sda of=/path/to/an/usbdrive/mbrBackup bs=512 count=1
```Remember to replace the dummy path following the of parameter above by the path to some usb key or similar.

If you need to restore your backup, boot again from the live cd and run
```
dd if=/path/to/an/usbdrive/mbrBackup of=/dev/sda bs=512 count=1
```Again you have to adjust the path to the file in which the backup is stored.

---

### Post by tombacker on 2009-09-02
Thanks!  I'll look into it later, have to leave for now.

Tom

---

### Post by tombacker on 2009-09-02
presence1960 wrote:

"Remember in GRUB numbering for disks and partitions starts with the number 0. sda1 = (hd0,0), sda2 = (hd0,1), sda3 = (hd0,2), etc".

Yes, I have understood that.  The problem is that the find operation tells me that /boot/grub/stage1 is on (hd0,5).  I know that Linux is on sda5, since if I enter:

```
root@ubuntu:~# mount /dev/sda5 /root
root@ubuntu:~# ls /root
bin    etc         initrd.img.old  mnt   sbin     tmp      vmlinuz.old
boot   grub        lib             opt   selinux  usr
cdrom  home        lost+found      proc  srv      var
dev    initrd.img  media           root  sys      vmlinuz
```

So, by that logic I should type root (hd0,4).  That gives the following output in grub:

```
grub> find /boot/grub/stage1
 (hd0,5)

grub> root (hd0,4)

grub> setup (hd0)

Error 17: Cannot mount selected partition
```

While doing the same when referring to hd0,5 gives the message I posted above.  It seems that there are some error in counting somewhere.  Could that be caused by the overlap?  See:

```
ubuntu@ubuntu:~$ sudo fdisk /dev/sda

The number of cylinders for this disk is set to 14593.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)
omitting empty partition (5)

Command (m for help): p

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95919591

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3188    25607578+   7  HPFS/NTFS
/dev/sda2            3189       11193    64300162+   7  HPFS/NTFS
/dev/sda3           11194       14593    27310500    5  Extended
/dev/sda4           14570       14593      192780   82  Linux swap / Solaris
/dev/sda5           11194       14568    27109624+  83  Linux
```

Here one partition is omitted, since it is empty.

Tom

---

### Post by tommcd on 2009-09-03
Try deleting that swap partition on /dev/sda4 as Springer_a suggested. Then see if you can reinstall grub from the Ubuntu live CD. Once you get back into Ubuntu you can then create a new swap partition with a GPArted or Parted Magic live CD.

---

### Post by tombacker on 2009-09-03
> **tommcd said:**
> Try deleting that swap partition on /dev/sda4 as Springer_a suggested. Then see if you can reinstall grub from the Ubuntu live CD. Once you get back into Ubuntu you can then create a new swap partition with a GPArted or Parted Magic live CD.
I did just that.  But I was very cautious, being new to Linux, so I did not want to run the risk of damaging my Windows partitions by using fdisk which I thought was somewhat dense in respect to documentation.  So I logged on to Windows and disk management.  There I deleted the last partition, and WHAM, everything but the Windows partitions was unallocated space.

Too bad, but not catastrophic.  It has taken me a few hours to restore everything, no big problem.

The interesting thing about the whole affair is that the moment the overlapping partitions was removed, gparted showed the correct partitions (alas, without my installation of Ubuntu), rather that saying that I than no other operating systems as it did before this operation.

I must admit that I cannot see how (a) I managed to generate overlapping partitions in the first place.  This must have been done with gparted at least a year ago, and  (b) why this situation cropped up at the same time as I had the first partition (alone) replaced with a new Windows XP installation.

On the other hand, I did install Ubuntu 9.04 on these partitions together with the former version of Windows XP a few weeks ago without any problems whatsoever.

I wondered whether the gparted program itself perhaps had beed modified in the past two weeks.  Therefore I tried downloading Ubuntu 8 earlier today and then used the live version.  No change in what gparted saw there.  So that is (probably) not the cause, unless that build has been generated in the past few weeks.  Somehow there must be a link to the fact that the first partition had been reformatted as a consequence of the re-installation.

My conclusion is that this is not really a bug in gparted, but perhaps a lack of a feature(s).  In some way or another I should have been informed that this problem existed, and what I possibly could have done about it.  To remove or replace a swap partition is not a big problem, but to loose a complete installation is a different matter altogether.  Admittedly, I did that I Windows, but I felt that I had few other options.  In this case it was not a problem for me (for me computers are completely neutral, but in a slightly malicious manner, therefore it pays to be slightly paranoid), but it could be for others.

In any case, somewhat weird.

Tom

Tom

---

### Post by tommcd on 2009-09-04
You should not use Windows disk management to alter linux partitions. Windows can't even read linux partitions, so it can not properly deal with them.

I don't know how the overlapping partitions were created. 
I have never had any problems setting up partitions with the Ubuntu installer. If I need to alter partitions after Ubuntu is instslled, I like to use the Parted Magic live CD:
[http://partedmagic.com/](http://partedmagic.com/)

---

### Post by tombacker on 2009-09-04
> **tommcd said:**
> You should not use Windows disk management to alter linux partitions. Windows can't even read linux partitions, so it can not properly deal with them.

I don't know how the overlapping partitions were created. 
I have never had any problems setting up partitions with the Ubuntu installer. If I need to alter partitions after Ubuntu is instslled, I like to use the Parted Magic live CD:
[http://partedmagic.com/](http://partedmagic.com/)
I do not believe in the argument about Windows not knowing about Linux.  We are talking about partitions, not the content.  The fact remains that Windows saw the five partitions and that two of the three non-NFTS partitions had some content. 

Under Linux, gparted did not see anything, neither the Windows nor the Linux ones.

Tom

---

