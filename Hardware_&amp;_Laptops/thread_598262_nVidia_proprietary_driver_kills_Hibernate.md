---
title: "nVidia proprietary driver kills Hibernate"
date: 2007-10-31
forum: Hardware &amp; Laptops
---

### Post by kortsen on 2007-10-31
I have a Toshiba Satellite 2800-C500 with integrated nVidia GeForce 2Go graphics.  When I use the generic nv driver, Hibernate works fine.  When I use the proprietary nVidia driver and try to hibernate, the signal is cut to the LCD but it remains on, and after a bit of disk access the power remains on and the system is completely hung.  I have to power-cycle and the system does a fresh boot (not a restore from Hibernate.)

The odd thing is that I am revisiting a problem I had with 7.04.  Feisty would not hibernate at all.  The nVidia driver behaved exactly as described above.  And it wouldn't hibernate with the nv driver either, but it did have the decency to puke up some error messages before it swallowed it's tongue.  I changed the driver from nVidia to nv and tried to hibernate, prepared to try and catch the errors.  Well sonomabiatch if Gutsy didn't hibernate! I changed back to the nVidia driver and the problem above returned (no signal and hung.

---

