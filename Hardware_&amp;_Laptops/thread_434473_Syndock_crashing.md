---
title: "Syndock crashing"
date: 2007-05-06
forum: Hardware &amp; Laptops
---

### Post by garren on 2007-05-06
I just installed Feisty (7.04) and it's having trouble with the touchpad in my laptop.  The touchpad is functioning, but I cannot configure it at all.  Whenever I open the keyboard and mouse configuration it tells me: > Please add the option 'SHMConfig ''on''' into the touch pad section of /etc/X11/xorg.conf
Then, when I shutdown my computer, a box pops up that says: 
> The application Synaptics Touchpad (syndock) crashed and caused the signal 11 (SIGSEGV).

The touchpad is an Alps toucpad with an "eraser" stick in the keyboard.  

There actually was no touchpad section in my xorg.conf until I reconfigured x.  After that there was a Synaptics Touchpad section.  I tried adding "SMHConfig" "on" as the error suggested, but to no avail.  I also tried suggestions I found in the forums [here]("http://ubuntuforums.org/showthread.php?t=417492"), also to no avail.  

Annoying problem; don't know how to fix it.

---

