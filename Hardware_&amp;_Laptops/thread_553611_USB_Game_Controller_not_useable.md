---
title: "USB Game Controller not useable?"
date: 2007-09-18
forum: Hardware &amp; Laptops
---

### Post by ar1stotle on 2007-09-18
OK, I have a Super Joybox 5 so that I can play SNES games on my Ubuntu box running MythTV. Now, when I log on to my normal account with an interactive login, the controller works fine in ZSNES. However, when it logs on to the mythtv user, the controller just acts like it's not there. When I press buttons to configure the keys, it just doesn't respond. Is there something that has to be set to allow an account to use these peripherals? 

Thanks!

---

### Post by ar1stotle on 2007-09-19
Any ideas? I don't think this has to do with my specific adapter, but all USB controlls in general. What is required in ubuntu for these to properly function?

---

### Post by geraldm on 2007-09-19
It may require loading module joydev
It needs a driver, possibly hiddev.  Does the file /proc/bus/usb/devices show that it 
has a driver? If so, what driver?

Gerald

---

