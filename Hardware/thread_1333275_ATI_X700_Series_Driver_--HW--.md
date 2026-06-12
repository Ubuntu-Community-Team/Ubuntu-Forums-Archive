---
title: "ATI X700 Series Driver --HW--"
date: 2009-11-21
forum: Hardware
---

### Post by kostaskoukos on 2009-11-21
Hi.

Does anyone knows how can i install some driver on Ubuntu 9.10 for ATI X700 Pro.
It seem that there is no available driver with 3D acceleration for this GPU in the repository.
When i try to enable the "Extra" visual effects so as i can use compiz the system didn't
found any restricted driver to use.

Not even envyng managed to find any compatible driver for this GPU.

After this i tried to install the official bin from ATI but this attempt failed as well.

Does anyone knows what can i do in this case or how can i build a kernel module for
this GPU?

Thanks.

PS * I read a previous note about a list of incompatible HW. I think it is good idea 
to have such a list of compatible or incopatible HW by category.

---

### Post by realzippy on 2009-11-21
You cannot;or you have to downgrade xorg..ATI stopped support for "old" cards since 9.04.If you want fglrx you have to choose ubuntu 8.10.
Which runs perfectly...

---

### Post by Citadel1980 on 2009-11-22
Check out this Ubuntu HowTo:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)


The X700 card is not an actively supported card by ATI. It is in the legacy category now. If you want to use the ATI driver then you need to use either Ubuntu 8.04 LTS or Ubuntu 8.10. From 9.04 onwards you can only use the drivers provided by the Linux community unless you do some extreme hacking.

Check out the above mentioned HowTo for further info.

I hope this helps.

El CId

---

