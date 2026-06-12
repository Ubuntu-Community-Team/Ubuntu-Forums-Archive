---
title: "Left/Right scroll on wireless mouse?"
date: 2006-02-12
forum: Hardware &amp; Laptops
---

### Post by Joey French on 2006-02-12
I have a Microsoft Wireless Desktop Deluxe which includes the wireless optical mouse 2.0. It works well out of the box under Breezy, but I have been unable to get the left/ right scroll to work. Anybody got any ideas on this? I have tried reconfigure-xserver to try to select other options beside the "generic mouse" or "3-button mouse options", but didn't see any thing else. Anyone else got their side scrolling mice working under Breezy?

Thanks in advance!
Joey French

---

### Post by Joey French on 2006-02-12
Anyone? I have searched for a fix, but only turn up posts for Intellimouse, etc. Maybe someone can suggest a start, i.e., what I should adjust in Xorg.conf to test different arrangements...? Or better yet, could someone post their conf. file that has L/R scrolling working, so I can get to work on it?

Thanks again, 
Joey

---

### Post by jrib on 2006-02-12
[https://wiki.ubuntu.com/MX1000Mouse](https://wiki.ubuntu.com/MX1000Mouse)

See if you can read that and somehow adapt it to your situation.


In a terminal run ```
xev
```

Press the left scroll and right scroll and look for something like (don't move your mouse while doing this since it will cause the information to scroll off the screen): 
```

ButtonRelease event, serial 26, synthetic NO, window 0x3c00001,
    root 0x9f, subw 0x3c00002, time 131752443, (48,45), root:(58,118),
    state 0x0, button 7, same_screen YES

```

See that ``button 7'' part, do you get something like that?

---

### Post by Joey French on 2006-02-13
Cool, I will try that when I get back to my box. So, I guess there is little hope in getting a somewhat native linux driver fix for this? (I know there are no linux native drivers for microsoft products). I need to try to get some extra keys on my wireless keyboard going as well.

---

### Post by Joey French on 2006-02-15
So, no luck with the previous method. When I try L/R scroll, I get no response  messaging at all, any other ideas?

---

### Post by jrib on 2006-02-15
I don't know if it will work, but read the guide and setup your mouse to use evdev (that part should be the same).  Then use xev to figure out which buttons produce what output.  For reference the mx1000 gives me 4 and 5 for scroll up and down and 6 and 7 for left and right.  If you can get your mouse to produce /something/ when you hit those buttons, even if settings the buttons line in xorg doesn't work right, you can always use xmodmap or even xbindkeys to get it to do what you want.

---

