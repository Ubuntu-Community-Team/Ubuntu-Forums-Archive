---
title: "Setting wireless default to off?"
date: 2011-06-03
forum: Hardware
---

### Post by tpprynn on 2011-06-03
I imagine there's some way I can do this - I've had a netbook a week which I use with Mobile Broadband if I'm online at all with it. If possible, rather than the wireless being on when I start up it would be set to off till I turn it on when occasionally near any wireless facilities. How would I do this?

This is a Packard Bell Dot S 410 with an Atom N 450 CPU running Ubuntu 10.04 32 bit.

Thanks.

---

### Post by mikewhatever on 2011-06-03
Some notebooks have a hardware wireless switch, you push it, and the wireless is of until it's pushed again. However, most notebooks only have a sofware or a keyboard combo, and if that's your case, I think that the only way would be to edit a config file to prevent the module from loading on startup, or, alternatively, to bring the wireless interface down on startup.

For example, if your wireless interface is wlan0, add the following line to /etc/rc.local:
```
ifconfig wlan0 down
```

Run 'ifconfig' to see the networking interfaces.

---

### Post by tpprynn on 2011-06-03
Thanks. I was a bit hopeful there but adding that line had the effect strangely of turning my wireless light off while leaving the wireless itself on.

Any further ideas are welcome.

---

