---
title: "jbd2 writing to HD every 2 or 3 seconds"
date: 2011-10-17
forum: Hardware
---

### Post by Mosabama on 2011-10-17
Hi,
I have made a fresh install of 11.10. although this problem existed in older versions of ubuntu.

first of all the Harddisk over heats, it reaches 42 C. no clicking sounds or anything .. only heat.

I checked IO using iotop. and found out that jbd2 is writing to disk every couple of seconds .. 3 or 4 seconds average. and I guess this is the problem.

I tried to add a commit=60 to fstab. but nothing happened I dont know why!.
I tried even to echo 1 to block_dump file .. still nothing.
I triedto edit the dirty file in vm.. still no effect at all.

and I am sure that these options take effect cause when I issue a mount command it appears "commit=60" !!

I cant stop ubuntu from writing on the HD every couple of seconds.

any one has a solution that makes ubuntu writes to hd every 2 minutes for example? 

Thank you.

---

### Post by Mosabama on 2011-10-18
up :mrgreen:

---

### Post by shimoda on 2011-11-27
I've a similar problem....

Do you found a solution?

---

### Post by yankee83 on 2011-12-16
Same problem here. Any solution available?

---

### Post by yannoo on 2012-01-07
This is bound to the (very long) bug report here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/607560](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/607560)

No solution has been provided yet.

---

