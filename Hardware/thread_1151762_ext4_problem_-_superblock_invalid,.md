---
title: "ext4 problem - superblock invalid,"
date: 2009-05-07
forum: Hardware
---

### Post by supersonicdarky on 2009-05-07
I tried to resize an ext4 partition from 90gb to 180 in gparted, however this is the error I get (after it moved it to the left)
```
e2fsck 1.41.5 (23-Apr-2009)
fsck.ext4: Superblock invalid, trying backup blocks...
fsck.ext4: Bad magic number in super-block while trying to open /dev/sdb2

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```
Not sure what exactly the command does, so decided not to run it to avoid data loss. Anyone mind helping recovering the partition? The data is rather important.

Running custom 2.6.29.2 btw.

Thnx.

---

### Post by Vms100 on 2009-05-07
Are you sure that gParted supports Ext4 yet? :)

---

### Post by whoop on 2009-05-07
Resizing ext4 partition is quite nasty at the moment:
[http://www.ubuntu.com/getubuntu/releasenotes/904#Possible%20data-loss%20problems%20resizing%20ext4](http://www.ubuntu.com/getubuntu/releasenotes/904#Possible%20data-loss%20problems%20resizing%20ext4)

---

