---
title: "Dell Latitude D810 overheating: can I throttle back CPU usage?"
date: 2010-01-18
forum: Hardware
---

### Post by clanmackay on 2010-01-18
My Dell Latitude D810 overheats to a temperature at which it shuts itself off when I am doing computationally-intensive tasks such as video transcoding.  Two questions:

1.  Is there a way in Ubuntu to specify a maximum processor load (50%, say) so that this won't happen?  Some sort of global nice?

2.  Not an Ubuntu problem, but any idea why this might be happening?  It didn't used to.  The fan still works, and will get louder and louder until the machine shuts down.  Is my machine dying?  Are there cooling solutions, such as better heat sinks, gel icepacks the size of placemats, or something?

Thank you.

---

### Post by bryanagee on 2010-01-18
You can add a CPU control to your task bar (right click-> add to panel-> CPU Freq. Scaling Applet) but this requires that you set the processor mode/speed manually everytime. It's also a little annoying that if you have a multicore, you have to open the settings and switch the applet to each processor, unless you add the applet once for each.

---

### Post by clanmackay on 2010-01-18
Thank you.  I can't figure out how to use it.  It has a dropdown with half a dozen clock speeds, as well as four of what I assume are presets, but no settings above the minimum speed option (800MHz) stick. Yes, I authorized as su.

More help, please?

---

### Post by bryanagee on 2010-01-18
You should be able to select any speed or a preset, and I imagine selecting 'conservative' would run cooler. Do you have a fan pad for it? If you are planning on doing a lot of intense processing, that might be better. You can pick up a usb powered one for ~$20, and that will drop a few degrees. Giving the laptop a once-over with a can of air might help too. Did you check to make sure that the heatsink is still seated on the cpu? There's normally a cover to get easy access to that--should be a couple of coppertubes that run from the CPU to a fan nearby.

---

