---
title: "many problems after power surges/power outage"
date: 2007-05-26
forum: Hardware &amp; Laptops
---

### Post by sverdlov on 2007-05-26
Hi All, 

I've been in a very deep problem since yesterday. 
Many power surges and outages happened to my computer yesterday, and now my Ubuntu does not mount my NTFS drive, and it also does not download torrents - for some reason it can only upload, and not download - ktorrent stays on Stalled.... 

Please tell me how could I repair my harddrive's filesystem, if the problem is there? I know how to do it in windows, but... 

Thanks!

---

### Post by Ken_Lewis81 on 2007-05-27
Power  surges and outages can damage computer hardware.  The following advice should not lose you data, but will highlight existing problems with your filesystem.  I hope that you have backups.

The 'fsck' tool is what you need to run to check your system.  The command ```
fsck -AN
``` will go through each of your filesystems and tell you if there are any issues.  Then ```
fsck -ASy
``` will go through the file systems in turn repairing what needs to be fixed.

Take care.
Ken.

---

