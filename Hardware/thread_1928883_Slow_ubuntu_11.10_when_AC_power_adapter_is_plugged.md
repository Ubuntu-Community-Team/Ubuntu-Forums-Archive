---
title: "Slow ubuntu 11.10 when AC power adapter is plugged in"
date: 2012-02-20
forum: Hardware
---

### Post by xizzling on 2012-02-20
I have a new laptop Lenovo ThinkPad L520 (7859-5BG) Core i5-2520M(2.5GHz) with 4GB RAM.

Having installed Ubuntu 11.10 32-bit, while browsing with Chrome on GNOME classic (no effects), I noticed 173% CPU usage by chrome browser process, and the system slowly got very very slow,

Now, at this stage as I removed the power adapter, the system suddenly got faster (and stopped the lagging behavior) and CPU usage drops down to 48% !! 

Can anyone tell me what exactly does this indicate ? What is wrong, is it some bug with power management or what ?


Regards,
:confused:

---

### Post by xizzling on 2012-03-20
I am in a position to explain further:

1. The system slowly starts to lag once the AC adapter is charging my battery.
2. As soon as charger/adapter is removed system is fine again (stops lagging, processes stop hogging CPU)
3. When battery is taken out of its compartment altogther, and AC adapter powers up laptop - then ubuntu sails smooth and quick !

So why does it lag as it is charging the battery ? Is it a bug ?

Any help will be highly appreciated - I have tried "top", "iostat" etc. to figure out but nothing much that seems unusual. Just that when adapter is connected (with battery inside) - just about every process take tripple its normal CPU usage.

---

