---
title: "Asus EeePC replacement screen brightness issues"
date: 2012-05-31
forum: Hardware
---

### Post by EmersonA on 2012-05-31
I recently replaced my screen on my Asus EeePC 1005pe, and now I'm having problems with the screen brightness.

When I power the computer up, the monitor is at full brightness while the normal, non-operating-system-specific stuff is loading (excuse my wording, I'm not the most computer savvy in the world), so I know it's not entirely a problem with the screen itself. Then, when Ubuntu starts loading stuff up, the screen is at 0% brightness, and it remains that way. When I go to adjust the brightness with the keyboard function buttons, the brightness bar in the upper right hand corner just stays at 0, regardless of which direction I adjust it. When I try to adjust it with the mouse via the brightness applet, the drop-down bar just closes when I click on the slider.

I'm hoping that this is enough information to give people an idea of what's going on here. If you need any more information let me know, and thanks so much for any help in advance.

---

### Post by EmersonA on 2012-06-01
Anybody?

---

### Post by Redblade20XX on 2012-06-01
Try reinstalling the graphics driver and if that doesn't work you can see if this helps.
[https://wiki.archlinux.org/index.php/Laptop#Screen_brightness](https://wiki.archlinux.org/index.php/Laptop#Screen_brightness)

- Red

---

### Post by EmersonA on 2012-06-01
I tried following what that link said to do, but when I go to input the line

sudo echo "10" > /sys/class/backlight/acpi_video0/brightness

it tells me that permission is denied. I'm sure I'm missing something obvious here...

---

