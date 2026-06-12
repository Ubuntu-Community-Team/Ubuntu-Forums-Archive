---
title: "Thinkpad T440s function keys in xubuntu 13.10"
date: 2014-02-26
forum: Hardware
---

### Post by jawknee530 on 2014-02-26
I'm having an issue with my brightness function keys in xubuntu 13.10 on my Thinkpad T440s. The brightness keys respond when pressed and the on screen display even shows up. The issue is that while the on screen display changes and shows button presses the physical brightness of the display doesn't actually respond except when the osd bar is at 0, 50, or 100%. Now i want to be able to set my brightness with more precision than that. Using xbacklight -set <##> works perfectly to set the screen to whatever % brightness I want so at least I've got that going for me. Any tips on a fix?

---

### Post by jawknee530 on 2014-02-26
I came across another thread where the user was told to run

for i in /sys/class/backlight/*; do echo -e "\n $i"; cat $i/{brightness,max_brightness,actual_brightness}; done

When running that the output for me is

 /sys/class/backlight/acpi_video0
35
100
35

 /sys/class/backlight/intel_backlight
60
851
60

Don't know if that could help with troubleshooting.

---

