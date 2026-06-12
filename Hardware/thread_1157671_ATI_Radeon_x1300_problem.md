---
title: "ATI Radeon x1300 problem"
date: 2009-05-12
forum: Hardware
---

### Post by tommah04 on 2009-05-12
I just recently install ubuntu jaunty so I'm fairly new, but I get the idea good enough....

but I've tried installed a driver for my ATI Radeon x1300 graphics card 3 times, and each time upon startup the screen is nearly blank with a few colored lines across the screen and I am unable to do anything and am forced to reinstall ubuntu.

I can deal without it... but if I can get it to work that'd be awesome

thanks in advance for time and patience

btw: I dual boot with vista and the card works fine on vista

---

### Post by sdowney717 on 2009-05-13
AMD drivers dont work with Jaunty. the last FGLRX AMD driver you can run works only with Intrepid. And this will never change.
You can only use the free ATI driver that comes with linux, not any AMD driver. 
If you want 3d apps to work with that card you got to use Intrepid or hope the free driver gets really good.

---

### Post by tommah04 on 2009-05-13
thanks for the reply,

the driver I got from linux applications didn't work.... guess I'll just wait untill I upgrade and get a nvidia

thanks a lot!

---

### Post by NormanFLinux on 2009-08-03
Install the open source drivers, edit the xorg.conf file to remark ATI as the default driver and upon reboot enable compiz. Its all that can be done on 9.04 as ATI is no longer supporting legacy cards like the Radeon X1300 Mobility. That's my fix to the issue. I hope it helps others with the same problem.

---

