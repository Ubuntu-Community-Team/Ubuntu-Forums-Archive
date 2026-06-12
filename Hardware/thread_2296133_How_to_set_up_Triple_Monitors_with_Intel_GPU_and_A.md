---
title: "How to set up Triple Monitors with Intel GPU and AMD Radeon in Ubuntu 15.04?"
date: 2015-09-23
forum: Hardware
---

### Post by YLTO on 2015-09-23
[COLOR=#111111][FONT=Ubuntu] I want to set up three monitors and so ...

[LIST=1]
[*]My ubuntu version is 15.04
[*]My Graphic card is : HIS AMD Radeon R9 380 IceQ X² OC 4GB[http://www.hisdigital.com/un/product2-887.shtml](http://www.hisdigital.com/un/product2-887.shtml)
[*]I have installed fglrx and catalyst control center
[*]My processor is : Intel i7-6700k with its iGPU Intel® HD Graphics 530
[*]My desired setup is one monitor using discrete gpu while the other two monitors using iGPU
[*]My Motherboard is msi-Z170A PC mate and have the option in BIOS to turn on the iGPU.
[IMG]http://i.imgur.com/rn6kxnN.png[/IMG]
[*]My triple monitor setup with iGPU + GPU enabled has worked well in Windows 10
[/LIST]
Unfortunately when I tried the same way I apply to windows 10, Ubuntu just doesn't work and it show like this image 
[IMG]http://i.stack.imgur.com/AiwJH.png[/IMG]


So How do I suppose to setup three monitors with iGPU and GPU enabled?


[/FONT][/COLOR]

---

### Post by QIII on 2015-09-23
I'm assuming this is a desktop?

Your motherboard may allow that, but I'm not sure the Linux drivers supplied by the OEMs will work together simultaneously.

---

### Post by YLTO on 2015-09-24
> **QIII said:**
> I'm assuming this is a desktop?

Your motherboard may allow that, but I'm not sure the Linux drivers supplied by the OEMs will work together simultaneously.

Yes this is a desktop. is there any workaround to make it possible?

---

