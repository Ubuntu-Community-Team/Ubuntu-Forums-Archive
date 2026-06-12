---
title: "Unusual Mouse - Need Help"
date: 2009-11-18
forum: Hardware
---

### Post by Maximus559 on 2009-11-18
I have a Micro Innovations 4D Scrollware mouse, which is laid out as follows: left button, middle button (a separate button, not part of a wheel), right button, side button, and two (that's right, TWO) wheels. It has a special driver for Windows 95 / 98 which allows the user to map these special buttons / wheels however he wants. The intended use for the two wheels is for one to control vertical scrolling and the other, horizontal. I would like to get it to work correctly under Ubuntu. That is to say, the mouse works now - just not as intended. At the moment, the left, middle, and right buttons, along with one of the wheels, work correctly. However, the side button and the second wheel do not. The side button simply functions as a duplicate of the middle button, and the second wheel is an inverted (up is down and down is up) and noticeably faster duplicate of the other wheel. I found the page explaining how to use xinput to remap a mouse, but when I use the "get-button-map" switch, it lists the mappings as 1, 2, 3, 4, 5, 6, and 7. Funny enough, some clicking in xev reveals that buttons 6 and 7 are not mapped to any buttons on the device. Also, there is a device in the xinput list called "Macintosh mouse button emulation" - I have no idea what that is for. Any suggestions as to how I can get this resolved? I just hope it's not as complicated as an IntelliMouse to configure...

---

### Post by diesch on 2009-11-18
[https://wiki.ubuntu.com/X/Config/Input](https://wiki.ubuntu.com/X/Config/Input) should help you

---

### Post by Maximus559 on 2009-11-19
Getting closer, but still no cigar... I'm able to remap or disable the middle button (as well as the left and right buttons), but I apparently have no control over the side button, as it always does exactly what the middle button does. Also, I have not been able to remap the second wheel. Does this mean I have to do one of those HAL things? Because I don't think I'm up to that.

---

