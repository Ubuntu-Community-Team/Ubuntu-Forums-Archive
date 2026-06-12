---
title: "Mouse scroll wheel problem"
date: 2011-09-30
forum: Hardware
---

### Post by SkyeFerret on 2011-09-30
I'm dual-booting Windows 7 and Ubuntu 11.04 on my desktop.

Under Win7, the mouse scroll wheel works just fine. Scrolls smoothly and reliably.

Under Ubuntu, weird stuff happens.
Half the time, it scrolls really, really slowly. Other times, it launches me halfway down the page in a single wheel movement. It does this pretty much at random (it'll switch between super slow and insane fast rather than one or the other per program).

I think it might be the drivers, but of course... Microsoft's drivers are Windows / Mac only. :|

Microsoft Wireless Mobile Mouse 3500.

Thanks!

edit: Putting this under hardware since it's a mouse problem; feel free to move it to the desktop forum if that's more appropriate.

---

### Post by rmf730 on 2011-11-11
I have the same probleme with the same mouse, and i found a forum where they seems to solve the probleme but i dont speak enough english to understand it... [https://answers.launchpad.net/ubuntu/+question/9200](https://answers.launchpad.net/ubuntu/+question/9200)

---

### Post by northd_tech on 2011-11-11
I'm assuming this wireless mouse uses a USB antenna & interface.  Can you post the output of the following terminal commands here using copy/paste:

```
lsusb
cat /etc/X11/xorg.conf 
```

Edit:  manufacturer link:

[http://www.microsoft.com/hardware/en-us/p/wireless-mobile-mouse-3500#details](http://www.microsoft.com/hardware/en-us/p/wireless-mobile-mouse-3500#details)

---

