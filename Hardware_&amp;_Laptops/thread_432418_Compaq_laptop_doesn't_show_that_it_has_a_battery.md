---
title: "Compaq laptop doesn't show that it has a battery"
date: 2007-05-04
forum: Hardware &amp; Laptops
---

### Post by jketvirtis on 2007-05-04
Hi-

I recently installed Ubuntu 7.04 on my Compaq Presario 2500.  I had used previous versions of Ubuntu (Dapper, Edgy) and Kubuntu (Edgy, Feisty) without any real problems.  This time I've run into something that stumps me.  Whenever I unplug the power, nothing happens.  The Gnome Power Manager never changes to show a battery.  When I went into Device Manager, the Battry Bay section says a battery isn't present when it actually is.  

When I type acpi -V, I get the following:
     Thermal 1: ok, 5.0 degrees C
  AC Adapter 1: on-line

My laptop runs pretty hot, so not only does it not show no battery but also the wrong temp.  Even when I unplug the laptop it still says the Ac Adapter is on-line.

The one thing I could think of to try was reinstalling a whole host of power-related things, such as acpi, acpid, and gnome-power-manager.  That did nothing.  I'm hoping you folks have some ideas that I could try.  This is odd because I never had any such problem with Kubuntu Feisty.  Any help you could provide would be much appreciated.

Thanks.

---

### Post by jketvirtis on 2007-05-04
I don't want to bump my own post, but this *is* kind of an important issue for me, and I would hate to have to try something like a reinstall to fix it.

---

### Post by jketvirtis on 2007-05-04
Okay, I tried reinstalling the kernel, and that didn't do anything either.  Still crossing my fingers to find something.

---

### Post by jketvirtis on 2007-05-04
I keep on posting to my own thread, but I tried something else that I thought might be informative: I tried booting in from the live cd to see if was just my particular install that wasn't working properly, but that was not the case.  Even the live cd did not recognize that I had a battery.  I'm going to file a bug report, but if anyone has any ideas, I'm still trying to fix this on my own.

---

### Post by jketvirtis on 2007-05-04
Well I don't know how it possibly worked, but I managed to solve my problem.  I popped in the Edgy live cd I still had lying around, and it was working: acpi -V displayed correctly and the gpm would change when I unplugged the computer.  I boot back into Feisty, and now it's working on my install too.  It seems odd to me, but I'm just happy it worked.

---

### Post by aubreyisland on 2007-12-02
I have an Acer 5050 and am having the same problem in Gusty 7.10. acpi -v same thing...

:(

I am going to try booting Feisty and see what happens...

---

