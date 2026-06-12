---
title: "Laptop tries to suspend when running on battery but fails -- returns strange error"
date: 2006-07-27
forum: Hardware &amp; Laptops
---

### Post by tirian on 2006-07-27
Hello,

   When I try to suspend my Thinkpad R51, it goes down for a suspend it goes all the way down ( the system switches to the virtual terminal that displays the system messages and then turns off ). However, then I hear a 'popping' from the speakers as the system powers back up instead of suspending fully.

   As the system is coming out of the quazi-suspended state, I can catch a few of the system messages displayed on the virtual terminal before X11 comes out of suspend. One of these messages is: "some devices failed to suspend: error -194". However, I've searched though my logs (messages, syslog, dmesg, etc.) but I can't find this message anywhere.

   The strangest part is that it only fails to suspend when my laptop is unplugged and running off of battery. If I plug it and and try to suspend, it works like a charm.

I've run my updates, and it hasn't helped yet.

Any ideas?

Thanks!

~Peter

---

### Post by nick122147 on 2006-10-27
Did you find a solution to this? I have the same problem in edgy.

---

### Post by tirian on 2006-10-28
Sorry, I still have this problem.

I was hoping that it would be fixed in Edgy :(

You might want to file a bug.

---

