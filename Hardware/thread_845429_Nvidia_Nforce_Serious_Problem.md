---
title: "Nvidia Nforce Serious Problem"
date: 2008-06-30
forum: Hardware
---

### Post by shonwein on 2008-06-30
First, this is day two under linux, so i don't understand a thing about this.
I downloaded the nvidia nforce (onboard) driver, but the driver only let's me choose a 640*480 resolution. Is serious 'cause i can't even run ubuntu fine because the "windows" are too big for the resolution and when i try to choose something the window moves by it's own and i can do nothing.

The other problem, is that without the driver, when i start with linux somthimes the resolution is 1024 , somethimes 800 , and so on. I'm going crazy with this.

---

### Post by phidia on 2008-06-30
What driver is listed in the device section of your /etc/X11/xorg.conf file? If it's isn't listed as "nvidia" you do not have the better quality graphics driver installed. 
To install the driver in 8.04 click System>Admin>Hardware Drivers and enable the nvidia driver-then you'll have to reboot.

---

### Post by shonwein on 2008-06-30
It's enabled. And then is where the 640*480 problem appear.

When disabled, i can run in 800*600 but when enable i can only run in 640*480.

---

