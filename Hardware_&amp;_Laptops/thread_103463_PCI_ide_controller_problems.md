---
title: "PCI ide controller problems"
date: 2005-12-14
forum: Hardware &amp; Laptops
---

### Post by hamiltonlight on 2005-12-14
Hello guys,

I've just added a Promise Ultra100 tx2 ide controller card to my machine and its having problems booting up now (post Breezy installation, also dual booting XP). 

I suspect its having trouble assigning the ide channels on boot up. After trudging the newsgroups I think I have to pass it ide="io address" parameters to make it assign the pci channels as ide2 and ide3. 

Since linux live distros and the breezy install disc hangs with the card installed I have not been able to list the ioports file to see what addresses the card uses. I can boot into XP with the card installed however and have found that XP lists a set of io ranges. 

Is it ok to pass these ranges to the linux kernel to force ide2 and ide3 assignment to the card? 

Also, some of the posts say use the append=ide2='io range' whilst others just use ide="io range". Can someone clarify this for me please. 

Relatively new linux here and not used to such low level workings of pc hardware. Soon to be changed however I guess! 

My motherboard is an asus A8V deluxe with BIOS 15. I've been through it again and again to try and find a way to make onboard ide controllers the "masters" but no luck so far. 

Any help or suggestions greatly appreciated. :smile: 

Thanks in advance.

Regards,

Hamiltonlight

---

### Post by hamiltonlight on 2006-01-10
Update.

Since starting this thread I have continued to try and get the ide controllers working but no luck. 

I've tried passing ideX=... parameters to the kernel and the cards in different slots etc many times. I'm beginning to think that its a problem with my motherboard and pci ide controllers. It just doesn't like them. 

Ultimately I needed the extra disk storage and have reverted back to Windows to use the ide and raid onboard controllers on the Asus A8V. 

If anyone has come across/solved this problem then please get in contact.

Thanks a lot.

---

