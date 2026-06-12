---
title: "GRUB and GRUB2 co-existence"
date: 2009-10-04
forum: Installation &amp; Upgrades
---

### Post by uaaquarius on 2009-10-04
Hi there,

I've installed Karmic beta (on sda3) along with my Jaunty (on sda1). The problem had arisen - Karmic's GRUB2 failed to detect my Jaunty. So, I could not boot my Jaunty. To fix this I changed MBR to previous state:
booted via liveCD, then
```
grub
root (hd0,1)
setup (hd0)
quit
```rebooted.

Now I'm able to boot Jaunty. But can't boot Karmic beta. I'd like to be able to boot both Jaunty and Karmic beta somehow.
How can I achieve this?
I've played a bit with chainloader in Jaunty's GRUB, but failed. GRUB is not passing controll to (Karmic's) GRUB2. Any idea how can I do this? :confused:
Another solution (less preferable) could be to change MBR to boot from sda3. I searched on [GRUB2 documentation]("http://grub.enbug.org/CommandList") but *root* command is replaced and *setup* is "unnecessary " :confused: I believe there is a simple way to achieve this, but I can't find it.

Any ideas how to:
1) make GRUB to call GRUB2 via chainloader
or
2) update MBR to boot from sda3?

Thanks

---

### Post by uaaquarius on 2009-12-01
I've finally solved the problem after reading this thread:
[http://ubuntuforums.org/showthread.php?t=1198145](http://ubuntuforums.org/showthread.php?t=1198145)
:D

---

### Post by u.b.u.n.t.u on 2009-12-01
Thank you for your follow up post, it was considerate of you and will help others.

---

