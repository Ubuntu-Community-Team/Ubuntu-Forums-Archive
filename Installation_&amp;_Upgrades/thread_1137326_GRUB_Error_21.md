---
title: "GRUB Error 21"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by AlienDK on 2009-04-25
Some days ago I installed Ubuntu on my laptop, works perfectly! But then I wanted to install it on my desktop, but I still need WinXP cause I got alot of stuff on it (incl. games I've lost the disc or cd-key for :(). So while installing I chose "Run side by side with other OS" or something like that, but when I booted, it came up with this GRUB Error 21. I searched for it and apperently its something with some .inf file or something :S. But I'm really a newb at Linux so I'm really lost here. So if someone could help me solve this I would be *very* happy :).

---

### Post by AlienDK on 2009-04-25
Bump.. I seriously need help. I'm kinda worried about loosing all my stuff :/.

---

### Post by AlienDK on 2009-04-25
Bump

---

### Post by SrWrangler on 2009-04-25
Hi.

I'm kind of new also.  I got the same problem, but I have Mint 6 XFCE on the other partition. Can you get to the grub menu?  If so, choose recovery mode, then fix broken packages, then normal boot into Ubuntu. If that works, try rebooting into windows.

Hope this helps.

---

### Post by AlienDK on 2009-04-26
well, I tried booting with a supergrub disc, and I can get to some menu, probably the grub menu, so I'll try :)

---

### Post by meierfra. on 2009-04-26
In order to get a clearer picture of your setup, I suggest to boot from the Ubuntu LiveCD and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post,  highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by AlienDK on 2009-04-27
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x04f104f1

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   614,405,924   614,405,862   7 HPFS/NTFS
/dev/sda2         614,405,925   976,751,999   362,346,075   f W95 Ext d (LBA)
/dev/sda5         614,405,988   976,751,999   362,346,012   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="743CD7623CD71DC4" TYPE="ntfs" 
/dev/sda5: UUID="DEB83D5DB83D34FD" TYPE="ntfs" 

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
/dev/sda1 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5 on /media/disk-1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=AlwaysOff /fastdetect 
```

---

### Post by meierfra. on 2009-04-27
> dev/sda1    *             63   614,405,924   614,405,862   7 HPFS/NTFS
/dev/sda2         614,405,925   976,751,999   362,346,075   f W95 Ext d (LBA)
/dev/sda5         614,405,988   976,751,999   362,346,012   7 HPFS/NTFS


How many hard drive you have?  

RESULTS.txt only shows one hard drive with two ntfs partitions. So no trace of ubuntu on your 500GB drive.

On the other hand it seems that you had Ubuntu installed  on a second hard drive:


> Grub0.97 is installed in the MBR of /dev/sda and [COLOR="Red"]looks on boot drive #2 in [/COLOR]
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.


Do you  have an external drive which was not plugged in while you run the Boot Info Script?

To be able to boot into XP, I recommend to install a Windows type MBR.

Here are two ways to do that

1)  Boot from the XP CD, press "r" to get to the repair console and then type

```
fixmbr
exit
```

2)  Boot from the Ubuntu Live CD, open a terminal and type

```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

---

### Post by AlienDK on 2009-04-28
I reinstalled WinXP (it was starting to run slow anyways). Thanks for helping tho :)

---

