---
title: "Problem formatting an NTFS partition to Ext4"
date: 2010-02-26
forum: Hardware
---

### Post by Servant on 2010-02-26
Hello,

I have a 160GB hard drive that had two partitions, both NTFS. I then booted up the live-cd and formatted the another one to Ext4.

I have done the formatting twice now, the first time Storage Device Manager reported the formatted drive as Swap, now it's reporting it as NTFS. If I try to use Disk Utility it hangs.

Also when trying to mount the (supposed) Ext4 partition I get:

Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sda1 on /media/sda1

The NTFS partition mounts fine, it's set to mount on startup via Storage Device Manager.

Here is my Fstab:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                  0  0  
# / was on /dev/sdb1 during installation
UUID=ee5e2f0f-b940-443b-9993-b36ca5fddb74  /               ext4         errors=remount-ro         0  1  
# swap was on /dev/sdb5 during installation
UUID=a7626283-20ac-4bb8-9d31-b9ad61562161  none            swap         users,user,dirsync        0  0  
/dev/scd1                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8     0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec,utf8  0  0  
/dev/sda2                                  /media/sda2     ntfs         nls=iso8859-1,umask=000   0  0  
/dev/sda1                                  /media/sda1     ntfs         nls=iso8859-1,umask=000   0  0
```

I'm not sure I provided all the info needed, please ask for more if in need.

---

### Post by jocko on 2010-02-26
More info needed; post the results of:
```
sudo fdisk -l
sudo blkid
```

---

### Post by Servant on 2010-02-26
sudo fdisk -l:

```
Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b07b7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9965    80043831   83  Linux
/dev/sda2            9966       19929    80035830    7  HPFS/NTFS

Disk /dev/sdb: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2a4a2a4a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2373    19061091   83  Linux
/dev/sdb2            2374        2482      875542+   5  Extended
/dev/sdb5            2374        2482      875511   82  Linux swap / Solaris
```sudo blkid:

```
/dev/sda1: LABEL="stnanmaxtorext4" UUID="a9101349-3ad7-4a7c-aea5-751e5d48db96" TYPE="ext4" 
/dev/sda2: UUID="E2C0336FC0334955" LABEL="stnanmxtor2" TYPE="ntfs" 
/dev/sdb1: UUID="ee5e2f0f-b940-443b-9993-b36ca5fddb74" TYPE="ext4" 
/dev/sdb5: UUID="a7626283-20ac-4bb8-9d31-b9ad61562161" TYPE="swap"
```

Oh, theres also a GRUB on either of the partitions, left over from a ubuntu 7 installation

---

### Post by jocko on 2010-02-26
Here's how to get your new ext4 partition to be mounted:
```
gksudo gedit /etc/fstab
```
Remove the entry for the old ntfs partition that you no longer have:
```
/dev/sda1                                  /media/sda1     ntfs         nls=iso8859-1,umask=000   0  0
```
And make a new line for your new ext4 partition:
```
UUID=a9101349-3ad7-4a7c-aea5-751e5d48db96 /media/sda1      ext4         defaults                  0  2
```

---

### Post by Servant on 2010-02-26
Did the edits you suggested, now the partition is mounted at boot time ok, but the owner of the partition seems to be root. I can't copy files there or unmount it.

I get:

Error unmounting: umount exited with exit code 1: helper failed with:
umount: only root can unmount UUID=a9101349-3ad7-4a7c-aea5-751e5d48db96 from /media/sda1

if I try to unmount it.

---

### Post by jocko on 2010-02-26
> **Servant said:**
> Did the edits you suggested, now the partition is mounted at boot time ok, but the owner of the partition seems to be root. I can't copy files there or unmount it.

I get:

Error unmounting: umount exited with exit code 1: helper failed with:
umount: only root can unmount UUID=a9101349-3ad7-4a7c-aea5-751e5d48db96 from /media/sda1

if I try to unmount it.
You need to change ownership on the file system (do this when it is mounted):
```
sudo chown -R $USER:$USER /media/sda1
```You need to be root to unmount. That's just the way it is. Unmount it by:
```
sudo umount /media/sda1
```

---

### Post by Servant on 2010-02-26
Thanks a bunch jocko! Everything seems to work now.

---

