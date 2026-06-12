---
title: "Dell XPS14z with Precise 12.04 doesn't recognize external monitor"
date: 2012-08-15
forum: Hardware
---

### Post by sombreroDuck on 2012-08-15
Hi everybody,
I'm running Ubuntu 12.04 on a Dell XPS 14z laptop and tried conncting it to a Dell monitor through a miniDispayPort-to-VGA adapter, and the laptop simply doesn't register that the monitor is there. Reading other threads I get the impression that it might have something to do with the nvida graphics card? I've tried installing bumblebee as was suggested in those threads, but this didn't help. I tried making some changes to the config file, e.g. setting ConnectedMonitor to DP1, but still no connection. 

Between each change I always restared. 

The only thing that gave any response was running "optirun glxspheres" from the terminal. This gave me a window with some psychadelic bubbles and the external monitor gave a twitch as if it was getting a signal, but as soon as I close the window the monitor went into "no signal" mode again. 

I've run out of ideas and can't find anything else in the older threads to try. :confused: Maybe I've done something in the wrong order? are there any other settings I could try to change? All tips are welcome!

Thanks!

---

