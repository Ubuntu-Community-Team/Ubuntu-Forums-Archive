---
title: "Multiple keys map to L Shift on keyboard"
date: 2014-10-27
forum: Hardware
---

### Post by lloyd-connellan on 2014-10-27
So I recently got a new keyboard (it is a Reddragon Centophorus) and a problem I've immediately had with it is that the Left and Right Ctrl, Alt, Shift and the Super key all have the effect of the L Shift. This is most easily confirmed by looking at the Keyboard Layout Chart (found in the top right of the Ubuntu desktop), and pressing each key individually. 

I've been trying to find a solution, some of which recommend using xmodmap to remap the keys, but the main problem is that all these keys seem to share the same keycode (keycode 50). In fact if I use showkey -s, it seems to imply that all the scancodes for these keys are the same too. Is there anything I can do to map the keys to their individual buttons or is this a fault of the hardware itself?

Thanks in advance.

---

### Post by stxy0509 on 2015-03-17
I have this problem too (my system is Debian),but the same keyboard in the windows 7 works fine,so i think  it is the problem of keyboard driver!        It is very painful,****!

---

### Post by vibhu on 2015-03-31
Same here. The keyboard ( RedDragon Lite) works just fine on Windows, but having issues on Linux - and only after the recent upgrade to 14.10. Was working fine earlier.

---

