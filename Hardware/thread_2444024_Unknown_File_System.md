---
title: "Unknown File System"
date: 2020-05-23
forum: Hardware
---

### Post by danteguerrerobarreto on 2020-05-23
I have a computer with an SSD and a HD. I recently installed Ubuntu 20.04 in my computer in the SSD and it runs ok. My problem is that when I look for the HD in Gparted it shows me this message: "Unknown File System" and I can't access to the information. It is a 2TB HD and I have more than 400 GB of data that I don't want to lose. Any idea what is going on and what can I do?

---

### Post by TheFu on 2020-05-23
Rather than trying to explain stuff, how about you show some facts.

```
sudo fdisk -l /dev/sd[a-z]
```
and
```
lsblk -e 7 -o name,size,type,fstype,mountpoint
```

Use _code tags_ when posting or the results will be unreadable here and you won't get any help.

If the HDD was connected to a Windows system previously, Windows probably left the file system mounted. The only fix for that is to have Windows close the file system. Nothing can be done from the Linux side.  Also, Windows has some new ways of dealing with file systems which are incompatible with Linux.  If the partitions are "basic", then you'll need to convert them, again, using Windows, for Linux to have easy access.

---

