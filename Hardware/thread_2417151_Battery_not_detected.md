---
title: "Battery not detected"
date: 2019-04-21
forum: Hardware
---

### Post by flyingpc on 2019-04-21
Hello,


 I have a laptop computer and I installed an ubuntu 19.04 on it. The  problem is that my battery is not detected by the kernel (I guess).


 I also know that this battery works with Linux since by booting on a  Fedora 29 live usb, the battery is correctly displayed under gnome.


 With ubuntu, there is nothing under /sys/class/power_supply/BAT* while with Fedora there is.


 I tried to compare what dmesg, lspci, lsusb, lsmod gives in both cases and I admit I found nothing.


 The kernel of ubuntu 19.04 is more recent than that of Fedora 29 so it should also work with ubuntu.


 Anyway, I'd like to know if anyone has any idea what I could look at to make my battery work too with ubuntu.


 Note: the battery was not detected either with ubuntu 18.04.


 Thank you in advance for your help.


 FlyingPC.

---

### Post by flyingpc on 2019-04-22
Maybe a bug since battery is working with fedora, isn't it ?

---

