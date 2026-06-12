---
title: "HDPARM and sda"
date: 2008-06-22
forum: Hardware
---

### Post by DanielReidal on 2008-06-22
I have two disks in my server. I tried to use these commands
hdparm -S12 /dev/sda
hdparm -S12 /dev/sdb

This works fine on sdb, but sda will never enter powerdown. I think it is because the root file system is located there.

I wan't both sda and sdb to enter power down state. Someone that has any ideas?

Cheers! Daniel

---

### Post by sdennie on 2008-06-22
What filesystems are the two drives using?  If you are using ext3, I don't think either disk will ever power down by default.  Have a look at this thread for information on how to set it up to do so: [http://ubuntuforums.org/showthread.php?t=833301](http://ubuntuforums.org/showthread.php?t=833301)

---

### Post by DanielReidal on 2008-06-22
Hi, I have ext3 on both drives. I can hear how sdb turns off after 60 sec (-S12)

I did not understand the discussion in the thread you recommended ;-(

The reason why I will do this is to save some power, the space where the server is placed sometimes get quite hot


DR

---

### Post by sdennie on 2008-06-25
Sorry for the long delay in responding.  I wrote a formal guide on how to do this here: [http://ubuntuforums.org/showthread.php?t=839998](http://ubuntuforums.org/showthread.php?t=839998)

---

