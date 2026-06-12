---
title: "df shows free space wrong"
date: 2007-07-13
forum: Hardware &amp; Laptops
---

### Post by Sukkula on 2007-07-13
Hi,

I have this weird "thing". The df shows the free disk space wrong.
I'm using Ubuntu 6.06 server with 2.6.15-28-server kernel.
df (GNU coreutils) 5.93
du (GNU coreutils) 5.93

```
miika@nurkkaboxi:~$ df -h /dev/sda
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda              151G   14G  131G  10% /mnt/sata
```

and with du
```
miika@nurkkaboxi:~$ du -chs /mnt/sata
du: `/mnt/sata/lost+found': Permission denied
99G     /mnt/sata
99G     total
```

and also a fdisk output if someone is interested

```
miika@nurkkaboxi:~$ sudo fdisk -l /dev/sda

Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
```

I format this hd in my other computer and put some data in it. Then put it in my server.
Is this some kind of bug in df or have I done something wrong.

---

