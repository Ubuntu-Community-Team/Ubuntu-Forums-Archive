---
title: "ATI HDMI troubles..."
date: 2008-11-28
forum: Hardware
---

### Post by chaotix on 2008-11-28
Hello,

I have a problem with my ATI 2400 HD card that is driving me nuts...

The card has three connectors (HDMI, VGA and DVI). When I installed Mythbuntu 8.04 I couldn't get the HDMI output to work with the fglrx driver so I used a DVI to HDMI connector. Everything worked fine.

When I upgraded to 8.10 I gave the HDMI connector another shot. It still wouldn't work with the fglrx driver at first, but I tried the radeonhd driver and everything worked fine. Even audio via HDMI. Well, nearly everything. As I found out the radeonhd driver does not support XVideo yet. Neither does the regular radeon driver. So back to fglrx it was.

But as I didn't want to give up I tried to get HDMI working with the  glrx driver again. And with Option "ForceMonitors" "tmds1" in xorg.conf it actually did. Unfortunately the picture was not in the center of the screen. It was a bit to the left, so the left border was cut of and I had a black bar at the right. After searching around I found a possible solution:

aticonfig --set-dispattrib=tdms1,positionX:0
aticonfig --set-dispattrib=tdms1,positionY:0
aticonfig --set-dispattrib=tdms1,sizeX:1920
aticonfig --set-dispattrib=tdms1,sizeY:1080

Well, as it seems, this was not the right solution for me, because at the next X server start the computer crashed. And it now always crashes when starting X except when I specify Option "ForceMonitors" "notmds1" in xorg.conf. But this disables HDMI again.

How can I reset those values? If X is started with notmds1 I cannot access or set the dispattrib values with aticonfig.

radeonhd is still working fine (except no XVideo which results in about 5 frames per second videos). But as soon as I use fglrx without notmds1 the whole box crashes without a trace in the syslog.

Does anybody have any idea how I can get reset the ATI card to its default values?

Thanks for your input,
Lars

---

### Post by dsm iv tr on 2008-11-28
rm /etc/ati/amdpcsdb

Will remove the config database the driver uses. fglrx will build a new one in the same spot the next time XOrg starts.

---

### Post by chaotix on 2008-11-29
> **dsm iv tr said:**
> rm /etc/ati/amdpcsdb

Will remove the config database the driver uses. fglrx will build a new one in the same spot the next time XOrg starts.

Thanks a lot. Now it actually works. No HDMI audio and still tearing issues, but hey, at least it's usable.

Thanks,
Lars

---

