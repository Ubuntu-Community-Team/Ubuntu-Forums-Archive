---
title: "Keytouch Problems"
date: 2009-07-08
forum: Hardware
---

### Post by KevinPS on 2009-07-08
Hey, this is my first major issue with Ubuntu that I haven't been able to work out. I just recently plugged my desktop (specs below) into my HDTV, so I wanted a wireless keyboard and mouse set for convenience. I found a great deal on Amazon on one of the only ones that uses a PS/2 interface (something I wanted given some of the USB horror stories). It's a Microsoft Wireless Optical Desktop 4000 according to Amazon, but really a Microsoft Wireless Comfort Keyboard 1.0A according to the label on the keyboard itself.

They keyboard worked pretty well out of the box; no hitches at first. But almost none of the special function keys (calendar, play/pause, etc.) produced any recognizable event. I did some searching and discovered KeyTouch, which corrected that problem. All the special keys got their own events which could be assigned to settings and hotkeys in Compiz and the GNOME Keyboard Shortcuts. However, after some use (I couldn't tell how long, since it seemed to vary), the keyboard would become non-responsive and the GUI would lock up. I could close and minimize/maximize windows, but I couldn't move them. I could launch programs from shortcuts, but not use my Main Menu on my GNOME Panel (it just wouldn't open). I couldn't type at all. Also, about half the time (I think it was if a special key had been pressed), Ubuntu would launch into an endless loop of bringing up the logout dialogue box. I would cancel every time, and it would just come up again. Because of that and the locked up GUI, I had to either log out or zap the GUI using Ctrl+Alt+Backspace. I tried both. Both just put me back at the beginning again, and didn't prevent a further lock-up.

The most recent time I had the lock-up problem, my GUI appearance settings actually got changed to a different setting. It was simpler than my usual ClearLooks theme, but I can't seem to find it in my Appearance settings menu. The GUI only returned to normal when I brought up the Appearance Settings dialogue (though I didn't even click anything; it reset on its own). For now, given these odd problems, I've uninstalled KeyTouch, which seems to have been the only thing that returned everything back to normal (including the non-functional special keys).

I don't know specifically which keys and/or special function keys cause these problems (or if there are even specific ones at all), but is there some kind of setting in KeyTouch that I need to change? Or is it possible that KeyTouch events are conflicting with Compiz or GNOME events? I'm completely lost here as to what the problem might be. I've searched around and can't seem to find anything. Apparently KeyTouch has been known to prolong the logout process in many instances in earlier versions of Ubuntu than Intrepid (what I'm running), but that's not exactly the problem I'm having.

Any help is appreciated. It seems like everyone else has gotten it to run flawlessly, so I feel a bit left in the dark.

~ Kevin


_SPECIFICATIONS:_

Dell Dimension 4600 motherboard
CPU: Intel Celeron processor, 2.4 GHz
RAM: 2.75 gig
Graphics: AT RV530LE - Radeon X1600
OS: Ubuntu Intrepid Ibex (8.10), all the most recent updates

---

### Post by KevinPS on 2009-07-08
UPDATE: I reinstaled KeyTouch twice, then rebooted a bunch of times, and set GNOME's keyboard layout to Microsoft Wireless Multimedia Keyboard 1.0a. Not sure which of those worked, but everything runs smoothly now.

---

