---
title: "Aopen 965 GM random blank login screen"
date: 2008-12-13
forum: Installation &amp; Upgrades
---

### Post by adere1 on 2008-12-13
Hello,

I'm experiencing some problems with a Aopen 965 GM and Ubuntu 8.0.4.

Everything works fine except, at random occasions, ubuntu does not correctly logs in the desktop environment.

Ubuntu does not crash, it's "behind" a blank screen.

If ALT-F2 and then ALT-F7 it normally gets me right in the desktop environment - exceptionaly i have to repeat it once or twice so it takes effect.

I've tried to edit the xorg file and specify the video driver in use. If i configure it to use "VESA" driver it runs fine - with-ought showing the blank screen. But then i can not use the 1680x1050 resolution for the purpose of this instalation. If i let the xorg without any "driver" definition, or if i configure it for the "intel" driver, then i am able to use the required resolution but with that annoying random blank login screen.

Is there anyone who may help me?!

---

### Post by PJSingh5000 on 2009-02-08
> **adere1 said:**
> Hello,

I'm experiencing some problems with a Aopen 965 GM and Ubuntu 8.0.4.

Everything works fine except, at random occasions, ubuntu does not correctly logs in the desktop environment.

Ubuntu does not crash, it's "behind" a blank screen.

If ALT-F2 and then ALT-F7 it normally gets me right in the desktop environment - exceptionaly i have to repeat it once or twice so it takes effect.

I've tried to edit the xorg file and specify the video driver in use. If i configure it to use "VESA" driver it runs fine - with-ought showing the blank screen. But then i can not use the 1680x1050 resolution for the purpose of this instalation. If i let the xorg without any "driver" definition, or if i configure it for the "intel" driver, then i am able to use the required resolution but with that annoying random blank login screen.

Is there anyone who may help me?!
I have an AOpen 965-DR and an AOpen 945-DR that both do the same thing randomly.  I typically press Alt-E to restart X, and the login screen comes back.

However, I have Sceptre and DCLCD flat panel monitors.  (I believe the actual manufacturer of both mointors is the same).

Although I am experiencing this problem with both AOpen machines, I suspect that the problem may actually be with the monitors.  I recall reading something in the owner's manual to the effect that if the monitor recives a signal burst that is too strong, it will blank out.  This may be what is happening when X 1st initializes.

Which monitor are you using?

Have you tried your AOpen with another monitor or an old fashioned CRT?

---

### Post by adere1 on 2009-02-08
Hello,

It's has nothing to do with the specific monitor, because it is also happening with other monitors, within new and old techologies, resolutions or connections.

I've managed to solve this problem by installing the Intrepid version of Ubuntu and updating to the latest "intel" driver version. The problem is gone, so it is a "video driver" malfunction.

Now i am experiencing a new problem: the "ELO" touch screnn driver i am currently using does not run under the Intrepid Ubuntu. I've tried other drivers (elographics, evtouch, etc) but any of them works properly.

So, i am stuck with the Hardy Ubuntu and waiting for an update of the "intel" driver that will fix the problem (PIPE A/B overun).

Hope you may find another solution.
Thanks.

---

