---
title: "dual monitors on HP zv6000 for presentations"
date: 2007-07-28
forum: Hardware &amp; Laptops
---

### Post by OneSeventeen on 2007-07-28
I've got an HP zv6000 laptop and I'd like to send video out the back VGA port so I can do a presentation with my compiz-enabled laptop.

I just want to have the same thing I see be sent out to the projector, not like I want to run dual monitors.

I don't mind just switching between the two monitors.  Any tips?

---

### Post by jonathanmotes on 2007-07-28
I was able to do this once without on a HP dv2000 laptop any problems using the nVidia control panel. Run it by hitting ALT + F2 and typing "nvidia-settings" (without quotes). I don't recommend trying separate X screens or allowing any changes to the X configuration file - I lost my main screen and had a hard time getting it back. 

This worked for me:
Choose "X Server Display Configuration"
Plug in the second screen if its not already
Click "Detect Displays" then click on "Configure..."
I believe I chose "Clone screens" or "Twin view" - I don't remember having to restart X - I wouldn't choose anything that does. 

Hope this helps. Let me know how it goes!

---

### Post by OneSeventeen on 2007-07-29
Unfortunately the zv6000 uses an ATI Radeon Xpress 200m chip :(

I guess I shouldn't bash ATI cards too much anymore considering compiz works beautifully on this 2 year old computer.

**EDIT** I would be willing to purchase any add-on cards/devices that might help this, as long as they are reasonably priced (around the $100 range or less).

Any tips?

---

### Post by OneSeventeen on 2007-07-30
Rewording the question:

How can I force all video to go to the external display rather than the internal?

Maybe that is the best solution, since I want to conserve processing for the presentation anyway.

Because I'm using the proprietary/binary ATI drivers, things like MergedFB and Xinerama won't work.  I'm hoping I can just write an xorg.conf file that I can pass commands to on startup to choose "presentation mode" that will set my resolution to 1024x768 and set the video device as the external port on the laptop.  Otherwise, have it use the current setup (1280x800 on the laptop screen)

Any tips?

---

### Post by buntunub on 2007-07-30
You can try ati-config to see if there is anything like that preloaded, but if not, at least in Sabayon, I know there is an ATI control panel. So there must be something in the repo's for that somewhere...

---

### Post by OneSeventeen on 2007-07-31
Well, apparently I'm dumb.
[list=1][*]Plug in External Monitor
[*]Restart X (or start up computer)
[*]Enjoy better mirrored output than Windows offers[/list]

It even shrinks the video to fit on-screen.  (So my laptop's 1280x800 looks good on the laptop and is squeezed into 1024x768 on the monitor, still looking good though)

---

### Post by Beuntje on 2007-08-10
Check out this post to make your laptop autodetect displays at boot.

[http://ubuntuforums.org/showthread.php?p=3167545#post3167545](http://ubuntuforums.org/showthread.php?p=3167545#post3167545)

---

