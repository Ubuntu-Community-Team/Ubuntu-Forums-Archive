---
title: "logitech mouse triggers randomly"
date: 2013-08-29
forum: Hardware
---

### Post by xcorvis on 2013-08-29
I have a Logitech corded mouse M500 that triggers the horizontal scroll buttons occasionally when moving the mouse. At first I thought it was a hardware problem but I find that my brand new replacement (same model) has the same problem right out of the box.

The symptoms are most noticeable in Chrome, when moving up to the tab area causes it to flip between tabs. It also makes right-click menus close or select randomly. I opened xev and ran the mouse around the event box for a while until I saw it trigger. Here's a snippet. I have my hand completely off the buttons and scroll wheel at this point, all I'm doing is moving the mouse.

> MotionNotify event, serial 41, synthetic NO, window 0x4800001,
    root 0xa6, subw 0x0, time 13683328, (55,142), root:(2436,725),
    state 0x10, is_hint 0, same_screen YES

ButtonPress event, serial 41, synthetic NO, window 0x4800001,
    root 0xa6, subw 0x0, time 13683328, (55,142), root:(2436,725),
    state 0x10, button 6, same_screen YES

ButtonRelease event, serial 41, synthetic NO, window 0x4800001,
    root 0xa6, subw 0x0, time 13683328, (55,142), root:(2436,725),
    state 0x10, button 6, same_screen YES

MotionNotify event, serial 41, synthetic NO, window 0x4800001,
    root 0xa6, subw 0x0, time 13683336, (55,141), root:(2436,724),
    state 0x10, is_hint 0, same_screen YES


I believe buttons 6 and 7 are the tilt-wheel/horizontal scroll. As a stopgap I've been running "xinput --set-button-map 14 1 2 3 4 5 15 16 8 9 10 11 12 13 14 6 7" to map the events to unused buttons.

While it's certainly possible that the second mouse is also bad (it looks new, not like a refurb), I have to wonder if it's a software issue. I had no issues with the first mouse early on. A coworker suggested that I might have some kind of mouse gesture tools installed, and I know I have installed (and uninstalled) some software to deal with my laptop trackpad. I can't spot anything. Any ideas on how to verify that, or nuke all my mouse configs and let them start over?

---

