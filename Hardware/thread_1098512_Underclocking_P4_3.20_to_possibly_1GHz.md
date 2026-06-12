---
title: "Underclocking P4 3.20 to possibly 1GHz"
date: 2009-03-17
forum: Hardware
---

### Post by second.exodous on 2009-03-17
I have an old zd7000 that has a P4 3.20 GHz in it, way more power than I need.

Anyway, it heats up really bad and even when I'm playing my nes emulator it over heats and shuts down.  I even took off the cover to the heatsink for my CPU and GPU thinking that would give it more air, but it still overheats.

I can find plenty of resources on underclocking in windows for my notebook but nothing for Linux.  I can't underclock through my BIOS either, it has to be done through software.

I'm actually considering getting a new CPU for it, what CPU could I drop into my notebook that is the same socket that generates less heat?

Thanx,
Stan

Edit:  Well, I did some research, although I can't find a page that tells me the exact socket that my notebook has 478 is what P4 is, so I think I can drop any 478 processor into it.  But is this better?  I can get a 2GHz P4 for under 50, will that produce a lot less heat?  Also, there are Celerons also, but they don't produce any less heat do they?

If someone knows for sure please let me know.

---

### Post by davidryderuk on 2009-03-17
Hi,
You could try the guide at the following link. This should work if you have the right kernel modules loaded. 

[http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html](http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html)

If the above guide doesn't work it might mean you have to load kernel modules that support frequency control in the p4 processor. There are details about doing this in the link shown below. 

[http://ubuntuforums.org/showthread.php?t=190921](http://ubuntuforums.org/showthread.php?t=190921)

Please note, i don't know for sure that this will allow you to control CPU frequency as i don't have the same processor, but it shouldn't do any harm.

---

