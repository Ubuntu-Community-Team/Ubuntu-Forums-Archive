---
title: "Move /Home to external USB drive partition - Help please"
date: 2005-11-16
forum: General Help
---

### Post by VicVega on 2005-11-16
I hope someone can help me with this. I am a total n00b to linux and Breezy.

**Problem:** I want to move the /Home directory to an external USB drive.

I really don't want to mess this up. I've looked at this How To: [http://ubuntuforums.org/showthread.php?t=46866]("http://ubuntuforums.org/showthread.php?t=46866") . However that is for moving /home to a different partition on the same internal drive. I think there are other issues (mount point) when moving to an external drive. I have searched the forums and done a lot of reading, but I just don't think I understand or have found something that applies to my setup. I would really like to hear from someone who has successfully done this. 

I dual-boot XP Pro (/dev/hda2) and Ubuntu. Ubuntu is installed on /dev/hda4 on my internal drive. I have a Western Digital 160 GB USB drive. There are 3 partitions on it. First is a small 620 mb fat32 for the software that came with the drive. Next is 94 GB ext3 **(/dev/sdc3)**for Breezy backup, this is where I would like my /home directory. Then 57 GB NTFS (/dev/sdc5) for XP backup. The rest is unallocated. This drive mounts fine and I can add files to it already.

Here is the output of:
**mtab**
```
/dev/hda4 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /dev/shm tmpfs rw 0 0
usbfs /proc/bus/usb usbfs rw 0 0
tmpfs /lib/modules/2.6.12-9-386/volatile tmpfs rw,mode=0755 0 0
/dev/hda2 /media/windoze ntfs rw,umask=0222 0 0
tmpfs /dev tmpfs rw,size=10M,mode=0755 0 0
/dev/sdc5 /media/WinXP\040BU ntfs rw,noexec,nosuid,nodev,uid=1000,gid=1000,umask=077,iocharset=utf8 0 0
/dev/sdc1 /media/WD\040MediaCtr vfat rw,noexec,nosuid,nodev,quiet,shortname=winnt,uid=1000,gid=1000,umask=077,iocharset=utf8 0 0
/dev/sdc3 /media/usbdisk ext3 rw,noexec,nosuid,nodev 0 0
```


**fstab**
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0
/dev/sdb        /media/usb1     auto    rw,user,noauto  0       0
/dev/hda2 	/media/windoze 	ntfs 	umask=0222	0 	0
```

**mount**
```
me@ubuntu1:~$ mount
/dev/hda4 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-9-386/volatile type tmpfs (rw,mode=0755)
/dev/hda2 on /media/windoze type ntfs (rw,umask=0222)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)
/dev/sdc5 on /media/WinXP BU type ntfs (rw,noexec,nosuid,nodev,uid=1000,gid=1000,umask=077,iocharset=utf8)
/dev/sdc1 on /media/WD MediaCtr type vfat (rw,noexec,nosuid,nodev,quiet,shortname=winnt,uid=1000,gid=1000,umask=077,iocharset=utf8)
/dev/sdc3 on /media/usbdisk type ext3 (rw,noexec,nosuid,nodev)
```

I hope all this makes sense.  Any help would be greatly appreciated.

Thanks,
Vic

---

### Post by RAOF on 2005-11-16
That howto should work fine for an external drive.  The only issue I can see is that the device node (/dev/sdc3) might change if you plug in more/different USB drives.  It should be possible to avoid/fix this (by using udev rules, or mounting by ext3 label, or something), but I have no idea of the details necessary.

---

### Post by VicVega on 2005-11-16
That's kind of what I was wondering about. That partition is mounted at /media/usbdisk and then I make /mnt/home within that?

Thanks,
Vic

---

### Post by RAOF on 2005-11-16
Ah, no.  As per that howto, you'd copy all of the stuff from your current /home to the usb disc, then change the mountpoint in the fstab to be /home

So, you'd end up adding a line like this to your fstab:
```

/dev/sdc3    /home    ext3    user_xattr,defaults     2      0

```
or something like that

---

### Post by VicVega on 2005-11-16
OK, that makes more sense. I think I was guilty of trying to over-think the process.  Thanks a lot for your input, I'll give that a try.

Thanks,
Vic

---

### Post by RAOF on 2005-11-16
No problem.  Just be sure to backup your data :)  I don't think this will do any harm, but it pays to be safe!

---

