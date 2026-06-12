---
title: "hdd location changing"
date: 2010-11-18
forum: Hardware
---

### Post by underworld288 on 2010-11-18
I am having a very strange problem. My HDD locations ( as in /dev/sdd1 ) are changing every time I boot. I have my /etc/fstab file setup to auto mount every partition where it needs to be but it isn't working because of this problem and it is getting annoying. I appreciate anyones help. 

thanks

---

### Post by efflandt on 2010-11-19
That is why you are supposed to use UUID's instead of /dev/sdd1, etc. in /etc/fstab.

You can find out the UUID of your partitions from **sudo blkid** run in a terminal.

---

### Post by underworld288 on 2010-11-19
Thanks for that information. You saved me a lot of headache.

---

