---
title: "Drives mount as SVault_ and usb_ instead of SVault and usb"
date: 2007-11-20
forum: Hardware &amp; Laptops
---

### Post by konungursvia on 2007-11-20
Is it a bug or an oddity? I right click on my external fat and ntfs drives in Places. They had been mounting as Disk, Disk-1, Disk-2 and so on, which was not descriptive enough for me. So under properties, I enter the mount point SVault on the vfat, and usbntfs on the ntfs. I'm trying to mount them under /media/SVault and /media/usbnts, which I made using mkdir.

Instead, linux adds an underscore, and root creates similar /media/SVault_ and /media/usbntfs_ dirs for them. Why? I can't edit them into fstab until I really know for sure what is causing this. Any ideas? It happened under feisty at times, and now with Gutsy.

---

### Post by konungursvia on 2007-11-24
Is the unwanted underscore character an ascii ansi thing, of should i enter a different end string character?

---

### Post by konungursvia on 2007-11-26
Surely someone knows why this is happening. It's been the case since before Dapper.

---

### Post by JoeHarr4 on 2008-02-10
Unmount the device and unplug it
Delete the entry you made in /media
Replug the device
It should mount as you intended.

The USB mounting system is attempting to make the directory you want, seeing that it is already there, suspecting that some other application is using it, and making a new entry with an underscore after it for its own use.  In general, keep your hands off /media.  Use /mnt instead for things you do manually.  Occasionally, if you have a crash, you will need to delete a leftover mountpoint from /media so that it doesn't mount on an underscore directory instead.

--jh--

---

