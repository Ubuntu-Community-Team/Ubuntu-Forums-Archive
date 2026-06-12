---
title: "How to have /boot partition on separate hard drive from / hard drive"
date: 2012-01-17
forum: Hardware
---

### Post by AsifHirai on 2012-01-17
I am planning to build my own computer and don't want to buy a gigantic ssd for fast speeds, just a fast boot speeds. I am going to buy a 32GB SSD to house my /boot partition and drivers. Is there a way to put the boot partition on the ssd and have the / "root" directory on the main 1TB Drive?

---

### Post by Rumo on 2012-01-17
> **AsifHirai said:**
> Is there a way to put the boot partition on the ssd and have the / "root" directory on the main 1TB Drive?

Yes, and it is also not that hard to do - if you know how to use the partition manager that is part of the installation process. You just have to create a partition on your ssd and set its "mount point" to /boot. Then create another partition on your hdd and set its mount point to /.

However, if you have a little more space on your ssd to spare I would recommend to put the whole root directory on your ssd (12 GB should suffice). You can then create another partition on your hdd and set its mount point to /home. This way all your data will be on the slow hard drive and the system and all software resides on your ssd, i.e. faster system AND program startup.

---

### Post by kevdog on 2012-01-18
This is totally possible to do. Only chime in to put your /home partition separately.  

Good luck.

---

