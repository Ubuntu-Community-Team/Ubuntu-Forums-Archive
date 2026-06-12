---
title: "DIsk utility - Forgot to install MBR"
date: 2011-10-23
forum: Hardware
---

### Post by s-lime on 2011-10-23
[http://www.shrani.si/f/3C/2f/47rm35P8/screenshot-1.png](http://www.shrani.si/f/3C/2f/47rm35P8/screenshot-1.png)

Take a look at the picture. Apparently I have working Disk without MBR. Everything is working fine, so what is wrong? I am worried that if I boot in windows anytime, windows will asume disk is empty and use it as swap. And in case of anything goes wrong.

So, how can I post-install MBR without having to copy everything again. This is usb disk and with 30MBps it would take a lot?

---

### Post by ajgreeny on 2011-10-23
What is the output of ```
sudo fdisk -l
```

---

### Post by s-lime on 2011-10-23
It says there are no partitions, neither on encrypted block, neither on raw block.

However, as apparent from the picture, disk utility detects one...

---

