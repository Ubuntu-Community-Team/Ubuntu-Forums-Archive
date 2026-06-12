---
title: "Synaptics touchpad acting just a little wonky"
date: 2013-08-28
forum: Hardware
---

### Post by CaptSaltyJack on 2013-08-28
I just bought a ThinkPad S431. I really like it, but the touchpad acts strange in a couple ways:

1) When moving the mouse and then letting the finger off the touchpad, sometimes the mouse pointer jumps by 5 or so pixels.
2) When tapping on the touchpad to click, sometimes the pointer jumps as well.

Is there anything I can do to tweak this? I'm pretty sure this doesn't happen under Windows.

---

### Post by CaptSaltyJack on 2013-08-28
I think I have a solution:

xinput set-prop "SynPS/2 Synaptics TouchPad" "Synaptics Noise Cancellation" 26 26

And of course the 26 26 can be increased to eliminate more noise.

---

