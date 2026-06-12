---
title: "Dell XPS 13 Dev 9360 - Track Pad Issues"
date: 2017-12-20
forum: Hardware
---

### Post by devnull3 on 2017-12-20
Hi Folks,

A while back I purchased a Dell XPS 13 Dev Model 9360 - Ubuntu 16.04 LTS  (no windows dual boot or partition, strictly running Ubuntu). I had  some issues with the Track Pad (as did many others with the same model).  The problem is that the track pad becomes unresponsive, flickers, and  jumps around. It was suggested to upgrade the firmware, which I did,  with no luck. I was told by Dell tech support that they are aware of the  issues and are currently working with Ubuntu devs. They suggested that  it may be an issue with Unity and GNOME is much better at handling this.  I have since upgraded to Ubuntu 17.10 running GNOME and still  experiencing issues with the track pad.

The following is a list of what I have done to no avail:

Current BIOS: Version: 2.4.2
-blacklisted psmouse
-installed xserver-xorg-input-libinput (this actually seemed to help the most)

I have tried entering the following in /etc/X11/xorg.conf.d/50-synaptics.conf

Section "InputClass"

        Identifier  "disable duplicate touchpad"
        MatchProduct "SynPS/2 Synaptics TouchPad"
        Option "Ignore" "on"

EndSection


Section "InputClass"
        Identifier "libinput touchpad catchall"
        MatchIsTouchpad "on"
        MatchDevicePath "/dev/input/event*"
        Driver "libinput"
        Option "Tapping" "True"
        Option "PalmDetection" "True"
        Option "TappingDragLock" "True"
EndSection

---------
So far none of this has had a significant effect. The track pad works  really well sometimes and other times it is completely unresponsive.

Not sure if this will be addressed/resolved when Ubuntu 18 comes out  later next year, but does anyone have a permanent solution for this or  is there another option I could try?

Thanks!

---

