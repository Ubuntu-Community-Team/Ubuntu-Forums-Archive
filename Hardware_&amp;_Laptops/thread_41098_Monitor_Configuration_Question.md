---
title: "Monitor Configuration Question"
date: 2005-06-11
forum: Hardware &amp; Laptops
---

### Post by hodgepodge on 2005-06-11
Hello,

I'm somewhat new to Linux, and am having some difficulties with my monitor.  My monitor, an Optiquest Q95, wasn't recognized by the system., or perhaps the process of installing the nVidia driver erased it, not sure which.  In any case, xorg.conf shows it was a "Generic Monitor".  This means I can't use a refresh rate above 60hz at 1280x1024, which aside from the subtle flashing, is hard on my eyes.

What is the best way of dealing with this problem?

Thank you!

--Hodgepodge

---

### Post by netrattler on 2005-06-11
My monitor wasn't picked up as well by Ubuntu, but all you need to do is edit your /etc/X11/xorg.conf and scroll down to your monitor section and change the HorizSync
and VertRefresh values. I looked at the companies website that made your monitor, your HorizSync value should be 30-86 and the VertRefresh should be 50-160. This is all I had to do to my xorg.conf file and it corrected my problems and allowed me to use a higher refresh rate. Hope this helps.

Joe

---

