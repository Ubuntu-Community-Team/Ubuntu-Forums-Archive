---
title: "How to mount dvdrom drive?"
date: 2005-10-05
forum: Hardware &amp; Laptops
---

### Post by EonDupe on 2005-10-05
I tried mounting with following but I get this "you must specify the file system type" and can't access my data. I am a newb, please help.

sudo mount /dev/hdc /media/cdrom0
Password:
mount: block device /dev/hdc is write-protected, mounting read-only
mount: you must specify the filesystem type

---

### Post by mlomker on 2005-10-05
Try:

```

sudo mount -t auto /dev/hdc /media/cdrom0

```

If that doesn't work then try udf and iso9660 instead of *auto*.

---

### Post by EonDupe on 2005-10-05
Thanks for the quick reply bro. 

I did what u suggested, here's what I got.

 sudo mount -t udf /dev/hdc /media/cdrom0
mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

What is my next step? I appreciate your help a lot. Thanks.

---

### Post by mlomker on 2005-10-05
If you've tried all three then it probably isn't going to work.  What kind of disc is this?  I've heard from people that haven't been able to mount those mini-dvd's like from camcorders...I don't think they're supported in linux.

---

