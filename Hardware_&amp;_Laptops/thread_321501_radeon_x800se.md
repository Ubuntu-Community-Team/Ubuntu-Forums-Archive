---
title: "radeon x800se"
date: 2006-12-19
forum: Hardware &amp; Laptops
---

### Post by Robx610 on 2006-12-19
So here goes. I'm in college for networking and network security and fairly new to Linux. A bunch of my buddies recommended I install Ubuntu. After numerous fails, I realized that Ubuntu didn't like my Radeon x800se 256 meg video card. As soon as I plugged in a gforce 2, It worked, installed and ran fine. What happened when I tried to use the Radeon is this: after the progress bar on the install screen, my screen would go black while leaving the monitor power button green (and no drive activity); when I installed using the gforce 2 and restarted using the Radeon, I got loads of vertical lines that look like video corruption and it just stopped. This is not a problem when I use widows XP so I don't think my card has gone bad. Essentially I'm asking if anyone has had this problem and/or found a way of resolving it. I would much appreciate any help. It was an expensive card, I don't want to let it go to waste.


~Rob

---

### Post by whoismilan on 2006-12-19
Seems I am not the only one, then :) (I don't have the X800SE, but the X800GT).

I don't know why this is (as in: haven't bothered to find out), but the open-source radeon drivers Ubuntu ships with doesn't work for me... at all. The weird part is that the radeon drivers do work in e.g. openSUSE and Fedora...

I installed Ubuntu by choosing "safe graphics mode" when booting the CD. This should make you be able to boot and get into X, then you can install the fglrx drivers (official Ati drivers), e.g. by following one of the ways posted in this thread: [http://www.ubuntuforums.org/showthread.php?t=221320](http://www.ubuntuforums.org/showthread.php?t=221320)

If you already have Ubuntu installed, edit xorg.conf (sudo nano /etc/X11/xorg.conf) and make it use the "vesa" drivers instead of radeon... that is, in:
```
Section "Device"
```
...make sure that: 
```
        Driver      "vesa"
```
...and not "radeon".

---

### Post by Robx610 on 2006-12-19
thanks. I'll try it out and see if it works tonight.

---

