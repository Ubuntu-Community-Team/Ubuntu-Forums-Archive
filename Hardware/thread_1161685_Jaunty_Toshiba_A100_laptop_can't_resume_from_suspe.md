---
title: "Jaunty: Toshiba A100 laptop can't resume from suspend"
date: 2009-05-16
forum: Hardware
---

### Post by wonderbuntu on 2009-05-16
This laptop has the Radeon Xpress 200M video chip, Atheros AR242x Ethernet, ENE CB1410 Cardbus bridge.

I'm very happy with Jaunty, and have been a long time Ubuntu user.  I'm trying to wean my wife off Vista on this laptop, and am totally hung up on the Suspend-to-ram feature.  She normally suspends the laptop about 3 times a day, so fixing this is critical for me to get her off Vista.

Anyway, I've spent two days reading, installing, re-installing, compiling, tweaking, and still no luck resuming from suspend.

I feel the closest I came was using the pm_trace utility, which at first pointed to the cardbus controller.  I then renamed the .ko file so it wouldn't be found on the next reboot, and then the hang pointed to[INDENT][FONT=Courier New]hash matches /build/buildd/linux-2.6.28/drivers/base/power/main.c:350[/FONT]
[FONT=Courier New]block ram14: hash matches[/FONT]
[FONT=Courier New]battery PNP0C0A:00: hash matches[/FONT]
[/INDENT]as this doesn't appear to be indicating a PCI device or even a module, I'm not sure how to address this.

Does anyone have suspend-to-ram working with Toshiba A100 on Jaunty?

thanks!

---

### Post by lisati on 2009-05-17
I have a Toshiba A100 but haven't used the suspend function. Even if I had, I think my A100 has a different chipset.....Yours came with Vista?????


Sorry I couldn't help.

---

### Post by wonderbuntu on 2009-05-17
Yes, it came with Vista Basic--lucky me.  The model is Satellite A100-VA1.  Can you try the suspend?  Just make sure you've saved any data before doing it.  You may find that to boot again, you'll need to pull the AC cord out, as well as remove the battery.  In other cases, you can just hold down the power button for 4 seconds or so to recover.  Thanks

---

