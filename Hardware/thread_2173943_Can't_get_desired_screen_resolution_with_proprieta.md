---
title: "Can't get desired screen resolution with proprietary ATI driver on 2008 iMac / 12.04"
date: 2013-09-12
forum: Hardware
---

### Post by Mx83HNG on 2013-09-12
I have a fresh install of 12.04 LTS on this iMac:

[http://www.everymac.com/systems/apple/imac/specs/imac-core-2-duo-2.8-24-inch-aluminum-early-2008-penryn-specs.html](http://www.everymac.com/systems/apple/imac/specs/imac-core-2-duo-2.8-24-inch-aluminum-early-2008-penryn-specs.html)

The video performance was abysmal, so I thought I'd update to the proprietary ATI Radeon driver, which I found here:

[http://www.amd.com/la/products/desktop/graphics/ati-radeon-hd-2000/hd-2600-pro/Pages/ati-radeon-hd-2600-pro.aspx](http://www.amd.com/la/products/desktop/graphics/ati-radeon-hd-2000/hd-2600-pro/Pages/ati-radeon-hd-2600-pro.aspx)

After installing the proprietary driver, the graphics performance is improved somewhat, but the screen resolution is fixed at 1600x1200, whereas the original and desired resolution is 1920x1200.

A steep learning curve, mostly about xrandr and xorg.conf, ensued.  Here is the output of xrandr:

```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1600 x 1200, current 1600 x 1200, maximum 1600 x 1200
default connected 1600x1200+0+0 0mm x 0mm
   1600x1200      61.0* 
```

If I go through all of the steps of xrandr --newmode, --addmode, and --output, I get an error message saying "screen can't be larger than 1600x1200"

I tried manually adding the "Virtual" line to xorg.conf. If I set it to 1920x1200, I get total chaos and have to use recovery mode to restore the previous xorg.conf.  (Just for an experiment, I tried setting "Virtual" to 3200x1200, and got a strange compressed scrollable screen that was twice as wide and half as high as my actual screen.)

I tried various other edits to xorg.conf, but none of them had any effect.

I'm about to give up and restore the open-source driver, but I'd REALLY like to keep using the proprietary one if I can because the graphics performance (especially things like CSS animations) were totally unacceptable with the original driver.

Any suggestions?

---

### Post by Mx83HNG on 2013-09-13
...Anybody? :(

---

### Post by Mark Phelps on 2013-09-13
Sorry, but you're stuck using an old AMD driver that they stopped support for over a year ago -- meaning, there will be no improvements or upgrades to it.

IF it doesn't work as is, you're stuck with the max resoultion that Xrandr allows.

---

### Post by Mx83HNG on 2013-09-15
Thanks for the reply Mr. Phelps!

...rolling back to the open-source driver with a heavy heart then...:(

---

