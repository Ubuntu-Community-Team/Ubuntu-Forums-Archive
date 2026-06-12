---
title: "HP Pavilion v70s monitor resolution issue"
date: 2005-09-26
forum: Hardware &amp; Laptops
---

### Post by Nihilist on 2005-09-26
hi.

i have the above monitor on my setup. it wont go above the lowest setting, which is quite the pain in the ass since most of the pages dribble off the screen and i cant read them. its more or less unusable.

i installed both xp and ubuntu today, and the xp problem was taken care of by updating the graphics drivers. i dont see a similar resolution being as this is linux.

i was using xandros before ubuntu as my linux, and i have to say i like ubuntu much better. please tell me theres some way to salvage this so the resolution can be brought up to something more usable.

thanks in advance.

---

### Post by Nihilist on 2005-09-26
bumpity bump bump

---

### Post by mlomker on 2005-09-26
The monitor isn't your problem, it's probably the drivers.  What kind of card do you have?

I think I need to put the following command into a hotkey or something.  ;) 

**sudo dpkg-reconfigure xserver-xorg** will allow you to select a different video driver.  Just take the defaults whenever you're not sure because it'll read your current settings.

---

