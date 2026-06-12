---
title: "Bluetooth in Karmic won't persist after shutdown"
date: 2009-12-21
forum: Hardware
---

### Post by tehGriggs on 2009-12-21
Hi everyone,

 I'm in need of help setting up two bluetooth devices (a microsoft keyboard and mouse) on my fresh install of Karmic. 
When already logged in, I can connect the mouse and keyboard just fine, they work perfectly etc. The problem is though that once I restart the machine, they are no longer connected and I cannot log in. 
I've done a bit of reading and found that I could add persistence if I go and edit the /etc/default/bluetooth and I would have, except its not there. So I did more research and found i could go edit /etc/bluetooth/hcid.conf to add persistence except its not there either... there's only audio.conf, input.conf, main.conf, network.conf, and rfcomm.conf
I also tried using the graphical methods (gnome-bluetooth, bluez, blueman) but none have worked so far.

So yeah, now I'm kinda left scratching my head and feeling like I've missed something pretty basic here. 

Any help would be great ;D
thanks in advance

---

