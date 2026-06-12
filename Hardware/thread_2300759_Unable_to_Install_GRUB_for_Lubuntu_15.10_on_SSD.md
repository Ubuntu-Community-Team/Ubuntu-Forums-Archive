---
title: "Unable to Install GRUB for Lubuntu 15.10 on SSD"
date: 2015-10-28
forum: Hardware
---

### Post by cobalt2 on 2015-10-28
I set up identical partitions for boot, home, root, and swap, and bridged them together with RAID arrays. The boot partitions with RAID 1 and the other 3 with RAID 0. Using the Lubuntu Alternate Installation, when trying to install the boot loader, it says the GRUB bootloader could not be installed. I was following the advice of the Ubuntu Official Documentation on Linux Software RAID found [here]("https://help.ubuntu.com/community/Installation/SoftwareRAID"). How do I get the bootloader on to the boot partition. Any advice or suggestion are greatly appreciated.

---

### Post by cobalt2 on 2015-10-28
I am using the Ubuntu 14.04  LIve CD in order to  install the GRUB on a  fakeRAID SSD. I tried to install the GRUB to my  SSD using the Lubuntu  15.10 Alternate Installation installer. The GRUB  installation appeared  to be successful, however when I restarted my  computer, I got an error  message:
```
Disk read error. Press Ctrl+Alt+Delete to restart.
```
Now I need mdadm in order to assemble the RAID arrays in Ubuntu 14.04 Live CD mode. It is not installed by default. When I try to install mdadm with apt-get install mdadm, instead of offering me the mdadm for Linux Software RAID, it offers something else. How to install mdadm in Ubuntu 14.04 Live?

---

### Post by oldfred on 2015-10-28
I do not know RAID, but believe this is the driver:
 sudo apt-get install lvm2

      
 LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
[http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html](http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html)
2014_02_22_Preparing Logical Volumes For Ubuntu Installations
[http://members.iinet.net/~herman546/2014_02_22_Preparing%20Logical%20Volumes%20For%20Ubuntu%20Installations.html](http://members.iinet.net/~herman546/2014_02_22_Preparing%20Logical%20Volumes%20For%20Ubuntu%20Installations.html)
[http://askubuntu.com/questions/470632/install-lvm-dual-boot-with-windows](http://askubuntu.com/questions/470632/install-lvm-dual-boot-with-windows)

---

### Post by cobalt2 on 2015-10-28
It's a OCZ Revodrive 3 PCIe. For this SSD, the RAID configuration is required in order to work properly with GNU Linux. It is a 120 GB disk consisting of two 60 GB sections. In BIOS it is 1 120 GB disk, while Ubuntu sees it as 2 60 GB drives.

---

### Post by weatherman2 on 2015-10-28
I don't understand why RAID is required?  What happens if you have a single 120GB partition (insteadof two 60GB)? Where do you get stuck?

You're getting no benefit to this type of RAID: no speed increase and no redundancy.  For either you'd need two separate devices, unless you can explain otherwise.

---

### Post by cobalt2 on 2015-10-28
Naturally the OS sees the SSD as 2 60 GB disks. In order to bridge them together as a whole disk, I need to create a RAID 0 array, using the mdadm --assemble command.

---

### Post by weatherman2 on 2015-10-28
Still don't get why you can't have one 120GB partition?  What is imposing that limitation?  What causes it to be limited to 60GB max partition size?

Even if I had two separate 60GB disks, I'd consider combining them into a single 120GB volume using LVM not RAID.

---

### Post by cobalt2 on 2015-10-28
> What happens if you have a  single 120GB partition (insteadof two 60GB)? Where do you get stuck?
I tried installing Ubuntu 15.10 on one of the 60 GB disks of the SSD, and the installer crashed in the middle of the installation. 

I want to see if I could get RAID configured, if not I'll use LVM.

---

### Post by Vladlenin5000 on 2015-10-28
Still don't get why you think you must keep that setup... I would remove those partitions and create new ones or just let the installer take care of it. If you don't intend to do any sort of dual boot that's all you need.

---

### Post by cobalt2 on 2015-11-05
Vladlenin and Weatherman:
Ultimately I took your advice. Using GParted, I removed all the partitions on the ssd, and created an ext4 primary boot partition (96 MiB). I thought it would be a good idea to have a backup boot, so I similarly formatted a 1 GB flash drive. Then in the Lubuntu installer, I formatted the unallocated space as LVM, and partitioned it into home, os (5 GB) and swap (4GB). I installed the grub into mbr of the 1st drive of the ssd. When I tried to install grub into the mbr of the flash drive, it failed. I booted from the ssd and was taken to the grub rescue. Then I tried installing grub to the partitions. I was able to install grub to the partitions of these drives. When booting from the flash drive I got the error "Missing operating system." Insert system disk and press enter. I tried using Boot Repair to install GRUB to the mbrs and to the partitions and had the same problems. Then I tried installing grub to a hd. I installed grub to the mbr. When that didn't work, I tried to install to the partition. The option remove and reinstall kernel was checked, and could not be unchecked. I knew this would be a problem, because whenever I run Boot Repair with this option force checked, the app gets stuck on 'Purge and reinstall kernel.' So I copied all files from ssd boot to hd boot. Then I used boot repair to purge and reinstall grub. 

I restarted the computer and was at long last, presented with the grub menu. I edited the 'Ubuntu' menu entry, replacing all references to (hd0,msdos1) with (hd1,msdos5): the partition where the os is located, pressed ctrl +x, and waited for the os to startup. After doing a filesystem check, I got this message:
```

Welcome to emergency mode!
root@BM:~#

```
I typed 'exit' in the shell, and the os started up once again. When it failed, I got this error:
```

Error getting authority: Error initializing authority: Could not connect: No such file or directory (g-io-error-quark, 1)
Welcome to emergency mode!
root@BM:~#

```

I edited the grub to check if update-grub works. The output was:
```

Generating grub configuration file...
Found linux image: /boot/vmlinuz-4.2.0-16-generic
Found initrd image: /boot/initrd.img-4.2.0-16-generic
EXT4-fs (sdb2): unable to read superblock
FAT-fs (sdb2): bogus number of reserved sectors
qnx4: no qnx4 filesystem (no root dir).
ufs: You didn't specify the type of your ufs filesystem
mount -t -ufs -o -ufstype= sun|sunx86|44bsd|ufs2|5xbsd|old|hp...
>>>WARNING<<< Wrong ufs filetype may corrupt your filesystem, default is ufstype=old

```
I'm very disappointed because I thought I would be able to set up the ssd to operate independently without relying on any external drives. Even worse, even with grub located on a hd, Lubuntu refuses to start. Anyone know how to fix this, so at least I'm able to boot from hard disk?

---

### Post by oldfred on 2015-11-05
I do not know your issues, but LVM makes it more complex.

Best to see more details:
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Do not run any autofix in Boot-Repair. It auto installs grub to every drive.
Better to use Advanced mode only with more than one drive.

---

### Post by cobalt2 on 2015-11-08
I fixed the problem by reinstalling the OS. Now Lubuntu is fully operational. Now I'm trying to figure out how to:

1. Boot from the SSD.
2. Boot from a USB flash drive as a backup.
2. How to permanently save edits made to the GRUB. Specifically, changes to the drive and partition numbers.

Boot Repair Info:
usb: paste.ubuntu.com/13077733

ssd: paste.ubuntu.com/13079694

ssd: paste.ubuntu.com/13080288

usb: paste.ubuntu.com/13085746

---

### Post by oldfred on 2015-11-09
You have grub installed to sdc.
If you just want to install grub to MBR of other drives, just do this:
       #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo parted -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

But for my flash drives, I prefer to have a full grub installed and manually create my own boot stanza. I then use flash drive to boot ISO and have a backup boot stanza for some of my installs.
      
 Examples:
Label partition - if label is grub2 & mount:
sudo grub-install --root-directory=/media/grub2 /dev/sdb
Newer versions automount with $USER name also, this one labeled MC4GB
sudo grub-install --root-directory=/media/fred/MC4GB /dev/sdb
Install grub2 2.00 boot loader to gpt partitioned flash drive from Raring (it used media/fred as mount)
mount and label is PreciseInstaller and flash is sde. Note space before /dev/sde
sudo grub-install --root-directory=/media/fred/PreciseInstaller /dev/sde

Grub uses UUID, do drive and partition numbers should not matter.

---

### Post by cobalt2 on 2016-02-09
[COLOR=#000000][FONT=Arial]> You have grub installed to sdc.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]That's the SSD. It's grub doesn't work. When I boot from it, it goes to GRUB rescue. When I list the files on the boot partition using ls (hd2,1)/, I get the error: No filesystem detected. It's a primary partition, ext4 filesystem and marked as boot. 

I was successfully able to install grub to the flash drive. Now my system boots much faster, and it's no longer dependent on a clunky HD for booting. Nonetheless, I want to have the option of booting directly from the ssd.
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]

---

### Post by oldfred on 2016-02-09
When you boot from a drive it always is hd0 as BIOS assigns boot drive as first drive.
Then other drives are usually in SATA port order.

So if in BIOS (or UEFI) you select sdc as boot drive it will be hd0. And grub installed in that drive should be seen correctly no matter what drive you boot from as it uses UUID not drive/partition.

---

### Post by cobalt2 on 2016-02-11
In BIOS, I set SSD as the first boot drive, then saved and rebooted. The boot process terminates at GRUB Rescue. The SSD grub is unrecognizable. When I query hd0,1, I receive this message: 
> Error: unknown filesystem.

---

### Post by oldfred on 2016-02-11
I do not see in your fstab mount of /home. I would think it still should boot as when /home is missing it creates a new default version.

Often unknown is either partition number/UUID is wrong or partition needs fsck. But it could be an old copy of grub looking for the old install which now does not exist.

Have you installer grub to MBR? You almost never install to partitions. You seem to be referring to partitions as "drives", but that is only Windows very confusing way where drive can be a drive or a partition. 
Linux makes it clear as you have drives like sda, sdb, sdc, and you have partitions like sda1, sdb1. And in your case you have the logical partitions or volumes in LVM.

I might try Boot-Repair's advanced mode of uninstall grub & reinstall to MBR of SSD drive.
Make sure LVM partitions are all mounted.

---

### Post by cobalt2 on 2016-04-11
It has been a long time since I last worked on this problem, but I now have some time to revisit it.

I understand the drive partition dichotomy. I use the term 'drive', because the BIOS sees the SSD as a SCSI drive. It does not recognize any partitions. To boot from SSD, I select SCSI OCZ REVODRIVE as the 1st boot drive in the BIOS settings.

> [COLOR=#000000]I might try Boot-Repair's advanced mode of uninstall grub & reinstall to MBR of SSD drive.[/COLOR]

Already tried that.

I found this tutorial explaining how to boot GNU Linux from OCZ Revodrive. The writer discusses using a RAID 0 array. Since I don't have a RAID 0 setup, It don't understand how to implement these instructions for a LVM configuration.

>     
HOW TO BOOT LINUX FROM OCZ REVODRIVE

[http://www.average.org/ssdroot/](http://www.average.org/ssdroot/)


A word of warning: be prepared to end up with unbootable system,
having to manually revive it in the grub interactive mode and in
inttiramfs's busybox. Keep manuals and howtos at hand, you won't
be able to look them up on the computer that is not running the
OS at the moment.


I did it with Revodrive 3 120 Gb. Procedure for different models
may vary.


Revodrive is a "fakeraid": it looks to Linux as two different
devices, but BIOS implements RAID0 on them, so at boot it looks
as one device. If you want grub to be able to boot from it, you
have to make Linux mdraid exactly match the BIOS RAID, then grub
will be able to see the boot filesystem.


Obviously, BIOS RAID implementation knows nothing about Linux
mdraid superblocks. So, in order to mimic the BIOS
configuration, we must make Linux RAID without superblocks, with
"mdadm --build". After setting up my system, I realized that
Linux RAID superblocks are located at the end of the devices,
so it could work with "proper" linux RAID, "mdadm --assemble".
That would simplify things a lot, and should not cause problems.
BIOS RAID would just have two last blocks containing odd data,
Linux would interpret them and RAID superblocks.


Anyway, I will be describing the "hard way" here.


In order to mount root, early userspace needs to either get the
RAID configured by the kernel, or do it itself. Kernel has a
command line attribure to configure supreblock-less RAIDs on
boot, described in Documentation/md.txt. Unfortunately, it does
not work.


So, let's add a custom script into initramfs. The easiest way is
to make it specific to our particular instance of the card.
Find which devices are the two revodrive sections:


$ ls -l /dev/disk/by-id|grep ata-OCZ-REVODRIVE
lrwxrwxrwx 1 root root  9 Mar 30 17:05 ata-OCZ-REVODRIVE3_OCZ-XXXXXXXXXXXXXXXX -> ../../sdg
lrwxrwxrwx 1 root root  9 Mar 30 17:05 ata-OCZ-REVODRIVE3_OCZ-YYYYYYYYYYYYYYYY -> ../../sdh


Apparently, factory default chunk size for the device is 64K. If
you've changed it in the maintenance tool, use that figure.


If your system uses initramfs-tools, add the following script
(under any name, e.g. "revodrive") into the directory
/etc/initramfs-tools/scripts/local-top:


===== Start script file =====
#!/bin/sh


if [ "$1" = "prereqs" ] ; then
  exit 0
fi


. /scripts/functions


wait_for_udev
mdadm --build /dev/mdN --level=0 --raid-devices=2 --chunk=64 \
        /dev/disk/by-id/ata-OCZ-REVODRIVE3_OCZ-H6O08ID5A0KR6Z69 \
        /dev/disk/by-id/ata-OCZ-REVODRIVE3_OCZ-0Q234E3G9J4Y9PR6
===== End script file =====


I suggest doing this on the live system: you will be able to (1)
check that it works, and (2) have ready initramfs images to copy
to the target drive. You can of course make the script more
generic, not bound to the particular instance of the device. Run
"update-initramfs -u" and check that the md device gets created
when you boot the system. Adding some sensible error handling to
the script might be a good idea, too.


I suggest to create disklabel and partition the raid.  Use
'-S 32 -H 32' to eusure that partitions start at "round"
bounraries vs. the flash erase blocks. This is optional, but you
will need reserved space for grub bootloader, and partitioning
ensures that there is such space, onto which the filesystems
will not try to stomp. Create partitions to your taste. Make one
partition bootable in case BIOS needs it. Note that you must
partition the md device, not the member disks, because BIOS will
see the RAID as a single disk, and expect partition table there.


Note: physically, the partition table will live in the first
chunk of the first member of the RAID, and on boot, the kernel
will "think" that the partition table belongs to the member
drive, and complain that it specifies incorrect size. This is
harmless and should be ignored.


Create filesystems, providing parameters suggested for SSD
media, for example:


# mkfs.ext4 -b 1024 -E stride=128,stripe-width=128 -O ^has_journal /dev/mdNpM


Mount all new filesystems under some point the way they will be
arranged on the target system, e.g.:


# mount -o noatime,discard /dev/md6p3 /mnt
# mkdir /mnt/boot
# mount -o noatime,discard /dev/md6p1 /mnt/boot


and copy everything you want to copy to the new place:


# cd /
# find . opt var -mount -depth -print | \
> grep -v lost+found | \
> time cpio -dumpv /mnt


Edit /mnt/etc/fstab to mount the new root and other filesystems,
and swaps. Use "dumpe2fs /dev/mdNpM | grep UUID" to find the
UUIDs, or you can safely put the devices names there, as
/dev/mdN is defined "by hand" and will never change on its own.
It is recommended to specify "noatime,discard" options for best
filesystem performance on SSD media.


Next thing, you need to convince grub installer that the RAID
is the thing that it will see as the boot disk.  Create this
entry in /mnt/boot/grub/device.map (possibly replacing the one
that was there before):


(hd0)   /dev/mdN


Prepare to do things in chrooted environment:


# mount -o bind /sys /mnt/sys
# mount -o bind /proc /mnt/proc
# mount -o bind /dev /mnt/dev
# chroot /mnt /bin/bash


In the chrooted environment:


# update-grub2 -o /boot/grub/grub.cfg
# grub-install /dev/mdN


Note that after you have switched to the new setup with root on
the SSD, when you run "update-initramfs -u" it will tell you
that because there is no /dev/mdN in mdadm.conf, your system
will be unbootable. In fact, it would have been unbootable if
you have not fixed it by including the script into initramfs.


If you go for superblock-full RAID, "mdadm --assemble", there
will be no need in a custom script in initramfs, and
"update-initramfs -u" will not complain about unbootable
system. All other steps should remain the same. But as said,
I did not actually test if this approach works.


== Eugene Crosser, 2013-04-01 (but not a joke).


---

