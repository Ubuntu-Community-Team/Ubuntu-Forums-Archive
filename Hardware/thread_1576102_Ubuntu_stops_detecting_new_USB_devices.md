---
title: "Ubuntu stops detecting new USB devices"
date: 2010-09-16
forum: Hardware
---

### Post by unc0nn3ct3d on 2010-09-16
It seems to happen randomly, but my LG R405 laptop will for no apparent reason just stop recognizing USB devices as they are plugged in.  I switch my mouse a couple times a day between my laptop and my desktop(running XP) sitting next to it so at first I thought it just the mouse problem but I just moved my usb headset over from my desktop to my ubuntu laptop and it wasn't detected.   I tried plugging it into all of the USB ports and nothing, although I can hear it click when I plug it in so something is going on, if only to do with power.
I tried then to move my usb mouse over my my desktop and the same problem was there.  

When running lsusb the headset nor the mouse show up, nothing shows up in dmesg, none of the logs in /var/log show anything and I've tailed most of them while plugging in a device and it doesn't trigger any error messages

The only way to fix this is to completely reboot the machine.. I've tried just restarting GDM and Xorg-server but that doesn't do the trick.

Any ideas?

---

