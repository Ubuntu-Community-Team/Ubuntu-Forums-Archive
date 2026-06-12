---
title: "Feisty and network roaming mode"
date: 2007-04-11
forum: Hardware &amp; Laptops
---

### Post by Vola on 2007-04-11
Hi all,

I just upgraded to feisty beta, and I see the new "roaming mode" option into the network manager.
Can someone explain me how this work? I read some post and seem these allow to connect automatically to the networks where available.
But on my laptop when this option is active the wireless is always unassociated:

$ iwconfig

eth1      unassociated  ESSID:""

My lap-top is a thinkpad R50e (intel centrino 1.7 with pro wireless 2200)

I usually use 2 wireless network at home without encryption and at work with wpa but I need to configure them every time for use.

Any ideas?

---

### Post by ukripper on 2007-10-27
use wlassistant your life will be easy. and configure your home ESSID and key in  
```
sudo gedit /etc/network/interfaces
```

---

