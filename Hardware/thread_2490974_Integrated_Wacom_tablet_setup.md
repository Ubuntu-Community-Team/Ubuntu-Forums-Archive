---
title: "Integrated Wacom tablet setup"
date: 2023-09-21
forum: Hardware
---

### Post by vt-all on 2023-09-21
Hello all,

I am typing this on my Fujitsu Lifebook t5010, a 2008 laptop-tablet that has a Wacom digitiser and stylus built in. 
Ubuntu (22.04 LTS) does not even see the device, as 
setwacom --list devices does not return anything and lsusb does not show any wacom devices.

Any help would be much appriciated!

---

### Post by guiverc on 2023-09-21
Do you need it to be recognized?

I have a 2009 motion computing laptop/tablet with wacom & stylus/pen, and I can't recall what is recognized, but it's just worked. I can move the mouse by waving the wand/stylus/pen above where I want it to move, using the pen's button(s) to click etc. The *pen* being read as a type of *mouse* device as far as I recall.

You weren't specific as to your 22.04 details; I'd try the older kernel stack option (*booting original 22.04 or 22.04.1 media will allow you to test that without change*;* ie. 5.15 kernel*), with 22.04.2 media containing the 5.19 kernel, and 22.04.3 using the 6.2 kernel. On older devices, I often have better luck with older stacks, but I can't recall my testing with the newer stacks on my 2009 device (*it has 5.15 kernel or the oldest installed I believe*).

I assume you installed Ubuntu 22.04 LTS Desktop, which defaults to the HWE kernel stack. Which media did you install with (22.04? 22.04.1? 22..04.2? or 22.04.3?) and did the mouse respond to stylus/pen before you actually installed; ie. the *kernel* on your *unstated* 22.04 media?

---

### Post by vt-all on 2023-09-21
Thank you for your quick reply!

The pen is not recognised as any device, and attempting to use it yields no result. It worked when i was using Vista on this device.

As for my Ubuntu installation, I am indeed running 22.04.3 LTS and installed with the same. It did not work before I actually installed it.

Again, thank you for your reply!

---

