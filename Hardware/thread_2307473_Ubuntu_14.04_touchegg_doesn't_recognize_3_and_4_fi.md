---
title: "Ubuntu 14.04 touchegg doesn't recognize 3 and 4 fingers gestures"
date: 2015-12-25
forum: Hardware
---

### Post by jhacked on 2015-12-25
Hello everyone! First of all merry christmas to all of you, I hope you're going to spend some good times during these holidays!
I have ubuntu 14.04 on an hp stream 13 (not the touchscreen version). Just to be clear [this is the computer]("http://www.laptopmag.com/reviews/laptops/hp-stream-13") I'm talking about

Now on windows 10 I fell in love with the multitouch gestures for the touchpad and I saw that I can do the same on linux distros with touchegg. So I compiled it from sources (1.1.1 if I don't go wrong) and I've also compiled touchegg-gce (nothing else than a graphical editor for its configuration file).
It works smoothly only disabling on startup synclients like this:

```

synclient TapButton2=0
synclient TapButton3=0
synclient ClickFinger2=0
synclient ClickFinger3=0
synclient HorizTwoFingerScroll=0
synclient VertTwoFingerScroll=0

```

The very big problem is that 3 and 4 fingers gestures doesn't work and the two fingers scrolling doesn't work as good as the synaptic driver, so I questioned the capability of my touchpad to support 3 and 4 fingers, but asking to xorg through terminal it says that the touchpad is capable of 3 fingers gestures. This is the command I used to check that: ```
xinput list-props 11 | grep Capabilities
``` and this is the result ```
Synaptics Capabilities (296):    1, 0, 0, 1, 1, 1, 1
``` to understand this result we can take a look at the documentation: [https://wiki.archlinux.org/index.php/Touchpad_Synaptics#Using_xinput_to_determine_touchpad_capabilities](https://wiki.archlinux.org/index.php/Touchpad_Synaptics#Using_xinput_to_determine_touchpad_capabilities)

What I want to accomplish is to use touchegg only for three fingers gestures (I need actually only one gesture) and use synaptic for everything else.
If it won't be possible (no matters what we try) at least I'd like to use synaptic for all the two fingers gestures and touchegg just for one two fingers gesture. I don't think this is possible but I ask it anyway :D I just need a swipe left/swipe right or everything else that is not occupied by default. I'm a developer, if the sources of the synaptic driver are released (and if the portion of the code that implements gestures is not written in a too much complicated way (a bit unlikely) we could do something together!)
So I'll wait for your ideas!! Thank you very much.

---

### Post by jhacked on 2015-12-29
No one here? :(

---

