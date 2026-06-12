---
title: "[SOLVED] How to find HDD uuid?"
date: 2008-12-31
forum: Installation &amp; Upgrades
---

### Post by kgriff on 2008-12-31
I just installed new 250GB hard drive in my system.(sda1)  I used gparted to create a 70GB partition as ext3.  Then chmod to give myself permission.  Created a mount point for it in /media.  Then mounted the drive.  Everything worked fine.  The only thing I can't seem to figure out is how to find out what the uuid is for this disk.  I have tried:

ls /dev/disk/by-uuid/ -alh.  

All of my other partitions show up, but not this one.

Anyone know how I can determine the uuid of this disk?

---

### Post by taurus on 2008-12-31
```
sudo blkid
```

---

### Post by kgriff on 2008-12-31
Thanks, taurus, for the response.  This gives the uuid, but leads me to another question.

Why do I see it here, but not using ls?

---

### Post by edfast on 2013-04-02
Thank you.

---

### Post by oldos2er on 2013-04-02
Closed, please don't bump old threads.

---

