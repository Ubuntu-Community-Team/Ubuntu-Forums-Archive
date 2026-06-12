---
title: "Sporadic graphics crash with Intrepid on Toshiba Satellite"
date: 2009-07-21
forum: Hardware
---

### Post by crismxml on 2009-07-21
I have a Toshiba Satellite A105-S4074. I installed Ubuntu 8.10 Intrepid Ibex a few months ago, after almost two happy years with Feisty. Since then, I have had three crashes, and I am trying to figure out where the problem lies.

In every case, I was moving the pointer leftwards with the Synaptics touchpad when the display soiled itself. In the first two cases, I was playing Aisle Riot solitaire and had just picked up a card using the double-tap-and-drag motion; in the third, today, I was just moving the pointer to the Firefox back button.

The screen blanked, did some strange and not easily described things, and then Ubuntu informed me that it was switching to low graphics mode. The reason I suspect the touchpad is that on one occasion, it then told me it couldn’t load a driver for the touchpad.

On restarting, the shutdown screen is mangled in a way that indicates that VRAM has gone wonky; the Ubuntu logo and thermometer are diffracted such that horizontal lines are kept together, but the lines are not placed next to each other. I’m having trouble describing it, but if you’ve seen it before, you’ll know what I’m talking about. After restarting, everything is fine for weeks.

Candidate causes I can think of include problems with the Synaptics touchpad driver, problems with the display driver, or physical damage to the laptop from any of the dozen small bumps it’s received over its lifetime. I haven’t been able to find any reference to problems like this while searching, however, and I am reluctant to upgrade to Jaunty since each upgrade seems to consume more memory, while this thing only has a half gig and already struggles just with Firefox and Flash.

Any thoughts?

---

### Post by emanresu on 2009-07-22
i had a Satellite laptop a couple of years ago. i bought it used and it was 3 or 4 years old at the time. when the screen starting to go batty after a couple of months, for no good reason, it turned out the video card connection was damaged. i needed a new video card and it was gonna cost more than a new laptop. 

after digging a little i found out a whole host of Satellite lines from the time of this my Satellite's manufacture had video problems and were causing tons of 5 lb paper weights. 

i'm not trying to say that's your computer's problem, but i'm just supplying a possible conclusion. good luck.

---

### Post by crismxml on 2009-07-22
Thanks for the info, emanresu. This one was bought new in 2006, but might possibly have similar problems. Maybe it’s just time to go shopping…

---

### Post by crismxml on 2009-09-08
It happened once again; and again, I was moving the pointer leftward, this time immediately after switching display panes in GNOME. If I can characterize this based on only four occurrences, it is that something moderately intensive is going on with graphics and the pointer is moving to the left. It has only happened four times in about six months, so I can definitely live with it, but if anyone has suggestions on any kind of logging to turn on to get a handle on the cause, they would be most welcome.

---

