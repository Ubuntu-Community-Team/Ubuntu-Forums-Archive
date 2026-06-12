---
title: "Blink LEDs; Nothing seems to work"
date: 2013-11-11
forum: Hardware
---

### Post by MFI-Spencer on 2013-11-11
I have been searching to a way to blink the LEDs on the keyboard as state indicator for a headless machine. Everything I have tried so far seems not to work. I have tried setleds. I have also tried to find the packages blink and blinkd

[http://manpages.ubuntu.com/manpages/hardy/en/man8/blinkd.8.html](http://manpages.ubuntu.com/manpages/hardy/en/man8/blinkd.8.html)

and tleds

[http://jintu.wordpress.com/2010/04/27/make-your-keyboard-blinking-to-represent-network-traffic-using-tleds-in-ubuntu/](http://jintu.wordpress.com/2010/04/27/make-your-keyboard-blinking-to-represent-network-traffic-using-tleds-in-ubuntu/)

I want to blink the LEDs when a certain network configuration is active because the network configuration allows the computer to communicate with a CNC machine but not with normal things like SSH or VNC.

---

### Post by MFI-Spencer on 2013-11-11
With some luck I found this:

[http://packages.ubuntu.com/lucid/i386/ledcontrol/download](http://packages.ubuntu.com/lucid/i386/ledcontrol/download)

And it works!!

Now I am going to try and make my script that includes it.

---

### Post by tgalati4 on 2013-11-11
There are USB devices that have programmable LED's that you can use for indicators.

---

### Post by MFI-Spencer on 2013-12-09
I've gotten the above to work very sparsely and pretty much gave up because it wont interact with my script correctly. I might come back to this in a little time.

---

