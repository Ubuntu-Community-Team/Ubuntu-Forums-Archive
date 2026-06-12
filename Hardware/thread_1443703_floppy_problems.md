---
title: "floppy problems"
date: 2010-03-31
forum: Hardware
---

### Post by cong06 on 2010-03-31
Yes, it's out-dated, but in backwaters its still cheaper then USB flash drives.

To start I have installed pmount and fdutils on 9.04.
I also tried the tricks here: [http://justanotherwebblog.wordpress.com/2009/03/01/howto-use-floppy-in-ubuntu-810/](http://justanotherwebblog.wordpress.com/2009/03/01/howto-use-floppy-in-ubuntu-810/)

The problem is that these commands fail:
```

root@kimende-s:~# fdisk /dev/fd0
Unable to read /dev/fd0
root@kimende-s:~# mkdosfs /dev/fd0
mkdosfs 3.0.1 (23 Nov 2008)
mkdosfs: unable to get diskette geometry for '/dev/fd0'
root@kimende-s:~# mkfs.ntfs /dev/fd0
The partition start sector was not specified for /dev/fd0 and it could not be obtained automatically.  It has been set to 0.
The number of sectors per track was not specified for /dev/fd0 and it could not be obtained automatically.  It has been set to 0.
The number of heads was not specified for /dev/fd0 and it could not be obtained automatically.  It has been set to 0.
Device is too small (3kiB).  Minimum NTFS volume size is 1MiB.

```
```

root@kimende-s:~# dd if=/dev/fd0 bs=256 count=1
dd: reading `/dev/fd0': Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 41.5924 s, 0.0 kB/s

```

And all the while /var/log/syslog is spitting out (about once per second):
```

Mar 31 17:30:04 kimende-s kernel: [  290.062894] floppy0: probe failed...

```
with an occasional
```

Mar 31 17:36:46 kimende-s kernel: [  692.697731] end_request: I/O error, dev fd0, sector 0
Mar 31 17:36:46 kimende-s kernel: [  692.697740] Buffer I/O error on device fd0, logical block 0

```

This is a new floppy, so it's possibly unformatted.
This makes the following a bit tricky to debug mounting:
```

root@kimende-s:~# mount /dev/fd0 /media/floppy0/
mount: you must specify the filesystem type
root@kimende-s:~# mount -t auto /dev/fd0 /media/floppy0/
mount: you must specify the filesystem type
root@kimende-s:~# mount -t ntfs /dev/fd0 /media/floppy0/
Error reading bootsector: Input/output error
Failed to mount '/dev/fd0': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
root@kimende-s:~# mount -t msdos /dev/fd0 /media/floppy0/
mount: /dev/fd0: can't read superblock

```

I've looked through: [https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/441835?comments=all](https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/441835?comments=all)
But it seems that 9.04 is working for everyone...
Is there some chance I uninstalled something that I need without realizing that it was for floppys?

---

### Post by cong06 on 2010-05-05
Can someone confirm that floppys do actually work out of the box in 9.04?

I've tested 3 different floppies, with three different errors.
If no one confirms, I'll go ahead and post the errors...

I didn't realize it'd be this hard getting a _working_ floppy disk

---

### Post by cong06 on 2010-05-23
So, I was wrong. They do work in 9.04. I just had bad luck finding one that actually worked.

Now I could use help finding a way to make it easily mountable.
I had to type the command line to get nautilus to respond to the floppy.

Automounting doesn't work, and clicking "Floppy" in the side bar doesn't work either.

---

### Post by and003 on 2010-08-21
> **cong06 said:**
> So, I was wrong. They do work in 9.04. I just had bad luck finding one that actually worked.

Now I could use help finding a way to make it easily mountable. I had to type the command line to get nautilus to respond to the floppy.

Automounting doesn't work, and clicking "Floppy" in the side bar doesn't work either.

Perhaps you can try the solution I found here:
[https://answers.launchpad.net/ubuntu/+source/util-linux/+question/120571](https://answers.launchpad.net/ubuntu/+source/util-linux/+question/120571)

---

