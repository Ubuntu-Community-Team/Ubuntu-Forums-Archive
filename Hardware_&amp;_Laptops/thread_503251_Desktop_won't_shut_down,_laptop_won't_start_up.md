---
title: "Desktop won't shut down, laptop won't start up"
date: 2007-07-17
forum: Hardware &amp; Laptops
---

### Post by pickarooney on 2007-07-17
I'm experiencing these conflicting phenomena on my two installations of Feisty Fawn at the moment.
On the desktop, when I choose to shut down I get as far as the Kubuntu shutdown screen. The blue/black bar gradually moves to the end, the screen goes black a moment and the bar (now completely black) and the kubuntu logo appear again. An hour later, they're still there.

Meanwhile, my laptop shuts itself off every hour or thereabouts when not in use and I have to remove the battery and turn it back on to get it back working again. I think there's some problem with it auto-hibernating and not waking up.

I have acpi=off noapic nolapic in my menus.lst on the desktop to work around an MP-BIOS bug, if that's relevant.

---

### Post by EXCiD3 on 2007-07-23
> **pickarooney said:**
> Meanwhile, my laptop shuts itself off every hour or thereabouts when not in use and I have to remove the battery and turn it back on to get it back working again. I think there's some problem with it auto-hibernating and not waking up.

Suspend/Hibernate in Ubuntu are very unstable as of yet. If you modify the power settings to disable auto-hibernate you can have it turn the screen off or shutdown the laptop instead. Many people have had problems with the nvidia driver conflicting with hibernate/suspend. Most of the time the laptop will not resume correctly leaving you at a black screen.

I would just recommend avoiding suspend/hibernate until there is better support for it. If you can't go without these, you can try tweaking ubuntu, which cuts startup/shutdown times, making it much easier to just shutdown your laptop for a bit, instead of hibernating or suspending.

Sorry i can't help with your desktop problem though...

---

