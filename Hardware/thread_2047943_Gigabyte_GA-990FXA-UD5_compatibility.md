---
title: "Gigabyte GA-990FXA-UD5 compatibility"
date: 2012-08-25
forum: Hardware
---

### Post by bartos on 2012-08-25
Does anyone have this mother board (Gigabyte GA-990FXA-UD5) that they can recommend it or decline it.
I want a motherboard that is fully supported by linux including suspend.

Thanks
Bart

---

### Post by marsanyi on 2013-01-09
I've spent two days unsuccessfully trying to set up 12.04LTS on a 990FXA-UD3.  Issues with networking and USB out of the box.  Would not recommend to anyone whose time is valuable.

---

### Post by Yellow Pasque on 2013-01-09
marsanyi, it's a fairly new board, so perhaps these things have been solved already (in Ubuntu 12.10 or later).

For the ethernet:
[http://www.twm-kd.com/linux/realtek-rtl81688111e-and-ubuntu-linux/](http://www.twm-kd.com/linux/realtek-rtl81688111e-and-ubuntu-linux/)
[https://launchpad.net/ubuntu/quantal/+package/r8168-dkms](https://launchpad.net/ubuntu/quantal/+package/r8168-dkms)

For USB: you may have hit this bug [https://bugzilla.kernel.org/show_bug.cgi?id=47791](https://bugzilla.kernel.org/show_bug.cgi?id=47791)

---

### Post by mcfudge on 2013-02-02
> **Temüjin said:**
> marsanyi, it's a fairly new board, so perhaps these things have been solved already (in Ubuntu 12.10 or later).


Post deleted - wrong mainboard.  My bad.

Myles

---

### Post by Thomas Lundström on 2013-08-07
> **bartos said:**
> Does anyone have this mother board (Gigabyte GA-990FXA-UD5) that they can recommend it or decline it.
I want a motherboard that is fully supported by linux including suspend.

Thanks
Bart

Hi Bart!

Did you ever get around the problem? I've just bought rev 3 of that same board as a replacement for another motherboard that the lightning killed and didn't check compatibility first.... I get absolutely no usb keyboard/mouse response when booting my installed 12.10 version or a new live-cd 13.10....

Best regards

Thomas

---

### Post by kurt18947 on 2013-08-07
I have a discontinued Gigabyte MA785-US2H.  It works pretty well with 12.04 and newer.  I recall some issues with earlier releases, particularly with some USB ports.  If I were looking to replace it and stay with AMD, I'd probably look at a 760 chipset, the 785 doesn't seem all that common.  Thanks to those who have reported on the 990, even if their experience is not what they'd like it to be.

---

