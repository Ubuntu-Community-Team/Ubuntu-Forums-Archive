---
title: "HFS+ Journalized USB Drive"
date: 2007-05-21
forum: Hardware &amp; Laptops
---

### Post by ericbarch on 2007-05-21
I need to be able to use a USB drive between my Mac and my Ubuntu machine. I need full read/write privileges on the Ubuntu machine. I'm running Ubuntu Server and trying to get the USB drive to be recognized. Is this possible to mount this drive with read/write privs? Just plugging in the drive does nothing and I don't see anything appearing in /media. Any help would be greatly appreciated. Thanks.

---

### Post by raintheory on 2007-05-21
You will need to turn off journaling in order to use it on Ubuntu I believe.

Here is some other info for HFS+ read/write/repair: [http://ubuntuforums.org/showthread.php?t=392287](http://ubuntuforums.org/showthread.php?t=392287)

---

### Post by ericbarch on 2007-05-21
I tried df -h and I don't even see the USB drive. Any reason for this?

---

### Post by ericbarch on 2007-05-21
I found the device. After following the steps on that page, when I try to create any files on the non-journalized HFS, I still get read only FS errors.

---

