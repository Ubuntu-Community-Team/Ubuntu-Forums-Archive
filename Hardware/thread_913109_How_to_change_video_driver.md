---
title: "How to change video driver?"
date: 2008-09-07
forum: Hardware
---

### Post by fdimmling on 2008-09-07
The Acer Travelmate 291LCi of my wife running Ubuntu 8.04 freezes on shutdown and even on logout most of the times. It has an Intel 855 graphics adapter. I would like to exchange the intel video driver in favor of the i810 driver. 
In earlier brands of Ubuntu there was a lengthy xorg.conf with a line 

Driver "intel"

in the Device section. Now you only have a single

 Identifier      "Configured Video Device"

entry.

How or where can I set the video driver. Despite some Google search I could not find the appropriate place to make the chanche.

Friedrich

---

### Post by overdrank on 2008-09-07
> **fdimmling said:**
> The Acer Travelmate 291LCi of my wife running Ubuntu 8.04 freezes on shutdown and even on logout most of the times. It has an Intel 855 graphics adapter. I would like to exchange the intel video driver in favor of the i810 driver. 
In earlier brands of Ubuntu there was a lengthy xorg.conf with a line 

Driver "intel"

in the Device section. Now you only have a single

 Identifier      "Configured Video Device"

entry.

How or where can I set the video driver. Despite some Google search I could not find the appropriate place to make the chanche.

Friedrich

Hi and you can try and use the command ```
gksu displayconfig-gtk
```
and set the driver there. If it fails then you can reboot into recovery mode and use the xfix option to restore the GUI. Also on a side note how much memory is shared with the intel graphics as you may be able to adjust the amount in bios to increase the performance.

---

