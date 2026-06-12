---
title: "External monitor with laptop"
date: 2007-09-28
forum: Hardware &amp; Laptops
---

### Post by MaximusTG on 2007-09-28
I'm thinking of buying a 19" widescreen tft (acer al1916was to be precise) which has a resolution of 1440x900. This monitor is going to be used with my laptop, an Acer 3680 with 1280x800 screen. It uses the i810 driver with the 915resolution package. Before I buy the monitor, I was wondering if it is "easy"  to set this up. I would like it (ideally) to be hotpluggable, but if I have to run a script to switch, that would be acceptable too. I don't require a dual monitor desktop, it should just be a clone of the laptop screen (at a higher resolution of course).

---

### Post by MaximusTG on 2007-09-28
I've been doing some more research, but I can't find a simple answer anywhere.. I've installed the "intel" driver, so I don't need 915resolution anymore, so that isn't an obstacle anymore. 
But I can't find a guide on how to install an external tft display to a laptop, at another resolution. In clone mode. Anyone?

---

### Post by peabody on 2007-09-28
**Update: just in case someone comes across this post, I have switched to the intel driver and use the xrandr program to extend the desktop.  Xinerama is dying at least on the intel driver, xrandr's the future.**

I didn't know that it was actually possible to have a clone at a separate resolution.  I thought the whole point of a clone was that it was a complete copy of the display.

I had trouble with the doing a clone or extended desktop with the intel driver.  I had to stick with the 915resolution package using the i810 driver and these directions: [http://ubuntuforums.org/showthread.php?t=361124](http://ubuntuforums.org/showthread.php?t=361124)

I tried them with the intel driver, but the server kept segfaulting for me.  Perhaps you'll have better luck.

---

### Post by Glycerine on 2007-09-28
I managed to use a higher resolution on an external monitor from my dell d600 using the "ati" driver shipped with fiesty.  Don't have the posts i followed handy, but for the ati driver, the relevant bits of xorg.conf are below.

Under vid card section:
```

 Option          "MonitorLayout" "LVDS,CRT"
 Option          "MergedFB" "true"
 Option          "CRT2Position" "Clone"
 Option          "MonitorLayout" "LVDS,CRT"
 Option          "MergedFB" "true"
 Option          "CRT2Position" "Clone"
 Option          "MonitorLayout" "LVDS,CRT"
 Option          "MergedFB" "true"
 Option          "CRT2Position" "Clone"

```

And i was just sure to put the resolution of the external monitor only in the screen section.  (laptop permanently in a docking station)

---

### Post by MaximusTG on 2007-09-28
Hmm, I really don't know too much about xorg.conf adjustments, hoping someone can enlighten me a bit on how this would practically work. If I were to boot with a display attached, would that be automatically recognized? From what I have read about the intel driver, that should work. However, I would probably be using the monitor in a more hotplug way. So, is it possible to activate an external monitor if you have already booted? Restarting the X server would be acceptable for me. Maybe a solution using a script to switch xorg.confs of some sort? 

Really hoping someone can shed some light on this. I'm planning to bundle all my findings on this matter in a the Tutorial&Tips section, when its working that is ;)

---

### Post by devliljohn on 2007-09-28
i have an asus z96j laptop and i plug in my 21 inch monitor at home. the way i got it to work was boot up and install the ati control panel to clone the desktop on to my external monitor. then a simple ctrl alt backspace to restart X and it works. keep in mind that both my laptop screen and my 21 inch external monitor are both 1680 x 1050, cloning will only work when both devices are at the same resolution so if you want to run the external monitor at a high resolution then you will have to turn your laptop screen off.

---

### Post by MaximusTG on 2007-09-29
Okay, but an Intel card obviously doesn't have a ATI control panel. As for turning the laptop screen off ( or having it display a clone at a wrong reso) doesn't matter to me. I would be using only one screen at a time. 
However, I read that Gutsy will have support for hotplugging of monitors (something to do with RandR 1.2) so I'm  going to try this with the live cd and my parents tft monitor (which is 1280x1024) tonight (european timezone :P)

Oh, and I also found these sites, they explain some more:

[http://budlite.blogspot.com/2007/09/hotplugging-secondary-display-on-linux.html](http://budlite.blogspot.com/2007/09/hotplugging-secondary-display-on-linux.html)

[http://burtonini.com/blog/computers/randr-2007-02-06-17-50](http://burtonini.com/blog/computers/randr-2007-02-06-17-50)

[http://www.thinkwiki.org/wiki/Installing_Ubuntu_6.06.1_on_a_ThinkPad_R60e#Ubuntu_7.10_with_Intel_Graphics_Media_Accelerator_950](http://www.thinkwiki.org/wiki/Installing_Ubuntu_6.06.1_on_a_ThinkPad_R60e#Ubuntu_7.10_with_Intel_Graphics_Media_Accelerator_950)

---

### Post by MaximusTG on 2007-09-30
It works! I didn't have time to test it on my parents tft, but I did test it with an 17" crt monitor

Using the script provided in one of the links in my other post, it could easily switch between my laptop screen (at 1280x800) and the crt monitor ( at 1024x768 ). Without restarting X!

This is the script (by Ross Burton) that I used (and changed resolutions according to my sitiuation)

```
if xrandr -q | grep -q  "VGA connected"; then
  xrandr --output LVDS --off --output VGA --mode 1680x1050
else
  xrandr --output VGA --off --output LVDS --mode 1024x768
fi
```

If your external display has a larger resolution than the internal, and you want to plug it in to your laptop after booting, you should add a line such as this:

```
Virtual 1440 900 
```

to the subsection display of section screen in your xorg.conf

This will work out-of-the-box in Gutsy (with the intel driver at least, not sure about others)

For Feisty,you can install Ross Burton's repository :
```

echo deb http://burtonini.com/debian/ feisty/|sudo tee -a /etc/apt/sources.list
sudo apt-key advanced --keyserver subkeys.pgp.net --recv-keys 0x510E0293

```

The neccesary updates will then appear in your update-manager

---

### Post by peabody on 2007-10-01
Maximus I could kiss you :).  This works great.  I don't have to run that hacky multiple xorg.conf files anymore!  Just a couple of things though.

I tried adding a virtual desktop section to my xorg.conf subsection display for 1280 1024.  That didn't seem to work though.  I have a widescreen laptop which runs at 1280x800.  When I turn on the VGA monitor, my laptop screen went to 12800x1024, but it wouldn't move the viewport when I moved the mouse down to the bottom of the screen, so the laptop's screen is effectively cutoff when running an external monitor.

Also, I tried to get a dual setup running via the instructions in one of your links (here specifically [http://budlite.blogspot.com/2007/09/hotplugging-secondary-display-on-linux.html](http://budlite.blogspot.com/2007/09/hotplugging-secondary-display-on-linux.html)).  However, everything I tried just caused xrandr to segfault.  Any advice?  I tried a Virtual Desktop of 2560 1824.

For the most part though I love this.  It's a much better setup than my last one and it was easy to get up and running too!  This makes me look forward to gutsy, so much promise!

**Edit: Got it working.  It's finicky.  It doesn't really want to go back to using one screen once setup, but it's promising!  Hopefully it'll be fixed in Gutsy.  The intel driver has a hardware limitation in which it can't accelerate a viewport with either dimension greater than 2048.  A clever way to get around this limitation is to place the screens on top of each other (most combined resolutions on the vertical axis won't be greater than 2048 ).  Don't forget to add the Virtual section to the Subsection under the display in xorg.conf.**

---

