---
title: "Lirc dying on reboot"
date: 2005-10-17
forum: Hardware &amp; Laptops
---

### Post by FlyDoc on 2005-10-17
I have Pinnacle PCTV pro card that comes with ir sensor connected to serial port . Couple of days ago I installed lirc, configuration reported that no additional modules had to be installed and everything went OK. I tried mode2 and irrecord, and remote was working.
When I typed **ls /dev/lir*** got something like this:

/dev/lirc
/dev/lircd
/dev/lircm

Problem is that after reboot **ls /dev/lir*** gives only:

/dev/lircd

If I try to start mode2 or irrecord I get error that /dev/lirc doesn't exist. Only way to correct this is to do make install after every reboot, but this is not the way to correct the problem.

My question is there a way to prevent /dev/lirc from dying after every reboot?

---

### Post by dsauter on 2005-11-21
Strange problem, but I've got it too.  Everything works great until I reboot, and then I can't get it running again.

I found a solution that worked for me.  The following site has a good how-to.  Step 21 and/or step 22 seemed to do the trick.

[http://mythtv.info/moin.cgi/UbuntuInstallation](http://mythtv.info/moin.cgi/UbuntuInstallation)

---

