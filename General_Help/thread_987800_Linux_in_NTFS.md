---
title: "Linux in NTFS"
date: 2008-11-19
forum: General Help
---

### Post by MillionFlame on 2008-11-19
sorry if this question is in the wrong catagory, but i was just curious, is the any version of linux that uses the ntfs file system?

---

### Post by Chunky Dunk on 2008-11-19
You can read and write to ntfs file systems from Linux, but I've never heard of it being installed on one (aside from Ubuntu's wubi).

---

### Post by y@w on 2008-11-19
Uses as in uses as a root partition or uses as in can read/write to NTFS? If the first, then not that I'm aware of. I'm not sure why you would want to.. If the second, then yes: [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by Chunky Dunk on 2008-11-19
> **y@w said:**
> Uses as in uses as a root partition or uses as in can read/write to NTFS? If the first, then not that I'm aware of. I'm not sure why you would want to.. If the second, then yes: [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

I can write to ntfs on mine, with a plain install and no tinkering...

---

### Post by MillionFlame on 2008-11-20
> **Chunky Dunk said:**
> I can write to ntfs on mine, with a plain install and no tinkering...

really? how did u manage that if u dont mind me askin?

---

### Post by TeXtonyx on 2008-11-20
Code:

sudo apt-get install ntfs-config
gksudo ntfs-config

This will prompt you to make a folder under /media which will
mount your ntfs partition and show a linking icon on your desktop.

---

### Post by Gausian on 2008-11-20
ntfs support is enabled by default in Ubuntu.  you shouldnt have to install separate packages.

---

