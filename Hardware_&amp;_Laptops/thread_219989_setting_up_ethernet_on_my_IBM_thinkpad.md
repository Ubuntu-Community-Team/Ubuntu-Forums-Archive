---
title: "setting up ethernet on my IBM thinkpad"
date: 2006-07-20
forum: Hardware &amp; Laptops
---

### Post by josh_g on 2006-07-20
I installed Ubuntu on my IBM thinkpad notebook and all seems well except that the internet is not working. How do I set up the Network to use the ethernet cable so that the internet will work?

---

### Post by kingmonkey on 2006-07-20
System>Admin>Network

---

### Post by josh_g on 2006-07-20
Do I want eth1 or eth0 to be active? Then, what settings do I need to use to get this shit sorted out? Will someone just get on AIM and IM me at: "Josh Gummersall"?

---

### Post by kingmonkey on 2006-07-21
type ifconfig and post the out put here.

---

### Post by susa on 2006-07-21
on all of my thinkpads, eth0 is the cable LAN connection and eth1 is my wireless connection, so if you have cable to your router, make sure it's set to dynamic IP and DHCP is enabled, then play with the eth0 settings. you may want to disable it and then reenable it and reboot machine to check if it works (if it does not work immediately)

---

### Post by josh_g on 2006-07-21
its good now.

---

