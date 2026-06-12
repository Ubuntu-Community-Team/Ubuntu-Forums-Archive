---
title: "Problems with USB 2.0 peripherals"
date: 2007-03-24
forum: Hardware &amp; Laptops
---

### Post by 'ntoni on 2007-03-24
Hi all, I recently bought a SITECOM usb HUB. It's external, it has an external power supply and it features 4 usb 2.0/1.1 ports. It works well, with USB 1.1 peripherals. The problem is, that when I connect my mp3 player (which is designed to work on linux) it has lots of problems. It works, I can see the mp3s and the files, but as soon as I try to copy anything, it fails. BTW if I connect my mp3 player to a normal USB port, it works perfectly.
Any suggestion? What shall I try to do? Might I force ubuntu to recognize it as an usb 1.1 device?
Thanks in advance,
'ntoni:KS

---

### Post by 'ntoni on 2007-03-31
Eventually I found out a working (raw) solution myself.
If you want to have all your peripherals to work in usb 1.1 mode instead of 2.0 one, you could simply unload the kernel module which provides support for usb 2.0.
Try
```

sudo su
# type in your password and then type
rmmod ehci-hcd
```
It's not the best solution at all, but it works.
Hope this will be useful.
P.S. The player is an Actions Semiconductors one, called "like ipod", made in China by "Wilson LTD"

---

