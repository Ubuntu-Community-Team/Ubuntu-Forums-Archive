---
title: "Touchpad doesn't work after Suspend"
date: 2006-07-11
forum: Hardware &amp; Laptops
---

### Post by sprocket87 on 2006-07-11
I have my system set to suspend when I close my laptop's lid. When I open the lid and the system comes back, the touchpad refuses to work. I can log in and function using the keyboard but the touchpad doesn't work whatsoever. So far I've just been plugging in a USB mouse when this happens but I need to find a solution if possible.

Is there a fix for this? If there's not a permanent fix, what about a way to reinitialize the touchpad manually from the console or something?

Specs:

Ubuntu 6.06 "Dapper Drake"
Gateway M460XL laptop
15.4" WXGA+ widescreen display
Intel Pentium M 2.0 GHz w/Centrino
2GB RAM

Thanks!

Jesse

---

### Post by sprocket87 on 2006-07-11
Anyone?

---

### Post by joske on 2006-07-12
I have the same problem on a dell latitude D820. The basic functionality works, but not the edge scrolling, and tapping the corners. I haven't found a solution yet :(

Though, I have found that logout/login makes the touchpad work again.

---

### Post by sprocket87 on 2006-07-12
> **joske said:**
> I have the same problem on a dell latitude D820. The basic functionality works, but not the edge scrolling, and tapping the corners. I haven't found a solution yet :(

Though, I have found that logout/login makes the touchpad work again.

Interesting, thanks for the comment. If no one knows the fix, I'd be satisfied with a workaround. This is linux, there *has* to be a way to manually initialize the touchpad from the console... right?

---

### Post by joske on 2006-07-12
I have just read somewhere else that not using the touchpad for 10 seconds or so after resume makes it work, but I haven't tried. Also specifying explicitely in xorg.conf to load the synaptics driver is also reported to work, haven't tried yet (at work).

---

### Post by joske on 2006-07-12
I just tried both methods, they don't work :(

---

### Post by sprocket87 on 2006-07-12
> **joske said:**
> I just tried both methods, they don't work :(

I see, thanks for the effort and the follow up. I'll try to do some digging on my own as well, although I'm pretty new. I'm wondering if I/we might have more success asking over at linuxquestions.org (I'll have to dust off my account ;))

---

### Post by sprocket87 on 2006-07-13
> **joske said:**
> I have just read somewhere else that not using the touchpad for 10 seconds or so after resume makes it work, but I haven't tried. Also specifying explicitely in xorg.conf to load the synaptics driver is also reported to work, haven't tried yet (at work).

I tried adding the synaptics driver line to xorg.conf as well, and then doing a "sudo synclient Touchpadoff=0/1" as well, but with no result.

Hmmm....

---

### Post by christian.convey on 2006-07-13
> I have the same problem on a dell latitude D820. The basic functionality works, but not the edge scrolling, and tapping the corners.
Same issue for me.  I have an HP dv4150 (from the dv4000 product line).

---

### Post by jslaker on 2006-09-13
I'm having the same issue with a Gateway MX6625.

I've filed a bug report here: [https://launchpad.net/distros/ubuntu/+source/xserver-xorg-input-synaptics/+bug/59867]("https://launchpad.net/distros/ubuntu/+source/xserver-xorg-input-synaptics/+bug/59867")

Short version is that it looks like (to my untrained eye) that the kernel isn't reinitializing the touchpad after the resume. That said, somebody has incorrectly IMO filed this as an X.org bug. Anyone know how I could go about getting that changed?

---

### Post by Beesquito on 2007-11-24
Having the same problem in Xubuntu 7.10 on a Gateway MX6027.  It seems to also break my wireless connection (using the drivers from the Restricted Drivers Manager.)  As a side note, I can only get it to suspend with Fn+F3 (my suspend key).  Even with gnome-power-manager installed, it will not suspend when I close the lid.  Anyone know how to fix any of these??

---

