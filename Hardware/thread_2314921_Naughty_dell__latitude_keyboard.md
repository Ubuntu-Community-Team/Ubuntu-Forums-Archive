---
title: "Naughty dell  latitude keyboard"
date: 2016-02-24
forum: Hardware
---

### Post by juan53 on 2016-02-24
Hi
I write this post because the keyboard backlight turns on each time I set on my laptop. My computer is a Dell Latitude e5450, and I'm running ubuntu 14.04.4 lts. Could you help me please?
I tried to modifying /etc/rc.local by adding:
echo '0' > /sys/devices/platform/dell-laptop/leds/dell\:\:kbd_backlight/brightness
alternatively I tried:
xset -led
Thanks.
:)

---

