---
title: "Nvidia 2080 RTX display won't standy when system shut down"
date: 2019-06-01
forum: Hardware
---

### Post by rbmorse on 2019-06-01
I just replaced my Nvidia GTX970 video card with an 2080 RTX using the same Nvidia 413 driver on Ubuntu 19.04. HDMI connection. The swap was plug 'n play once I remembered the locking tab on the end of the PCIe slot when I tried to remove the old video card.  

The machine came right up without an error.   I didn't notice any anomalies until I shut the system down for the night, and although the machine powered off normally, the display entered stand-by mode as it should, then immediately re-activated. A couple of seconds later the display flashes an "entering standby mode" banner, then the cycle repeats until I either kill power to the display or power the PC back up. 

Power-saving display blanking (where the display goes into standby after the specified period of inactivity) works normally. 

Pulling the plug on the power mains (once the machine is shut down) makes no difference so I don't think it's there's any residual voltages leaking through the video card, unless it takes a <LONG> time for the caps in the card's voltage regulators to leak down. 

I haven't seen any other reports of this with the RTX series...the problem that everyone else seems to have is that the machine (or display) won't come back after entering standby mode. That part works for me.  

My next step will be to buy a DP cable so I can see if the problem persists there, but I'd rather not buy another cable if the problem may lie elsewhere. 

Any and all ideas welcome

---

### Post by CatKiller on 2019-06-01
I remember reading a while ago that Nvidia were changing the way they handled DPMS: sending a different type of signal. It seems possible to me that your old card was using the old way and the new card is using the new way, but I can't remember the details.

If you don't manage to find a setting to fiddle with, I'll see if I can find more details about it later.

---

### Post by rbmorse on 2019-06-01
Thanks!  That gives me something to search on.

---

