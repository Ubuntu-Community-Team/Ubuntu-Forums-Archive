---
title: "My Touchpad is Possessed"
date: 2006-07-24
forum: Hardware &amp; Laptops
---

### Post by hizaguchi on 2006-07-24
I just got an Acer Aspire 5100 and I'm having a little trouble with my Synaptics touchpad.  The best I can tell, it is gremlins.

First off, I had to set both MaxTapTime and TapButton1 to "0" to stop the touchy tapping and dragging effect so common to laptops... but it still, seemingly randomly, resumes the tap to click behavior.  Restarting X fixes it back to the way I set it in xorg.conf.

Secondly, my left mouse button doesn't always work.  It is fine in Windows, but probably 1/3 of my clicks in Ubuntu don't register.  The problem is especially obvious when I try to drag icons on the desktop.  It is almost impossible.

I don't know if the problem has to do with this being a funky 3-button touchpad, or if it has to do with the 64 bit Ubuntu (maybe even the synaptics driver?), but it is annoying.  I'll try to rule out the 64 bit part with a live CD after work.  But in the mean time, anybody got some holy water?

Edit: Sweet! I found a nUbuntu disk in my desk.  Seems to work fine with the 32 bit Ubuntu, so maybe this is more of a bug report than a cry for help.

---

### Post by cmoz on 2006-07-26
I'm having the same problem with the primarny mouse button on my GateWay MX7515. Only about 1/3'd of the clicks seem to register. Holding down the button does not seem to register at all. Holding and dragging dosen't work at all either. Very frustrating :(

If anyones been able to resolve this without moving away from the 64 Bit version I would really apreciate you sharing how.

---

### Post by hizaguchi on 2006-07-26
I commented out the touchpad from the inputs section of my xorg.conf as a temporary fix.  Moving on the touchpad still works, and clicking with the buttons works through the mouse driver.  You just can't tap or scroll.  I might try to compile a newer synaptics driver tonight if I have time.

---

