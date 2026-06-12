---
title: "Suggestions on UPS that works well with Ubuntu"
date: 2013-01-16
forum: Hardware
---

### Post by jam1492 on 2013-01-16
Hello,

Does anyone have suggestions on purchasing an uninterupted power supply (UPS) that works easily in Ubunutu -- either models that work particularly well or models to avoid?  

My linux skills are not too great and I don't have lots of extra time on my hands, so I'm hoping to find something that more or less works out of the box, including the automated shutdown on blackouts.

Thanks very much for any suggestions you might have.

Alex

---

### Post by SeijiSensei on 2013-01-16
I like APC because it is [well-supported in Linux]("http://ubuntuforums.org/showpost.php?p=12176130&postcount=2").

---

### Post by d4m1r on 2013-01-16
I use an APC UPS as well, but it makes little to no difference in my opinion....UPS units are OS agnostic.

---

### Post by tgalati4 on 2013-01-16
I like the older APC units with metal cases.  The plastic ones melt and tend to catch fire.

---

### Post by SeijiSensei on 2013-01-17
> **d4m1r said:**
> I use an APC UPS as well, but it makes little to no difference in my opinion....UPS units are OS agnostic.

Only if the device includes software that works with Linux as well as Windows.  The apcupsd daemon executes a graceful shutdown when the batteries run low, and it can notify the other machines on the network so they can shut down gracefully as well.

---

### Post by geudrik on 2013-01-17
I run two APC SmartUPS units, a 3000va and a 1500va, both with Remote Access Cards. The cards give you a Web interface to interact with, as well as a way to have it talk to a monitoring server. 

Go APC, linux support is pretty native (especially in their higher end models)

---

### Post by jam1492 on 2013-01-21
> **geudrik said:**
> I run two APC SmartUPS units, a 3000va and a 1500va, both with Remote Access Cards. The cards give you a Web interface to interact with, as well as a way to have it talk to a monitoring server. 

Go APC, linux support is pretty native (especially in their higher end models)

Thank you all very much for the advice!  It sounds like APC is the way to go.  

I'm not familiar with remote access cards.  Should I add them as a card to the computer attached to the UPS?  Do they come with the UPS or are they bought separately?

---

