---
title: "gnome-screensaver sometimes makes Thinkpad X60s freeze"
date: 2007-12-06
forum: Hardware &amp; Laptops
---

### Post by schallstrom on 2007-12-06
When I lock my screen and then want to unlock it my Thinkpad X60s sometimes (maybe 3 out of 10 times) completely freezes so I have to turn it off and on with the power button.

When the screesaver is active, the normal behavior when you move the mouse or press any key is: the screensaver goes away and instead theres the password prompt. But about 3 out of 10 times the screensaver just halts and I have to power cycle the laptop. This is a big pain in the *** because I'm often working in a library, and when I go away from the laptop in a public space I have to lock the screen of course, so this bug has a big impact on my productivity :(

I'm using Ubuntu 7.10 on the laptop.

Is anyone experiencing the same problem or maybe someone even got a solution?

---

### Post by dragonflyseven on 2007-12-08
I am having the same problem, but it is every time the screensaver comes on. It just started since I upgraded to ubuntu studio, which gave me a new kernel. I have an invidia card with an intel core 2 duo.

---

### Post by schallstrom on 2007-12-10
> **dragonflyseven said:**
> I am having the same problem, but it is every time the screensaver comes on. It just started since I upgraded to ubuntu studio, which gave me a new kernel. I have an invidia card with an intel core 2 duo.

Thanks for your answer. At least I'm not the only one experiencing this. Looks like it's not a fault of the graphics driver or something like this cause you have an Nvidia chip, I have a Intel graphics chip.

```

root@shuriken:~# lspci|grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

```

What is Ubuntu Studio?

---

### Post by sceo on 2007-12-13
I am on a desktop and have the Intel 945 graphics chip.  I'm using the Intel experimental driver, which is blacklisted in Compiz (so my effects are disabled).

Whenever a screensaver starts, I just get a black screen and the computer is locked completely (have to power cycle).  I've just switched to no screensaver, and just use power-management after 20 minutes... but some of the screensavers are really cool so was wondering what the problem might be.

---

