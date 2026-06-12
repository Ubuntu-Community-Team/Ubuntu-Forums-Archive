---
title: "Gigabyte GA-EP35-DS3L Motherboard Overheating"
date: 2008-10-22
forum: Hardware
---

### Post by awg on 2008-10-22
I've been having a very odd issue since I bought this motherboard.  The southbridge (Intel ICH10) overheats.  It happens predictably when I stream movies or music over NFS to my other computer.  It does have four hard drives (two RAID1 arrays) in it, but this seems like a reasonable load for a southbridge.  I do have AHCI turned on in the BIOS, if that makes any difference.  I'd be tempted to say it's a defective motherboard, but it happened on another motherboard that was completely different except for having an ICH10.  I have a fan pointing directly at the (fanless) heatsink, so it doesn't seem to be a cooling issue (although if it persists, I might try putting on a bigger heatsink).  I'm running Xubuntu Hardy amd64.

Is it possible that there's a bug in Hardy's drivers that would be causing this?  Would using CIFS instead of NFS help?  Any suggestions?

Thanks.

Edit: It's actually an ICH9, not an ICH10.  I think the other board I had this problem with was an ICH10.

---

### Post by ardvark71 on 2008-10-22
Hi...

In terms of your settings, I don't see how this would be cause of your problem. It might be a design or manufacturing flaw in the chipset that causes it to overheat.

If you want to try a bit more aggressive attempt at keeping it cool, you can try this product from Thermaltake...

[http://www.computersonics.com/_e/Chipset_Fans/product/CF-TT-4458/Thermaltake_Extreme_Spirit_chipset_cooler_.htm](http://www.computersonics.com/_e/Chipset_Fans/product/CF-TT-4458/Thermaltake_Extreme_Spirit_chipset_cooler_.htm)

A futher writeup of the product by the manufacturer is available here...

[http://www.thermaltakeusa.com/coolers/chipset/a1899.htm](http://www.thermaltakeusa.com/coolers/chipset/a1899.htm)

EDIT: After looking closer at this product, the southbridge heatsinks don't look very big, defeating the purpose. Take a look here instead for some larger heatsinks...

[http://www.frozencpu.com/cat/l2/g40/c16/list/p1/Air_Cooling-Chipset_HeatsinksCoolers.html](http://www.frozencpu.com/cat/l2/g40/c16/list/p1/Air_Cooling-Chipset_HeatsinksCoolers.html)

Hope this helps... :)

Best Regards...

---

