---
title: "nVidia 330M Screen Stretching Resolution"
date: 2011-01-19
forum: Hardware
---

### Post by sounddezign on 2011-01-19
I've got an issue with a new VAIO VPCF12M0E Laptop and its screen resolution in Ubuntu 10.10

The laptops 16.4" display is 1920x1080

Ubuntu is setting the resolution to 2048x1536 causing the bottom and right side of the desktop to be off the edge of the display. When you move the mouse off the bottom or side it just disappears and doesn't pan around.

If I try to set the resolution to 1920x1080 using Monitor Preferences under "System" -> "Preferences" the desktop remains off the viewable area appearing to take up the same physical size but the desktop gets stretched to fit this size.

The screen is exactly the same if I boot into just a terminal in recovery mode, with the shell prompt being off the bottom of the screen eventually coming into display after several commands or holding down the return key. So it doesn't sound like an X issue, it must be with something at a lower level.

I have edited grub to use 640x480 hoping this would help but it hasn't made a difference. By the way the grub boot options menu displays fine.

Please help, I haven't used Linux for about 2 years, I've forgotten how to do some things and a lot has moved on since then.

Thanks,
Andy

---

### Post by sounddezign on 2011-01-19
Just figured it out after playing around using xrandr:

```
xrandr --fb 1920x1080 --output LVDS-1 --mode 2048x1536
```

This fixes the problem. Now I need to figure out how to keep so it doesn't change when I restart

---

