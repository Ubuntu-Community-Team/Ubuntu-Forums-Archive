---
title: "External keyboard crazy after suspend"
date: 2009-07-13
forum: Hardware
---

### Post by dibon on 2009-07-13
At home I use my laptop with an external monitor and a external keyboard. The problem I'm having can be considered two problems:

1) Keyboard crazy after resuming from suspend

I have the Logitech Illuminated keyboard which has the nice feature of being backlit with multiple levels of brightness.

When resuming from suspend the keyboard is looping through all the brightness levels, and if I try typing on the keyboard nothing happens. I then have to plug in and out the USB plug for it to work again.

2) Keyboard layout changes when external keyboard is connected

My keyboard layout is "Norway Macintosh", but when I connect my keyboard the layout changes to the standard "Norway" layout. When I check System->Prefs->Keyboard it says that the Norway Macintosh layout is active, but it's not!

To get it working again I have to do some minor change, like go into Keyboard Prefs->Layout->Layout Options and just check and uncheck one of the settings, then everything is back to normal.

Even though I have found a fix for my problems it is every annoying to have to do this very time after suspend. So please, does anyone have any suggestions for a permanent solution?

---

### Post by prshah on 2009-07-13
> **dibon said:**
> 
To get it working again I have to do some minor change, like go into Keyboard Prefs->Layout->Layout Options and just check and uncheck one of the settings, then everything is back to normal.

This problem and workaround looks similar to ones in the links below: Maybe the given solution is worth a try?


[[SOLVED] keyboard layout disappears on boot]("http://ubuntuforums.org/showthread.php?t=850040&highlight=setxkbmap")
[[SOLVED] Keyboard Layout Settings won't stick after reboot]("http://ubuntuforums.org/showthread.php?t=813567&highlight=setxkbmap")
[[SOLVED] Keyboar layout keeps resetting to US]("http://ubuntuforums.org/showthread.php?t=898384&highlight=setxkbmap")
[Keyboard preferences lost on automatic login]("http://ubuntuforums.org/showthread.php?p=5860154&highlight=setxkbmap#post5860154")

Summary: Add "setxkbmap" to your startup sessions.

---

### Post by dibon on 2009-07-14
I've tried that, but unfortunately it doesn't work.

It should be noted that I have edited the /usr/share/X11/xkb/symbols/no file to be the corrent norwegian mac layout, but I don't think that should have anything to say since I haven't added a new layout, just edited the old "Norwegian Macintosh"

Does anyone else have any suggestions?

---

