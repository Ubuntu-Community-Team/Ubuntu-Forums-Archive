---
title: "Laptop backlight turns off when on battery"
date: 2007-12-03
forum: Hardware &amp; Laptops
---

### Post by archivalbackup on 2007-12-03
I an issue on a Gateway Tablet TA6 after upgrading to 7.10 from Feisty.

When switching from AC to Battery, the LCD back light turns off. Completely. If I get a bright light I can still see the data on the screen, just no back light which makes it nearly impossible to read. 

 I found that I could restore the back light for a few seconds by using the built in brightness controls (Fn+F1, FN up/down). The back light goes off after a few seconds again and basically make my computer unusable on batter power.

I don't get any entries in dmesg when I switch from AC to battery.

I also changed my power management to do nothing when on battery, lid closed, inactive etc. I put Dim Brightness at 100% and dim when inactive unchecked.

Help?!

---

### Post by madamore on 2007-12-03
this thread might be the same problem:
[http://ubuntuforums.org/showthread.php?t=580535](http://ubuntuforums.org/showthread.php?t=580535)

---

### Post by archivalbackup on 2007-12-04
> **madamore said:**
> this thread might be the same problem:
[http://ubuntuforums.org/showthread.php?t=580535](http://ubuntuforums.org/showthread.php?t=580535)

Well at least it is not just me. That makes sense. 

I'll wait for a bugfix/update, since I found that if I tap the contrast key (fn+f8) the screen turns back on, and as long as I disable all of the power management features it will stay on until I plug-in / unplug again.

---

