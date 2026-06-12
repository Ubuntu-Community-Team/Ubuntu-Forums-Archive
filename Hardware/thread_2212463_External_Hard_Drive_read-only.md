---
title: "External Hard Drive read-only"
date: 2014-03-21
forum: Hardware
---

### Post by katie3 on 2014-03-21
I have an external hard drive which was lent to me by a friend that I seem to be unable to write to.

fdisk -l gives the following result for the external drive:
> 
WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.




Disk /dev/sdc: 249.8 GB, 249828597760 bytes
255 heads, 63 sectors/track, 30373 cylinders, total 487946480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1   487946479   243973239+  ee  GPT




I attempted the following, which was unsuccessful:
> 
$ sudo mount -o remount,uid=1000,gid=1000,rw /dev/sdc1
mount: can't find /dev/sdc1 in /etc/fstab or /etc/mtab

and then this, which was also unsuccessful:
> 
$ sudo mount -o remount,uid=1000,gid=1000,rw /media/Clickfree_Storage
mount: warning: /media/Clickfree_Storage seems to be mounted read-only.


Also:
> 
$ parted -l /dev/sdc
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label                                  


Warning: Unable to open /dev/sr1 read-write (Read-only file system).  /dev/sr1
has been opened read-only.
Warning: The driver descriptor says the physical block size is 512 bytes, but
Linux says it is 2048 bytes.
Ignore/Cancel? I                                                          
Error: Can't have a partition outside the disk!


I'm not really sure where to go from here... anyone able to offer some useful advice?

---

### Post by ajgreeny on 2014-03-21
We need to know what filesystem is on that hard disk that is causing the problem and your command with parted might help if you use ```
sudo parted -l
``` as it needs to be run as root.  Do you know if you can write to the disk as root?

I am wondering if the drive is formatted as one of the ext# filesystems which will need a change to ownership of the mountpoint for you to write to it as user rather than only as root.

---

### Post by katie3 on 2014-03-21
sudo parted -l gives the following (I assume the location has changed so /dev/sdb due to it being unplugged and plugged back in):
> 
Model: Clikfree Backup Drive (scsi)
Disk /dev/sdb: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt


Number  Start   End    Size   File system  Name                  Flags
 1      20.5kB  210MB  210MB  fat32        EFI System Partition  boot
 2      210MB   250GB  249GB  hfs+         Untitled


And yes, I have already tried moving the files using sudo, and get the same read-only message when I try to do so, so I can't write to the disk as root either.

---

### Post by varunendra on 2014-03-21
Welcome to the forums Katie! :)

An important information that you should post with each of your attempts of remounting it is the output of "**mount**" command. Please show it to us now.

**PS:**
Terminal commands & outputs should always be posted within '**Code**' tags to preserve their formatting and make the post compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by katie3 on 2014-03-22
> **varunendra said:**
> Welcome to the forums Katie! :)

An important information that you should post with each of your attempts of remounting it is the output of "**mount**" command. Please show it to us now.

The drive is mounted automatically when I plug it in. I also provided the output of the mount command on both attempts to remount it in the OP.

---

### Post by slooksterpsv on 2014-03-22
```

2 210MB 250GB 249GB hfs+ Untitled

```

You'll need to install hfsprogs to attempt to even write to the drive.
[http://askubuntu.com/questions/332315/how-to-read-and-write-hfs-journaled-external-hdd-in-ubuntu-without-access-to-os](http://askubuntu.com/questions/332315/how-to-read-and-write-hfs-journaled-external-hdd-in-ubuntu-without-access-to-os)

---

### Post by varunendra on 2014-03-22
> **katie3 said:**
> The drive is mounted automatically when I plug it in. I also provided the output of the mount command on both attempts to remount it in the OP.

I meant "mount" without any arguments or parameters. Without arguments, the mount command shows all the current mount points and the options they are mounted with.

Output of "parted -l" will show us the available partitions and filesystem on them, and "mount" will show us the options they are mounted with, so we can determine if something is wrong/missing in the mount options.

---

### Post by katie3 on 2014-03-22
> **varunendra said:**
> I meant "mount" without any arguments or parameters. Without arguments, the mount command shows all the current mount points and the options they are mounted with.

Output of "parted -l" will show us the available partitions and filesystem on them, and "mount" will show us the options they are mounted with, so we can determine if something is wrong/missing in the mount options.
Ah, thanks for clarifying. Here it is:
```

$ mount/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/katie/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=katie)
/dev/sr0 on /media/DVD-CRT-195 D4 type udf (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8,umask=0077,dmode=0500,uhelper=udisks)
/dev/sr1 on /media/Clickfree_System type iso9660 (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500,uhelper=udisks)
/dev/sdb2 on /media/Clickfree_Storage type hfsplus (ro,nosuid,nodev,uhelper=udisks)

```

---

### Post by katie3 on 2014-03-22
> **slooksterpsv said:**
> ```

2 210MB 250GB 249GB hfs+ Untitled

```

You'll need to install hfsprogs to attempt to even write to the drive.
[http://askubuntu.com/questions/332315/how-to-read-and-write-hfs-journaled-external-hdd-in-ubuntu-without-access-to-os](http://askubuntu.com/questions/332315/how-to-read-and-write-hfs-journaled-external-hdd-in-ubuntu-without-access-to-os)
Thank you! The instructions in the link you provided worked, after installing hfsprogs.

---

