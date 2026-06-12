---
title: "No signs of HD existence."
date: 2008-04-17
forum: Hardware &amp; Laptops
---

### Post by jairajs89 on 2008-04-17
So bought a new 500GB Seagate external hard drive today and came back and plugged it in. At first it mounted, but it was in NTFS, so I reformatted it to ext3. And then it disappeared. It doesnt show up when I browse through the "Computer" folder or in /media. In /dev it shows up as /dev/sdb & /dev/sdb1. But I cant mount it or open it. The only way I can do anything with it is if I open GParted, but then I can only see where it is and reformat it. Basically I just want to be able to use it like my other HD's. Please help, because I cant get a refund on this $120. Thanks!

---

### Post by dabl on 2008-04-17
Probably you would be better off formatting it to FAT32 or else back to NTFS.  I don't think ext3 is a format that can be used for removable media, if you ever expect to "hotplug" or "hot unplug" that drive. I'd say try FAT32 first and see if that is satisfactory.  You can do that from a Windows PC, then try it again on your Linux box.

Once recognized in Linux, it should show up in /media, and on the device list when you run lsusb. :)

---

### Post by jairajs89 on 2008-04-17
I actually had it already reformatted to FAT32 on my friends Mac, but it still doesnt show up. And there is also no record of it in /etc/fstab. It shows up when I run lsusb as "Bus 005 Device 025: ID 0bc2:3000 Seagate RSS LLC" .  Thanks.

---

