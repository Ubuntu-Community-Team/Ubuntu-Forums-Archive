---
title: "Weird exFAT mount error (EOD entry)"
date: 2012-01-23
forum: Hardware
---

### Post by Ryupower on 2012-01-23
Hey all!
First of all, I'm very thankful for this community, and thank you for helping me out quickly and nicely in the past. :)

Now,
I installed FUSE for exFAT and scons(if it has much relevancy, I found a script in another thread and tried using it. Unfortunately it didn't work :( ).

And, well, I try to mount the exFAT partition (sdd1) via shell into the mountpoint 'media/name_WD'. And this happens:

```
root@ubuntu:/# mount -t exfat-fuse /dev/sdd1 name_WD
FUSE exfat 0.9.6
ERROR: missing EOD entry (0x20000, 0x20000). 
root@ubuntu:/# 
```

This is really strange. I have gotten it to work once, but then I changed back to XP and updated Ubuntu Linux  with apt-get-updgrade a little when I returned to the ubuntu partition. Ever since it has not worked for some odd reason, and I've been getting that stupid error!

Anyone here to help this lil' gal out? ;)
thanks! :)

----
Further information:
running. Oneiric Ocelot
hard drive is still dev/sdd1, it has not changed.
USB 3.0 (if that even makes a difference here)
Works neither in XFCE nor Unity desktop environments.

---

### Post by Ryupower on 2012-01-23
bump?

---

### Post by Ryupower on 2012-01-24
anyone? This is a big problem for me!

---

### Post by Ryupower on 2012-01-28
for extra information, I installed exfat-utils as well. Still to no avail.

---

