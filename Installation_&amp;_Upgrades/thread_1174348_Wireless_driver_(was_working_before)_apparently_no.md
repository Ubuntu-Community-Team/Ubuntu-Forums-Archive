---
title: "Wireless driver (was working before) apparently not loaded on new jaunty install"
date: 2009-05-30
forum: Installation &amp; Upgrades
---

### Post by markhepworth on 2009-05-30
I have installed jaunty twice in quick succession on an old desktop. The first time, wireless worked out-of-the-box. I then did some dumb experimenting, and reinstalled as it seemed the quickest way back. This 2nd time, wireless does not work. It's a wireless dongle called an inventel UR054g(R01), and it shows up in lsusb as Bus 002 Device 002: ID 1435:0427 Wistron NeWeb, but sudo lshw -C network only brings up my wired connection. In addition, networkmanager applet does not show a wireless option. This dongle has always been shaky, so maybe it wasn't detected during the 2nd install?

As it appears that jaunty can find and install it on one install, is there some way to revive it?

Thanks in advance for any help, Mark

edit: iwconfig gives:
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

---

### Post by markhepworth on 2009-05-31
The darn thing just fixed itself. No idea how or why.

---

