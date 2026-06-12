---
title: "NVIDIA X-Server Auto-detect External Displays"
date: 2010-11-26
forum: Hardware
---

### Post by SeanInSeattle on 2010-11-26
Can someone help me to configure Ubuntu 10.04 to automatically detect and switch to a either a saved or a new X-Server configuration that includes those monitor(s)?  

My situation is that I have external monitors that I use at work I have my NVIDIA X-Server configured to extend my desktop to those monitors, but when I take my laptop mobile it can't extend to monitor(s) that doesn't exist. It would be really cool to get it to set the configuration automatically.  

Any help is much appreciated.

---

### Post by botbender on 2011-03-21
I totally agree, I have the same problem.

At home the laptop has an external display, and I have configured the Nvidia X server settings applet to extend the desktop onto the external monitor and saved the xorg.conf.

But when the laptop is mobile and starts without the external display, dual display mode is still active and it is very easy to lose the pointer off the edge of the screen. Essentially every time I start the laptop without the external monitor I have to launch the settings applet and make a change (any change, just so the Apply button does something - I change the resolution field to something else, then reset it), click Apply, then quit the setting applet without saving the xorg.conf. Then the mode is set to single display until the next X server start.

total pain for what is pretty basic and normal laptop use. Anyone got any suggestions for this? Is it a nvidia proprietary thing that can't be easily fixed, and if so is there a workaround?

---

### Post by qw3rty_rocks on 2011-04-15
I have the exact same problem does anyone know the best way to fix this?

---

### Post by GaryParr on 2011-05-12
I found a solution that works for me using [Disper]("http://willem.engen.nl/projects/disper/"). This utility is meant as an easy way to enable/disable external displays and projectors but it handles this situation just as well. I use a bash script running [FONT="Courier New"]disper -d auto -e[/FONT] when my session starts and so far I'm rather happy.

---

### Post by almightybunghole on 2011-12-23
Hi,

I also have this issue, although slightly different, so not sure whether I can use disper to help. At work I have an external screen connected via a docking station, I use this as my only display whilst working. 

Whilst using the laptop away from work, I often use the machine then suspend it. If I connect it to the dock whilst suspended in this way, X never correctly starts - I suspect its unaware of the screen hardware change - and I have to hard reset the machine. Likewise if I suspend the machine on the dock, then remove it and boot, the same thing happens.

I can however (if I remember) unsuspend the machine OFF the dock, put it in the dock, then go through nvidia-settings and detect displays, select the external display, disable the internal, and close. 

This process quite a pain and am looking for a way to get the machine to do this automatically on resume. Would make my mornings substantially better!

Thanks

EDIT: Have read the disper documentation and I don't think it's going to do what I need - seems to support extending or cloning the desktop but not swapping from one display to another.

---

### Post by bregenspan on 2012-01-04
> **GaryParr said:**
> I found a solution that works for me using [Disper]("http://willem.engen.nl/projects/disper/"). This utility is meant as an easy way to enable/disable external displays and projectors but it handles this situation just as well. I use a bash script running [FONT="Courier New"]disper -d auto -e[/FONT] when my session starts and so far I'm rather happy.

This works perfectly for me (bound it to a shortcut key), thanks for posting it!

---

### Post by GaryParr on 2012-01-04
> **almightybunghole said:**
> Have read the disper documentation and I don't think it's going to do what I need - seems to support extending or cloning the desktop but not swapping from one display to another.

You may want to try it anyway as the flag [FONT="Courier New"]-d auto[/FONT] is used to detect displays, which in theory should pick up on the fact that the original display is missing and a new one has been added.

> **bregenspan said:**
> This works perfectly for me (bound it to a shortcut key), thanks for posting it!

Glad it worked for you!

---

### Post by Seq on 2012-01-04
> **almightybunghole said:**
> I also have this issue, although slightly different, so not sure whether I can use disper to help. At work I have an external screen connected via a docking station, I use this as my only display whilst working.

[...]

EDIT: Have read the disper documentation and I don't think it's going to do what I need - seems to support extending or cloning the desktop but not swapping from one display to another.

Your situation is that you have a laptop with a built-in screen, and when your secondary screen is connected you wish to only use it. Basically, you only ever use one screen.

```
disper --cycle-stages='-s : -S' --cycle
```

That should switch between using only your primary display (-s for 'single') and only your secondary (-S for secondary). Set that to a hot-key, and you should be able to toggle your display setting fairly easily.

(I have not tested this, but will when I get home)

---

