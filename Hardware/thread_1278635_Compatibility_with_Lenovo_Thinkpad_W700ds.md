---
title: "Compatibility with Lenovo Thinkpad W700ds"
date: 2009-09-29
forum: Hardware
---

### Post by ElijahLynn on 2009-09-29
Hey gang,

I have been putzing with Ubuntu for the past 2 years and am gearing up to buy a new laptop soon. One of my "must have" requirements for a laptop is a "touchstick", ya know, instead of the touchpad.

Anyways, I would buy a System 76 because it would "just work" but they do not offer this. I would also buy a Macbook Pro since I could run Final Cut Pro but they to do not have touch sticks (who wants an efficient computer when you can have a pretty one, right?)

So, I came across the Lenovo Thinkpad w700ds laptop the other day and it is a beauty! Something I could really see living with for the next 5 years. I am curious to see if you guys think I could get everything working with this, I searched the forums but no cigar.

It has a wacom tablet, pantone color calibration, dual screen and much more. Here is the link. I wish Ubuntu was treated first class, this is a dream machine and if I could use Ubuntu + Openshot, I would have a pretty good mobile video editing workstation. I wouldn't mind migrating away from Final Cut Pro over the next 5-10 years in favor of Linux and all of it's cool tools!

Here is the link to the specs for the laptop.

[http://shop.lenovo.com/us/notebooks/thinkpad/w-series/w700ds]("http://shop.lenovo.com/us/notebooks/thinkpad/w-series/w700ds")

---

### Post by Coder543 on 2010-01-12
*bump*
sorry for the late reply, but i would be very interested to know how ubuntu handles that pop out second monitor in real time. Anyone know?

---

### Post by ChazKato on 2010-01-15
I just installed 9.10 on my W700ds this morning.  Out of the box the monitor is supported... sort of, the one issue is that it won't let me rotate the monitor in the Display Preferences GUI.  As a result it is rather unusable because it registers it as a normal 1280*768 monitor.  How do I go about rotating the monitor.  The rotation option shows up when I select both the 17 and 11 inch monitors but the only selection available is "Normal".

On another note, if any one is interested.  The built in tablet also is sort of working.  I can move the cursor with it but it does not recognize right or left clicks.  I'm not as concerned about that since I don't really use it.

---

### Post by Favux on 2010-01-15
Hi ChazKato,

Welcome to Ubuntu forums!

Usually the ThinkWiki is the best resource (but a little sparse for your model):
[http://www.thinkwiki.org/wiki/Category:W700ds](http://www.thinkwiki.org/wiki/Category:W700ds)
[http://www.thinkwiki.org/wiki/Category:W700](http://www.thinkwiki.org/wiki/Category:W700)
Likely many issues are addressed on other pages.

> the one issue is that it won't let me rotate the monitor in the Display Preferences GUI.
It may partly depend on what video chipset you have and your current driver for it.  See the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1").
> The built in tablet also is sort of working. I can move the cursor with it but it does not recognize right or left clicks.
It's probably a serial Wacom tablet so you just need to install the appropriate .fdi and then use wacomcpl (wacom control panel) to configure the stylus buttons.  See the [LinuxWacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

Hope this helps.

---

