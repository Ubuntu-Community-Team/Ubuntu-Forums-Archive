---
title: "desperately seeking sleep, acer aspire 3002lci"
date: 2005-08-15
forum: Hardware &amp; Laptops
---

### Post by edheil on 2005-08-15
I am using Hoary on an Acer 3002LCi laptop.  I followed the instructions in another thread to fix the DSDT on my machine so that Ubuntu could see battery status and the like with acpi.  Woot!

I do not yet have a working sleep/hibernate/suspend/whatever option.  I've looked into getting a kernel with suspend2 (swsusp2) compiled but as far as I can tell it is beyond my abilities.  (I am not sure I trust something that bleeding edge anyway.)

I would be happy, I think, if suspend-to-ram worked.  I've tried commenting in and out many of the options under /etc/default/acpi-support and running /etc/acpi/sleep.sh.  This results in the laptop going to sleep as it should (its power light goes off and the fan shuts down).  When I hit a key it "wakes up" as it should, or tries to -- the power light comes back on, I get disk activity and the fan comes on.  However, the display is blank.  It's not clear whether keyboard input is working either; a control-alt-backspace followed by a control-alt-delete does not have any effect.  I don't have another machine at hand to try ssh'ing in to it.  It doesn't seem to be a purely X problem, because it's exactly the same when I do it from the console.

I've fiddled with various values of POST_VIDEO, SAVE_VIDEO_STATE, and USE_DPMS, with no effect so far (though I'm not sure I've exhausted every possibility of the options).

I was wondering if anyone had had success getting any kind of suspend or sleep going on this or a similar machine and Hoary.  It's a real drag having to power the beast down whenever I have to take it somewhere.

Thanks,

Ed

---

