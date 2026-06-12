---
title: "Problem with eee 701's wireless."
date: 2009-04-28
forum: Hardware
---

### Post by LordLandon on 2009-04-28
I have an eee 701 running ubuntu, which has severe problems using wifi:
timeouts occur all the time, dns takes forever to resolve, if it resolves at all, packets seem to come in bursts, and then again not come in at all.
This is a problem consistent throughout 8.10, 9.4 live, and 9.4 installed, so I suspect it has something to do with the hardware. I've also confirmed that it's not a problem with the network, as a different laptop inches away from the eee works flawlessly.

Now, I'm suspecting that this is something that I broke myself, somehow - perhaps trying to mess with WEP cracking tools (aircrack-ng, and kismet) because the wireless worked correctly before... The problem is, I know very little about NICs and such, and have absolutely no clue as to how even begin to diagnose/fix this...

So far, I've tried setting interfaces' modes to managed, running ifconfig -promisc on them, using wicd instead of Network Manager, and checking dmesg for any errors that might be relevant to no avail.

---

