---
title: "[USB] USB harddrives not automatically mounted"
date: 2008-12-01
forum: General Help
---

### Post by kakyoism on 2008-12-01
My USB drives were plugged and functioning well until a moment ago the disk-mounter on gnome-panel suddenly appeared empty and 

"ls /media"  gives nothing but cdroms
"fdisk -l" gives nothing at all!

I tried removing the drives and plugging them back and nothing happened.
Help!

---

### Post by taurus on 2008-12-01
What filesystem is it?

---

### Post by kakyoism on 2008-12-01
two of them are FAT32, and the other one is NTFS

---

### Post by kakyoism on 2008-12-01
I had to restart my laptop to call them back.
A gnome restart didn't solve this.

Are there any easier ways?

---

### Post by taurus on 2008-12-01
```
sudo fdisk -l
```
doesn't even show that external harddrive?  What is the output of this command?

```
dmesg | tail
```

---

