---
title: "Adding 3rd monitor when existing graphics only allow for 2"
date: 2021-10-19
forum: Hardware
---

### Post by nginmu on 2021-10-19
My laptop relies on CPU integrated graphics (core i3 M330); the CPU specs mention it supports a maximum of 2 monitors. 

The laptop has an HDMI and a VGA port.

I've found if I try and use either port, all's fine - however if I plug in a VGA and also an HDMI monitor, to try and extend the desktop to 3 monitors, arandr gets confused and locks one out. 

I guess that's expected if the video in the CPU is only designed to run 2 monitors.

 I'm trying to use.. 

1. laptop's builtin display 
2. an external HDMI-only monitor 
3. an xp-pen drawing tablet which is essentially a touch sensitive HDMI-only monitor  all together. 

Is there something I can plug in to add capability for a 3rd monitor that will work with lubuntu? 

I did find a few USB-A to HDMI adapter boxes but they all expressly disclaimed compatibility with linux, and also noted the max resolution was quite a bit lower for USB2 v USB3. All I've got is USB2 A-type ports.

---

### Post by nginmu on 2021-10-19
Sorry it's a double post, have moved along just a little. I found an old USB2-to-VGA adapter that'll help me free up the laptop's HDMI port so I can use it with the drawing tablet, whilst still retaining a second (albeit small) extra monitor on the table next to the laptop.

At first it wouldn't work at all, caused a screenful of fleeting text followed by a logout as soon as plugged in every time.

It has a DisplayLink chip in it:

[https://www.lindy.co.uk/downloads/42744v3.pdf](https://www.lindy.co.uk/downloads/42744v3.pdf)

So I downloaded and installed the DisplayLink driver:

[https://www.synaptics.com/products/displaylink-graphics/downloads/ubuntu](https://www.synaptics.com/products/displaylink-graphics/downloads/ubuntu)

Now, everything seems to work fine except, no actual display on the VGA monitor, and neither lxqt-config-monitor nor arandr seem to be aware of it's presence but other than that no bad things seem apparent

System Information recognises it under USB devices, the monitor is announcing a valid VGA signal every time the USB is replugged, the driver install went fine with no errors.

Wondering what I could look into next?

edit.. Would love to know why, but after a while rebooting & replugging it just started working. The release notes for the driver do mention something about an embedded firmware image & the fact that some older dongles might take a while to update themselves using it. Maybe.

---

