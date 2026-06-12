---
title: "Problem with driver for ATI Mobility Radeon 7500"
date: 2010-03-03
forum: Hardware
---

### Post by Thomas Korbel on 2010-03-03
Hello,
I'm a newcomer concerning Linux and ubuntu. I have a problem with the driver for my graphic-card (ATI Mobility Radeon 7500). I think the automatically driver is not the proper one! It would be nice if some can help me! I'm using a ThinkPad T40.

Cheers Thomas :KS

---

### Post by lucazade on 2010-03-03
> **Thomas Korbel said:**
> I have a problem with the driver for my graphic-card (ATI Mobility Radeon 7500). I think the automatically driver is not the proper one! It would be nice if some can help me! I'm using a ThinkPad T40.

Hi!
You don't need to install any driver, just use the open source provided by default.
That old chipset is not supported by proprietary Ati driver (fglrx) and you can't use other drivers then the opensource radeon.
You can just tweak xorg.conf settings to gain performances (not needed in Lucid Lynx btw), i'll attach the one i use on my T40. ;)

---

### Post by lucazade on 2010-03-05
Solved?

---

### Post by quidome on 2010-03-12
I have problems with the lucid install on my T41. It seems highly unstable. After a very short time of using X the whole system freezes.

If I log into X and switch to vt1 to work there, the system won't freeze. I did my update/grade that way, without a problem. Once I switch back to X, it freezes, within a minute.

This really feels as an X/driver problem. I'll try your setup once I'm home again.

---

### Post by Thomas Korbel on 2010-03-13
It is working! Thank you!

---

