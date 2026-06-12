---
title: "NTFS USB HDD Problem switching from Ubuntu to Kubuntu"
date: 2007-06-26
forum: Hardware &amp; Laptops
---

### Post by gilforsyth on 2007-06-26
I just recently decided to try switching to KDE for a little bit and most things migrated over without a problem, but my external HD is causing me some little headaches.  
Initially, the drive wouldn't show up in KDE at all.  I reinstalled ntfs-config and it detected my drive, which is at /dev/sdb5, but checking the "external devices writable" left my HD readable but not writeable.  Only when I clicked to allow internal devices was the drive detected and writable.  
However, since it thinks it's an internal drive, if I turn it off, I have to go through ntfs setup again to get it to mount on the desktop.  

I can access my drive by just using simple pmount, but I'm wondering if anyone has any thoughts on how to get my drive to automount with a little less hassle.  

Also, it's an old WD250 internal that I just threw into an enclosure when my last desktop died.  Think that could be causing problems?  

Any advice is appreciated.

---

