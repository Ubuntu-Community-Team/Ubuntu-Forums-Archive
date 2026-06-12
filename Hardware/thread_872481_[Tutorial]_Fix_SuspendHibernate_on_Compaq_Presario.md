---
title: "[Tutorial] Fix Suspend/Hibernate on Compaq Presario V3xxx Laptops!"
date: 2008-07-28
forum: Hardware
---

### Post by SidStudios on 2008-07-28
I've created a tutorial based on TheAlmightyCthulhu's post on Foxconn motherboards. My laptop, a Compaq Presario V3633AU did not work with suspend and hibernate on Hardy until I read his post and tried something out myself.
I decompiled my own DSDT table only to find something relatively similar--Linux gets a different ACPI table than Windows. I thought this was a bit strange, so I modified it and recompiled it so that Linux had the same table as Windows. 
I rebooted, and guess what?
***_SUSPEND AND HIBERNATION FINALLY WORK!_***
I've posted the tutorial on my own site, here:
[http://hacktalk.org/fix-the-suspend-and-hibernate-functions-on-compaq-presario-v3000-v3500-series-laptops-16/](http://hacktalk.org/fix-the-suspend-and-hibernate-functions-on-compaq-presario-v3000-v3500-series-laptops-16/)
[B]
I do NOT have ads on the website, I have nothing to gain from people visiting.[/B]
This is for the good of the community, and if moderators feel that I should not 'advertise' like this, please edit my post and remove my link. I feel that this will greatly benefit all those using HP/Compaq laptops.
Just for information's sake, here are my specs:
Processor: AMD Turion X2 (TL-58, 1.9GHz Dual Core)
RAM: 4GB (3.1GB Recognized on Ubuntu 8.04 32bit)
Video Card: NVidia Go  7150
Motherboard (?): NVidia MCP67
Speakers: Altec Lansing

I hope this helps! Thanks,
Sid

---

### Post by SidStudios on 2008-07-28
Reserved for future updates and FAQ.

---

### Post by mma8x on 2008-09-11
404 error.  why not post it here as well?

---

### Post by Gnuus on 2008-12-04
Doesn't help if the link [http://hacktalk.org/fix-the-suspend-and-hibernate-functions-on-compaq-presario-v3000-v3500-series-laptops-16/](http://hacktalk.org/fix-the-suspend-and-hibernate-functions-on-compaq-presario-v3000-v3500-series-laptops-16/) is dead.............

---

### Post by LaLLi on 2009-09-20
This is why you shoud post these on more than one forum.

---

