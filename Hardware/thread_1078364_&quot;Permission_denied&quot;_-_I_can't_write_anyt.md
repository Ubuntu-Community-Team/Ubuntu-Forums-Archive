---
title: "&quot;Permission denied&quot; - I can't write anything onto this disk!"
date: 2009-02-23
forum: Hardware
---

### Post by alacarte on 2009-02-23
Hi,

I'm a long time user of Windows and have only recently started using Ubuntu in my home server. I have a lot of plans for said server, however I can't even seem to mount the server's second hard drive properly!

I'm using 8.10 and the hard drive is a brand new WD GreenPower 640GB formatted to FAT32 with GParted. The first time around I tried various fstab commands to mount to /media/monolith to no avail - the drive was owned by root and I would either have the new folder command greyed out or active but with a 'Permission Denied' error. 

- sudo chmod and chown on /media/monolith gave an error when the drive was mounted and appeared to work fine when it wasn't, but really didn't do anything.

- sudo nautilus to try and change permissions didn't work - I could change them, but they immediately changed back. Attempting to change ownership or group resulted in a 'you do not have permission' error (?)

- assigning to group using gid=users in fstab for some reason gives me no permissions at all - even read permissions!

...so I've started again. Following [this guide]("http://tombott.com/Automatically_Mount_Additional_HD_in_Ubuntu_8.10") has gotten me the furthest, with the drive mounting properly, owner set to andrew and group set to users, however attempting to create files or folders without sudoing gets the same 'you do not have permission error', even when mounted in /home/andrew/monolith!

Sorry, I know this question has been asked tons of times, but I've read quite a few of those threads and nothing seems to solve this problem!

Thanks in advance!

---

### Post by Archmage on 2009-02-23
Please give us the output of the command (in the terminal) while mount and while unmount.

ls -l /home/andrew/monolith

---

### Post by albinootje on 2009-02-23
> **alacarte said:**
> attempting to create files or folders without sudoing gets the same 'you do not have permission error', even when mounted in /home/andrew/monolith!


Please post the output of the following :
```

sudo fdisk -l
cat /etc/fstab
mount

```

---

### Post by sowelie on 2009-02-23
Why are you using fat32 anyway?  I'd recommend using ext3 or even ntfs...fat32 stinks.  If you plan on sharing the drive, your windows machines will still be able to read it properly through the samba share.

---

### Post by alacarte on 2009-02-23
> **Archmage said:**
> Please give us the output of the command (in the terminal) while mount and while unmount.

ls -l /home/andrew/monolith

Unmounted
```

total 0

```

Mounted
```

total 16
drwxr-xr-x 2 root root 16384 2009-02-24 01:26 test

```

---

### Post by alacarte on 2009-02-23
> **albinootje said:**
> Please post the output of the following :
```

sudo fdisk -l
cat /etc/fstab
mount

```

sudo fdisk -l
```
Disk /dev/sda: 6144 MB, 6144284672 bytes
255 heads, 63 sectors/track, 747 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x38a7390b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         708     5686978+  83  Linux
/dev/sda2             709         747      313267+   5  Extended
/dev/sda5             709         747      313236   82  Linux swap / Solaris

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ba952

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       77825   625129281    b  W95 FAT32

```

cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=3fbb4f94-a89d-45a5-925b-5665836a61e9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=e2a2680a-dae1-437c-a384-f1174d1ba4c9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1	/media/bigrig	vfat	defaults	0	0

```

(Note: tried changing mount point there to bigrig, no effect)

mount
```
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/andrew/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=andrew)
/dev/sdb1 on /home/andrew/monolith type vfat (rw)

```

(currently mounted on monolith again)

---

### Post by alacarte on 2009-02-23
> **sowelie said:**
> Why are you using fat32 anyway?  I'd recommend using ext3 or even ntfs...fat32 stinks.  If you plan on sharing the drive, your windows machines will still be able to read it properly through the samba share.

The drive may have to be read directly from other Windows machines, so I figured to just go the safer route on that (ok, safer in terms of compatibility :D). Also GParted didn't let me NTFS it :S

---

### Post by alacarte on 2009-02-23
If it matters, I'm doing most of this via VNC remote desktop while logged in as andrew.

---

### Post by albinootje on 2009-02-23
> **alacarte said:**
> 
```

/dev/sdb1	/media/bigrig	vfat	defaults	0	0

```


Please try changing that line into :
```

/dev/sdb1       /media/bigrig   vfat    rw,iocharset=utf8,umask=000     0       0

```
Remount the partition, then check with the "mount" command to see the difference, and try writing to it.

And remember : FAT32 is inherited from the DOS age, it is ancient, it has a very primitive ownership/permission structure (or rather none), it cannot handle files larger than 4 Gb (Was it in a previous FAT version even 2 Gb ?), and it will eat more of your disk space by default.

---

### Post by alacarte on 2009-02-23
> **albinootje said:**
> Please try changing that line into :
```

/dev/sdb1       /media/bigrig   vfat    rw,iocharset=utf8,umask=000     0       0

```
Remount the partition, then check with the "mount" command to see the difference, and try writing to it.

And remember : FAT32 is inherited from the DOS age, it is ancient, it has a very primitive ownership/permission structure (or rather none), it cannot handle files larger than 4 Gb (Was it in a previous FAT version even 2 Gb ?), and it will eat more of your disk space by default.

My god, that was so head-slappingly simple. It worked! Thanks a ton! I swear I've tried the rw and umask things before though, what does iocharset do?

And yeah, I realise FAT32 is old fart. Would've preferred NTFS but GParted greyed it out for some reason - I was going to look into that, but getting the thing working was the higher priority. Guess I should figure that out now, thanks again!

---

### Post by sowelie on 2009-02-23
If you can't get GParted to format it...boot up a windows install cd and go to the repair prompt.  You can format it there.

---

### Post by alacarte on 2009-02-23
ntfsprogs is formatting the drive right now, hopefully that'll be fine.

---

### Post by albinootje on 2009-02-23
> **alacarte said:**
> I swear I've tried the rw and umask things before though, what does iocharset do?

Good that you have it working now ;-)
More information :
[http://www.cyberciti.biz/faq/mounting-windows-partition-onto-ubuntu-linux/](http://www.cyberciti.biz/faq/mounting-windows-partition-onto-ubuntu-linux/)

---

