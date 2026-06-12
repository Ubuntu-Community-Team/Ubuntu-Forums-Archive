---
title: "X1600 Dynamic Power Scaling?"
date: 2012-05-01
forum: Hardware
---

### Post by Benjamindaines on 2012-05-01
As the title says, I'm looking to optimize my battery life. I've already configured laptop-mode-tools and have gotten better power management from that, but my concern is the video card. I have an ATI Mobility X1600 using the open source driver. I've tried to follow these instructions, but I get an error in terminal saying that the power_mode file doesn't exist, and I cannot create one manually. My guess is that KMS isn't enabled in my kernel since it's the standard one that comes with Ubuntu (3.2.0-24-generic). I found another method to enable power saving on my card using xorg.conf, however the log shows that the driver just ignores those options.

```
Section "Device"
    Identifier "Configured Video Device"
    Option "DynamicPM" "on"
    Option "ClockGating" "on"
EndSection

```
Powertop shows my graphics card usage is 100% all the time, however the suggested tweak for it has been enabled by laptop-mode-tools (and powertop lists the entry for the card as good).

Now I'm thinking there's pretty much two answers to what's going on here; either the dynamic power scaling isn't supported by the RV530 driver or there's another way to get this working that I haven't been able to find. What I would like to have happen is the GPU usage be scaled / automatically clocked up and down with demand. Catalyst drivers aren't an option as the X1600 support was dropped a while ago, and the older drivers only work on 8.something, which I'm not really trying to roll back to.

Thanks a lot! Please let me know what my options are, either way.

---

