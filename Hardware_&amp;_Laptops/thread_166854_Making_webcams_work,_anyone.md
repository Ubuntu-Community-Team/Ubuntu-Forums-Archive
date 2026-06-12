---
title: "Making webcams work, anyone?"
date: 2006-04-27
forum: Hardware &amp; Laptops
---

### Post by opera on 2006-04-27
I can see from device manager that dapper recognizes my webcam; however, neither EasyCam nor spca5xxx do the trick.  Anyone?

---

### Post by antivert on 2006-04-27
Find the chipset your webcam is using and see if any drivers support it! It should be in device manager, or you can tail -f /var/log/syslog and then plug the camera in and see what it says. It may be that your chipset isn't supported by any known driver.

---

