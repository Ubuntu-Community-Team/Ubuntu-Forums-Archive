---
title: "Displaylink Monitor on Ubuntu 13.10 (green screen)"
date: 2013-11-25
forum: Hardware
---

### Post by anujmonster on 2013-11-25
Hello,

I have an AOC E2251FW USB monitor.  I have blacklisted the udlfb module and enabled the udl module.  In addition, I have installed the xserver-xorg-video-modesetting driver.  I have looked all over the net, and apparently a green screen means that Ubuntu can see and talk to the monitor.  How can I get it working?  Thanks!

---

### Post by dchallet on 2014-01-16
> **anujmonster said:**
> Hello,

I have an AOC E2251FW USB monitor.  I have blacklisted the udlfb module and enabled the udl module.  In addition, I have installed the xserver-xorg-video-modesetting driver.  I have looked all over the net, and apparently a green screen means that Ubuntu can see and talk to the monitor.  How can I get it working?  Thanks!

I had the same problem with vanilla 13.10.

Solving it is quite easy: upgrade your kernel to the latest mainline ppa version (3.13rc7 in my case) and everything works as it should.

---

### Post by anujmonster on 2014-01-19
Thanks! This worked perfectly.  Upgraded to 3.13rc8 and it works flawlessly after loading udl/unloading udlfb.

---

### Post by Qing_Yu on 2014-03-05
Hi Anujmonster,

I have upgraded myone to 3.13rc8 and myone is still not working, when I loads udl, the extra monitors using displaylink are not turned on, when I load udlfb, they are in green screen. Any suggestion?

Thanks

---

