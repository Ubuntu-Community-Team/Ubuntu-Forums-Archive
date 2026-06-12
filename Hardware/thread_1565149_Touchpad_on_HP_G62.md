---
title: "Touchpad on HP G62"
date: 2010-08-31
forum: Hardware
---

### Post by kjbeau on 2010-08-31
I can't get the neat feature of disabling the touchpad on my HP G62 to work.  Normally I should be able to tap a small hole at the top left of the touchpad to disable the touchpad and illunimate an indicator light.  This is a very nifty feature - and I really wish it worked in Linux.  [It is much, much better than the common fix of disabling for a few seconds after using the keyboard, it really is,...]
Any ideas greatly appreciated.

---

### Post by Aviendha09 on 2010-09-08
Same here. I've been trying all kinds of suggestions, to the point where I'm getting confused (and my computer too). Any news on the Linux gesture suite promised by Synaptics in april?

---

### Post by fett2k on 2011-04-27
*bump*

---

### Post by kjbeau on 2011-04-28
I worked around things by creating two Keyboard Shortcuts.

Disable Touch uses the command = gksudo rmmod psmouse

Enable Touch uses the command = gksudo modprobe psmouse

I set disable to be Crtl+space and enable Mod4+space

Not as nifty as tapping the illuminated spot but it works - so I'm happy.

---

### Post by tulipán on 2011-09-18
kjbeau, you rule! it works! now i need to find a nifty key combination! :) thank you so m uch! (nifty being the key-word in this thread :)) (i am still hoping for a solution for the light-tap though)

---

