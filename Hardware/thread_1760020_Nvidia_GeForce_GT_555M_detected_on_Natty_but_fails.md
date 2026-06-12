---
title: "Nvidia GeForce GT 555M detected on Natty but fails after installing drivers"
date: 2011-05-16
forum: Hardware
---

### Post by ZaHACKieL on 2011-05-16
Hi everyone. I installed Natty on my new Dell XPS 17 (has a Nvidia GeForce GT 555M)and after installation I got Unity, which I didn't like so I changed to Classic Ubuntu, and Compiz works fine with advanced effects and I also get the gears of glxgears so it seems the card is being detected.

Then I got the message about installing the restricted drivers. I did that and after restart, I had no Unity nor advanced effects/glxgears.

I tried then with the Nvidia official drivers and didn't work either.

What I get is the "Activated but not currently in use" status in the Additional drivers app. I have tried the official manual, removing noveau drivers, editing xorg.conf but nothing has worked until now.

Any tips? Anyone having problems with this card?

Thanx!

---

### Post by FatalChaos on 2011-05-30
Not sure about your particular card, but most Nvidia GT 555M set ups I have seen support Optimus, which is currently unsupported by Linux. What I'm guessing ubuntu is doing is disabling the card and using the integrated graphics, which is actually better than what many computers do (flip out and refuse to boot). Alternately, I have heard that natty has some bugs when telling users what drivers are in use, ie telling users that a certain driver is not in use when other tests clearly indicate that it is. I think what some users did in this situation is just run more graphically intense stuff that an integrated graphics card couldn't handle to test whether or not the NVIDIA card was working.

---

