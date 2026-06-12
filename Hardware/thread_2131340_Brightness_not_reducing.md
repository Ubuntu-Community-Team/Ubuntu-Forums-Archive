---
title: "Brightness not reducing"
date: 2013-04-01
forum: Hardware
---

### Post by kikloo on 2013-04-01
Hi,

I am trying to reduce the brightness but its not. How to do ?

Thanks.

---

### Post by gordintoronto on 2013-04-01
You might provide a few hints so people can help you. For example:
 - I am using Ubuntu 12.04 64-bit
 - my computer is an XXX model YYY
 - the video card is an WWT model 1234
 - I did install the additional drivers from the software center
 - the monitor is a TYUI model 9876
 - I use such and such method to reduce the brightness.

---

### Post by kikloo on 2013-04-02
> **gordintoronto said:**
> You might provide a few hints so people can help you. For example:
 - I am using Ubuntu 12.04 64-bit
 - my computer is an XXX model YYY
 - the video card is an WWT model 1234
 - I did install the additional drivers from the software center
 - the monitor is a TYUI model 9876
 - I use such and such method to reduce the brightness.

Hi,

The info you asked is following:

Ubuntu 12.10 32-bit
Laptop is Acer Aspire 5738
Video Card is: Intel GMA 4500MHD
I don't know what additional drivers i have to install and how.
There's no monitor, i am on laptop.
I used Ubuntu Settings and both the combination keys on my laptop keyboard.

Thanks.

---

### Post by Isamu715 on 2013-04-02
Try adding *acpi_osi=Linux* and *acpi_backlight=vendor* to GRUB_CMDLINE_LINUX in */etc/default/grub*. Modify it so it looks like that:
```
...
GRUB_CMDLINE_LINUX="acpi_osi=Linux acpi_backlight=vendor"
...
```
Run:
```
sudo update-grub
```
Reboot and try changing brightness.

---

