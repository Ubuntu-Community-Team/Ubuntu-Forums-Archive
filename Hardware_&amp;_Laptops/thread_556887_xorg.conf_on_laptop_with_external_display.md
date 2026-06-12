---
title: "xorg.conf on laptop with external display"
date: 2007-09-21
forum: Hardware &amp; Laptops
---

### Post by frone on 2007-09-21
Hope I'm posting in the right area...

I have a laptop computer running Feisty (display looks great on clamshell) with an external LCD screen that is showing some faint, but noticable horizontal flashes.

I'm certain that I have a problem with the refresh rates I am allowing as the GUI setup only has the option of 75% and the screen calls for 60%.  I'm new to editing the xorg and was hoping someone can help me create the proper entries.  I know it has something to do with the 'monitor' section, but that's about the bulk of my knowledge.  I don't need dual display either, really just the external display.  The clamshell will be closed as the external just runs through the screensaver.  Have done a bit of leg-work and can give the specs for both devices as follows:

computer:  max res of 1024x768 at 16.8 million colors, refresh rate of 60Hz

LCD screen:  30~85 KHz(H) / 50~80Hz(V)    Max. 1360x768 @60Hz

Interesting note (I think) The LCD says it supports 1024x768 at 75Hz or 60Hz...

Hope this helps - will be glad to provide any other needed info...

---

### Post by dcstar on 2007-09-22
> **frone said:**
> Hope I'm posting in the right area...

I have a laptop computer running Feisty (display looks great on clamshell) with an external LCD screen that is showing some faint, but noticable horizontal flashes.

I'm certain that I have a problem with the refresh rates I am allowing as the GUI setup only has the option of 75% and the screen calls for 60%.  I'm new to editing the xorg and was hoping someone can help me create the proper entries.
..........

Easiest thing may be to save the original xorg.conf file and then do the following:

Install the **discover1** and **xresprobe** packages, then in a terminal (with the external monitor connected), do:

```
sudo dpkg-reconfigure xserver-xorg
```

and let it detect the monitor and set up a new xorg.conf file with all the correct settings.

Then, if you like, you can cut-and-paste any settings from the original into the new so both monitors are supported.

---

### Post by frone on 2007-09-22
David -

Thanks for the advise.  I will give this a shot and report back - should be able to test this sometime this week...

Thanks again!

---

