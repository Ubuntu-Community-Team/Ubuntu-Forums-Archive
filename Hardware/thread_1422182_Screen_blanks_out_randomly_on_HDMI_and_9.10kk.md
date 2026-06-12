---
title: "Screen blanks out randomly on HDMI and 9.10kk"
date: 2010-03-05
forum: Hardware
---

### Post by exelan on 2010-03-05
[FONT="Arial"]Hey folks,

Now, some time back I installed 8.10 on my Asus G2S laptop.  I have it going HDMI out from the laptop to my 27" Samsung TV / Monitor running natively at 1360x768.  Everything installed fine, worked like a charm except for this annoying problem where my screen would blank out for a couple seconds EVERY 5 - 20 seconds.

So, When Window$ was floppin' around on the laptop, it ran great (as far as Windows standards are concerned) but when installing Ubuntu 8.10, I would get random screen blank-outs and the Samsung would say "searching for signal" pop back into the desktop, then randomly back out to black screen again searching for signal.  This was random, sometimes every 2 seconds up to sometimes 30 seconds of usage until it would happen.  So I migrated back to Window$ and waiting for hopes that maybe later versions of Ubuntu would clear up any issues involving this.

Now I tried again with 9.10kk and same results.  
[B]
** What I've Tried and Deduced **[/B]

1.)  Fresh install using default Xorg drivers results in the same "blank screen randomness".  Installing nVidia drivers and adjusting xorg.conf to appropriate resolution and changes yielded no results.  So I have kinda deduced that it isn't a video driver issue.  

2.) VGA out works just fine... perfect in fact, except for it not being as sharp and not being able to pass audio through the cable to my receiver.

  * ... which brings me to #3*

3.) I thought it might have something to do with Ubuntu trying to send audio through the HDMI cable so I adjusted some settings and installed alsa drivers which yielded no results pertaining to the screen issue, but am now able to hear audio through the HDMI cable..  some artifacts and popping occur as if it's trying to pass audio or mess with driver settings.

**** What Works / Doesn't Work ****

1.) I can run a 9.10 guest on Windows host via Virtualbox and it works fine, obviously different configurations are taking place but, this might be interesting.

2.) Haven't been able to test it on another HDMI Monitor, could be something with the settings that Samsung has?  Not sure... 

Anyway, if ANYONE has this same issue or might know where to go with this I would be EXTREMELY grateful.  I want this laptop to be my main box for now and would love it to run Ubuntu as it's primary O/S.

**THANKS IN ADVANCE!!! ** :P[/FONT]


**UPDATE / EDIT**

I just tried something.  I opened a video in VLC and have been playing it for 5 minutes now with NO screen blankage or shut-off.   Very interesting.  It seems as though something in Ubuntu is constantly searching or auto-adjusting something to make it randomly lose signal.

I tried something else.  When installing regular Ubuntu 9.10, it gets me to the desktop with BOTH the laptop and the 27" TV working.  Except the TV is displaying what it seems a duplicate of the laptop resolution which is set to 1920x1200.  No screen problems, until I adjust the resolution to 1360x768 under nVidia settings.

Ok, playing VLC by default it uses the analog audio hardware and playing movies STILL give me bad results.
So I switch the hardware audio to digital which sends audio through the HDMI and I get NO problems at all and can finally navigate around the desktop un-interrupted. 
.. BUT, then I stop the vid and it goes back to blankin out evey couple seconds.

---

