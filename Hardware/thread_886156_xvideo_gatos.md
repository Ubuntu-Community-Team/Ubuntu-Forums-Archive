---
title: "xvideo? gatos?"
date: 2008-08-10
forum: Hardware
---

### Post by fishbulb1022 on 2008-08-10
Hi, I'm running Hardy and I haven't been able to get a tv program to work (i've tried several like tvtime, mplayer, xine, and all sorts of others). tvtime worked fine in the previous version of Ubuntu, so I know the card is supported (its an ati tv wonder, an analog card). When I try to run tvtime in Hardy, it pops a black window up as if its about to start, then closes immediately. I tried running it through a terminal and this is what i got...```
chris@chris-desktop:~$ sudo tvtime
[sudo] password for chris: 
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/chris/.tvtime/tvtime.xml
xvoutput: No XVIDEO port found which supports YUY2 images.

*** tvtime requires hardware YUY2 overlay support from your video card
*** driver.  If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: http://gatos.souceforge.net/
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.

chris@chris-desktop:~$ 

```
I opened the link for the Gatos drivers, but it says it can't find the server. I checked the synaptic package manager for "Gatos" and with everything that came up intalled, it still does the same thing. This is where I'm stuck. Any advice would be appreciated.


Solved: it doesn't work with the closed drivers

---

