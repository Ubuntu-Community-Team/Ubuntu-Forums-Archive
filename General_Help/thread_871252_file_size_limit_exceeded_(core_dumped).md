---
title: "file size limit exceeded (core dumped)"
date: 2008-07-26
forum: General Help
---

### Post by wcunkefe on 2008-07-26
Hi all... I am unable to move files >2GB onto my Ubuntu server... here is my setup.  On the server... the OS is installed on an ext3 HDD and I have a large NTFS HDD for storage.  I am trying to move a > 4GB file onto the server via the network from another ubuntu machine on an ext3 filesystem.  Any help would be greatly appreciated.

sudo fdisk -l on server
```
wcunkefe@MediaServer:~$ sudo fdisk -l

Disk /dev/sda: 30.7 GB, 30750031872 bytes
255 heads, 63 sectors/track, 3738 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5a3e5a15

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3693    29663991   83  Linux
/dev/sda2            3694        3738      361462+   5  Extended
/dev/sda5            3694        3738      361431   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
240 heads, 63 sectors/track, 41345 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xc8fec8fe

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       41344   312560608+   7  HPFS/NTFS

```


ulimit -a on server
```
wcunkefe@MediaServer:~$ ulimit -a
core file size          (blocks, -c) 0
data seg size           (kbytes, -d) unlimited
scheduling priority             (-e) 0
file size               (blocks, -f) unlimited
pending signals                 (-i) 1015
max locked memory       (kbytes, -l) 32
max memory size         (kbytes, -m) unlimited
open files                      (-n) 1024
pipe size            (512 bytes, -p) 8
POSIX message queues     (bytes, -q) 819200
real-time priority              (-r) 0
stack size              (kbytes, -s) 8192
cpu time               (seconds, -t) unlimited
max user processes              (-u) 1015
virtual memory          (kbytes, -v) unlimited
file locks                      (-x) unlimited
```

---

### Post by wcunkefe on 2008-07-30
There must be an easy fix... I feel like I have provided enough data for someone out there to help.

-Wayne

---

### Post by geirha on 2008-07-30
Are you doing this using shared folders (samba)? If so I believe you need to set an option in smb.conf to allow > 2GiB files. I hardly ever use samba, so I can't help you much on that part. It might be easier to use ssh, which does not have this limitation.

---

### Post by wcunkefe on 2008-07-31
I am using samba... and did not even think about restricitions that could be imposed on that end.  I will check it out tomorrow and let you know what happened.  I will look for smb.conf settings that could be causing the issue and I have heard someone say that I should mount the smb drive using the following:
```
mount -t smbfs -o lfs //server/share /localdir
```

Hopefully someone can confirm this before I mess around with it... apparently the lfs signifies "Large File Support".  I have not looked into it... so I dont know if this is true.

---

### Post by editorreilly on 2009-03-10
wcunkefe, did you ever find a solution?  I am experiencing the same issue, with smb to ubuntu from a windows machine.

-Ryan.

---

