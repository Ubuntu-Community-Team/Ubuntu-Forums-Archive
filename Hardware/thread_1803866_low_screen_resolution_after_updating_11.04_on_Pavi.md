---
title: "low screen resolution after updating 11.04 on Pavilion dv6"
date: 2011-07-14
forum: Hardware
---

### Post by Billsmithaustin on 2011-07-14
I have a Pavilion dv6 laptop with a 1920x1080 display, running Ubuntu 11.04.  This evening, after installing the latest updates, I can't set the screen resolution  higher than 1280x1024.  How do I troubleshoot this?

Thanks,
Bill Smith

---

### Post by Billsmithaustin on 2011-07-14
I figured out the problem.  While trying to fix an unrelated problem, I made some changes outlined in comment 27 of [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/699802](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/699802).  Backing out those changes fixed  my screen resolution.

---

