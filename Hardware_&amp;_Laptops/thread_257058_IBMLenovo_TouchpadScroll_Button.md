---
title: "IBM/Lenovo Touchpad/Scroll Button"
date: 2006-09-14
forum: Hardware &amp; Laptops
---

### Post by smart61 on 2006-09-14
I have an IBM Thinkpad T40 and would like to figure out if there is a way to do the following 2 things:

1) I would like to disable the touch pad - I'm perfectly happy with the mini keyboard red joystick thingy, which works fine.

2) I would like to enable the blue scroll button (between the two mouse buttons).  On Windows, this properly works as a great substitute for the mouse wheel (i.e. holding the blue button down and moving the mouse scrolls windows instead of moving the cursor).  This doesn't seem to work on Ubunto and I can't find any settings to enable it.

I figure someone must have the right drivers for these devices somewhere.

Help?

Thanks,
smart61

---

### Post by marin.r on 2006-09-14
Hi there,

I'm using IBM ThinkPad T23 and its very similar.
The "thingy" is IBM Trackpoint, its very easy to setup the scrolling + middle button actions, and to disable the touchpad too.
Go to thinkwiki.com, and check the Trackpoint article.
All you need to do is change xorg.conf accordingly, and possibly change speed/sensitivity settings for the trackpoint (although at my Dapper install this doesn't work - worked with slack before).
I'm not with my laptop now so I can't post you my xorg.conf, but I'm sure you'll make it based on thinkwiki's info.

Good luck and post back here if there's anything unclear :)

---

