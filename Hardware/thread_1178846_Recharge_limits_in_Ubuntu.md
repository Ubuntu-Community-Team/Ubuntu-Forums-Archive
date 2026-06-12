---
title: "Recharge limits in Ubuntu?"
date: 2009-06-04
forum: Hardware
---

### Post by alccode on 2009-06-04
Hi everyone,

After reading up a bit on proper "care and feeding" of Lithium-ion batteries in laptops (in this specific case, a Lenovo Thinkpad X200's battery), I came across some recommendations about recharge behaviours.  Specifically, during general battery use,


[LIST]
[*]let the battery drain to at least 40% before recharging
[*]only recharge to 95% of capacity, not more
[/LIST]
This apparently maximizes the life of the battery (I don't recall the source, but can probably find it if needed).

Now, the real question is, can this behaviour be implemented in Ubuntu?  Specifically, at least the second point -- i.e., to stop recharging once the battery is at 95%.

What my Vista partition on this laptop can do is be configured so that, whenever the power cable is plugged in, it will supply power to the system, but *not* recharge the battery, unless the battery charge is below 40%.  At that point, it will charge up to 95%, and stop there.

Any info is appreciated.  If this is just not possible, then I guess I'll do it myself, by manually plugging and unplugging the power cable as necessary.

---

### Post by Steelmourne on 2009-06-05
The only real battery advice I've read is to discharge the battery completely to 0% occasionally, then fully recharge to make sure it keeps power. I'm not aware of any app that does what you want under Ubuntu.

---

