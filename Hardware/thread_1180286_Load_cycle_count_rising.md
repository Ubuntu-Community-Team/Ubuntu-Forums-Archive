---
title: "Load cycle count rising"
date: 2009-06-06
forum: Hardware
---

### Post by svenskmand on 2009-06-06
Hello,

I recently noticed that my hdd spin down, just to spin up around 15 seconds later, then around 30 seconds later it spins down again.

I checked if the load cycle count increases with 

```

sudo smartctl -a /dev/sda | grep 193

```

and it increases regularly.

So my question is how do I disable this, so my hdd will not shorten its life-span dramatically?

Best regards :)

---

### Post by ssri on 2009-06-06
Try "sudo hdparm -B 254"

You can check which power management settings are set via:

"sudo hdparm -I /dev/sda"

Then monitor the load_cycles using smartctl

---

### Post by svenskmand on 2009-06-07
> **ssri said:**
> Try "sudo hdparm -B 254"

You can check which power management settings are set via:

"sudo hdparm -I /dev/sda"

Then monitor the load_cycles using smartctl

this works :), then how do I changed it so it remains after boot-up/reboot?

---

### Post by ssri on 2009-06-08
> **svenskmand said:**
> this works :), then how do I changed it so it remains after boot-up/reboot?

It should automatically retain the settings after you changed it, at least it did for me.  Reboot and run the info command I listed earlier to see if ubuntu retained your settings.  Here's a sit that goes into greater detail in changing the startup settings if your changes were not kept.

[http://www.theworldofstuff.com/linux/ubuntufix.html](http://www.theworldofstuff.com/linux/ubuntufix.html)

---

### Post by svenskmand on 2009-06-10
Thanks, it seems to work, just as you said :)

---

