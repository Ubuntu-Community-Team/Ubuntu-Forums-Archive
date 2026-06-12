---
title: "XFS 2 GB maximum filesize ?"
date: 2008-07-29
forum: General Help
---

### Post by _markus_ on 2008-07-29
Hi,
I am running Ubuntu 8.04 LTS Desktop Edition 32 Bit. 
I have formatted my root partition with XFS. 

I am trying to record video from a DVB transport stream, but after exactly 2GB the recorder fails with the message "file too large".

How can an XFS partition have a maximum filesize of 2 GB ? 
Is there a way to fix this ?

Thank you,
Markus

---

### Post by deanjm1963 on 2008-07-29
XFS can handle VERY large files. How big are your root and home partitions?

If you don't have enough tmp space you will end up with errors.

---

### Post by _markus_ on 2008-07-29
Yep, that's why I use it :) 
(It's a HTPC for HDTV recording)

My / partition is 1 TB. /home is under the same partition.

/tmp is mounted on the same partition.

Here's my /etc/fstab :

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=fa916286-133a-48f3-804d-3c86ed279557 /               xfs     relatime        0       1
# /dev/sda1
UUID=754ff043-f760-402a-ab3f-e44ed6339afc /boot           ext2    relatime        0       2
# /dev/sda2
UUID=9cf41969-2ff0-495f-abee-4513c5460d6d none            swap    sw              0       0

```

and df -h:

```

$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             930G  9.3G  921G   1% /
varrun               1013M  244K 1013M   1% /var/run
varlock              1013M     0 1013M   0% /var/lock
udev                 1013M   68K 1013M   1% /dev
devshm               1013M   12K 1013M   1% /dev/shm
lrm                  1013M   39M  975M   4% /lib/modules/2.6.24-19-generic/volatile
/dev/sda1             177M   36M  132M  22% /boot
gvfs-fuse-daemon      930G  9.3G  921G   1% /home/markus/.gvfs

```

Thanks,
Markus

---

### Post by deanjm1963 on 2008-07-29
You have more than plenty of room for large files. 

I know from personal experience I've always had problems burning files larger than 4gb (e.g. dvds) from XFS partitons, no matter what distro it is. I prefer to use JFS for really large partitions.

Have you had success using other distros with the same file system and setup?

---

### Post by _markus_ on 2008-07-29
No,
I didn't try any other distro with this setup.

I just stumbled upon this wikipedia article: [http://en.wikipedia.org/wiki/Large_file_support](http://en.wikipedia.org/wiki/Large_file_support)

> 
To support writing portable code that makes use of LFS where possible, C standard library authors devised mechanisms that, depending on preprocessor constants, transparently redefined the functions to the 64-bit large file aware ones.


The problem might be with my own code.

I use this in C++ function to write to the file:
```

inline ssize_t cTBFile::SysWrite(const void *Buffer, size_t Length) const {
        return ::write(*this, Buffer, Length);
}

```
and no special preprocessor constants.

I will look into recompiling it and post my results.

Thanks

---

### Post by _markus_ on 2008-07-29
compiling my code with  -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE  fixed it !

Markus.

---

