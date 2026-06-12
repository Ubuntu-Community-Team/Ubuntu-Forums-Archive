---
title: "Turn off backlight with locked screen in 9.10"
date: 2009-10-31
forum: Hardware
---

### Post by scebert on 2009-10-31
In previous versions of Ubuntu, when I locked the screen, the backlight would turn off after a short period of inactivity. In 9.04, it follows the timeout set in the gnome power settings, and turns off after the same amount of time whether the screen is locked or not. I do not want the screen to turn off unless it is locked, but if I set it to "never", it doesn't turn off when it is locked either. The best I managed was a workaround to bind the command 
```

gnome-screensaver-command --lock && sleep 10 && xset dpms force off
```

to a keyboard shortcut. This command locks the screen and turns off the backlight after 10 seconds. However, if it comes on due to some activity, it will not turn off again.

---

