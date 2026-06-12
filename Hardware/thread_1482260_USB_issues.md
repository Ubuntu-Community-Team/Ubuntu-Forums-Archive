---
title: "USB issues"
date: 2010-05-13
forum: Hardware
---

### Post by Brothman on 2010-05-13
I'm totally new to Ubuntu and Linux, and am trying the new distro within Windows 7 to make sure I can do all my military stuff on it (forms, etc through military software).  It's installed on a HP/Compaq NX7400 with 1GB ram.

The issue is that once I finally got it updated and the wireless running right (took a proprietary driver), it ran fine for a day and then the USB ports stopped working altogether.

The only thing out of the ordinary that I can remember before the USB port shutdown is that Rythmbox wouldn't let me safely eject my iPod before I shut down Ubuntu.  I had to shut down Ubuntu with the iPod still plugged in.

When I get my dedicated hard drive in for Ubuntu, I'll see if it's an issue.  However, no USB ports being active kind of hampers my experimentation.  I love the OS so far and until last night, it was doing absolutely everything I needed it to  If anyone more experienced than me has any ideas...

---

### Post by khelben1979 on 2010-05-13
Try to attach something to your usb ports and do
```
lsusb
```

If the output gives you the attached devices, your usb ports are still working.

---

