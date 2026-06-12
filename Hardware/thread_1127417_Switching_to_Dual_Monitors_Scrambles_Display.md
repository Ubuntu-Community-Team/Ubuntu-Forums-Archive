---
title: "Switching to Dual Monitors Scrambles Display"
date: 2009-04-16
forum: Hardware
---

### Post by kingdogbert on 2009-04-16
I'm having a problem with ATI Catalyst Control Center (ACCC) where whenever I plug in a second monitor and try to activate it, both monitors get scrambled (random lines all over the place). After the "your settings will reset after X time" message times out and the configuration resets, my original monitor is still scrambled (the second monitor turns off correctly). The laptop is still working, as I can see the mouse moving around, and I can click on stuff. I just can't make sense of anything I'm seeing. If I can successfully click on the scrambled "keep settings button", I can reboot and have dual-screen working on reboot. So basically, I need a solution where either I can hot-switch between single- and dual-monitor or have dual-monitor operational all the time even when an external monitor is not plugged in.

Laptop: Thinkpad T42p
Graphics: FireGL Mobility T2
Processor: Pentium M 2Ghz
ACCC: Version 2.1
Driver: Version 8.54.3

I'll link a picture of the scrambled desktop if I can. Thanks in advance for the help

---

### Post by kingdogbert on 2009-04-16
Been messing with this some more, and I've learned some more. First, I can fix the scrambling by logging in and out. However, this only works once. If I try to open ACCC again after this, the entire machine freezes; I can't even use Ctrl+Alt+F# to switch to a command-line screen. Second, the screen capture came out perfectly clear, so apparently the system is still OK, just not the frame buffer on the graphics card or something. Third, the problem only occurs when switching from single screen to dual screen. Once I'm in dual screen, I can switch between cloned display and extended desktop just fine. 

Anyways, the logout thing gives me hope. Its certainly sufficient to get me through my upcoming presentations. Additionally, if some could be me instructions on how to get X to restart or to completely redraw the display, that might be all I need. Thanks

---

### Post by kingdogbert on 2009-04-16
New twist in the tale. I went in and updated the ATI driver, which helped significantly with the hot-changeable displays. However, now I have a "AMD Unsupported Hardware" watermark in the bottom-right corner of the display. I've done some searching on this problem, but nothing helped. So if you know how to kill the watermark, that'd be great. Otherwise, how do I downgrade the driver?

---

