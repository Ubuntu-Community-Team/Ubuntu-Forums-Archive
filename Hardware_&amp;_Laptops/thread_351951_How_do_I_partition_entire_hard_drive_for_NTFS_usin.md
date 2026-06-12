---
title: "How do I partition entire hard drive for NTFS using 64K clusters"
date: 2007-02-02
forum: Hardware &amp; Laptops
---

### Post by mugshot-joe on 2007-02-02
How do I partition entire hard drive for NTFS using 64K clusters.  I would like to partion drive /dev/sda1 with a single partion for entire drive.  I want to use 64K cluster size.  I am using Ubuntu 6.10 Edgy on drive /dev/hda1.

Gparted does not seem to allow the selection of cluster sizes for NTFS.  Please help as I do not want to have to buy a program.

---

### Post by MoLE on 2007-02-03
Are you sure you want to use NTFS for a new drive on a computer you only have Ubuntu on?  NTFS is a prorietary disk format, so not all the features have been reverse-engineered yet for use by open-source software.  Writing to NTFS drives under linux using open-source tools is only partially supported and very new.

Why not check out the [linux-ntfs]("http://www.linux-ntfs.org/") project for details?


If you want a high-quality journalling filesystem, I'd recommend Ext3 or ReiserFS, but there are many others.

---

