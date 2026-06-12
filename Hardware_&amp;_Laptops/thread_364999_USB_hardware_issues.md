---
title: "USB hardware issues"
date: 2007-02-19
forum: Hardware &amp; Laptops
---

### Post by BradNeuman on 2007-02-19
I have an Acer Aspire 5102WLMi laptop which I got about a year ago. I have installed Kubuntu 6.06 x64, and so far I have been pleased. One issue I have which is really just an annoyance is that sometimes my USB devices aren't recognized when I plug them in. I have a USB mouse and I also use an External USB soundcard. These both work fine most of the time, but sometimes if they are unplugged they are not recognized when I plug them in. They don't even get any power for the computer (I think) because the mouse doesn't light up, nor does the power light on the soundcard turn on.

The bad part is that the same thing happened with Windows. Under both operating systems, logging out of the current user fixes the problem. In fact, my USB devices get power while I am logging out on both OSs.

Does anyone know a possible permanent fix for this? I have a feeling it might just be my laptop, but at least can someone tell me how to re-scan the USB devices or restart some service or something instead of having to log out each time this happens?

---

### Post by gradedcheese on 2007-02-19
yeah, it sounds like a hardware problem.  perhaps there's an updated BIOS that you can flash?  they may have fixed it there.

I don't remember if 6.06 still uses hotplug, but if it does you can:

sudo /etc/init.d/hotplug restart

if not, then the new way is:

sudo /etc/init.d/udev restart

That should force a re-scan.

---

