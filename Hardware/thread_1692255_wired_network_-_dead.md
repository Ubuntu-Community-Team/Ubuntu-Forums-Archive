---
title: "wired network - dead"
date: 2011-02-21
forum: Hardware
---

### Post by andreas lianos on 2011-02-21
Hi all,
I'll get straight to the point. My wired network card is not responding anymore.

I have set it up in interfaces file (static address). eth0 up and down works like a charm, network restart the same. ifconfig lists things as expected. I cannot ping further than myself though! 

The LEDs on the NIC dont lit, neither the ones on the switch (it just periodically blinks). Its not a cable problem, tested with known-to-work cables! 

I have uninstalled network-manager (because it was the original problem, bloody erasing my resolv.conf all the time).

Finally i need to say that I installed the latest updates (not sure when exactly the net went down though) and now shutdown is not working!

Made a live cd, booted with it and nothing works there aither (not even wireless network).

You are my last resort of ideas!

thanks!

---

### Post by andreas lianos on 2011-02-21
I installed windows on a partition and the leds came back on. I logged back in ubuntu live cd and vuala, it worked. Now theres a miracle to ponder upon. Consider it solved!

---

