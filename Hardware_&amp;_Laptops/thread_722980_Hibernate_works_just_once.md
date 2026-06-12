---
title: "Hibernate works just once"
date: 2008-03-13
forum: Hardware &amp; Laptops
---

### Post by jazzgossen on 2008-03-13
I have a Dell Latitude D800 that has been able to hibernate. However, since I upgraded the RAM to 2 GB from the original 512 MB, I'm having trouble. I moved and enlarged the swap partition. It used to be 1 GB at the end of the drive, now it's 7 GB (much too large, I know, but it's temporary) in the middle. 

Hibernation always works once, after a clean boot, but the second time I try to hibernate, I just get stuck at a black screen and have to kill the power. 

Is there any way to get more verbose output to see what's going wrong? I haven't found any hibernate.log on my system.

---

### Post by logos34 on 2008-03-13
post the output/files forthe following:

sudo fdisk -l

cat /etc/fstab

ls -l /dev/disk/by-uuid

---

### Post by jazzgossen on 2008-03-13
```

~> sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc986c986

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196    6  FAT16
/dev/sda2   *           8        1728    13823932+   7  HPFS/NTFS
/dev/sda3            2400        4864    19800112+   5  Extended
/dev/sda4            1729        2399     5389807+  83  Linux
/dev/sda5            4734        4864     1052226   82  Linux swap / Solaris
/dev/sda6            3326        4733    11309697   83  Linux
/dev/sda7            2400        3325     7438032   82  Linux swap / Solaris

Partition table entries are not in disk order

```
```

~> cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

# /dev/hda4
UUID=05899d4d-d843-4389-ba4d-aade5e047bf2 / ext3 defaults,errors=remount-ro 0 1

# /dev/hda6
UUID=338dec52-0538-49f5-a143-081fa4aaabdf /home ext3 defaults 0 2

# /dev/hda1
#UUID=07D4-0217  /media/hda1  vfat  defaults,utf8,umask=007,gid=46 0       1

# /dev/hda2
UUID=3AB82F02B82EBC6F /mnt  ntfs  defaults,nls=utf8,umask=007,gid=46 0  1

#/dev/sda5 none  swap  sw  0     0
#/dev/sda7 none  swap  sw  0     0
UUID=f25ddee3-1fba-4772-b65b-29b42232b0c9 none  swap  sw  0     0

/dev/scd0        /media/cdrom0 udf,iso9660  user,noauto  0      0

sshfs#mmn@llserver:  /home/martin/mnt/llserver  fuse  defaults,noauto,user  0  0
sshfs#mmn@tjorven:   /home/martin/mnt/tjorven   fuse  defaults,noauto,user  0  0


```

I have only one disk. Ubuntu calls it "sda". The "hda" comments must be some old remnants.

```

~> ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 Mar 12 21:01 05899d4d-d843-4389-ba4d-aade5e047bf2 -> ../../sda4
lrwxrwxrwx 1 root root 10 Mar 12 21:01 338dec52-0538-49f5-a143-081fa4aaabdf -> ../../sda6
lrwxrwxrwx 1 root root 10 Mar 12 21:01 3AB82F02B82EBC6F -> ../../sda2
lrwxrwxrwx 1 root root 10 Mar 12 21:01 47CF-97D3 -> ../../sda1
lrwxrwxrwx 1 root root 10 Mar 12 21:01 b92cdc00-4a30-422b-a20b-69a04b4ea626 -> ../../sda5
lrwxrwxrwx 1 root root 10 Mar 12 21:01 f25ddee3-1fba-4772-b65b-29b42232b0c9 -> ../../sda7


```

My swap is on /dev/sda7. The old (too small) swap partition is /dev/sda5. I plan to delete it and assign the space to my home partition.

```

~> cat /proc/swaps 
Filename                                Type            Size    Used    Priority
/dev/sda7                               partition       7438024 16528   -1

```

---

### Post by logos34 on 2008-03-13
> **jazzgossen said:**
> more verbose output to see what's going wrong? I haven't found any hibernate.log on my system.

system>admin>system log

The UUID appears correct:
> lrwxrwxrwx 1 root root 10 Mar 12 21:01 f25ddee3-1fba-4772-b65b-29b42232b0c9 -> ../../sda7
...

UUID=f25ddee3-1fba-4772-b65b-29b42232b0c9 none  swap  sw  0     0


You could go back to using '/dev/sda7' instead of the UUID...I'm not sure it will help because it's obviously mounting.  Or before trying to hibernate a second time do 

sudo swapoff -a 
sudo swapon -a

There's also this fix:
[http://ubuntuforums.org/showthread.php?t=471855](http://ubuntuforums.org/showthread.php?t=471855)

---

### Post by jazzgossen on 2008-03-21
Doing swapoff/swapon works. At least it has worked twice now. Thanks a lot!

But why does it work?

---

