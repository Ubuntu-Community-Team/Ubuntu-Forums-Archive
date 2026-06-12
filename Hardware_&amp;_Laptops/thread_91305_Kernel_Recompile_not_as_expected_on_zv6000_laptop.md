---
title: "Kernel Recompile not as expected on zv6000 laptop"
date: 2005-11-16
forum: Hardware &amp; Laptops
---

### Post by OneSeventeen on 2005-11-16
I have had this zv6000 laptop since it was brand new on HP's site, and have run a few different operating systems on it, including 5.04, and I just upgraded to 5.10.

This laptop has ALWAYS had major issues, almost all of which are caused by the ATI chipset and the ATI video card inside.

I just rebooted after recompiling the kernel with a timerhack patch, and after booting up, I am able to browse the web (via my WEP encrypted wireless network using ndiswrapper), check my mail, use OOo 2.0, and use blender just fine with no tweaking.  And my CPU usage is reading closer to 0% than the 50% it was stuck at before, and the clock is correct.

I just wasn't expecting this... the last kernel compile required much tweaking and way too much work just to get the graphics to work again.  I may not have 3d accellerated graphics, but since its an ATI card, I'm not missing much anyway.  (try and render 3d scenes with an ATI driver in blender! ha!)

Anyway, just thought I'd post this, so other zv6000 users would know that there is hope, and the infamous "timerhack" works!

---

### Post by kking on 2005-11-24
Could you explain the timerhack patch?

I've also got a ZV6000 and I'm facing a problem with the 1st boot from the HD right now, but I'm interested in this once I get up and running.  Or I wonder if this could help me now...

---

### Post by benguin on 2005-11-25
Hey OneSeventeen,
I have  zx5000, with Broadcom, ATI sound, IDE, graphics (the usual troublemakers). I am interested about that TimerHack patch too. Please educate me as well?

Thanks,
_J_

---

