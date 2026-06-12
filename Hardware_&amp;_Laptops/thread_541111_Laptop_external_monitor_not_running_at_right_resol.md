---
title: "Laptop external monitor not running at right resolutoin"
date: 2007-09-02
forum: Hardware &amp; Laptops
---

### Post by mrmikerich on 2007-09-02
*Sorry for the dupe -- I accidentally posted this in the Gutsy forum. *

I have a Thinkpad T61 running at 1680x1050, as well as an external LCD monitor with a native resolution of 1680x1050. I'm trying to clone the laptop display onto the external monitor (I prefer to work on the bigger monitor when I'm at my desk.)

When I plug the external monitor into the VGA port on the laptop, I can get the display to output to the VGA by running this:

xrandr --output VGA --auto

What is happening is somewhat strange, and a little hard to explain. The laptop does appear to be outputting a 1680x1050 screen, but the monitor is only running at 1400x1050. The display looks blurry, like when you use an LCD monitor at a non-native resolution, and it would appear that the laptop is making a 1680x1050 screen fit into a 1400x1050 resolution. (If I make a browser full-screen on the laptop, it is also full-screen on the external monitor with no overlap.)

I can see that the monitor is running 1400x1050 by bringing up the monitor's internal menu and looking at its resolution: It says its running at 1400x1050. But the laptop thinks its outputting 1680x1050.

Sorry for the poor description; like I said, it's a little difficult to explain what is happening. But hopefully someone knows what is going on.

---

### Post by puuma2 on 2007-09-02
xrandr --output VGA --auto <--- this solved my problem !!! thank you

---

