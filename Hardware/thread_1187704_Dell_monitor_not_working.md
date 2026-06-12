---
title: "Dell monitor not working"
date: 2009-06-14
forum: Hardware
---

### Post by xarhelios on 2009-06-14
Well, ever since I updated to Intrepid, my Dell 15" UltraSharp monitor would not boot into GDM, but would display the message "Cannot Display This Video Mode." I found that my resolution had been set to 1680x1050 on a 1024x728 display, and it was not happy. So, i hooked it up to another monitor (this one happened to be 1680x1050), and changed the resolution to the appropriate one.

After this, I rebooted my computer and instead of booting into GDM, I was given a black screen with a flashing underscore in the top left corner and, frankly,  I'm stumped. 

It would also be worth mentioning that I am having a problem with my CD/DVD drive so anything requiring a live CD is going to be a problem.

Thank you in advance, 
xarhelios

---

### Post by xarhelios on 2009-06-15
So, it turns out that the flashing underscore was there because my system was trying to boot into Saving Private Ryan on DVD. Something now tells me that my cd drive isn't as messed up as I thought.

Anyway, I still could not boot into GDM and was greeted with the message, "Cannot Display This Video Mode." I will try to switch monitors and reset the resolution, but is there a way I can do this permanently? What would I need to edit on my xorg?

---

### Post by xarhelios on 2009-06-15
I found this:

```
  Horizontal Resolution:   1024 
  Vertical Resolution:      768 
  Vertical Refresh Rate:   60.00 Hz 
  Horizontal Refresh Rate: 47.80 KHz 
  Dot Clock Frequence:     60.80 MHz 

 # HorizSync 42.0 - 52.0 
 # VertRefresh 55.0 - 65.0 
 Modeline "1024x768" 60.80  1024 1056 1128 1272   768  768  770  796 

```

If I paste this into my xorg under Monitor, will it work? Or will I need to configure something else?

---

