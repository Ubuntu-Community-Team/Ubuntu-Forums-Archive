---
title: "Can't change refresh rate on unknown monitor to needed value"
date: 2011-05-07
forum: Hardware
---

### Post by gottobtru on 2011-05-07
We have tried two different monitors (HP L1170 and Dell IN2020M) on this computer and neither is recognized by Ubuntu 11.04, according to the Monitor Preferences screen.  We cannot find a Linux driver for either monitor; this is surprising because both vendors sell computers with Linux installed.

Various programs we run tell us that we need the monitor refresh rate set to 60hz but when we go to Monitor Preferences to set it up that speed is not an option; depending on the resolution, 50hz, 51hz, 53hz, 100hz are available.

I have tried sudo dpkg-reconfigure xserver-xorg - nothing happens.  The command completes without doing anything.

I have adujusted nVidia X Server settings.  Interestingly enough, the nVidia card has no problem identifying the monitor and can be set to 60Hz. This has no influence on the monitor settings.

---

