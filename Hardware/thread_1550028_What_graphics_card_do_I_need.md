---
title: "What graphics card do I need?"
date: 2010-08-10
forum: Hardware
---

### Post by steve-buntu on 2010-08-10
Hi, I am Currently using the built in graphics on my motherboard, I was going to get a new graphics card, but do not know what interface type my board uses, (it does not say on the board)  do not know th name of the motherboard model, but I know the model name of another motherboard that uses the same port. The motherboard is an Intel desktop board D845GRG. Could somebody find out what graphics card I need from the information I've provided.

---

### Post by howefield on 2010-08-10
> **steve-buntu said:**
> Could somebody find out what graphics card I need from the information I've provided.

Does it look something like the brown slot in the image ?

AGP connector supporting 1x, 2x, and 4x AGP cards (1.5 V only) or an AGP
Digital Display (ADD) card

---

### Post by PresenceofMind on 2010-08-10
Hello,

> do not know what interface type my board uses, (it does not say on the board)The name (or type) of slots found on motherboards are printed right next to the slots themselves. This is true for all motherboards. You just have to look at the letters carefully (things like PCI, AGP etc. are printed right next to the slot that they represent. Just look carefully)

---

### Post by Zorgoth on 2010-08-10
I think sudo dmidecode should tell you what kind of slot you have somewhere.

---

### Post by wookieshaver on 2010-08-10
The Intel desktop board D845GRG has an available agp slot and 3 regular pci slots. So an agp or old pci (not pci-express) video card would do just fine for that board. The nvidia cards might be best as there are outstanding drivers for them with 10.04 ubuntu! Something like this would work just fine:
 
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814134076](http://www.newegg.com/Product/Product.aspx?Item=N82E16814134076)

---

