---
title: "Accessing Ubuntu data when Windows is booted?"
date: 2008-08-26
forum: General Help
---

### Post by Huggle67 on 2008-08-26
Hi All, 

I am new to Ubuntu and Linux in general. I have managed to install Ubuntu 8.04 to an external hard drive with minimal difficulties and can now boot it. But I need to be able to access the data in my external hard drive when my internal Windows hard drive is booted. When I go to My Computer my D:, which is my Ubuntu drive, is not there. Is it possible to access this data?

Thanks in advance. :)

---

### Post by ibuclaw on 2008-08-26
There is a [filesystem module]("http://www.fs-driver.org/") out there for Windows, but it is an unjournalised driver, so any crash on Windows can potentially mess your Ubuntu partition up.

Regards
Iain

---

### Post by ajgreeny on 2008-08-26
I suggest you get **explore2fs** for your windows box from [here]("http://uranus.it.swin.edu.au/%7Ejn/linux/explore2fs-old.htm"). It allows you simply to read and export and view files on your ubuntu file system when booted into windows, but not to write to the file system so there is no real danger to the ubuntu install.  I have used it for about 3 or 4 years and never had a problem with it.  I don't really use it any more, but that's because I so seldom boot into windows any more.

---

### Post by WRDN on 2008-08-26
> **ajgreeny said:**
> I suggest you get **explore2fs** for your windows box from [here]("http://uranus.it.swin.edu.au/%7Ejn/linux/explore2fs-old.htm"). It allows you simply to read and export and view files on your ubuntu file system when booted into windows, but not to write to the file system so there is no real danger to the ubuntu install.  I have used it for about 3 or 4 years and never had a problem with it.  I don't really use it any more, but that's because I so seldom boot into windows any more.

FS- Driver also allows for a read-only mode of the partition(s), so the deciding factor is compatibility and dependability.

---

