---
title: "RandR cannot be disabled with catalyst"
date: 2011-06-13
forum: Hardware
---

### Post by graylion on 2011-06-13
Hi guys

I just installed a HD6950 in my system. My two screens are in clone mode and do not let themselves be convinced to do anything else. With a bit of googling I found [this old thread]("http://ubuntuforums.org/showthread.php?t=1137576") where it is recommended to turn RandR off:

Re: remove xrandr 1.2 and let ati setup my screens
I ran into the same problem last week and was just trying to remember how I did it because a coworker wanted to know. So for your and his benefit...

Edit /etc/ati/amdpcsdb
In the section labeled [AMDPCSROOT/SYSTEM/DDX]
add this:
Code:

EnableRandR12=Sfalse

Also, in /etc/X11/xorg.conf in the "Device" section add:
Code:

Option      "EnableRandR12" "false"

I did this, but when I type aticonfig --query-monitor

I get:

Error: option --query-monitor is not supported when RandR 1.2 is enabled!

even though the disable option actually is in both config files. And yes I have rebooted ;)

help?

I am pretty sure that RandR is what disables my Catalyst from controlling the displays. but how do I get rid of it?

Thanks all

---

