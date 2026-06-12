---
title: "[SOLVED] External Graphica Card?"
date: 2008-11-28
forum: Hardware
---

### Post by Yezinki on 2008-11-28
Hello there my friends,

My Sony machine has an Intel 945 GM with built in 128 MB of grahics.

I cannot increase it more than 128 MB.

Is it technically possible to add another Nvidia or ATI 1GB specs of a graphic card?

I know its a long shot...the mainboard may not have an empty PCI slot?

This machine has 4 USB slots......can a a PCI be changhed to a USB using some sort of an adapter?

Hoping to hear from you smart geniuses,

Regards,

Yezinki.

---

### Post by the3dman on 2008-11-28
Not that I know of. Never seen anything like that.

---

### Post by Yezinki on 2008-11-28
If they can make an IDE DVDRW wwork as a USB.......I think its hypothetically possible??

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-28
How if I remove the TV Tuner card, Would a graphic card fit in it's place?

Would'nt the main board have an empty slot for a PCI Graphic card?

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-28
[IMG]http://i4.photobucket.com/albums/y129/eDOC/4.jpg[/IMG]

This is the TV Tuner card.....if I get it removed, Can I than place a PCI graphics card??

If yes what are my options?

Regards,

Yezinki.

---

### Post by sgarman on 2008-11-29
I've never heard of an external video card. One of the reasons for this is that video cards need to have extremely fast access to the computer's internal buses, and external ports such as USB, Firewire, PCMICA, etc. are nowhere near as fast as an internal AGP or PCI Express bus.

Scott

---

### Post by Yezinki on 2008-11-29
Thanks Scott,

Could I replace the displayed TV Tuner card with a Graphic card?

Regards,

Yezinki.

---

### Post by ratmandall on 2008-11-29
> **Yezinki said:**
> [IMG]http://i4.photobucket.com/albums/y129/eDOC/4.jpg[/IMG]

This is the TV Tuner card.....if I get it removed, Can I than place a PCI graphics card??



Yes you can put a PCI graphics card in where the the tv tuner card was if the tv tuner card is PCI, 
Which to me it looks like PCI but not sure if it's express or not because I am a hardware N33Wb ^-^

---

### Post by Yezinki on 2008-11-29
Thanks ratmandall,

I plan replacing the TV Tuner with a graphic card since this machine has a built in 128 MB 945 GM Intel graphics & get a USB TV Tuner card.

[http://accessories.us.dell.com/sna/products/TV_Tuners_Remote_Viewing/productdetail.aspx?c=us&l=en&s=dhs&cs=19&sku=A1640658](http://accessories.us.dell.com/sna/products/TV_Tuners_Remote_Viewing/productdetail.aspx?c=us&l=en&s=dhs&cs=19&sku=A1640658)

What AGP/PCI card what you recommend?

Regards,

Yezinki.

---

### Post by sgarman on 2008-11-29
> **ratmandall said:**
> Yes you can put a PCI graphics card in where the the tv tuner card was if the tv tuner card is PCI, 
Which to me it looks like PCI but not sure if it's express or not because I am a hardware N33Wb ^-^

That doesn't look like a PCI card to me (or any PC expansion card style, for that matter). I think the OP is out of luck.

---

### Post by Yezinki on 2008-11-29
Thanks Scott,

I appreciate your assistance.

Will have to live with 128 MB of video....

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-29
Scott your views about partitions?

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-29
What does Sony mean by this:

[B]```
One PCMCIA - Type II/Type I card slot with CardBus support.

One ExpressCard /54 Slot.
```[/B]

---

### Post by Yezinki on 2008-11-29
[B]```
Thanks for your reply.

Being a med doc I really didn't get all of it.


"One PCMCIA - Type II/Type I card slot with CardBus support.

One ExpressCard /54 Slot."  

Is any of them FREE?    

Can I install a graphic card or any other device?

Can I change my TV Tuner card to a different
brand one & if yes what are the specs of my present TV card?

 Hoping to hear from you,

PS: Please reply in depth , am not concerned about warranty or your recommendations, cause this is my own choice to use 3rd party tools/hardware etc.



```[/B]

---

### Post by Skripka on 2008-11-29
> **Yezinki said:**
> If they can make an IDE DVDRW wwork as a USB.......I think its hypothetically possible??

Regards,

Yezinki.

Nope.

A graphics card needs LOTS of power-especially current generation cards (which need their own nuclear reactors to power them).

A PCIe x16 slot can provide a MAX of 75W of power, a USB port can only put out a tiny fraction of that (only 3-4W, IIRC).  Most modern graphics cards at full load need 200W+.  You see the technical impossibility, yes?  Also USB2 is nowhere NEAR fast enough to handle current gen graphics cards.

Also that TV Tuner pic you posted did NOT come out of a PCI slot.  It isn't AGP either-I don't recognize what it is OTTOMH.

PCMCIA is a interface used on laptops to gain functionality--if you don't have a laptop-you don't have a PCMCIA slot. Plain and simple.  All these different connectors are not interchangeable and cannot be made to interface.  A PCI is a PCI, a PCIeX16 is a PCIeX16, an AGP is an AGP, a PCMCIA is a PCMCIA--if your device is one it cannot be made to interface with another.

---

