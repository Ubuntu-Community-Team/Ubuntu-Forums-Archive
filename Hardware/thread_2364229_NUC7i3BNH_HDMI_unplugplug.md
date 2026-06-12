---
title: "NUC7i3BNH HDMI unplug/plug"
date: 2017-06-20
forum: Hardware
---

### Post by herbmilleriw on 2017-06-20
I'm running a NUC7i3BNH through HDMI to a Samsung DB22D-T. If I unplug the HDMI cable then plug it back in, the signal does not come back. Has anyone else experienced this? Do you know of any fixes or workarounds? I tried writing a custom udev rule to detect this scenario but I'd say it works about 80% of the time.

I've also noticed this on other displays and on the NUC6i3SYH.

Xubuntu version is 16.04.2.

---

### Post by efflandt on 2017-06-21
I cannot answer for certain, but displays are recognized when X starts or if you use "Detect Displays" button on "Displays" gui. So maybe hot plugging any video connection is not necessarily automatic.

Some operating systems can actually respond to HDMI CEC. For example using a TV remote for cursor movement, selection, or shutting down the OS if the display is turned off with the remote. But I don't know if Ubuntu responds to that without an optional package. I know that turning off my HDTV does not do anything to Ubuntu, because I do that when inactive, but leaving the computer idle and it comes right back on when I turn on the TV. But I am not unplugging the HDTV (and is actually connected DVI to HDMI, which can do audio). But maybe some hardware or OS intended for media responds to CEC (like what used to be called XBMC).

[https://en.wikipedia.org/wiki/Consumer_Electronics_Control](https://en.wikipedia.org/wiki/Consumer_Electronics_Control)

---

