---
title: "Vista boot menu problem."
date: 2009-02-22
forum: Installation &amp; Upgrades
---

### Post by Dakings on 2009-02-22
Ever since I installed Windows Vista(about a year ago now) the boot menu will not display anything but Vista. I've tried various distros of Linux, all are the same way. I have also tried going into Windows repair and doing both a fixboot and fixmbr. I've even tried using a separate hdd for the different OS, and that still doesn't do anything. Lastly, I even reformatted my hdd and reinstalled Vista fresh, and still it won't display anything but Vista at the boot screen.

What I find weird is when I go into System Startup and Recovery it displays both Winodws Vista and Ubuntu, but in Msconfig it only displays Vista.

Also should mention... When I had Windows XP installed, Ubuntu was one of my boot choices, once I upgraded to Vista, thats when Ubuntu disappeared from the boot menu.

Any ideas on what can fix this?

---

### Post by caljohnsmith on 2009-02-22
In order to get a clearer picture of your setup, how about booting your Ubuntu Live CD (the Ubuntu install CD), download the **Boot Info Script** to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by Dakings on 2009-02-22
Alright...  And as for the Opensuse listed, its not really there.  You enter it and it tells you to run Windows Repair.

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda1 has 
                       622535180 sectors, but according to the info from 
                       fdisk, it has 625140337 sectors.
    Mounting failed:
Failed to read last sector (622535180): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
Failed to read last sector (622535180): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /ntldr /NTDETECT.COM 
                       /wubildr.mbr

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0cd0b419

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   625,140,399   625,140,337  42 SFS

/dev/sda1 ends after the last cylinder of /dev/sda

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9d5e9d5e

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   156,299,364   156,299,302   7 HPFS/NTFS

/dev/sdb1 ends after the last cylinder of /dev/sdb

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="94A8CB6EA8CB4E04" TYPE="ntfs" 
/dev/sdb1: UUID="CCB846CBB846B42C" TYPE="ntfs" 
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


================================ sdb1/boot.ini: ================================

[boot loader]

timeout=30

[operating systems]

C:\grldr="openSUSE 11.1 installer (LOCAL)"

```

---

### Post by caljohnsmith on 2009-02-22
It looks like you tried to do a Wubi install, or install Ubuntu inside of Windows, but your installation was not successful. If you want to install Ubuntu inside of Vista, you'll probably have to turn off all of Vista's security checks an also all of your anti-virus software. Did you intend to install Ubuntu in Windows, or did you want to give Ubuntu its own partition?

---

### Post by Dakings on 2009-02-22
I've actually done it both ways. Inside Windows with Ubuntu installer and straight from the CD.  And yes, I do intend to give Ubuntu its own partition.

---

### Post by caljohnsmith on 2009-02-22
So which drive do you want to install Ubuntu to, your 320 GB sda drive or your 80 GB Vista sdb drive? Also, what is on partition sda1? The file system is listed as SFS.

---

### Post by Dakings on 2009-02-22
On the 320gb harddrive.  I believe the sd1 is what is suppose to be the Ubuntu installation.

Everything else on that Hard drive is games, music, and movies.  I have the ability to back all of it up if needed.

---

### Post by caljohnsmith on 2009-02-22
Are you sure you can still access all your personal files on the 320 GB drive? For one thing, the file system appears to be NTFS, so you should probably change the "SFS" file system ID back to NTFS. You can do that with:
```
sudo sfdisk -c /dev/sda 1 7
```
But the script was not able to mount the sda1 partition, so can you access that partition in Vista still?

---

### Post by Dakings on 2009-02-22
Yes, I can still acess all of it.  On that drive, it creates a "Ubuntu" folder which size is 15gb(the partition size I gave it when installing from the cd).  I can acess the folder and all the files inside of it.

However, right now running Ubuntu from the cd, it won't let me access the drive.  I ran the line of code you gave.

---

### Post by caljohnsmith on 2009-02-22
It looks like the boot sector of that sda1 partition might need fixing, which maybe is part of the reason why Ubuntu can't mount that partition. I would recommend using testdisk to see if it needs fixing:
```
sudo apt-get install testdisk
sudo testdisk /dev/sda1
```
After starting testdisk, choose "Proceed", "None", "Advanced", "Boot", then choose "Rebuild BS"; if testdisk gives you a warning that the "Extrapolated boot sector and current boot sector are different", then choose "Write". After that, please post the output of:
```

sudo ntfsresize -if /dev/sda1
sudo mount -t ntfs-3g /dev/sda1 /mnt && ls -l /mnt
```

---

### Post by Dakings on 2009-02-22
It says "E: Couldn't find package testdisk" when trying to run the first line of code.

---

### Post by caljohnsmith on 2009-02-22
First make sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then try running the apt-get/testdisk commands again.

---

### Post by Dakings on 2009-02-22
Well something I did rewrote the drive to FAT32.  I am going to just reformat the drive, everything important was already backed up, so I didn't lose anything.

---

### Post by caljohnsmith on 2009-02-22
As long as you plan on reformatting, I would suggest using gparted (System > Admin > Partition Editor) to do the reformatting, and also I would use gparted to set up your Ubuntu partitions so they will be ready for the installer. Here is a tutorial on using gparted to set up the Ubuntu partitions:

[http://mywebsite.bigpond.net.au/dfelderh/linuxmaniac/p22.html](http://mywebsite.bigpond.net.au/dfelderh/linuxmaniac/p22.html)

Let me know how that goes.

---

### Post by Dakings on 2009-02-22
Alright thanks, you've been a great help.

---

### Post by Dakings on 2009-02-22
It works it works!  Thanks so much :).

---

### Post by caljohnsmith on 2009-02-22
Glad to hear you were able to install Ubuntu successfully; cheers and enjoy Ubuntu. :)

---

