---
title: "855resolution problem"
date: 2005-12-05
forum: Hardware &amp; Laptops
---

### Post by quietglow on 2005-12-05
I'm getting closer to getting my laptop's screen at native 1280x800 res.

I've installed 855resolution. I've changed the proper lines in /etc/default/855resolution. I've made sure that 1280x800 (and only 1280x800!) are in my xorg.conf.

Now I can switch to 1280x800 in System>Pref>ScreenResolution, but when I do, I get a virtual desktop. That is, my the desktop is larger than my screen--I get to the hidden parts by pushing the mouse to the side of the screen which causes the screen to scoll.

Obviously, I don't want that virtual screen setup. Anyone have any ideas?

---

### Post by quietglow on 2005-12-05
I've been working on this now for the last 22 hours or so straight with a couple of hours of sleep thrown in there. I've tried everything I have found which others have done to get the 915gm card working and nothing is helping. I think the trick is getting the 1280x800 to be an option--I haven't found ANY mention of the virtual desktop problem I'm having once 1280x800 is enabled.

I'd take even shots in the dark at this point. I'm starting to wonder if I should think about bringing this thing back and suffering the restock fee.

---

### Post by quietglow on 2005-12-05
In the interest of answering my own questions :-):

When I start X with the wierd 1280x800 virtual desktop, my Xorg log shows this error:

```
(II) I810(0): Generic Monitor: Using hsync range of 48.00-50.00 kHz
(II) I810(0): Generic Monitor: Using vrefresh range of 59.00-61.00 Hz
(1280x800,Generic Monitor) mode clock 83.46MHz exceeds DDC maximum 80MHz
(--) I810(0): Virtual size is 1280x800 (pitch 2048)
```

That looks significant to me...anyone? (I'm chanting "there's no whine in Linux" right now!)

---

