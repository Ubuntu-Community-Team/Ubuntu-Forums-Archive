---
title: "unknown partition / please help"
date: 2009-12-25
forum: Hardware
---

### Post by shara on 2009-12-25
hello
I was in ubuntu 9.4
after upgrading to 9.10 with ext4 format on root path , I can not access to my /home partition.
all of my projects and backups will be in /home partition and my /home partition is very important for me.

with Disk Utility software in ubuntu 9.10 I can see my sda5 partition but this is unknown partition and I can not mount this partition.

what can I do to mount this partition?
is problem in partition table?
what can I do to fixing this problem? :(

```

root@sharacle:~# e2fsck -p /dev/sda5 
e2fsck: Bad magic number in super-block while trying to open /dev/sda5 
/dev/sda5:  
The superblock could not be read or does not describe a correct ext2 
filesystem.  If the device is valid and it really contains an ext2 
filesystem (and not swap or ufs or something else), then the superblock 
is corrupt, and you might try running e2fsck with an alternate superblock: 
    e2fsck -b 8193 <device> 

```

```

root@sharacle:~# mount /dev/sda5 
mount: can't find /dev/sda5 in /etc/fstab or /etc/mtab 

```

```

root@sharacle:~# fdisk -l 
 
Disk /dev/sda: 160.0 GB, 160041885696 bytes 
255 heads, 63 sectors/track, 19457 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x90909090 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1               1         243     1951866   82  Linux swap / Solaris 
/dev/sda2   *         244       19457   154336455    f  W95 Ext'd (LBA) 
/dev/sda5            2855       12401    76686246   83  Linux 
/dev/sda6             244        2854    20972794+  83  Linux 
/dev/sda7           12402       19457    56677288+  83  Linux 
 
Partition table entries are not in disk order 
root@sharacle:~# cat /etc/fstab  
UUID=82985ceb-1a1c-42c2-99e7-af3bda372951 swap swap sw 0 0 
UUID=80c18994-e510-445c-8e47-91c7aca1840c /var ext4 defaults 0 2 
UUID=665178d4-50b6-4775-a9b0-5fdc57ee6a98 / ext4 defaults 0 1 

```

---

### Post by taurus on 2009-12-25
How about

```
mkdir /media/sda5
mount -t ext4 /dev/sda5 /media/sda5
df -h
```

Otherwise, run this command as suggested in e2fsck

```
e2fsck -b 8193 /dev/sda5
```

p.s.  What filesystem, ext3 or ext4, is /dev/sda5?

---

### Post by shara on 2009-12-26
thanks
don't work :(
```

root@sharacle:~# mkdir /media/sda5
root@sharacle:~# mount -t ext4 /dev/sda5 /media/sda5/
mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@sharacle:~# mount -t ext3 /dev/sda5 /media/sda5/
mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@sharacle:~# mount -t ext2 /dev/sda5 /media/sda5/
mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@sharacle:~# e2fsck -b 8193 /dev/sda5
e2fsck 1.41.9 (22-Aug-2009)
e2fsck: Bad magic number in super-block while trying to open /dev/sda5

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>



```

---

