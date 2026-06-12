---
title: "Adding another harddrive"
date: 2009-05-21
forum: Installation &amp; Upgrades
---

### Post by alexlaban on 2009-05-21
I ordered new hdds for my work pc which will arrive either tomorrow or on Monday. Anyway as I will not fit all my current hdds in my work pc I want to put one of my current 1TB hdds in my server, anyway would it be possible to make that hdd appear as an folder in home with the name vdws and of course it should automatically mount if the server ever get restarted.

---

### Post by .nedberg on 2009-05-21
Should not be a problem

create the mount point:
mkdir ~/vdws

add an entyr in /etc/fstab:
/dev/sdb1 /home/username/vdws ext3 auto 0 0

Remember to change sdb1 and username (and perhaps the filesystem) to the correct values! You can also play around with more options if you get problems.

---

