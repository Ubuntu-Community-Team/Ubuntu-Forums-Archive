---
title: "nVidia Drivers Not Supported By Monitor"
date: 2010-09-20
forum: Hardware
---

### Post by Shadow21 on 2010-09-20
I installed Ubuntu today and I'm using an HDTV as a monitor. I had a problem right after I installed it and rebooted it the first time because I didn't install the nVidia driver so it tried to boot into low-graphics mode and then it wouldn't boot into the gui. 

This time I did install the current nVidia drivers but when I tried to boot into Ubuntu after they were installed my HDTV went black and said "Not Supported" (although Ubuntu did boot all the way). I did try another one of the nVidia driver revisions but it still didn't work with my TV. I do have another monitor which does show Ubuntu (with the nVidia drivers installed) but I would like to make my HDTV work with the nVidia drivers installed.

How do I get my HDTV to work with the nVidia drivers installed?

Let me know if you need any more info.

Thanks

---

### Post by efflandt on 2010-09-21
Either your HDTV cannot handle whatever resolution your system is set for, or more likely it is set for a refresh rate the HDTV cannot handle.

Refresh rate for 720p or 1080p HDTV should be 60 Hz in US, or maybe 50 Hz in Europe.

---

### Post by Shadow21 on 2010-09-21
> **efflandt said:**
> Either your HDTV cannot handle whatever resolution your system is set for, or more likely it is set for a refresh rate the HDTV cannot handle.

Refresh rate for 720p or 1080p HDTV should be 60 Hz in US, or maybe 50 Hz in Europe.

So wouldn't I be able to change those settings in Ubuntu to something that my TV can handle?

Edit: I went and changed the resolution in Ubuntu (to 1024x768) on my monitor and switched it back over to my HDTV and it did work but I restarted the computer (to make sure it would still work after a reboot) and the Ubuntu boot screen showed up but the TV tried to auto-configure the screen and it must have changed the resolution again because it turns black and says "Not Supported" again.

I need to figure out how to make it so Ubuntu automatically changes the resolution back to 1024x768.

Edit2: I was able to make it so Ubuntu booted with the correct resolution so it does show up on my HDTV. The only bad thing is that it doesn't take up the whole scree.

---

