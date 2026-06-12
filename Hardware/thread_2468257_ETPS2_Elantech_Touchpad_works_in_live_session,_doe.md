---
title: "ETPS/2 Elantech Touchpad works in live session, doesn't work when installed to storag"
date: 2021-10-22
forum: Hardware
---

### Post by spectatorx on 2021-10-22
I have hp pavillion gaming laptop with this hellish touchpad. I tried possibly all methods i was able to find via google and duckduckgo, touchpad still doesn't work. What is interesting touchpad works on live session of ubuntu loaded from usb but once ubuntu is installed on ssd. I checked with xinput -list and list of input devices is different between live session and user session.
In live session i have elan0718:01 04f3:30fd touchpad device, elan0718:01 04f3:30fd mouse device and etps/2 elantech touchpad device, on user session only etps/2 elantech touchpad device.


Any ideas how to enable these elan devices? Seems like that would be proper solution to extremely common issue with elantech touchpad on linux.


After trying weird workaround of booting OS by selecting boot device from boot device menu F9 touchpad indeed works properly and as i assumed xinput -list returns in result all three devices i mentioned earlier. With this workaround touchpad works until a reboot.

---

