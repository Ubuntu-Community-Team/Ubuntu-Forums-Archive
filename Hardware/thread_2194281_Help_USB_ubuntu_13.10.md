---
title: "Help USB ubuntu 13.10"
date: 2013-12-17
forum: Hardware
---

### Post by miguel-filipe-j on 2013-12-17
Hey :)

I have a problem when I install ubuntu on my laptop from an usb stick.

My laptop have 2 usb ports(one 2.0 and one 3.0).When i install ubuntu from the 2.0 port the other port don`t work and [COLOR=#444444][FONT=arial]the other way around.[/FONT][/COLOR]

---

### Post by varunendra on 2013-12-20
Welcome to the forums miguel-filipe-j !

If you use Ubuntu in live mode, does the other USB port work in the live session?

Linux kernel has good support for both USB2 and USB3, and there should be no problem in handling either ports. When being in Live session ("Try", not "Install"), please open a terminal (Ctrl-Alt-T) and post back the output of -
```
lsusb
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

