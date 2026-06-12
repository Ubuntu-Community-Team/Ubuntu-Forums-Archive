---
title: "NTFS or Ext3/4 formatting in storage Sata HDs"
date: 2009-08-04
forum: Installation &amp; Upgrades
---

### Post by bn127 on 2009-08-04
I run Jaunty amd64 in a 3 SATA HDs system: 1 (160GB/Ext4) for Ubuntu and 2 (500GB/NTFS and 1TB/NTFS) for media and other stuff storage which I mount when necessary. It already happened twice that these NTFS disks reported errors that Parted Magic point out to be solved by running chkdsk /f in Windows. I'm 100% on Ubuntu it makes more than a year now and I don't have any way to run and check the HDs in Windows. Is there a way to solve this kind of problem out of Windows? Is it better to format the 2 HDs in Ext3 or Ext4?

I'd very much appreciate your advise on this matter.

Best.

bn127

---

### Post by merlinus on 2009-08-04
Linux tools for working with and troubleshooting ntfs partition:

[http://man.linux-ntfs.org/](http://man.linux-ntfs.org/)

```
sudo apt-get install ntfsprogs
```

---

### Post by bn127 on 2009-08-04
Thank you. I'll use it if the problems come again.

Any advice on formatting the storage HDs with Ext?

Best.

Bn127

---

### Post by merlinus on 2009-08-04
From perusing any number of posts, ext4 has lots of promise, but at the moment is not as stable or reliable as ext3.

I would only use ntfs if you plan to share the data with windows.

---

### Post by bn127 on 2009-08-04
As I don't use Windows anymore I'll re-format one of the disks which is now empty with Ext3.

Thanks a lot for your information and advice.

Best.

bn127

---

### Post by merlinus on 2009-08-04
Glad to be of assistance.  Have fun!

---

