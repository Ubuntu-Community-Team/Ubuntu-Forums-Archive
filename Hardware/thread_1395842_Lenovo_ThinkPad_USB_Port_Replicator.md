---
title: "Lenovo ThinkPad USB Port Replicator"
date: 2010-02-01
forum: Hardware
---

### Post by t.rain on 2010-02-01
**Hi forum,**

I'm using ibm/lenovo thinkpads for years always in combination with linux, and I'm highly satisfied with this so far!!

Now it's time for a new notebook, and I'm going to get the X301 this time: 
[http://shop.lenovo.com/us/notebooks/thinkpad/x-series/x301](http://shop.lenovo.com/us/notebooks/thinkpad/x-series/x301)

i have multiple workplaces, so I do rely on a good docking solution. To my surprise, lenovo stopped equipping thinkpads with a docking port :( They now suggest to buy the USB docking solution, like this one here:

[http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-72822](http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-72822)

**My questions:**
(i) Does the USB docking work with Linux? i somehow heard that they use displaylink technology, so is the displaylink driver compatible? Does anyone use the Lenovo USB docking with linux/ubuntu?

Thanks a lot!

t_rain

---

### Post by wiswaud on 2010-02-10
> **t.rain said:**
> 

**My questions:**
(i) Does the USB docking work with Linux? i somehow heard that they use displaylink technology, so is the displaylink driver compatible? Does anyone use the Lenovo USB docking with linux/ubuntu?


I have an X300 and am contemplating the purchase of that dock as well, and was wondering the same thing... i might just go ahead and buy it, but hopefully will find some info in the meantime!

I can say that the X300 works wonderfully with Ubuntu, though. I absolutely love that laptop.

---

### Post by wiswaud on 2010-02-10
Found out a few things.

The Lenovo USB port replicator doesn't seem to use DisplayLink, which is the new "standard" technology that makes a display work over USB (it's basically a graphics chip which connects to the computer through USB instead of through PCI or PCIX like normal graphics cards do). I can't find anything pertaining to using that dock under linux; my guess is that it's a fairly proprietary thing, and that it might not now nor ever work with linux, because it's a custom lenovo device.

If you venture into DisplayLink port replicators, however, you have a better chance of them working. The [Kensington dock]("http://us.kensington.com/html/17444.html") is [cheaper]("http://www.amazon.com/Kensington-Universal-Notebook-Docking-Ethernet/dp/B002EREH74"), for example, and uses DisplayLink.

I found [this review]("http://www.geardiary.com/2009/11/18/review-kensington-k33926us-universal-notebook-docking-station-with-vgadvi-and-ethernet/") for it which says everything on it *except* the display works on linux, but that displaylink support is coming to linux real soon, and might work right now if you're willing to recompile stuff yourself, since [there's already a linux driver]("http://libdlo.freedesktop.org/wiki/") for many DisplayLink chipsets.

What i don't know is how the driver presents itself - will it looks like another monitor and will the Gnome display settings allow you to just extend your desktop to it, or what? No clue. It's not very expensive, so i might spring for it and try it out anyways.

---

### Post by t.rain on 2010-02-12
@ wiswaud

thanks for you're reply...

I would love to hear from you if you got the docking working under Linux (lenovo's original or the displaylink based). Pls. keep us updated here..

I'm still thinking of buying an x200 instead of the x300. It's all about the docking....

thanks
t_rain

---

