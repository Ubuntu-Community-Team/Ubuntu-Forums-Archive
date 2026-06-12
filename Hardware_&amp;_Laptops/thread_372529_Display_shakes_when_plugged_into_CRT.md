---
title: "Display shakes when plugged into CRT"
date: 2007-02-28
forum: Hardware &amp; Laptops
---

### Post by Pathian on 2007-02-28
Hello all, I was wondering if you could help me with this problem thats preventing me from using my laptop at my desk workstation.

I installed Breezy Badger a while back before I had a larger monitor to use with it when at my desk, so it's configured to just use the default LCD. My new monitor is a Sony GDM-FW900 CRT (yeah, a behemoth). My problem is that when I plug the VGA into my laptop and toggle display to the CRT, the image of my desktop that comes up seems to buzz or vibrate very quickly from side to side. I tried going into the display options to change what I could, but my only option was the refresh rate which was locked into 60. It's been quite a while since I've tried to edit a xorg.conf file manually, so I figured I'd ask before I did anything silly.

Thanks in advance,
Justin

---

### Post by taurus on 2007-02-28
Yeah, you probably need to add the vertical and horizontal refreshing rates for your Sony CRT monitor in /etc/X11/xorg.conf.

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by Pathian on 2007-03-01
Thanks for the help! Any idea what the code would look like though? I'm not that familiar with adding devices.

---

