---
title: "Edgy on older laptops ext3 needs constant fsck"
date: 2007-01-04
forum: Hardware &amp; Laptops
---

### Post by mrguytx on 2007-01-04
Ever since I installed Edgy (from scratch) on my Dell laptop (latitude C800) I had constant fsck errors on boot, and a read only filesystem within minutes of booting.
After reading various posts I decided it was the ext3 filesystem that Edgy prefers to install.
If you are having this issue, and it's a PAIN IN THE *** issue which basically makes you reboot and fsck every 10 minutes, if you don't entirely lose your data, which happened to me twice, you can revert from the ext3 filesystem to ext2.

Just use this and it should fix it. My system has been perfect ever since, and faster as well.
I guess older hard drives in laptops don't handle journaling very well in the ext3 filesystem.

[http://www.redhat.com/docs/manuals/linux/RHL-7.3-Manual/ref-guide/s1-filesystem-ext2-revert.html](http://www.redhat.com/docs/manuals/linux/RHL-7.3-Manual/ref-guide/s1-filesystem-ext2-revert.html)

Good luck, and Ubuntu still rocks.

G

---

