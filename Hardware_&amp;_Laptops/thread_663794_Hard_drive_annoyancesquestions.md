---
title: "Hard drive annoyances/questions"
date: 2008-01-10
forum: Hardware &amp; Laptops
---

### Post by silverhammermba on 2008-01-10
In addition to my Ubuntu partitions, I have two NTFS partitions that I use for Windows and storage. I want access to these partitions from Ubuntu because, for example, I keep my music there. But every time I restart my computer Ubuntu "forgets" about these partitions. They disappear from my desktop, my bookmarks, and AmaroK can't find any of my music. I have to manually open each partition in Nautilus (which then prompts me for my root password) before I can use them. It's annoying to do this every time I restart. Is there any way to make Ubuntu recognize them automatically?

Also, I recently read that NTFS is read-only from Ubuntu - but I've been adding and deleting files from these partitions without any trouble. One weird thing that I've noticed is that when I delete files from them, they don't end up in the Ubuntu trash but I also don't think that they're deleted permanently. Where would these files end up and how would I go about deleting them permanently?

Thanks in advance.

---

### Post by LaRoza on 2008-01-10
No, NTFS in Gutsy is easily read and written to. You can delete files safely.

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

The trash will be named ".trash-username", you can delete it and its contents to remove the files.

---

### Post by taurus on 2008-01-10
Do you try to mount those ntfs partitions from /etc/fstab?  Can you post the outputs of these commands from a terminal?

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by silverhammermba on 2008-01-10
I have not tried to mount the partitions from /etc/fstab. However, I believe that the partitions are mounted because when I boot up I can see them under /media/. I think the problem is that Ubuntu needs my root password to actually access them, so none of my programs can use them until I do so.

Anyway, here's that output:
```
max@apotheosis:~$ sudo fdisk -l
[sudo] password for max:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x16261625

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2832c82a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19861   159533451    7  HPFS/NTFS
/dev/sdb2   *       19862       30026    81650362+  83  Linux
/dev/sdb3           30027       30401     3012187+   5  Extended
/dev/sdb5           30027       30401     3012156   82  Linux swap / Solaris

max@apotheosis:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=4f5cb9ca-3458-4bd0-86c6-ccf377eef333 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=04db0347-7073-4f17-bd08-dc9005effc5e none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

max@apotheosis:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb2              77G  7.3G   67G  10% /
varrun                503M   96K  503M   1% /var/run
varlock               503M     0  503M   0% /var/lock
udev                  503M   84K  503M   1% /dev
devshm                503M     0  503M   0% /dev/shm
lrm                   503M   38M  466M   8% /lib/modules/2.6.22-14-generic/volatile
/dev/sdb1             153G   52G  101G  35% /media/Psalms
/dev/sda1              75G   46G   29G  62% /media/disk

```

---

### Post by taurus on 2008-01-10
Why not edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add these two entries for your ntfs partitions.

```

/dev/sdb1   /media/sdb1   ntfs-3g   defaults   0   0
/dev/sda1   /media/sda1   ntfs-3g   defaults   0   0
```
Save it and close down gedit window.  Then, install ntfs-3g driver and create those two new mount points.

```
sudo apt-get update
sudo apt-get install ntfs-3g
sudo mkdir /media/sda1 /media/sdb1
```
Reboot and those two parititons now will be mounted to /media/sda1 & /media/sdb1.  Now, you should be able to read and write without root privilege.

---

### Post by silverhammermba on 2008-01-10
Yeah, it turns out they weren't being mounted automatically. Your solution worked perfectly! Thanks.

---

