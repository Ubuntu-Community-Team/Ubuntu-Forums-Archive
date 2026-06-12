---
title: "Chromium not opening from lubuntu 16.04 with raspberry pi 3 model B"
date: 2016-11-29
forum: Hardware
---

### Post by matteoraggi on 2016-11-29
I have installed lubuntu 16.04 on raspberry pi 3 model B and then I have installed chromium 53 trough LUBUNTU SOFTWARE CENTER, but then chromium is completely not opening. sometimes I see a crash popup asking me if I wand to send the crash report, it happened only when firefox was already opened.

---

### Post by TheFu on 2016-11-29
Try running it from a bash shell. Any output in the terminal that might help?

---

### Post by matteoraggi on 2016-11-29
I write: 
```
chromium-browser
```
and it answer:
Segmentation fault (core dumped)
[4numbers:4numbers:4numbers/6numbers:ERROR:sandbox_linux.cc[(343)] InitializeSandbox() called with multiple threads in process gpu-process.

---

### Post by TheFu on 2016-11-29
Looks like a known bug: [https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1563184](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1563184)

---

### Post by matteoraggi on 2016-11-29
thanks! I will update it if I will find similar chromium bugs with raspberry pi 3 model b and other distros :-)

---

