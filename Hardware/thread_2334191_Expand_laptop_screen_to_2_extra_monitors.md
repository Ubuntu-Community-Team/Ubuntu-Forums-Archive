---
title: "Expand laptop screen to 2 extra monitors"
date: 2016-08-17
forum: Hardware
---

### Post by sebastiaan5 on 2016-08-17
Hello

I was wondering if it is possible to extend my laptop screen to 2 extra   monitors, I searched on google but the information I found was pretty   outdated and not successful so I want to ask it here.

I have a Lenovo y50-70 i7 nvidia 860m gtx.
I have 1 HDMI 2USB 3.0 and 1USB 2.0.

Is it possible to split HDMI into 2*HDMI? Or some external video card USB to HDMI?

Any possibility whatever the cost is greatly appreciated.

Greetings

---

### Post by TheFu on 2016-08-17
There are USB-based video output devices (call them "video cards" or "GPUs" if you like). I don't know if any work with Linux or not. That's the big question.

Generally, for multiple outputs, a video card or multiple video cards are needed which have VGA, DVI, HDMI, and/or DisplayPort outputs. If a video card made in the last 5 yrs has multiple outputs, usually it is just as simple as connecting those outputs to monitors and using a GUI tool to enable the output to each monitor.  I haven't used nvidia for a few years, but they used to provide a GUI tool with the driver to address this.  For the built-in drivers (not proprietary), using **lxrandr** to enable the multiple outputs is trivial.

HDMI splitters just replicate the image to multiple HDMI outputs. They aren't GPUs.

According to this: [http://www.geforce.com/hardware/notebook-gpus/geforce-gtx-860m/specifications](http://www.geforce.com/hardware/notebook-gpus/geforce-gtx-860m/specifications)  the card has VGA, HDMI and DisplayPort outputs, so you should be able to just plug in those 3 cords and connect them to compatible monitors.  Whether Lenovo makes those putputs available on this specific model or not is something only you can determine.

---

### Post by sebastiaan5 on 2016-08-18
Thank you for your reply, but actually I mean with my questions if I could expand my laptop screen with 2 monitors with LINUX. With Windows it will work I have bought a device "usb2vga2e displaylink" but this doesn't work on Linux, now I'm searching for another device that will work for Linux, I am from Europe so I'm looking for a device that is being sold in Europe.

---

### Post by TheFu on 2016-08-18
And the outputs on the laptop don't already work? Is there VGA, HDMI and DisplayPort outputs on it?  I vaguely remember that DisplayPort supported daisey-chaining multiple monitors - that would be where I started.  [http://www.displayport.org/cables/driving-multiple-displays-from-a-single-displayport-output/](http://www.displayport.org/cables/driving-multiple-displays-from-a-single-displayport-output/)  I don't have **any** equipment that supports DisplayPort, so can't check this myself.

---

### Post by sebastiaan5 on 2016-08-19
I have 1 HDMI 2USB 3.0 and 1USB 2.0.

The device won't work on Linux apparently I asked someone from the company and he said it only works for Windows :(

---

### Post by bikergeek2 on 2016-08-19
DisplayPort in theory supports daisy-chaining multiple monitors.  However, the monitors, cables, and graphics hardware all have to support DisplayPort version 1.2, and, even then, it seems like success isn't guaranteed.  There's also lots of hardware that claims to support v1.2 and doesn't.  Right now I have a pair of brand new Dell Ultrasharp 2415 monitors that I can't get to work in daisy-chain fashion.  Couldn't get the daisychain configuration to work with my work-issued MacBook Pro running Yosemite, either, via the Thunderbolt port.

Ironically, the OS that supports daisy-chained DP monitors best is recent versions of Windows.  :/

---

