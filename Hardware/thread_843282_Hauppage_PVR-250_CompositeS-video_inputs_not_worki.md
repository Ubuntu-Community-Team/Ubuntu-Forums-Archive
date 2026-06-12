---
title: "Hauppage PVR-250 Composite/S-video inputs not working"
date: 2008-06-28
forum: Hardware
---

### Post by XeroZohar on 2008-06-28
I'm at my wits end, and have Googled my heart out trying to figure out this odd problem.

I am running Hardy Xubuntu, and my previously working Hauppage PVR-250's composite and S-video inputs aren't working anymore.  Thing of it is, they used to, back when I was running Edgy and the kernel was still back around 2.6.20 or so.  Of course, I was using a custom built ivtv module to run it at that time since it wasn't part of the kernel, not to mention a custom kernel to get my audio working.  I'm using the stock kernel and ivtv module now since all those problems went away after 2.6.23 I believe.

Anyway, I didn't use the card for a long time and when I finally come back to it looking to capture some video from a console game, those two inputs don't work.  I've tried checking cables, reloading the ivtv module, seeing if I could edit some parameters of the card via the ivtv or v4l2 controller apps, but to no avail.  I know the card itself is still working because I get a signal from the tv tuner.  It's just when I switch it via v4l2-ctl to the S-video or composite inputs, I get a blank video window.  And not even the usual blue screen that the card used to give me when there was no actual signal on those inputs.

The final nail in the coffin which makes me think I may have zapped those inputs with a static charge or something by accident, is that the Windows program and driver that you'd think would work flawlessly with it, have the exact same problem, and they didn't used to either.

So, my question to you, the great Ubuntu community, is whether you think I've missed a step or an idea somewhere, or if maybe that part of the card's bitten the dust like I suspect?

Thanks so much for any ideas. :)

---

