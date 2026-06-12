---
title: "problem in detecting pen drive"
date: 2008-09-13
forum: Hardware
---

### Post by nuke_fluke on 2008-09-13
Transcend JF V30  2 GB is not being detected in my ubuntu 8.04...

---

### Post by cariboo on 2008-09-13
What is the out put of:

```
lsusb
```

with your usb device plugged in.

What is the output of:

```
dmesg
```

When you plug your device in?

JIm

---

### Post by IntuitiveNipple on 2008-09-13
> **cariboo907 said:**
> 
What is the output of:

```
dmesg
```

When you plug your device in?

JIm

There won't be any - dmesg is copy of the initial start-up sequence :)

The log I think you meant is **/var/log/kern.log**.

---

