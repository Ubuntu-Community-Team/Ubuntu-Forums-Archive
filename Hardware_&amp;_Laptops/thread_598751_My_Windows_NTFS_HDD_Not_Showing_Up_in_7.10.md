---
title: "My Windows NTFS HDD Not Showing Up in 7.10"
date: 2007-10-31
forum: Hardware &amp; Laptops
---

### Post by coollettuce on 2007-10-31
I just installed ubuntu about 30 mins ago and in the livecd my ntfs drive showed up. But after installing it its not showing up under "computer" but it does show up when i use gnome-parted but it says its unable to read the contents of the file system. also, is it possible to format ntfs somehow in linux becuase i left over 90gb from my install so i could later format it ntfs for a backup. thanks.

---

### Post by coollettuce on 2007-10-31
OK I solved it, I used "sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force". Thanks anyway for your help which I know you would have given me.

---

### Post by taurus on 2007-10-31
Why not add an entry in /etc/fstab so it would be mounted automatically each time you boot into Ubuntu.  Then, you don't have to mount it by hand every single time.

```
gksudo gedit /etc/fstab
```

```
/dev/sdb1     /media/sdb1   ntfs-3g   defaults,locale=en_US.utf8   0   0
```

---

### Post by puleen on 2007-10-31
I have a similar problem. Following is the scenario for me:

1) Windows XP (NTFS) partition is on the same drive as Ubuntu.
2) Another physical drive also NTFS partition I use to store all my projects.
3) Another external USB drive I use to store my personal files, photos etc.

Sometimes when I start Ubuntu, 1) and 2) show up and get mounted, and they have appropriate entries in /etc/fstab. And almost always 3) gets mounted without any problem.

Any reason why 1) and 2) sometimes get mounted, while other times do not get mounted?

Here is a copy of my /etc/fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=d9d78dcc-3ca7-489d-9a41-9a6d6bcbce1c /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=B8E8526AE8522742 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb1
UUID=4CE4A994E4A98136 /media/sdb1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=e7df3cf0-e15b-4d40-9995-ca8a68497509 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0


Thanks,

Puleen

---

### Post by taurus on 2007-10-31
Next time when /dev/sda1 and /dev/sdb1 don't mount at boot time, try to mount them by hand from a terminal and see if there is any error message.

```
sudo mount -t ntfs /dev/sda1 /media/sda1
sudo mount -t ntfs /dev/sdb1 /media/sdb1
```

---

### Post by puleen on 2007-10-31
You are absolutely correct, the problem turned out to be that Windows didn't shutdown properly previously and after booting into windows and shutting it off properly, resolved the problem.

Thanks!

Puleen

---

