---
title: "nVidia 7300GT as &quot;unknown device&quot;, proprietary drivers don't help"
date: 2011-11-20
forum: Hardware
---

### Post by zenchicken on 2011-11-20
Hi all.

I've just installed Ubuntu 11.10 on my main desktop. Last version I had used was 9-something, things sure do look different!

I'm using a PCI Express nVidia 7300 GT graphics card. After installation I noticed in "System Info" graphics were listed as "unknown device", so I installed recommended proprietary graphics and rebooted waiting for things to change, but to no avail. It still comes up as "unknown device", but the "additional drivers" windows says the driver is running.

lspci | grep VGA in terminal shows the following:

```
01:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce 7300 GT] (rev a1)
```so no surprises there.

I'm not very Linux-savvy and never had to fiddle around with graphics drivers before... does anyone have any idea how to fix this?

Thanks in advance.

---

