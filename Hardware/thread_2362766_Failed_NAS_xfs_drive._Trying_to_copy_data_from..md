---
title: "Failed NAS xfs drive. Trying to copy data from."
date: 2017-06-01
forum: Hardware
---

### Post by mmmelvin on 2017-06-01
New to Ubuntu for only the purpose of recovering this data from a failed NAS drive.  The drive is using the xfs file system. The drive returned bad from a manufacturer diagnostic, so I used Clonezilla to place the contents on a functioning drive. I am normally a Windows guy, so I found a program called fsproxy that would allow me to read the contents of this copied drive, but the program is consistently failing (no longer supported). I have copied some data off of it, but it only works for about 5 or 10 minutes and then looses connection. So I decided to try Ubuntu to see if I could recover the files with this OS. The drive is recognized as /dev/sdb non boot drive, with a fresh install of Ubuntu on an SSD drive to help speed things along. However, I am not able to mount this drive. I am confused why I could see it with fsproxy and not inside of a Ubuntu OS? Could someone shed some light on what I am missing in this. I ran gparted and it does see the partitions on it, alas still unable to mount or copy the data.

---

### Post by SeijiSensei on 2017-06-01
Did you try to mount the dev, /dev/sdb, or the partitions on it?  You can only mount partitions with filesystems.  If the XFS filesystem is on partition 1, try
```
sudo mount /dev/sdb1 /mnt
```
Linux should recognize the XFS file system automatically.  If not you can try
```
sudo mount -t xfs /dev/sdb1 /mnt
```

There are XFS tools that you may need to run if you cannot mount the filesystem.  You may also need to load the xfs module manually.  Install the **xfsprogs** package and read this:  [https://wiki.ubuntu.com/XFS](https://wiki.ubuntu.com/XFS)

When you're done, get rid of XFS and reformat with ext4.  My experience is that XFS is pretty fragile and is prone to losing data if there's a power outage.

---

### Post by mmmelvin on 2017-06-05
That worked! Still attempting to find and copy data, but that did let me mount the partition. I did not know I had to mount that partition. Thanks for the help Sensei.

---

