---
title: "How can I choose an X11 configuration at startup?"
date: 2009-04-08
forum: Hardware
---

### Post by Bobnox on 2009-04-08
I have Intrepid running on a macbook 3.1. When home, I use dual monitors, but when I travel, I just use the laptop.

The xserver settings don't adjust automatically when I unplug the 2nd monitor. It kind of works but the xserver resolution is too big. Going from just the laptop to 2 monitors doesn't work at all.

So I have 2 xorg.conf files, one for dual monitors, and one for just the laptop. The actual xorg.conf is a softlink to the appropriate configuration. This works, but I don't know of a way to pick a configuration on boot-up. Does anyone know of way to specify the xorg.conf file to use, or can I do this with a script that creates the softlink before starting the Xserver?

---

### Post by Sam Lars on 2009-04-09
I also switch between configurations.
The X server in Jaunty has some interesting changes... it seems to change its resolution based on what it detects as connected.  When I have my external monitor plugged in, it automatically adjusts the resolution to nicely clone on both.
I've ended up writing some scripts for things that depend on the resolution, like AWN, to change their settings based on what the monitor configuration is.
I also wrote a script that restarts my resolution-dependent programs and then changes the resolution to large or small, depending on what it detects is the current resolution.
I use xrandr to determine what the current configuration is, and to set the resolution.
My Xorg.conf is the default, I haven't changed anything in it.  I just use xrandr to change the resolution as necessary.
When I get back to my laptop I can share the xrandr commands if you would like to see them.
I'm not sure xrandr would work before X starts, but there may be some way to detect if your second monitor is plugged in and link the X configuration accordingly.

---

### Post by Bobnox on 2009-04-10
Thanks Sam. Those scripts may help. Before I trouble you for the scripts and understanding how you use them, I'm curious what other approaches there may be.

It seems to me that since I have 2 working xorg.conf files, it'd be simpler to just run a script before X starts to link to the correct one. I'm just not sure at what point in the boot-up process a script could be run to do this. Maybe I could default to one configuration in grub, and allow a time to choose the other, if it's possible to execute a script from within grub.

---

### Post by Sam Lars on 2009-04-10
I'm not sure how you'd get it to run from Grub, and I'm not sure what command would get you the right info before X starts.
Could you back up your Xorg.conf and make a new clean one?  X is really supposed to do the detecting of monitors and changing of resolution on its own... so if it will do something of that, maybe with as little in the Xorg.conf as possible, then that would be good.
What I would try is running a script either manually or automatically after you log in that would make the necessary changes based on whether you have a second monitor attached.

---

