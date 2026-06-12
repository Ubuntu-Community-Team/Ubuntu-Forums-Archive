---
title: "SCIM segfault"
date: 2008-10-02
forum: General Help
---

### Post by HyperHacker on 2008-10-02
SCIM seems to have stopped working. I get messages in /var/log/syslog when it starts: ```
Sep 28 21:50:58 mercury kernel: [1475422.018169] scim-launcher[3692]: segfault at b7b7ce6c eip b7b7ce6c esp bfd8115c error 4
```Trying to launch it from a terminal:
```
hyperhacker@mercury:~$ scim
Smart Common Input Method 1.4.7

Launching a SCIM process with x11...
Loading socket Config module ...
Creating backend ...
Loading x11 FrontEnd module ...
SCIM has exited abnormally.
```
scim-setup works, and it was working a while ago. I'm not sure what I did to break it, just noticed one day the little floating toolbar was gone.

---

