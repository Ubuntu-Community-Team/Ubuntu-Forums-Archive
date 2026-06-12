---
title: "Can't write to an HFS+ external USB 2.0 HDD"
date: 2006-07-09
forum: Hardware &amp; Laptops
---

### Post by LoneIgadzra on 2006-07-09
My Windows installation recently bit the dust (due to totally mysterious reasons, possibly relating to the usage of RegCleaner and/or the uninstallation of Blindwrite without rebooting - basically it just sits at the XP logo running its little blue bar forever) and I need to backup many many GB of data before I reformat and reinstall. The only way I have to do this is a 120 GB external HFS+ formatted USB 2.0/firewire hard drive and my Dapper installation (on a partition on the Windows drive, so I'll to back it up as well since my last Windows installation totally wiped Linux despite me doing my utmost not to mess with the Linux partitions). Allegedly Dapper has some software installed to read and write HFS volumes, but that seems not to be the case. The drive mounts on my desktop just fine, and by all appearances I am the owner, have full write permissions, and even the mtab file claims it is mounted as writeable:

> /dev/hda5 / ext3 rw,errors=remount-ro 0 0 
 proc /proc proc rw 0 0 
 /sys /sys sysfs rw 0 0 
 varrun /var/run tmpfs rw 0 0 
 varlock /var/lock tmpfs rw 0 0 
 procbususb /proc/bus/usb usbfs rw 0 0 
 udev /dev tmpfs rw 0 0 
 devpts /dev/pts devpts rw,gid=5,mode=620 0 0 
 devshm /dev/shm tmpfs rw 0 0 
 lrm /lib/modules/2.6.15-25-386/volatile tmpfs rw 0 0 
 /dev/hda1 /media/hda1 ntfs rw,nls=utf8,umask=007,gid=46 0 0 
 /dev/hdb1 /media/hdb1 ntfs rw,nls=utf8,umask=007,gid=46 0 0 
 **/dev/sda1 /media/sda1 hfsplus rw,noexec,nosuid,nodev,uid=1000,gid=1000 0 0**
 /dev/hdc /media/cdrom0 iso9660 ro,noexec,nosuid,nodev,user=william 0 0

However that seems not to be the case. I simply cannot write to the drive, and get a very terse error message every time I try. E.g.:

```
william@hal:/$ sudo mount -o remount,rw /media/sda1/ 
 william@hal:/$ cd /media/sda1 
 william@hal:/media/sda1$ mkdir backup 
 mkdir: cannot create directory `backup': Read-only file system 
```

Here's from dmesg: ```
[17186529.492000] HFS+-fs: Filesystem is marked journaled, leaving read-only.
```

Is there any way to get this to work, or is this the same deal as NTFS or something depressing like that? (Formatting the drive is not an option. There's already stuff on it that would be extremely troublesome to lose.) The HDD itself is ridiculously generic. All it says on the side is "Disk Go by Edge".

---

### Post by LoneIgadzra on 2006-07-09
**Update:** Nevermind, found the solution in OS X:

```
diskutil disableJournal volumeName
```

---

### Post by bhuot on 2006-08-04
The following is the exact command I gave

```
diskutil disableJournal "/Volumes/LaCie Disk"
```

The following is the exact response I got

```
Journaling has been disabled on /Volumes/LaCie Disk
```

I am on to trying it on Ubuntu 6.06 to see if it works.

Thanks for the tip.

I also tried it with Disk Utility graphically but it didn't work that way.

---

### Post by LoneIgadzra on 2006-08-05
Yikes, I should have updated this topic. After I disabled journaling, the Linux mounting of the drive continued to be totally borked, though at the time I was probably too 'vigorous' in getting it to be writeable, since I didn't know that 'chown'-ing a drive from root to my name would stick. Then I plugged it back into the Mac and it was unreadable. Somehow Linux had messed up the formatting. Luckily it was still readable in Linux and I was able to get my stuff off it and reformat it as FAT32.

In summary, be careful. I probably did something wrong in my infuriated attempts to make the drive writeable in Linux, but then again maybe not.

---

