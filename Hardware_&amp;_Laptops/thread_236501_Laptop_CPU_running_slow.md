---
title: "Laptop CPU running slow"
date: 2006-08-14
forum: Hardware &amp; Laptops
---

### Post by Melcar on 2006-08-14
For some reason, my laptop's CPU always runs at 1/2 speed under Ubuntu, even when it's plugged into an outlet.  I already tried looking in Power Management but options are limited.  Is their any other power manager for laptops besides the crappy one in Ubuntu?

---

### Post by [h2o] on 2006-08-15
Mine does this as well, but I don't think it's a bad thing. Less power -> Less heat -> Longer life. I doubt that you can even notice any difference in speed from 1/2 to 1/1 during normal operation.

---

### Post by Melcar on 2006-08-15
Well, this Sempron hardly uses energy even at full 2GHz.  As for the speed difference, it is noticeable when doing CPU intensive stuff.  
I found a "fix" for it.  I downloaded kpowersave from the repos; I think it's the power manager for Kubuntu.  It lets me set "powersave" and "performance" options.

---

### Post by tribaal on 2006-08-15
If you run gnome I highly suggest you install the emitfreq-applet package, which is a nice panel applet that lets you set the CPU speed you wish to use, while it shows the CPU's temperature.

I just love it.

- trib'

---

### Post by Melcar on 2006-08-15
> **tribaal said:**
> If you run gnome I highly suggest you install the emitfreq-applet package, which is a nice panel applet that lets you set the CPU speed you wish to use, while it shows the CPU's temperature.

I just love it.

- trib'


I installed it.  Now how do you launch it and get it to work?

---

### Post by tribaal on 2006-08-15
You right-click on one of your gnome panels, and select "add to panel".
There from the list, pick the applet, and you're all set! You'll find it in the "utilities" section of the applets list.

Hope this helps :)

- trib'

---

### Post by Melcar on 2006-08-15
> **tribaal said:**
> You right-click on one of your gnome panels, and select "add to panel".
There from the list, pick the applet, and you're all set! You'll find it in the "utilities" section of the applets list.

Hope this helps :)

- trib'


Everytime I try to change the CPU speed it tells me that the daemon in charge of changing CPU speed is not activated.

---

