---
title: "Dual head resolution problem, intel 945GM"
date: 2008-06-24
forum: Hardware
---

### Post by khul on 2008-06-24
I have an hp compaq tc440 tablet PC with a 945GM graphics controller. I run dual head with an external Fujitsu-Siemens 5110 FA display in my office. I run a few applications in the external display while at work, then close them (usually) and only use the laptop screen when I'm away. I do not re-start X, as I usually have many applications running for many days on the laptop screen. 

If I start the X session with the external screen connected everything is fine. I can disconnect, work on the laptop screen, and later re-connect to the external one and start evolution and firefox on that. But when I start X *without* the external screen (which I sometimes have to) and plug it in later, I get the wrong screen setup. xrandr reports a number of modes, including 1600x1200 at 56 Hz which is the one selected. The picture is rather fuzzy, not at all as crisp as when I start X with the screen connected (in which case the selected mode is 1600x1200 at 60Hz). I tried adding a modeline in xorg.conf and selecting that (picking up the settings reported under additional Video Mode in the Xorg log). This seems to be completely ignored.

So it seems the external screen characteristics are obtained when X starts, and are not updated when the screen is connected, or else that the updating does not work.

I'm having this problem with ubuntu 8.04. With 7.10 it was the other way round: I had to start X without the screen connected. That was better!

I would be happy if I could disable automatic display detection altogether and set up a bunch of modelines in xorg.conf and then select one with xrandr for the external display. I could then select display without re-starting X. Alternatively, is there a way to trigger a proper display detection after connecting the external monitor?

This is not a big problem, but sometimes it's rather annoying. It would be great of someone has a solution!

---

