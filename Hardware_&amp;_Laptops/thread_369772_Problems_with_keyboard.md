---
title: "Problems with keyboard"
date: 2007-02-24
forum: Hardware &amp; Laptops
---

### Post by ladysorka on 2007-02-24
I recently installed Ubuntu onto my new Dell XPS M1710 laptop, and I'm having... very strange problems with the keyboard.

Namely, that I'll be randomly typing along and suddenly my typing will open a context menu, or randomly paste whatever's currently in the cache.  Sometimes, it just randomly pastes whatever's in another open window, even if I never actually copied it.  Using GAIM, it will randomly press enter during my conversations. 

I've checked my keyboard shortcuts, and there's nothing in there that should be giving me any of this.

Help?

---

### Post by tgalati4 on 2007-02-24
Any keyboard problems in windows?  Spill any Red Bull in the keyboard?

Does that laptop have a large trackpad?  Is there an option to turn off accidental presses?  Sometimes when typing, the track pad will pick up stray touches and register them as double-taps.  This will paste buffers at your cursor location.  And this is annoying.

Try turning down trackpad sensitivity and see if that helps.

Let us know what works.

---

### Post by ladysorka on 2007-02-25
Nope, no keyboard problems in Windows.  And no spills.

And a double tap on the trackpad isn't actually working right now either - it registers as me wanting to open the context menu (possibly because I have my USB trackball set to left handed?).

...actually, I just noticed that I can't find the place to deal with my touchpad.  My USB mouse is under "mouse", and I'm not finding touchpad options anywhere.  I rarely use the touchpad, so I hadn't previously gone looking.  It looks normal in xorg.conf, though, despite the... not exactly working.  (I am, I admit, fairly new to Ubuntu.)

---

### Post by ladysorka on 2007-02-25
I have been able to get the keyboard problems to stop now - by completely turning off tapping on the touchpad.  Reducing the sensitivity didn't help, but completely turning it off did.

Not the best solution in the long run, but it did work.

---

### Post by Riverside on 2007-03-04
> **tgalati4 said:**
> Try turning down trackpad sensitivity and see if that helps.
How can this be done?  I want to make a few changes to trackpad behaviour, but there doesn't appear to be any means of doing so.  I am running 6.06.1 on a Dell Inspiron 6400 however Gnome System > Preferences > Keyboard seems to think that a conventional keyboard is attached to the machine (one isn't, and never has been).  I have also been unable to find any alternative means of adjusting trackpad settings.

---

### Post by tgalati4 on 2007-03-04
The trackpad is treated as a mouse.  Look under Preferences-->Mouse.  You can set sensitivity, acceleration, and threshold.

You didn't mentioned that you were using a USB trackball at well.  That could cause some hardware confusion because you can input from either the trackpad or the USB trackball.

Perhaps you can turn off the trackpad in BIOS?  Linux will handle input from two sources, but the trackpad is sensitive to capacitive changes and simply hovering over it can cause spurious input.  When you have a finger on the trackpad--it sets a baseline capacitance and it works as expected.

The mac powerbook has a setting to ignore accidental touches which helps in this situation.

Try using a PS/2 mouse if your computer has a PS/2 port in the back.  That way you will get a more dedicated mouse instead of waiting on USB interrupts which can be shared with several other devices.  

I'm not sure how the Linux kernel handles USB mouse input vs PS/2 mouse inputs especially with a built-in trackpad.

It's time to experiment and let the community know what works.

Good luck.

---

