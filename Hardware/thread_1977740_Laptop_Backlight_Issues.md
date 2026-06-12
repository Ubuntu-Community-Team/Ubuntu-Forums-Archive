---
title: "Laptop Backlight Issues"
date: 2012-05-10
forum: Hardware
---

### Post by Aaron42 on 2012-05-10
Hello, I've dual booted Ubuntu on my laptop starting with Maverick.  Since Natty came out, I've had the backlight problem solved with 
```
sudo setpci -s 02:00.0 F4.B=00
```and then putting the line (minus 'sudo') into /etc/rc.local.  Now, having done a fresh install from CD image of UbuntuStudio 12.04, this code works from a terminal, but not in /etc/rc.local.

Thanks so much for help on this as well as the answers I've found in the past.

---

### Post by Aaron42 on 2012-05-10
I have no idea how or why, just ran Update Manager, rebooted and it works now !?! Must have been a fix in there somewhere.:)

---

