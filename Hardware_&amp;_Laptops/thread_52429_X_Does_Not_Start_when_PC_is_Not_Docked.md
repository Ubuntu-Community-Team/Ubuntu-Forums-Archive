---
title: "X Does Not Start when PC is Not Docked"
date: 2005-07-27
forum: Hardware &amp; Laptops
---

### Post by apollo2011 on 2005-07-27
Hi everyone!

I have used Ubuntu on my desktop for a couple of months now and I have recently put it on my laptop.  I have a Dell Inspiron 8600.  Everything except the Wi-Fi card (Broadcom) seemed to work, and once I compiled and installed Ndiswrapper, I had the Wi-Fi card working too.

However, when I tried to boot the laptop when it was disconnected from the base station, it seemed to freeze at the "Loading Modules..." section of bootup.  I figured out that Ndiswrapper was what was causing the freeze, so I removed it from /etc/modules and let everything else stay.  The next problem I had was that it took forever to get passed the "Configuring Network Interfaces..." section because it was obviously trying to configure the ethernet, which is disconnected when it isn't docked.  I used ifplugd to determine when the eth0 device was connected.  Once I had that sped up, it reached the section where it seems like it is done booting and should start X, but instead, it goes to a blank screen and never comes back.

All of these problems, including the problem with X, ONLY occur when the laptop is not docked.  When it is docked, everything works great.

**EDIT: If it helps, I am still using the stock video driver.  I have an NVidia graphics card.**

Your help and timeliness is greatly appreciated :)

---

### Post by sn33kyP3t3 on 2005-08-01
I have the exact same problem... Except I haven't tried unloading the ndiswrapper module...

Have you had any luck since you last posted this?

One thing I might try is to disable acpi if not plugged in...

---

