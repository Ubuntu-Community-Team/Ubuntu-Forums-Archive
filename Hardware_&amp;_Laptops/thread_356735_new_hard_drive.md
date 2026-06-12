---
title: "new hard drive"
date: 2007-02-08
forum: Hardware &amp; Laptops
---

### Post by StOnE LiBeRaTiOn on 2007-02-08
Hi, I just got a new 320 gig seagate ide hard drive for storage purposes.  I plugged it in but it seems like ubuntu doesn't recognize it or somthing?  I tried booting up in my windows, and windows recognized the drive and said that it was formatted in ntfs.  How do I allow ubuntu to see the harddrive, and then re-format it to ext3 or fat32? (What would be best).

thanks a bunch

---

### Post by taurus on 2007-02-08
It's up to you which filesystem you want to format that new harddrive to.  If you use ext3, Windows can read it with [http://www.fs-driver.org](http://www.fs-driver.org).  But if you format it as fat32, then you can't save a file larger than 4GB to it.

So, install gparted if you haven't done so and use it to format it to either ext3 or fat32.  Then mount it with

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
-or-
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

