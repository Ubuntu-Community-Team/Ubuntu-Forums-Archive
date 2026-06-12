---
title: "access to the internet"
date: 2009-09-30
forum: Installation &amp; Upgrades
---

### Post by oskarpetersen on 2009-09-30
On my desktop I run Ubuntu 9.04 and Windows XP. Everything is fine except for one thing: Ubuntu has no access via Firefox to the Internet. Firefox is said to be offline.

On my laptop I run Ubunto 9.04 without any problems at all, and access to the Internet is OK. I have made the same settings on my desktop as I have on the laptop, but it does not work. Please give me some good advice.

oskarpetersen

---

### Post by wojox on 2009-09-30
Do you have access at all? Open a terminal:

```
ping -c 5 www.google.com
```

Post the output. Have you checked File > Work Offline isn't checked.

---

### Post by rreese6 on 2009-09-30
We need more information.
Post the output of these commands:
```
sudo lspci -vvv |grep Ethernet -A15
ifconfig -a
```

---

### Post by Lars Noodén on 2009-10-01
Verify that the box File->WorkOffline is not checked.  If it is checked, then FF will run in the offline mode regardless of whether you are connected to the net or not.

---

