---
title: "Can I Reduce Sensitive Area of Touchpad?"
date: 2010-01-20
forum: Hardware
---

### Post by clevertomato on 2010-01-20
This probably seems like a really strange question, but is there a way I could make the bottom edge (maybe 1/16") of my touchpad ignore touching? The buttons on my new notebook PC are too short for my thumb and there is no insensitive area between buttons and touchpad. This results in my thumb accidentally touching the bottom edge of the touchpad while it's resting on the button, which sends the pointer teleporting from one part of the screen to another.

I thought maybe there's a config file that would allow me to set the x,y coordinates of the touchpad area that I want to be sensitive to touch. Shot in the dark but it doesn't hurt to ask, I suppose.

---

### Post by pi/roman on 2010-01-21
Yes. Fist type "synclient -l" in a terminal and you will get a list of options. At the bottom you should see AreaLeftEdge AreaRightEdge AreaTopEdge AreaBottomEdge which are probably set to 0. If you change these to a nonzero value the you it will define the edge of the touchpad.  Use your LeftEdge RightEdge TopEdge BottomEdge values as references because they are close to the edge of your touchpad.

For instance my BottomEdge=4300 so I would try:
synclient AreaBottomEdge=4300

After you determine the values you need then you can put them in your HAL configuration file.

---

### Post by clevertomato on 2010-01-21
Thanks!

---

