---
title: "Lost Hard Drive Space"
date: 2004-11-16
forum: Hardware &amp; Laptops
---

### Post by DaGr8Gatzby on 2004-11-16
I have a 120 Gig Hard Drive. I installed Ubuntu with all defaults and updated via the network after restart. So I look in nautilus and it says I have 105 Gigs left. That's 15 gigs I have lost. I don't know if this is normal or not. Output of df -H

/dev/hda1              121G   1.7G   113G   2% /
tmpfs                  132M      0   132M   0% /dev/shm

Someone help. :) It's not really TOP priority just wondering. :)

---

### Post by randy on 2004-11-16
I'm guessing df is right and nautilus is wrong.  There might be a bug in nautilus.  Try searching around online for reports of this.

---

### Post by DaGr8Gatzby on 2004-11-16
Lol regardless df -H states that my HD is 120 gigs and that only 2 gigs are being used...I dunno it's just weird...

Filesystem             Size   Used  Avail Use% Mounted on
/dev/hda1              121G   2.2G   113G   2% /
tmpfs                  132M      0   132M   0% /dev/shm

After upgrading to Hoary.

---

