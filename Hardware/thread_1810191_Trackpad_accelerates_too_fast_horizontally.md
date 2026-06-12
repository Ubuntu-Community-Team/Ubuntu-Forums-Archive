---
title: "Trackpad accelerates too fast horizontally"
date: 2011-07-22
forum: Hardware
---

### Post by sytheii on 2011-07-22
Hello.

I recently installed Natty on a toshiba laptop of mine. I notice that the touchpad accelerates way too fast when moving the mouse horizontally. 

For a comparison, if i put my cursor on the far right of my screen, and at a normal speed slide it to the left, i will cross my entire screen with a little extra travel area left over. In contrast, when scrolling from bottom to top, I only get a little under halfway. 

This is incredibly annoying, as it makes navigating the mouse to small targets like close/minimize/maximize almost unbearably difficult.

Any ideas on how to solve this? There are no options that I can see for acceleration options of vertical as well as horizontal, just a default "acceleration" slider.

---

### Post by sytheii on 2011-07-23
Does no one else notice this on their laptops? Am I missing something elementary and simple?

---

### Post by kchida on 2011-08-02
I have the same problem with my new Apple Trackpad. If I were using synaptics drivers, I'd just make some quick changes to my xorg.conf and be done with it, but I'm using the uTouch stack instead.

If you're using synaptics, you can do 'man synaptics' in the command prompt to read about what options you have available.  Here's what I was experimenting with:
```
Section "InputDevice"      
    Identifier      "Apple Wireless Trackpad"
    MatchIsTouchpad "on"
    MatchVendor     "05ac"
    MatchProduct    "030e"
    Driver          "synaptics"
    # these two options are for multiple monitors 3:1 ratio.
    Option          "VertResolution"   "1"
    Option          "HorizResolution"  "3"
EndSection
```

Obviously, you'll need to enter your own identifier and device matching info.  The Vert and Horiz Resolution are what you need to adjust.  Again, for more info read the man pages.

Of course, this is all assuming that you're using synaptics drivers, unlike me.  :(

---

