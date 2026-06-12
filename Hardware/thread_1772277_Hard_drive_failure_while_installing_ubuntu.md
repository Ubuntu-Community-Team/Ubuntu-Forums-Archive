---
title: "Hard drive failure while installing ubuntu"
date: 2011-05-31
forum: Hardware
---

### Post by VishmanX on 2011-05-31
Hi, I need help with Ubuntu installation. I had Ubuntu 6.06 Dapper Drake on my HP Pavilion 512n and one day I was trying to install Fedora 7 over it and then the computer froze while partitioning. I booted the computer again to see the "Operating System Not Found" message. I then went back to install Ubuntu and got to the partitioning phase. I then selected guided partitioning SCSI 0,0,0 on my 60 GB hard disk. However when I started to partition, every Ubuntu disk I tried said error /dev/sda and said retry, ignore, or cancel options. I really don't know what is wrong but want to reinstall Ubuntu, so if anyone knows my answer, please help.

---

### Post by psusi on 2011-05-31
First, 6.06 has been obsolete and unsupported for years; you need to get a more recent release.

Second, what exactly are you looking for here?  You said the hard drive is failing, so... replace it.

---

### Post by Yellow Pasque on 2011-05-31
Boot a Linux CD. Figure out what disk you want to format using:
```
fdisk -l
```
Then use dd to zero the disk (this example uses /dev/dsa):
```
dd if=/dev/zero of=/dev/sda
```

If that doesn't work, you may be in the market for a new disk :\

---

