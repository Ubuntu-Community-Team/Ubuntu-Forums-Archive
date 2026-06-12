---
title: "Dual booting Ubuntu and Windows 7 with two drives if /dev/sda is the Ubuntu disk"
date: 2014-07-20
forum: Hardware
---

### Post by jazzbeenjamin on 2014-07-20
I have a PC on which I installed Ubuntu and I have been using for some time. Recently I was given another PC, but the hardware components weren't as good. So I decided to put the hard drive of the latter PC into my first one, and I installed Windows 7 on it. So now, if I want to use Windows, I have to boot up the PC, press f12 at the right time, select the disk on which Windows 7 is installed, and let it continue. Someone told me recently that there's a way to set it up so that it asks you which drive you want to boot from automatically without you having to press f12. How do I do this?

---

### Post by weatherman2 on 2014-07-20
1. In your BIOS settings, choose the Ubuntu drive as your initial boot drive.
2. Boot the computer; it should now boot Ubuntu by default (without a menu - yet).
3. Open a terminal window (Ctrl - Alt - t)
4. In the terminal window type

```
sudo update-grub
```

(when asked, entered your admin password)

This should create a Grub boot menu that you see when start up the computer, with Ubuntu as the default choose, but you can choose Windows 7 using the down arrow and pressing Enter.

---

