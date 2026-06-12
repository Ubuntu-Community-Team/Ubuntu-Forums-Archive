---
title: "Found the problem: laptop brightness fail"
date: 2011-10-31
forum: Hardware
---

### Post by biji on 2011-10-31
Hi,
after a little console hacking, i found the cause of my laptop (old lenovo laptop) brightness problem. There are two backlight interface control in /sys:


ls /sys/class/backlight/
ideapad  
intel_backlight


have tried to echo 7 > brightness, the one works is ideapad. but intel_backlight only give max_brightness to 1. And... the system use it as backlight control. Is there any to disable intel_backlight, or maybe force using ideapad??

Thanks

---

### Post by biji on 2011-11-15
Hmmm no body has this problem too?
Do you know how to disable intel_backlight from loading?

thx

---

### Post by awolff on 2011-12-05
The kernel from following PPA solved the problem on my lenovo S10e and 11.10:
[https://launchpad.net/~kamalmostafa/+archive/stuck-backlight](https://launchpad.net/~kamalmostafa/+archive/stuck-backlight)

I still have the kernel parameter acpi_backlight=vendor

---

