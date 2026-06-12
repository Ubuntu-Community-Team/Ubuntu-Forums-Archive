---
title: "Error when use PM-Utils to hibernate my computer"
date: 2014-11-29
forum: Hardware
---

### Post by inconsapevole2 on 2014-11-29
Hi,


I have a problem that presents itself to me when I go to hibernate the PC via pm-utils.
Mine is a mini PC on which I installed ubuntu without a GUI, then when I give pm-hiberante the computer actually hibernates but just before it displays an error:


pciehp 0000: 00: 1c.0: pcie04: Device 0000: 01: 00.0 already exists at 0000: 01: 00, can not hot-add
pciehp 0000: 00: 1c.0: pcie04: Can not add device at 0000: 01: 00


this obviously having hibernated intends screen when you turn, and as I often do a resume on this computer hibernates this error accumulates and it bothers me.
How do I figure out what is it? I tried a lot, I read in some places that it is a bug, which is in some other form or do not get mad response.
Can anyone give me a hand for debugging? At least I understand what creates this error.

---

### Post by inconsapevole2 on 2014-12-01
noone help me?

---

### Post by weatherman2 on 2014-12-01
Hibernation is not well supported in Linux across different hardware.  In the desktop versions of Ubuntu, it is not even enabled by default anymore.  You might try to use Standby instead.  It probably consumes almost the same power anyway.  Even a computer "powered off" but plugged into the wall still consumes a small amount of power, a few watts maybe.  In standby it wouldn't consume much more.

---

