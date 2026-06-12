---
title: "modifiy sleeping behavior of Lucid Lynx?"
date: 2010-09-05
forum: Hardware
---

### Post by WebJakob on 2010-09-05
**Which scripts should actually be modified to change sleeping behavior of Lucid Lynx?**

I have just made a clean install of Ubuntu 10.0.4(x?) Lucid Lynx on a DELL LATITUDE D600 (year 2003) for my 7 year old daughter.
The machine exhibits suspend problems, which makes it too quirky for daily use by a seven year old.

I have installed 'uswsusp', and running s2ram, it reports "This machine can only suspend without framebuffer."

So I take that to mean that this particular hardware is simply not capable of suspending (with current Ubuntu)?

Going on that assumption, I would like to simply abandon 'suspension' and just go with 'hibernation'.
So I have made hibernate the default option for both pressing the powerbutton, and closing the lid.

I also tried to follow the instructions given here:
[http://www.ubuntugeek.com/fix-for-suspend-and-hibernation-problem-for-laptops.html](http://www.ubuntugeek.com/fix-for-suspend-and-hibernation-problem-for-laptops.html)
In order to call uswsusp rather than the default system, because it performs a more informative process, when sleeping and waking up.
So I modified '/usr/lib/hal/scripts/linux/hal-system-power-suspend-linux' (and the other one for hibernate) like so:
#!/bin/sh
/usr/sbin/s2disk
but apparently these scripts are not called, because the machine still sleeps in the default way. Googling this reveals that other people have encountered this problem, and are asking for which scripts are actually called now in Lucid Lynx

Explicit question: Which scripts should actually be modified to change sleeping behavior of Lucid Lynx?

I have also tried a kludge, to call a uswsusp script from a launcher in the top-panel. However my daughters account is not an administrative account, and therefore cannot perform calls to uswsusp.
I added her account to the group 'sudo' and made the script like this:
#!/bin/sh
gksu /usr/sbin/s2disk
so now her account can use the launcher and type her password in order to do a better hibernate, but definitely not as elegantly as I would prefer. Also I'd like to not make her a sudoer.
I assume that if I was able to modify the behavior of the 'normal' sleep-routines - power-button-lid etc. I wouldn't have to bother myself with launcher at all, but anyways **would there be a way to call uswsusp from a non-admin without the password-hassle?**

[B]Any ideas on ways to make this machine friendly to a seven-year-old?

Thank you in advance
[/B]

---

