---
title: "Laptop Screen"
date: 2009-01-12
forum: Hardware
---

### Post by kbines on 2009-01-12
Dumb newbie mistake - doh!

I have a Delld630 laptop and a docking station with 2 screens attached. All has been working fine for a few months  but for some reason this morning the external screens would not fire up (this happens every now and again).  So i went into the configure screen utility to turn the 2 screens on and the laptop screen off (which normally works). Now no screens work at all. Have tried rebooting in recovery mode and reconfiguring X server but still get no screen. Have disconnected laptop from docking station and rebooted but now screen appears. Not a hardware problem as I can boot into XP.

K

---

### Post by linux_tech on 2009-01-12
Hi, 
Welcome to the forums,
In Terminal- Applications > Accessories > Terminal-

Please post output of ```
xrandr
```  (this shows avail displays)
Also post:
```
ls /etc/X11 
``` (lists xorgs in /etc/X11)

```
cat /etc/X11/xorg.conf 
```  (shows contents of current xorg)

What dual display configuration are you using?

---

### Post by black3ug on 2009-01-12
potentially dumb suggestion: have you checked if you haven't turned off the external display via the "FN+XXX" key of your laptop? I did this once, hehehe. 

I also solved a problem my friend had which is similar to this. In his case, the "external display" was set to off in his BIOS. Worth a peek at least, eh?

---

