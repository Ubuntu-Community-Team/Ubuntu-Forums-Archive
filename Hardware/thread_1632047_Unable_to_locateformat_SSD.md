---
title: "Unable to locate/format SSD"
date: 2010-11-27
forum: Hardware
---

### Post by bluedalek on 2010-11-27
Hi All

Just purchased and installed a Patriot 32GB SSD.  I have had no luck in getting any *buntu OS installed.

I first started installing Kubuntu 10.04, and the installer located the drive fine.  I partitioned it to /swap and /ext2.  The installer started formatting the drive, then returned an I/O error.

The partitions were setup, but the ext2 partition was not formatted.  I attempted to re-do it.  Same I/O error.

I figured it could be a bad burn, so I tried another CD.  I attempted to install Ubuntu 9.10, and it could not even see the drive.  After following a number of steps on this, and other forums, I have the following to share below:

```
ubuntu@ubuntu:~$ sudo fdisk -l
ubuntu@ubuntu:~$ ls /dev/sd*
/dev/sda
ubuntu@ubuntu:~$ sudo mkfs -t ext2 /dev/sda
mke2fs 1.41.11 (14-Mar-2010)
/dev/sda is entire device, not just one partition!
Proceed anyway? (y,n) y
mkfs.ext2: No medium found while trying to determine filesystem size
```

Any help or pointers greatly appreciated!

---

### Post by coffee412 on 2010-11-27
> **bluedalek said:**
> Hi All

Just purchased and installed a Patriot 32GB SSD.  I have had no luck in getting any *buntu OS installed.

I first started installing Kubuntu 10.04, and the installer located the drive fine.  I partitioned it to /swap and /ext2.  The installer started formatting the drive, then returned an I/O error.

The partitions were setup, but the ext2 partition was not formatted.  I attempted to re-do it.  Same I/O error.

I figured it could be a bad burn, so I tried another CD.  I attempted to install Ubuntu 9.10, and it could not even see the drive.  After following a number of steps on this, and other forums, I have the following to share below:

```
ubuntu@ubuntu:~$ sudo fdisk -l
ubuntu@ubuntu:~$ ls /dev/sd*
/dev/sda
ubuntu@ubuntu:~$ sudo mkfs -t ext2 /dev/sda
mke2fs 1.41.11 (14-Mar-2010)
/dev/sda is entire device, not just one partition!
Proceed anyway? (y,n) y
mkfs.ext2: No medium found while trying to determine filesystem size
```Any help or pointers greatly appreciated!


/dev/sda is entire device, not just one partition!

mkfs -t ext2 /dev/sda1

(your forgetting the partition)

---

### Post by bluedalek on 2010-11-27
Your right, I did miss that, but now I get this:

```
ubuntu@ubuntu:~$ sudo mkfs -t ext2 /dev/sda1
mke2fs 1.41.11 (14-Mar-2010)
Could not stat /dev/sda1 --- No such file or directory

The device apparently does not exist; did you specify it correctly?
```

Not sure what to do now

---

### Post by bluedalek on 2010-11-27
so it looks like I've bricked a 2nd one.. anyone have any thoughts?

---

