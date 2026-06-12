---
title: "Linux disk on a windows PC"
date: 2009-08-04
forum: Hardware
---

### Post by toreadore on 2009-08-04
Hi, 
I have a old Matrox HDD, here named "Mickey", which until recently served as disk in my LAMP server. Since the server PC crashed, I need to retrieve some of the files from Mickey onto my Windows XP PC ? I have a USB adapter to put Mickey into, and windows finds it, but does not map it as a drive.. Any solution?

Tore V

---

### Post by GoldenSun on 2009-08-04
the hd may be pwnd?
try to mount it in linux.  If no luck you may have to photorec it for the info.

---

### Post by balaknair on 2009-08-04
Windows does not read *nix filesystems by default, only NTFS and FAT. Try fsdriver to let windows read your linux filesystem(ext3 by default on Ubuntu)
[http://www.fs-driver.org/](http://www.fs-driver.org/)

If you're using Ubuntu 8.10 or 9.04, fs-driver might not work(problems with reading the larger inode size on these version).
In that case, try ext2fsd
[http://www.ext2fsd.com/](http://www.ext2fsd.com/)
It's what I'm using at present on Ubuntu 9.04

---

