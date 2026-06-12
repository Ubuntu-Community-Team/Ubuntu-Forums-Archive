---
title: "Ubuntu 11.10 &amp; Xfce 4.8 Power Management Issue"
date: 2012-03-04
forum: Hardware
---

### Post by WildWalker on 2012-03-04
Hello All,

I have installed Ubuntu 11.10 on a Fujitsu laptop, so far everything is running fine except for the power management. This might seem a small issue, but I am trying to reduce power consumption for some of my services, and I have decided to stop using a 1U server for my media server (Windows Server, using 150-200 Watts constantly)

Insted I have decided to firstly use this laptop, and then move on to a Raspberry Pi. The latptop uses 20 watts with the screen on, and about 12 when it is off. 

I set the power management to turn off the screen after a couple of minutes, which worked fine (so power consumption went down to 12 watts) but after about 10 minutes, the screen saver comes on, pushing the power back up to 20 watts.

If I disable the screen savers the power management does nothing. If I use black screen, I get a black, but backlit, screen, so still uses 20 watts.

Now no matter what I do, I can not get Ubuntu to just turn off the screen, even if I put all the settings back to their defaults.

Any help greatly appreciated.

Best Regards,
Alan Walker.

---

### Post by EtoIxPi on 2012-03-04
Agreed. Ubuntu power management is lacking in all respects.

---

### Post by schurtek on 2012-03-06
Sadly, the Ubuntu development for ARM is for v7 of the architecture and not supporting v6 as the Pi uses.

---

