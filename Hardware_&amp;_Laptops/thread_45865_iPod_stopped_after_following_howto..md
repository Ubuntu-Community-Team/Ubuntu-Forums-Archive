---
title: "iPod stopped after following howto."
date: 2005-07-02
forum: Hardware &amp; Laptops
---

### Post by recover82 on 2005-07-02
I followed the steps in the HowTO guide found [here](http://ubuntuforums.org/showthread.php?t=36632) and my iPod was working....but it seems after the dosfsck command when I plug in my iPod it just starts taking charge from the firewire port.

Any ideas?

---

### Post by recover82 on 2005-07-02
well..with a  little tinkering i figured out my problem.  i don't know why it was a problem to start with after a restart...but it still persisted.
i did an rmmod for ieee1394, raw1394, and sbp2
edited my /etc/fstab file to include the /dev/sda and linked to /mnt/ipod and restarted.  

the iPod connected and all was running nicely.  
no offense to this forum, but it seems like no one is ever very willing to help around here.  kinda sucks.

---

