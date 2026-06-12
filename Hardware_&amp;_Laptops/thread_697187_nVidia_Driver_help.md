---
title: "nVidia Driver help"
date: 2008-02-14
forum: Hardware &amp; Laptops
---

### Post by Enforcer83 on 2008-02-14
I need to install the nvidia drivers to gain access to some of the functions associated with my card.  I have a Geforce 7600 GT made by eVGA.  I have tried both the proprietary and the open source versions of the driver.  Gutsy's Xserver, and for that matter Hardy Heron's server does as well,  seems to hate the driver and always crashes forcing me to use the original xorg.conf file.  Fedora has no issues with the proprietary driver, however.
[B][SIZE="4"]
What must I do to get either of these drivers to work properly?[/SIZE][/B]

---

### Post by oldsoundguy on 2008-02-14
You might try ENVY (3rd party program) for installing.  I did on 3 boxes with NVida cards and all went smoothly.

---

### Post by Enforcer83 on 2008-03-16
Thanks works like a charm.

---

### Post by sultanoswing on 2008-03-17
> **Enforcer83 said:**
> Gutsy's Xserver, and for that matter Hardy Heron's server does as well,  seems to hate the driver and always crashes forcing me to use the original xorg.conf file.
[B][SIZE="4"]
What must I do to get either of these drivers to work properly?[/SIZE][/B]

I had a similar problem with a 6600GT - no end of crashes / freezes, which seemed to be resolved, only to 'fail to startX' on the next restart, with constant re-tweaking of the xorg.conf. I tried envy, synaptic and the drivers off the website, but all to no avail.

Finally permanently and sweetly solved by removing all 'nvidia' related items using Synaptic, then (and only then) reinstalling the drivers using the driver package (169.12 in my case) from the nvidia homepage. Sure, you have to enter the shell to do it, but it was WELL worth it in my case.

---

