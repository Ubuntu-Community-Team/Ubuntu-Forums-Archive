---
title: "Kernel tainted by ATI Proprietary driver"
date: 2010-11-01
forum: Hardware
---

### Post by Guerreiro on 2010-11-01
Esteemed people,

My ubuntu freezes from time to time, I am running the Maverick Meerkat (10.10) version. I think it is the driver for the ATI Radeon 2400 HD PRO card, as this came up in the kern.log :

Oct 26 09:34:52 soloweb-desktop kernel: [   22.807442] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.

Or is there anything else I should be looking at? Does not matter what I do, it just hangs like *snap* that. 

Regards,

---

### Post by coffeecat on 2010-11-01
The tainting comment is standard when you use a proprietary binary driver - it is added automatically. This is for the benefit of the kernel devs when dealing with bug reports. They, obviously, have no control over binary blobs and need to know when one has "tainted" the kernel, because this might be the cause of the bug. The taint comment is added to the kernel logs because bug-reporters often fail to mention they're using proprietary binaries. It doesn't necessarily mean that there is a problem.

That being said, you may be right that the fglrx driver is the cause of your problem. I couldn't find out how well the default open-source driver supports your card. When you first installed, what was video performance like? Did you get any freezes with the open-source driver? What was your reason for installing the proprietary one?

---

### Post by Guerreiro on 2011-03-08
Sorry for gravedigging, I totally forgot to check up on this one again. :$ 

My performances are excellent with the open source driver, I was just new to linux and it had the nice icon on the panel saying install additional drivers and I thought well why not? My mistake, and I will warn lots of others here not to install the ATI propriety driver. I installed it on my laptop same thing there, as well as in other OSs the driver just messes up your display. So no more ATI for me :D

Thanks though for the explanation. :)

---

### Post by coffeecat on 2011-03-08
> **Guerreiro said:**
> Sorry for gravedigging, I totally forgot to check up on this one again. :$ 

My performances are excellent with the open source driver, I was just new to linux and it had the nice icon on the panel saying install additional drivers and I thought well why not? My mistake, and I will warn lots of others here not to install the ATI propriety driver. I installed it on my laptop same thing there, as well as in other OSs the driver just messes up your display. So no more ATI for me :D

Thanks though for the explanation. :)

Yes, many people are misled by that additional drivers prompt popping up making them think they need it. When you say "no more ATI for me", I hope you mean "no more proprietary ATI driver for me". If an ATI card does what you want with the open source driver then that's good. I'm very happy with the ATI open source driver on both my desktop machine and one of my laptops.

---

