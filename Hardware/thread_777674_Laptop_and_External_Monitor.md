---
title: "Laptop and External Monitor"
date: 2008-05-01
forum: Hardware
---

### Post by rshol on 2008-05-01
I have posted this question each time after downloading and installing the last three ubuntu releases.  I have Ubuntu 8.04 x86_64 running and happy on my Dell Latitude D820 laptop with the non-free nvidia drivers.  I would like to use it with the 22 inch dell flat screen monitor attached to my docking station, but as with each release previous tho 8.04, when I boot the laptop in the docking station the attached screen blanks and goes into power saving mode when X starts.

Kudos to Ubuntu for making suspend to RAM work out of the box on my laptop (my other big complaint) but how, for the love of all things penguin, can I use my external monitor with my laptop?  Where is the auto-config goodness of xrandr this release was supposed to bring?

---

### Post by TubaTodd on 2008-05-02
Ok, I'm not sure this will FIX your problem but it is worth a shot. First check your BIOS setting to make sure you have the video output set correctly. Now, I did not have a problem getting the video to appear on my 22" monitor, but I did have some display issues. The following code can be put in a script. It will tell X windows to use your external monitor as primary and disable the laptop display when connected. If the external monitor is not connected, the laptop screen is set to primary

```

#!/bin/bash

if xrandr -q | grep -q "VGA"
then
  xrandr --output LVDS --off
fi

exit 0
```

If you are connected with DVI, I believe you just have to replace "VGA" with "DVI" Good luck.

---

### Post by rshol on 2008-05-03
Thanks for the response.  Where should I put the script (or a link to it) so that things work correctly on boot?

---

