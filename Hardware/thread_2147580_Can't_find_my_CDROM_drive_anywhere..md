---
title: "Can't find my CDROM drive anywhere."
date: 2013-05-22
forum: Hardware
---

### Post by A Traveller on 2013-05-22
Hi All.

As the subject says, I am having problems installing my CD-ROM drive. I am using Ubuntu 10.04 and have tried suggestions from various websites but still cannot solve the issue.

My CDROM drive doesn't show up in the 'Places' menu or in 'Disk Utility'. There is no 'cdrom' folder in the 'media' folder (only floppy and USB folders there).

This is what's in the fstab file:-

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=851bc081-8b92-4d24-8f39-2aaf09b27070 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e5b0d2bb-30ee-476e-9e3d-502d4f48afcd none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0



This is what appears if I do 'mount' in the Terminal:-

root@mypc:/home/username# mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/username/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=username)
root@mypc:/home/username# 


Any help would be appreciated!

Thanks.

---

### Post by sudodus on 2013-05-22
1. Are you running Ubuntu Server 10.04 LTS? Then it is still going strong until April 2015. But if you are running Ubuntu desktop 10.04 LTS, it passed end of life last month. So you are not getting any more security updates for the desktop specific packages.

2. But back to your question: I will tell you what it looks like in Ubuntu desktop 12.04.2 LTS:

I don't see much when the drive is empty, but there is the device [FONT=courier new]**/dev/sr0**[/FONT], where it is will be mounted, when a disk is inserted.

When a disk is there it will be mounted like this (it is a Clonezilla boot disk)

***df*** prints
```
 /dev/sr0          113134    113134            0 100% /media/2.0.1-15-i486
```

and ***mount*** prints
```
/dev/sr0 on /media/2.0.1-15-i486 type iso9660 (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500,uhelper=udisks)
```

*Edit*: You need no entry in /etc/fstab for the CD/DVD drive to work

---

### Post by A Traveller on 2013-05-22
Hi sudodus. Thanks for your reply. I am running  Ubuntu desktop 10.04 LTS and the reason I wanted my CDROM now was that I wanted to install 12.04 via CD, haha.

I had inserted a blank disc so that I could burn the 12.04 iso to and have left the disc there, so there is a disc in the drive.

I do not understand what I need to do with the info you've posted.

Thanks.

---

### Post by sudodus on 2013-05-22
You need not do anything with that information, if your burning program finds the CD drive. Otherwise you could check if your computer finds something, when you insert a drive with something written on it.

You can also search for it with the following command ```
 dmesg |grep -i cd.rom
```

But now, I suggest that you use for example Brasero or k3b to burn the CD. If no go, I think something is wrong with your CD drive or the connection to it. 

In that case maybe you can make a USB boot drive and install from that drive instead.

---

### Post by A Traveller on 2013-05-22
Thanks sudodus. I think the problem was a set of faulty cabling coming from the PSU. I removed one set and connected another and it seems to work now. I still haven't got it to appear in 'Places' with no CD in it, but as long as it's working with the CD inside for the moment, I can look into making it appear in 'Places' at a later time. I did try to use Brasero initially but it didn't find the CDROM (because of the fault). It should find it OK now. The thing I'm wondering though, is that if it was the power cable/connector that was faulty, how come the light on the drive still came on and I could still open and close the drive door?? Thanks again for the help and suggestions. I appreciate it.

---

### Post by sudodus on 2013-05-22
I can't explain. I don't remember how many of the power connectors that are really used, only two or several of them (and maybe with different voltage). You can find that out browsing the internet.

Maybe there was some bad connection due to an oxidized connecting pin or something like that, and that was fixed, when you wiggled or disconnected-reconnected either the power cable or the signal cable.

---

### Post by A Traveller on 2013-05-27
Hi sudodus. Just to update, it was in fact the IDE cable that turned out to be faulty. I attached a new one and it's working fine now. Thanks.

---

