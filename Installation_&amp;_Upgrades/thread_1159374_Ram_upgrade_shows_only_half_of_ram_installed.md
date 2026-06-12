---
title: "Ram upgrade shows only half of ram installed"
date: 2009-05-14
forum: Installation &amp; Upgrades
---

### Post by YMS_1975 on 2009-05-14
So I decided to upgrade my sons older PC with new ram, and just ran into a bit of a hiccup.

The motherboard is an [ECS P4M800PRO-M(V2.0)]("http://www.ecsusa.com/ECSWebSite/Downloads/ProductsDetail_Download.aspx?detailid=673&DetailName=Manual&DetailDesc=&CategoryID=1&MenuID=6&LanID=9"). I know this because I opened up the case and verified it physically on the board. According to the motherboards manual, it's capable of a maximum upgrade of 2 GB total ram, which is what I attempted to upgrade it to.

I ordered Kingston ram using the Kingston ram configurator, and ended up purchasing this type of [RAM]("http://www.directcanada.com/products/?sku=12410BD0889&vpn=KVR533D2N4/1G&manufacture=KINGSTON").

Before the upgrade, there was only 512 MB of ram (1 chip). After the upgrade, it shows 1024 MB. I removed the old ram chip and then installed the two new ones. I know the new ram's not defective because I've taken each chip out, and when I booted the PC it recognized the chip was in there, BUT it only recognizes HALF of what the chip actually is.

So two 1 GB sticks of ram shows up only as 1 GB of ram. What gives?

---

### Post by kidders on 2009-05-16
Hi there,

Sounds like the module density is too high. Your motherboard may only support low density RAM, but the manual doesn't seem to specify.

If I'm right, and you're using the latest available BIOS version, you may have to swap your RAM for a low density equivalent. Does anyone you know have a newer motherboard you could check your RAM with ... just to be sure it works?

---

### Post by coffeecat on 2009-05-16
> **YMS_1975 said:**
> Before the upgrade, there was only 512 MB of ram (1 chip). After the upgrade, it shows 1024 MB. I removed the old ram chip and then installed the two new ones. I know the new ram's not defective because I've taken each chip out, and when I booted the PC it recognized the chip was in there, BUT it only recognizes HALF of what the chip actually is.

So two 1 GB sticks of ram shows up only as 1 GB of ram. What gives?

Could you clarify exactly what you mean, because I might have a similar issue with an ECS board (a different one - GeForce6100PM-M2)? Do you mean that if you put a single 1GB stick in, the BIOS only shows 512MB? Or do you mean that a single 1GB stick is shown as 1GB, but two still only show up as 1GB?

The reason I ask is that my ECS motherboard has two DDR2 slots, each capable of taking a module up to 4GB, making a total maximum of 8GB. Or, at least, that's what the manual says. Crucial don't stock 4GB modules compatible with this m'board, but I haven't bothered to check other makes. Whatever, I've tried two matched pairs: 2 x 1GB and 2 x 2GB, both pairs from Crucial. Even though each works singly in slot 1 (and is recognised as 1GB or 2GB, whichever it is), I can't get the second to be recognised. (The 2 x 2GB pair are working quite happily in another machine now.) I tried using single sticks in slot 2, and the machine wouldn't even start. I can't see anything in the BIOS to activate slot 2, so I've concluded that slot 2 is defective. According to the manual for my board, you can put one stick in either slot, so leaving slot 1 empty should work.

So, have you tried a single stick that you know works in slot 2? It's possible you may have a dud slot 2 like mine.

Once I'd worked out what was going on I just shrugged my shoulders and concluded I was unlucky. But if you confirm that you are getting the same, it will be the last ECS board I'll buy. Unless someone can point me to somewhere in the BIOS that I've missed.

---

### Post by YMS_1975 on 2009-05-16
> **coffeecat said:**
> Could you clarify exactly what you mean, because I might have a similar issue with an ECS board (a different one - GeForce6100PM-M2)? Do you mean that if you put a single 1GB stick in, the BIOS only shows 512MB?

**That's exactly what I mean.**

> **coffeecat said:**
>  The reason I ask is that my ECS motherboard has two DDR2 slots, each capable of taking a module up to 4GB, making a total maximum of 8GB. Or, at least, that's what the manual says. Crucial don't stock 4GB modules compatible with this m'board, but I haven't bothered to check other makes. Whatever, I've tried two matched pairs: 2 x 1GB and 2 x 2GB, both pairs from Crucial. Even though each works singly in slot 1 (and is recognised as 1GB or 2GB, whichever it is), I can't get the second to be recognised. (The 2 x 2GB pair are working quite happily in another machine now.) I tried using single sticks in slot 2, and the machine wouldn't even start. I can't see anything in the BIOS to activate slot 2, so I've concluded that slot 2 is defective. According to the manual for my board, you can put one stick in either slot, so leaving slot 1 empty should work.

So, have you tried a single stick that you know works in slot 2? It's possible you may have a dud slot 2 like mine.

Once I'd worked out what was going on I just shrugged my shoulders and concluded I was unlucky. But if you confirm that you are getting the same, it will be the last ECS board I'll buy. Unless someone can point me to somewhere in the BIOS that I've missed.


**My conclusion is that ECS motherboards sucks.**  :D

---

### Post by YMS_1975 on 2009-05-16
> **kidders said:**
> Hi there,

Sounds like the module density is too high. Your motherboard may only support low density RAM, but the manual doesn't seem to specify.

If I'm right, and you're using the latest available BIOS version, you may have to swap your RAM for a low density equivalent. Does anyone you know have a newer motherboard you could check your RAM with ... just to be sure it works?

I have a P4 but not sure if the ram would work in it. Besides, the ram was cheap and to be honest...I'm not willing to open up the P4 case. It's just not worth the hassle. The fact that it recognizes 1 GB is ok with me, but if it's a setting issue I can tinker around with the OS.

---

