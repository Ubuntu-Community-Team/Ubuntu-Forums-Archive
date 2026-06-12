---
title: "Error when trying to boot using Ubuntu CD"
date: 2009-07-27
forum: Installation &amp; Upgrades
---

### Post by Esmerelda on 2009-07-27
Hey,
I haven't installed it, but I'm trying it out by booting it with the CD.  After I get pass the main screen i get something that says:
 
Mp-BIOS bug: 8254 Timer not connected to IO-APIC
Kernel panic - not syncing: IO-APIC  + timer doesn't work! boot
ith apic=debug and send a report. Then try booting with the noapic option.
 
No idea what that means. I don't know a whole a lot about computers, so could someone try and explain what I should?
 
Thanks.

---

### Post by fbugnon on 2009-07-27
At the very first boot screen, after choosing your language, press **F6** and choose **noapic**.

If you want to understand what it means, check

[http://wiki.linuxquestions.org/wiki/APIC](http://wiki.linuxquestions.org/wiki/APIC)
or
[http://en.wikipedia.org/wiki/Apic](http://en.wikipedia.org/wiki/Apic)

Hope this helps you boot correctly.

---

