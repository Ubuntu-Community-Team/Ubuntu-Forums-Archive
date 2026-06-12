---
title: "How do I create virtual input devices with evdev?"
date: 2018-03-28
forum: Hardware
---

### Post by ovgvo on 2018-03-28
I am using evdev and currently can simulate events on my trackpad.
I will be doing this on a RPi which doesn't have a connected trackpad.

How can I add a **virtual** device under ```
/dev/input
``` so I can send events to it?
Is it just that I need a driver for a trackpad installed and then use modprobe to load it? (Its my first time using evdev/uinput and I'm not exactly sure how things work)

Further, I actually will be wanting to simulate a touch screen (I just want to get something working first!). Is adding a virtual touchscreen device similar to adding a virtual trackpad?

---

