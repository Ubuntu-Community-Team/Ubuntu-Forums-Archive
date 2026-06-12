---
title: "Mouse &amp; Touchpad issues."
date: 2006-01-10
forum: Hardware &amp; Laptops
---

### Post by gcain on 2006-01-10
Hi guys!

I have two problems, but only one is active at a time, so any solutions for either problem will be most appreciated!

Firstly I just bought a brand new MS Wireless mouse for my laptop. The thing goes totally nuts if I use it with the 2.6.10-686 kernel. Opens windows, deletes stuff, moves applets about. It's really quite entertaining, till I need to get some work done.
It works 100% okay with the 2.6.12-686 kernel though.

The Touchpad on the other hand works perfectly with the 2.6.10-686. With the 2.6.12-686 kernel though, I can't get it to double-tab-drag no matter what I try.

Does anyone have any solutions to how I can get around this, it's driving me nuts because some times I use the Touchpad (sitting on the couch for example) and some times I use the mouse (playing an FPS for example).

I'm running a Dell Inspiron 9300, which means a Synaptics touchpad.

Any suggestions will be most appreciated!

---

### Post by jpfinley on 2006-01-23
Hi gcain.

I'm not sure if your problem was resolved already, but I'll put this out there for anyone else who might be curious.

I am also the proud owner of a Inspiron 9300, and I was having some touchpad issues as well:  tracking was impossibly slow, tap-to-click wasn't working, no scrolling, etc.  After some searching, I found [this program]("http://gsynaptics.sourceforge.jp/").  Its a "settings tool for the Synaptic driver".

I have installed it but cannot yet tell you if it works - I still have to get back home and modify Xorg.conf.  I will post back with my results sometime this afternoon. As for your mouse problem, I don't know anything about that, sorry.

---

### Post by gcain on 2006-01-23
Hi jpfinley,

I am still having the weird mouse issues.
My touch pad randomly clicks and the mouse pointer gets stuck and jumps around the screen.

The strange part is that if I swap kernels, my optic mouse suffers from the same reason and the touch pad works fine...

Either way, I'm interested in how things turn out for you, please let me know!

:)

---

### Post by jpfinley on 2006-01-24
Has your touchpad ever worked outside of Linux?

I followed the directions for gsynaptics, and after restarting X I now have a touchpad settings tool under System > Preferences.  My touchpad was cured of what ailed it afterwards.  Try that, and report back.

---

