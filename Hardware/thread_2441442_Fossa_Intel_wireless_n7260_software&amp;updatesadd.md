---
title: "Fossa Intel wireless n7260 software&amp;updates/additional drivers state device error"
date: 2020-04-23
forum: Hardware
---

### Post by alexukalex on 2020-04-23
Hello everyone - just installed 20.04LTS and am loving it already of course.
Poking around in the software&updates/additional drivers - I get the notification that my Intel wireless 7260 (dual band n-7260) isnt working.... however I can connect wirelessly on 2.4 and also 5ghz... my bluetooth is also working. Any ideas why it should be flagged as not working???
lshw -C network shows ethernet & wireless....
Any of you knowledgeable people any ideas?

---

### Post by kc1di on 2020-04-24
The intel drivers have been moved to the Kernel and there is not longer any driver to install with addition driver tool. So I'm guessing it can find a working driver and thus thinks the card is not working.  If it working fine I wouldn't worry much about it.

---

### Post by alexukalex on 2020-04-26
Thanks for the reply Dave, great work on the kernel then. Focal Fossa is great so far.

---

