---
title: "All networking fails after hibernate"
date: 2008-05-11
forum: Hardware
---

### Post by rambomedic on 2008-05-11
Hibernate used to work flawlessly in Gutsy, all I had to do was disable wireless and networking before I hibernated and everything was great. However, since I've upgraded, whenever I hibernate and resume, my network manager is unable to connect to anything, wireless or hardwire. It detects networks just fine, but when it tries to connect, the first dot won't even turn green. 

I've tried using the console to restart networking with

```
sudo /etc/init.d/networking restart
```

but to no avail. I've tried using modprobe to remove my network module right before I hibernate and restart it once I resume, but I can't figure out which module to stop.

Thank you for your time and help.

---

### Post by Megalorian on 2008-05-23
I'm having a similar problem on my Dell Inpiron Laptop

---

