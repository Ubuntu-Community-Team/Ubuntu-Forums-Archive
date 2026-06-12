---
title: "New HD"
date: 2008-10-25
forum: General Help
---

### Post by MrZehl on 2008-10-25
I installed a new HD, partitioned it, formatted it ext3, made a mounting point and added it to my fstab. In fstab I copied the line from an other working hd (same brand, type and size).
The hd is recognised and mounted at start up. But... it seems I have no writing rights on the new partition. Since I copied the line in fstab from an other partition that is working and is also ext3 and one single partition on the hd, it is not to expect that the problem is in fstab.

So.. my question is....  how do I get my right to write?

Using Ubuntu 8.04 AMD64.

---

### Post by cantormath on 2008-10-25
try:
sudo chown youruser -R /mountpoint

What fstab entry did you use?

---

### Post by MrZehl on 2008-10-25
chown didn't work.

I copied the line from my second working hd.
/dev/sdb1	/media/sdb      ext3   rw,user,relatime,errors=remount-ro 0       1

And my new tird hd becomes
/dev/sdc1	/media/sdc      ext3    rw,user,relatime,errors=remount-ro 0       1

I also tried:
/dev/sdc1	/media/sdc      ext3    defaults 0       1

---

### Post by MrZehl on 2008-10-25
Okay now it works. Restarting nautilus wsn't enough, so I restarted Ubuntu. And now I can write to the partition. Thanks.

---

