---
title: "only root can print"
date: 2008-01-01
forum: Hardware &amp; Laptops
---

### Post by lowebb on 2008-01-01
Hi, for some reason my printer will only print through suer root. When I load up the computer the printer is mounted to "/dev/usb/lp0". An ls -l returns

crw-rw---- 1 root lp 180, 0 2008-01-01 16:57 lp0

As you can see its only root that is allowed to access this. The question is why? And secondly how do ~I change this permanently. As a work around I am currently manualyl running 'chmod' to get it working. Any help is very much appreciated

---

