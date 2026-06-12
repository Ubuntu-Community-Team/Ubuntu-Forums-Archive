---
title: "Synaptics Touchpad Lag on Asus V6J"
date: 2007-12-11
forum: Hardware &amp; Laptops
---

### Post by Thief on 2007-12-11
So far, I have tried Ubuntu 7.04, 7.10, FC7, and FC8. They all exhibit this same behavior. When I attempt to move the pointer via the touchpad, it lags. The degree of lag varies with every touch. Sometimes it's a brief split-second delay, sometimes I can move my finger across the entire touchpad before the pointer starts moving, at which point it stops because my finger just moved off the touchpad. Once I get it moving, however, it continues to move with me until I stop and release my finger from the pad; it never gives out once in use.  Once I let go, however, it starts all over again and I play "lag roulette."

It's so bad, it basically makes my laptop unusable. I've tried playing with qsynaptic, disabling touch-clicking, dragging, gestures, etc. I've tried various sensitivity options in xorg.conf and the gui config tools. Nothing improves it. It doesn't matter how hard I touch or what I set the sensitivity to.

Response is instantaneous and consistent in WinXP, so I know it's not a hardware problem. Any suggestions?  Here's the relevant section from my xorg.conf file:

Section "InputDevice"
   Identifier  "Synaptics TouchPad"
   Driver      "synaptics"
   Option      "SendCoreEvents" "true"
   Option      "Device" "/dev/psaux"
   Option      "Protocol" "auto-dev"
   Option      "HorizEdgeScroll" "0"
   Option      "SHMConfig" "true"
 EndSection

I'd appreciate any help you folks can give me.  I have Ubuntu running just fine on a desktop machine and would love to do the same with my laptop.

---

### Post by Thief on 2007-12-13
An update and a bump.

I've been playing with syndaemon, and that doesn't appear to be it.  I don't have it set up to run by default.  When I do run it, it returns the words "Disable" or "Enable" depending on what it or I are doing.  It switches to "Disable" once I start typing, at which point the touchpad stops working altogether.  Once I stop, it waits whatever time interval that's set (or 2s default), and the word "Enable" is returned.  Once it says "Enable," I'm back at my usual sitation; Lag Roulette. :-?

Also, I have connected an external USB mouse (no PS/2 ports), and it works flawlessly.  I need the touchpad, though, as I often use my laptop in places that don't accommodate mouse usage.

---

