---
title: "reinstall to compensate for disk hardware problem ?"
date: 2013-03-23
forum: Hardware
---

### Post by gscratch on 2013-03-23
This is a generic Intel box with a single internal 80GB disk (probably Seagate, but I don't remember.  I can find out if it matters) 
running 12.04LTS native (ie, NOT a partitioned disk dual-boot with Windows)
 
Recently, Ubuntu takes a long time to start and the disk makes the 'scrape scrape scrape pause scrape scrape scrape' noise when I start FireFox.
I'm able to see the file system, and have copied important data onto an external USB drive.

Would it help to completely re-install Ubuntu?  is it worth it? or should I just go buy another internal disk (which would require a complete new install anyway)

thanks

---

### Post by ibjsb4 on 2013-03-23
Check you HDD with "Disk Utility" to see what shape its in.  It should already be installed in your system.

[https://apps.ubuntu.com/cat/applications/precise/gnome-disk-utility/](https://apps.ubuntu.com/cat/applications/precise/gnome-disk-utility/)

---

### Post by ahallubuntu on 2013-03-23
~

---

### Post by mörgæs on 2013-03-23
If the bad sectors are in one area of the disk, for example the first 10 GB, you can create an empty (unused) partition there and only use the rest.

---

