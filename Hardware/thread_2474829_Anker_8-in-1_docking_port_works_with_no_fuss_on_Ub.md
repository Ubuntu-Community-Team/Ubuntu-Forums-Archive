---
title: "Anker 8-in-1 docking port works with no fuss on Ubuntu 22.04"
date: 2022-05-09
forum: Hardware
---

### Post by gleedadswell on 2022-05-09
Obviously, "results may vary".  But, since I didn't see a lot posted on this when I googled it I thought it might be helpful to post this in case other people are having trouble finding docking ports that are compatible with linux.  The main things that probably matter are the fine details of your usb-c port, in particular, whether it is a "thunderbolt" port.  I was initially discouraged when I read this:

[https://www.addictivetips.com/buying-guides/laptop-docking-stations-linux/](https://www.addictivetips.com/buying-guides/laptop-docking-stations-linux/)

because while it lists docking ports that work for linux, all of the ones it lists are quite pricey.

I am running a fairly freshly installed Ubuntu 22.04 on an HP Omen laptop with i7 core processors and an Nvidia RTX graphics card.  The usb-c port on this laptop doesn't have a battery symbol next to it, so I doubt it supports usb-c power delivery.  So I can't comment on whether the power delivery feature of the docking ports I tried works.

First I got a JCreate JCD381.  I could get the usb-A ports on it working after a bit of futzing around.  But after trying various things to get working displaylink drivers I couldn't get the HDMI port on it to work. Looking around it looks like displaylink can be very hit and miss on linux.

So I tried an Anker PowerExpand 8-in-1, product number A8383.  That worked straight out of the box, with absolutely no fuss.  I can confirm that the usb-a ports, usb-c ports, and HDMI ports all work, with the HDMI port giving me 1920X1080 at 144 Hz on my second monitor, which I think is the full capability of that (old!) monitor.  I do see posts out there that people are unable to get 4K video at 60 Hz with this docking port.  But with my ancient old monitor everything is fine.

---

