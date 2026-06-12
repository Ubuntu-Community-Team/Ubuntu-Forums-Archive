---
title: "jbd2 Preventing e2fsck from running"
date: 2010-12-27
forum: Hardware
---

### Post by worldgnat on 2010-12-27
A day or two ago, a crash corrupted my root filesystem (ext4) (when I try to boot I get messages that proc and sys can't be mounted and get dumped at a busybox terminal.) I booted an Ubuntu Maverick live cd and tried to run e2fsck to fix the error, and I got this:
```
ubuntu@ubuntu:~$ sudo e2fsck /dev/sda4
e2fsck 1.41.12 (17-May-2010)
e2fsck: Device or resource busy while trying to open /dev/sda4
Filesystem mounted or opened exclusively by another program?

```

mkfs isn't any more promising

```
ubuntu@ubuntu:~$ sudo mkfs -n /dev/sda4
mke2fs 1.41.12 (17-May-2010)
/dev/sda4 is apparently in use by the system; will not make a filesystem here!
```

So I tried
```

ubuntu@ubuntu:~$ sudo lsof -ln | grep sda4
lsof: WARNING: can't stat() tmpfs file system /cow
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/ubuntu/.gvfs
      Output information may be incomplete.
jbd2/sda4  538        0  cwd       DIR       0,17      300          2 /
jbd2/sda4  538        0  rtd       DIR       0,17      300          2 /
jbd2/sda4  538        0  txt   unknown                                /proc/538/exe

```

It seems to me that jbd2 is preventing e2fsck from running. It seems that people have run into this issue before and have solved it by reformatting the partition. I'd really like to save the data here if possible and figure out why this is happening. Any ideas?

(By the way, on a whim I tried kill -9 538, which had no effect. I've also tried disabling journaling, but I can't because the needs_recovery flag is enabled and the -f option will not force it to remove journaling.)

---

### Post by scottmmmm on 2011-01-21
I've had this same problem today. I am currently in a state where I cannot mount or access my hard disk with Ubuntu installed. I have reistalled on a different hard disk but I would like to be able to retrieve my data if possible

---

