---
title: "limited resolution on ASUS vh222h"
date: 2009-07-07
forum: Hardware
---

### Post by Techmobowl on 2009-07-07
I recently upgraded to an ASUS widescreen monitor.  I am unable to get it to run at full 1920x1080 resolution in Ubuntu, instead I'm stuck at 1440x900.  My pc is dual booted and I can get full resolution in winXP.  I tried manually setting the display to 1920 1080 in xorg.conf but no luck.

For winXP I had to tell the driver that I the signal was formatted HD North America (or something like that).

---

### Post by shatterblast on 2009-07-07
What video card type do you use?  If you use nVidia, then you can set the resolutions separately through its configuration software.  You can access it through:

System -> Administration -> NVIDIA X Settings

There after, you could just visit the Display Configuration part and then choose Detect Displays.  ...But that's all assuming you have nVidia.

---

### Post by Techmobowl on 2009-07-08
I've been using the nVidia X-config utility.  The highest res it detects for my display is 1440x900.  (GeForce fx5500)

I checked back in XP, under the nVidia control panel.  I have to tell it to run as an HD display, 1080p format.  Is this a format that nVidia does not have under their X-server utility?

Thanks for your help, I'm going to google "linux 1080p"

This looks promising...
[http://ubuntuforums.org/archive/index.php/t-425527.html](http://ubuntuforums.org/archive/index.php/t-425527.html)

---

### Post by shatterblast on 2009-07-08
The best solution would be probably updating your video drivers then if possible.  nVidia has a history of putting the basics into a Linux driver first and then adding features as time goes on.  This includes monitor resolutions, and I've gone through the issue as well.

I would recommend installing "envyng-qt" from Synaptic.  It can be found under:

System -> Administration -> Synaptic

The Jaunty version of EnvyNG should be enough, but in case you aren't running that version, here is a link.

[http://packages.ubuntu.com/jaunty/envyng-qt](http://packages.ubuntu.com/jaunty/envyng-qt)

---

### Post by Techmobowl on 2009-07-08
Option "UseEdidFreqs" "false"
Option "ModeValidation" "NoMaxPClkCheck, AllowNon60HzDFPModes, NoVesaModes, NoXServerModes, NoPredefinedModes"

I added these two lines to xorg.conf as discussed in the post I linked to.  Now I have beautiful 1920x1080p for my ubuntu desktop.  Victory!

---

### Post by shatterblast on 2009-07-09
Congratulations!

---

