---
title: "eATX Power Supply"
date: 2009-12-27
forum: Hardware
---

### Post by GroogFish on 2009-12-27
I recently bought an eatx board and I'm noticing that my old power supply doesn't seem to suffice. The pins fit but there is extra space on the end.

[http://gamearsenal.net/image1.jpg](http://gamearsenal.net/image1.jpg)

And there is another male connector on the board that I haven't notice on others before near the processor. I've got another female but it's also too short.

[http://gamearsenal.net/image2.jpg]("http://mail.google.com/mail/?ui=2&ik=c98f6a2b06&view=att&th=125d1ba1349a2403&attid=0.0&disp=inline&zw")

The power supply says it support 12v output but only has 160w. On the side near the power cord (the one that goes plugs into the wall outlet) has a switch on it where you can switch the power from 160w to 230w. Will this power supply not work or my eatx board?

[http://gamearsenal.net/image3.jpg]("http://mail.google.com/mail/?ui=2&ik=c98f6a2b06&view=att&th=125d1bfdbdb62832&attid=0.0&disp=inline&zw")

---

### Post by cascade9 on 2009-12-27
Your picture links dont work (putting stuff on gmail just takes people to the gmail loggin page). 

I think I know whats happening, at least in part, but I'd rather see the pics before I say anything (and if you cant post links, then the hardware specifications might be nearly as good)

---

### Post by GroogFish on 2009-12-27
Sorry about that. I'll change the urls of the original post.

edit: Grrrrr, image shack won't upload them because their large. I will upload them to my own webspace.

---

### Post by GroogFish on 2009-12-27
Am I allowed to bump this?

Even though I just did :P

---

### Post by mathuna on 2009-12-27
An EATX is typically for servers. It will have PCI-X (64-bit) slots and probably more than one Processor socket and probably be set up for ECC versions of memory which are much more expensive and typically slower. PCI-X cards are usually used for hardware RAIDs. Also, cases which accommodate ATX cards may be too small for the EATX. Finally EATX cards often have up to three sets of connectors for power supplies for a primary and up to two backup power supplies.

I can build a righteous gaming machine for less than $800 including ATX motherboard, 1 TB hard Disk, DVD Drive, Case, Power Supply, Vid card, 4G memory, and Phenom II Quad processor. To get equivalent functionality from an EATX, I would need to spend about $1700. Of course the EATX would be expandable to double that performance and the ATX would not..
==================================
[enterrement de vie de garçon idée](http://www.enterrementdeviedegarconidee.com)
[free internet dating](http://www.betterdatingsites.com/)

---

### Post by cascade9 on 2009-12-28
Pic 1- 20 pin ATX power connected to a 24 pin connector. Should work, but its not a good sign. 

Pic 2- 6 pin (??? looks like a 6 pin PCI- Express, but on that power supply?) connected to 8 pin EPS.No idea if this should even work, but not good at all IMO. Also, that sure looks like the heatsink for an opteron in the background. Heres the proper power connector you want- 
[IMG]http://www.playtool.com/pages/psuconnectors/eps.jpg[/IMG]

Pic 3- A Dell 160 watt power supply? *blinks* and your got this connected to waht motherboard? Anythign that needs a 8 pin EPS will porbably need far more power than that. Even if it is a single opteron you will be pushing it very hard to run on 160 watt power supply.

 Get a new power supply. 

Neat page on all the connectors (and other stuff as well) here- 

[http://www.playtool.com/pages/psuconnectors/connectors.html#eps8](http://www.playtool.com/pages/psuconnectors/connectors.html#eps8)

BTW-very bad idea to put motherboards, etc. on to carpet. Carpet can build up a nasty static charge, and that can kill your components. 

> **mathuna said:**
> An EATX is typically for servers. It will have PCI-X (64-bit) slots and probably more than one Processor socket and probably be set up for ECC versions of memory which are much more expensive and typically slower. PCI-X cards are usually used for hardware RAIDs. Also, cases which accommodate ATX cards may be too small for the EATX. Finally EATX cards often have up to three sets of connectors for power supplies for a primary and up to two backup power supplies.

Yeah, EATX is typically for servers, but there are EATX 'normal' motherboards arounf, here is just 2 examples-

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813188048](http://www.newegg.com/Product/Product.aspx?Item=N82E16813188048)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813188058](http://www.newegg.com/Product/Product.aspx?Item=N82E16813188058) 

EATX is just a from factor (like ATX, mirco ATX, baby AT, etc.). 'Extended' ATX, is just bigger than standard ATX (EATX =  305 high ×330 wide, ATX = 305 high ×244 wide). The reason why 'server' boards tend to use EATX is the extra space so they more CPU sockets, RAM slots, etc fit. 

There quite a few ATX cases that fit EATX motherboards, but the majority will not. 

Generally, your right, EATX 'server' boards tend to use ECC, buffered or registered RAM, not standard SD/DDR RAM. Also, server boards can have multipule power connectors for redundant power supplies, but that is an option as well. I've seen more than one 'server' motherboard with multipule CPUs that only use 1 power supply.  

BTW, for new EATX setups, your probably right. I've seen some really cheap dual-CPU motherboards etc on ebay, etc. I'm sure I've even posted on some thread here where someone got a dual opteron motherboard, with CPUs (dual core CPUs) of ebay for something like $30 US.

---

### Post by cascade9 on 2009-12-28
Ohh, I am silly. 

The guy who bought that dual opteron setup (price- $31 US) was the OP. Thread here- 

[http://ubuntuforums.org/showthread.php?p=8548680#post8548680](http://ubuntuforums.org/showthread.php?p=8548680#post8548680)

No wayyy is that going to work with a dell 160watt power supply. 

I also forgot...

> On the side near the power cord (the one that goes plugs into the wall outlet) has a switch on it where you can switch the power from 160w to 230w.

That will not be 160w to 230w. Its a 160watt power supply, thats it. That 'switch' is to change from 110/120 volt to 220/230/240 volt. If your in north america, you've got 120 volt. 230 volt in europe (and pretty much the rest of the world)

---

