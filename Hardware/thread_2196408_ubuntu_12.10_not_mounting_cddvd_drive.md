---
title: "ubuntu 12.10 not mounting cd/dvd drive"
date: 2013-12-29
forum: Hardware
---

### Post by keith_summers625 on 2013-12-29
Hello, I have installed ubuntu 12.10 on my hp laptop. Mostly everything is ok, but I cannot use the dvd/cd drive. It will not read anything, I have tried to follow instructions from other peoples questions obviously with no luck.
The drive shows up when I open the disk utility app, [ATTACH=CONFIG]249001[/ATTACH]
~$ sudo mkdir /mnt/cdrom
~$ sudo mount /dev/cdrom /mnt/cdrom
mount: no medium found on /dev/sr0
~$ 

But it wont seem to mount.
~$ ls -l /dev/cdrom
lrwxrwxrwx 1 root root 3 Dec 29 11:40 /dev/cdrom -> sr0

~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=7d9ffca2-70ea-41d2-b10a-f64770c05f1e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=7fbb1927-7749-489c-83fb-2a0e123955d5 none            swap    sw              0       0


I dont know what else to try. Is there anything else I should post? I hope someone knows what is wrong with me.

---

### Post by varunendra on 2014-01-02
Welcome to the forums Keith !

Can you confirm whether the drive itself is physically functional or not? Because software can't do anything if the drive is broken.

If you have a bootable CD/DVD (CDs are easily readable compared to DVDs), can you boot with it? If not, maybe the drive itself is malfunctioning.

But if yes, please insert a clean CD in it while being in Ubuntu (preferably a data CD, not an audio CD), let the drive read it, then post back the outputs of -
```
dmesg | tail -20
mount
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

