---
title: "High temperatures with occasional impeded cooler spin rates"
date: 2021-05-04
forum: Hardware
---

### Post by smith73 on 2021-05-04
After the expiration of the 2 year warranty for an HP 8GB RAM notebook the following activity appeared.
Its main cooler occasionally began to emit audial signs of spinning with some interference. 
The (CPU) temperature readings from psensor jump to 40-50 C during ClamAV scans (always) and sometimes 
from Tor usage. Also there was some sound (very rarely) from an optical DVD drive reader as if it was going 
to be ejected, though it haven't been used for months.

I am planning to clean the cooler. Is there anything else which can be done for maintenance while notebook's
bottom housing is removed? Are there some command line or other tools to figure out this situation?

This may be another question, but I tried to disable several unnecessary modules (like cupsd, avahi for printers and
Apple device which I don't use) consuming CPU resources with lsmod. I used "lsmod --status-all" command to
 find the active module names, but now this command is not applicable, and just "lsmod" provides apparently another
 list of modules. Can disabling several or more modules (temporarily) help to prevent these high temperatures?
I suppose not much, but still would be curious to know how to disable unnecessary modules like bluetooth for example,
which a user currently is not using.

I'm using Ubuntu Mate 20.04 LTS.

---

### Post by CatKiller on 2021-05-04
> **smith73 said:**
> I am planning to clean the cooler. Is there anything else which can be done for maintenance while notebook's bottom housing is removed?  

Depending on how easy it is, you could change the thermal interface material between the processor and heatsink. Some cooling solutions are better than others, and some hardware is more accessible than others. Otherwise, compressed air through the vents to blow the dust out. 

> I tried to disable several unnecessary modules (like cupsd, avahi for printers and
Apple device which I don't use) consuming CPU resources with lsmod. 

Don't do that. You're just going to break it. You're using Linux like Windows - running antivirus and "disabling unnecessary services." Linux isn't Windows. Kernel modules for hardware you aren't using use zero resources. 

> Can disabling several or more modules (temporarily) help to prevent these high temperatures?

You don't have high temperatures. 40-50 °C in a laptop is perfectly respectable. If you were up to, like, 90 °C you'd have high temperatures.

---

### Post by Yellow Pasque on 2021-05-05
It could just be a loose wire/cable.

> **CatKiller said:**
> Depending on how easy it is, you could change the thermal interface material between the processor and heatsink. 

That seems unnecessary to me, for a laptop that is only 2 years old and not overheating.

> Don't do that. You're just going to break it.

I've been running Ubuntu variants for over 15 years, and one of the first things I always do on a new install is fire up Synaptic and get rid of the cruft. I've yet to "break it" doing that.

---

### Post by CatKiller on 2021-05-05
> **Yellow Pasque said:**
> That seems unnecessary to me, for a laptop that is only 2 years old and not overheating. 

Sure, but OP asked about useful maintenance that could be done. I'd always consider changing the thermal paste whenever I was fiddling with the cooling, although the result of the consideration would often be not to. 

> I've been running Ubuntu variants for over 15 years, and one of the first things I always do on a new install is fire up Synaptic and get rid of the cruft. I've yet to "break it" doing that.

An experienced user removing unneeded packages is an entirely different thing to an inexperienced user randomly removing kernel modules.

---

