---
title: "Intel xrandr dual monitor crashes X"
date: 2015-11-06
forum: Hardware
---

### Post by reakter on 2015-11-06
Hello everyone,
I'm having an issue where my Xubuntu 14.04 system is suddenly crashing X completely when I try to enable my second monitor. By completely, I mean upstart doesn't even restart lightdm when X crashes. I have been doing this just fine for the past year, this issue cropped up approximately a week ago. What gives?

Here's a paste of the Xorg.0.log.old: [http://pastebin.ubuntu.com/13125064/](http://pastebin.ubuntu.com/13125064/)

Here's the /var/log/lightdm/lightdm.log.old: [http://pastebin.ubuntu.com/13125104/](http://pastebin.ubuntu.com/13125104/)

Here's my hardware: [http://pastebin.ubuntu.com/13125176/](http://pastebin.ubuntu.com/13125176/)

I'm connecting this second monitor via my displayport, the laptop screen is eDP1 and the external monitor is usually DP1, DP2 or DP2-1. I've tried a number of different things, even compiling my own Intel graphics drivers with checkinstall but no luck. I've reverted everything back to standard. Any ideas?

---

