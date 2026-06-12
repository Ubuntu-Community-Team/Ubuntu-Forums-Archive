---
title: "t42p frezzying when booting 9.04"
date: 2009-04-23
forum: Hardware
---

### Post by danielfarley on 2009-04-23
Just upgrade to 9.04 and now when i boot, i get the splash screen loading then the computer freezes, with a black screen, caps lock doesn't work any more etc...  (this is booting the 2.6.28-11 kernel)

If i boot 2.6.27-11, everything works, fine.

When i boot the broken kernel, and look at the log file for xorg it is getting to the point that it is trying load libint10.so and stops there no error message or anything.

It is worth noteing to make my ATI video car sleep properly i am runing radeonfb, as per [http://www.thinkwiki.org/wiki/Problem_with_high_power_drain_in_ACPI_sleep](http://www.thinkwiki.org/wiki/Problem_with_high_power_drain_in_ACPI_sleep)

Any ideas?

Thanks Daniel

---

### Post by danielfarley on 2009-04-26
ok, this is strange it seems that the new kernel doesn't like my pcmcia to cf card adaptor, as when i remove this the new kernel boots and works fine.   Any ideas how to fix this?

Thanks Daniel

---

