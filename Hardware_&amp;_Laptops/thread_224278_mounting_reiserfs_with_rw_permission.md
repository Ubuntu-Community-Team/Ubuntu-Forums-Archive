---
title: "mounting reiserfs with rw permission"
date: 2006-07-27
forum: Hardware &amp; Laptops
---

### Post by IdoMcFly on 2006-07-27
Hello !

I have a second hard drive which is reiserfs and mounted by ubuntu on boot but I can't write on it.

the mount point /media/hdc1 is root:root with 755 permission

I can't find any uid or gid options for reiserfs.

my fstab :
```

/dev/hdc1 /media/hdc1 reiserfs defaults 0 2

```

how to mount it so normal users can read/write?

thanks for any help

---

### Post by pclogic on 2006-07-27
Try creating a directory under /media/hdc1 using root.  Then, chown the directory to one of the regular users:

sudo mkdir /media/hdc1/myuserdir
sudo chown myuser:myuser /media/hdc1/myuserdir

---

### Post by jpkotta on 2006-07-27
In the mount man page, there are a number of options supported by all filesystems (though some filesystems ignore them).  uid and gid are among these options.  Here is my /etc/fstab; I have no reiser partitions, but you should be able to get something out of it.  When I mount my external USB drive, which is FAT32, it mounts it as me and with permissions of 600 for files and 700 for directories.

---

### Post by IdoMcFly on 2006-07-28
I've tried 
> 
/dev/hdc1 /media/hdc1 reiserfs defaults,uid=XXX 0 2


and it pop:
```

mount: wrong fs type, bad option, bad superblock on /dev/hdc1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

dmesg | tail gives me:
[17181072.856000] ReiserFS: hdc1: warning: unknown mount option "uid=1000"
[/code]

---

### Post by IdoMcFly on 2006-07-28
bump

---

### Post by IdoMcFly on 2006-07-31
ok I found out how to do.
Once the drive is mounted:
```

sudo chown user:group /media/hdc1

```

change hdc1 by your drive.

reiserfs is a filesystem that managed the uid and gid in a tranparent way.

---

