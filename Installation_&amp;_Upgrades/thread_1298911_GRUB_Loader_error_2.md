---
title: "GRUB Loader error 2"
date: 2009-10-23
forum: Installation &amp; Upgrades
---

### Post by JonnyCube on 2009-10-23
When I install Ubuntu 9.04 from the live CD onto my solitary, freshly-formatted hard drive, I get a GRUB Loader error 2 (disk doesn't exist) and my computer won't boot.

I've read a lot of posts about people having problems with error 2, but they all have multiple hard drive configurations and dual-boot setups. How could this be happening under such simple circumstances?

---

### Post by presence1960 on 2009-10-23
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by JonnyCube on 2009-10-23
I'm not sure how helpful this will be.  I no longer have Ubuntu installed - I did a full format and installed XP. Does that make this information useless? Should I install Ubuntu again and post results? If so, it would then be a dual-boot situation, not like the situation in my original post.

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xffffffff

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   156,232,124   156,232,062   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2032 MB, 2032664576 bytes
64 heads, 63 sectors/track, 984 cylinders, total 3970048 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                 249     3,967,487     3,967,239   6 FAT16


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="580C98FC0C98D67A" TYPE="ntfs" 
/dev/sdb1: SEC_TYPE="msdos" LABEL="NO LABEL" UUID="339C-F96B" TYPE="vfat" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
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
/dev/sdb1 on /media/NO LABEL type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn
```

---

### Post by presence1960 on 2009-10-23
you are correct that info is now absolutely useless. Sometimes you have to be a little more patient when posting a thread asking for help. We are not paid support and you may have to wait a little until someone who knows how to troubleshoot your problem comes along.

We could probably have saved your Ubuntu install as GRUB errors are fixable. That point is moot now.

---

### Post by JonnyCube on 2009-10-23
I'm sorry. I don't think you understand the situation entirely. I spent most of yesterday battling a virus on my computer. I installed both Ubuntu and Windows multiple times in my various attempts to erase the virus. I have a work deadline tomorrow that requires that I use Windows. Getting Windows running again was a huge victory.

I need Windows, but I want Ubuntu.  I tried installing it various ways, both on its own clean hard drive and on a partition on a secondary hard drive. I always get Grub error 2. Before I make another attempt (which I will do) I wondered if anyone knew why this error was occuring or what I might do about it.

I'll post the results text file up here when I get a chance to install Ubuntu again. Again, I'm sorry. I wasn't trying to give you a hard time.

---

### Post by presence1960 on 2009-10-23
> **JonnyCube said:**
> I'm sorry. I don't think you understand the situation entirely. I spent most of yesterday battling a virus on my computer. I installed both Ubuntu and Windows multiple times in my various attempts to erase the virus. I have a work deadline tomorrow that requires that I use Windows. Getting Windows running again was a huge victory.

I need Windows, but I want Ubuntu.  I tried installing it various ways, both on its own clean hard drive and on a partition on a secondary hard drive. I always get Grub error 2. Before I make another attempt (which I will do) I wondered if anyone knew why this error was occuring or what I might do about it.

I'll post the results text file up here when I get a chance to install Ubuntu again. Again, I'm sorry. I wasn't trying to give you a hard time.

No apology necessary. I didn't think you were trying to give me or anyone else a hard time.

When you are ready install Ubuntu again as  adual boot on that other disk. if you get a GRUB error run the boot info script again and post the results. GRUB errors are fixable.

Here is a list of GRUB errors including GRUB error 2 from the GRUB 0.97 manual: [http://www.gnu.org/software/grub/manual/grub.html#Stage1_002e5-errors](http://www.gnu.org/software/grub/manual/grub.html#Stage1_002e5-errors)

---

### Post by JonnyCube on 2009-10-24
In tried installing Ubuntu again alongside Windows XP. For some reason, it works perfectly now. I suspect there may have been an issue with my other hard drive.

Anyway, thank you so much for your help!

---

