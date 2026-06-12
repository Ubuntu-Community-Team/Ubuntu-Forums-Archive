---
title: "External monitor resolution limited by intel laptop lcd"
date: 2009-08-07
forum: Hardware
---

### Post by veromarybr on 2009-08-07
Hi,

I'm wondering if I have a bug here.  I've been trying to increase the resolution on a big external monitor when using the laptop at home.  

The laptop is 1024x800, the monitor I'm trying to use at 1600x1200.
The video card is an Intel 855 onboard graphics thing.

The default jaunty gui way tries to make a big virtual screen encompassing both screens adding some lines to xorg.conf - something like:
    SubSection "Display"
        Virtual       2624 1200
    EndSubSection

and asks to restart X and when I log in I get a white screen with a blue 
horizontal stripe just left of centre.  There is some response from the 
mouse with grey squares appearing erratically, but totally unusable.
This is when I found that Ctrl-Alt-Bkspace had been disabled in Jaunty.

So reset the xorg.conf file with xfix and tried:

disabling dri, acceleration, tiling(whatever that is)
Turning off extra animations.
tried using the xorg-edger's version of xorg-xserver-video-intel which
gave a black screen and white cursor to wave around with the mouse.
Tried scaling back the Virtual Screen to 1600 1200 which gave the most promising
results.  Could get the laptop and crt to both display side by side.

But the laptop's owner would like the lcd off and crt take over when vga
plugged in.

I've installed i810switch which switches off the laptop screen fine.

But haven't found a way to get the crt to take over satisfactorily.

Dug into xrandr and what I want is:

xrandr --output LVDS --auto --output VGA --mode 1600x1200 --same-as LVDS

but running this crashes X with a flickering green screen on the crt.

I'm thinking this is an intel driver bug.  I haven't logged a bug before 
so thought it wise to run it by the forums that I've been dredging for
ideas for some hours today.

Right now I'm back on my own eeepc - tried out that xrandr line with a monitor
plugged into the eee and it works fine.  This one's an Intel 915GM/GMS/910GML.
Also my eee runs debian with xorg-video-intel version 2:2.3.2-2.

Tomorrow I'll try assemble all the stats off the troublesome laptop -
Centoris Optima I think an Australian variant.  

Do you think I have a bug?

---

### Post by veromarybr on 2009-08-07
Is the weekend a bad time to get a response on this?

---

### Post by hackerseraph on 2009-08-14
bump

---

