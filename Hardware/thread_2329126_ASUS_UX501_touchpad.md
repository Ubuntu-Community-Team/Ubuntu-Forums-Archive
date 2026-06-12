---
title: "ASUS UX501 touchpad"
date: 2016-06-28
forum: Hardware
---

### Post by g-rodola on 2016-06-28
Hello. On my brand new UX501 the touchpad works kind of ok (precision isn't great) but what does not work at all is the 2-fingers scrolling. I've been searching on Internet *a lot* but haven't find any solution so far.
Also when a left-click some text in order to copy it, then I release the leftclick, the pointer moves randomly, so that it's impossible to copy the right text.
In general, the touchpad is lamost inusable (on Windows it works perfectly).
This is supposed to be the touchpad model ("USBest Technology SiS HID Touch Controller"):


```
$ sudo libinput-list-devices  | grep -i touch -5
Device:           USBest Technology SiS HID Touch Controller
Kernel:           /dev/input/event10
Group:            5
Seat:             seat0, default
Size:             341.25x195.00mm
Capabilities:     touch
Tap-to-click:     n/a
Tap-and-drag:     n/a
Tap drag lock:    n/a
Left-handed:      n/a
Nat.scrolling:    n/a
Middle emulation: n/a
Calibration:      identity matrix
Scroll methods:   none
Click methods:    none
Disable-w-typing: n/a
Accel profiles:   n/a

```

Any advice? Is it just me?

---

### Post by Echylo on 2016-06-28
I have the same problem on my new archlinux install with gnome, but I think the device you listed is the touch screen, not the touchpad, grep by pointer.

---

### Post by eddiemonroe on 2016-10-15
Anyone find any solution to this? 

I have the same problem with this laptop with kernel 4.8.0. It appears the kernel is recognizing the device ("FTE1001:00 0B05:0101") as a mouse and not recognizing it as a touchpad. 

There is a bug regarding this filed here, but not sure if any action will be taken to resolve: [https://bugzilla.kernel.org/show_bug.cgi?id=120181](https://bugzilla.kernel.org/show_bug.cgi?id=120181)

Thanks!

---

### Post by qu1-g0n-j1nn on 2017-04-26
I have the same problem. I'm using ASUS X556UV with kernel 4.5.3. Could anybody help us?

---

### Post by mörgæs on 2017-04-28
If you read the link posted above (the bottom part of it) you will see that it's fixed in kernel 4.10. This indicates that 17.04 is the best version to try.

---

