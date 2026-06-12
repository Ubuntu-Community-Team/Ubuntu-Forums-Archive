---
title: "[SOLVED] Battery charging problems in HP dv 6515"
date: 2008-06-01
forum: Hardware
---

### Post by harsh1kumar on 2008-06-01
I have a HP dv 6515 laptop with Ubuntu 8.04 on it. I have noted that the battery is at 94% charged when I boot into Ubuntu. It recharges then. I don't power off the laptop before it completely shuts down.
Is it a bug?? Is it bad for the battery life?? What can I do about it??

Thanks in advance.

---

### Post by bdoe on 2008-06-04
It's normal. Batteries don't hold a full charge forever, and the charging circuit may not kick in immediately when the battery discharges slightly. I don't know exactly what the threshold is for a Li-ion charging circuit to kick in and top off the battery, but - when you shut down and later power up again, it may kickstart the charging circuit to top off the battery charge.

On the other hand, if you know that the battery is fully charged (100%) when you shut down, but notice it is significantly lower when you power back up after a few hours or a day or two, then it's likely that your battery has aged and cannot hold a full charge anymore.  How old is your laptop?

---

### Post by harsh1kumar on 2008-07-18
Sorry for replying after so long time but I found out the thing that you told me in your post from a friend. 
Thanks for the post

---

### Post by msun on 2008-07-21
Another possibility - for example for a Thinkpad laptop I use a utility called "Battery Maximiser" which allows you to set thresholds for charging. This utility works under Windows and so far I have found no equivalent for Ubuntu.

However, if different thresholds are set under windows, I notice these settings are preserved when switching to Ubuntu on a dual-boot setup. So I am guessing that such settings are independent of OS and it would be nice to have some utility to view/change these under Ubuntu.  :)

---

