---
title: "TV Turns Off If I Let The Screen Turn Off"
date: 2017-01-18
forum: Hardware
---

### Post by ThePowerpuffGirls on 2017-01-18
I have a TV connected to my computer as a monitor, if I don't deactivate the screen turn off via an applet called 'caffeine'.
The problem is the TV take a bloody 10-12 seconds to turn on.
So, in short, if the screen goes off, the TV goes off with it. With a monitor, I could just press any key and it would light up again.

I think this is a driver issue or something like that as I always had problems with Ubuntu and televisions:
When I had Ubuntu 12.04, connected to the SAMSUNG SmartTV, I would get a weird error message on the screen and install would fail. I would use a monitor instead and it worked fine.
With Ubuntu 16.04, I don't have that issue, but that TV also turns itself off.

Maybe there is a setting in the TV menu that can prevent this?
We have 3 computers connected to TVs here, all have Ubuntu 16.04.

---

### Post by efflandt on 2017-01-18
TVs do not do DPMS like monitors do. So there is nothing wrong with your TV or Linux. If my system trys to put my HDTV into standby, the lack of video signal just puts my TV into a screen saver mode for 10 minutes, then shuts off. To turn the TV on again I have to use my remote (since just receiving a video signal will not do it).

I have not looked into whether Ubuntu has something to be able to do CEC via HDMI like what used to be called XBMC can on a Raspberry Pi. For example that is what can allow the remove for a BluRay player to turn on your TV or TV remote to control a connected BluRay player, etc. I would think that CEC through HDMI (or DVI to HDMI) might be a way to turn a connected TV on when the graphics card tries to bring a monitor out of standby. The question is whether anyone has anything like that set up for use in Ubuntu.

[https://en.wikipedia.org/wiki/Consumer_Electronics_Control](https://en.wikipedia.org/wiki/Consumer_Electronics_Control)

---

### Post by ThePowerpuffGirls on 2017-01-25
Thank you. :)

---

