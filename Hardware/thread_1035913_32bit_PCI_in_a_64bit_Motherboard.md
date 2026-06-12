---
title: "32bit PCI in a 64bit Motherboard??"
date: 2009-01-10
forum: Hardware
---

### Post by amityak on 2009-01-10
Hello ubuntuers

I just got a new (used) computers and have to set up now wireless support.
so i thought of getting this card, which has good linux reviews:

[TP-Link 108MBit WLAN PCI Karte eXtended Range TL-WN651G (link for photo)]("http://www.2direkt.de/i-sell2u/images/bilder/WL0016.jpg")

My motherboard however is 

[GeForce 6100-M9 (link for full specifications)]("http://www.biostar.com.tw/app/en-us/mb/content.php?S_ID=26")

now it sais on the card specifications (PCI) an on the motherboard as well, however, it seems to me it would only fit in the PCIeX16 slot which is already taken by the graphic card.

any ideas? or maybe for other pci wlan cards which might fit ?
i could actually also do fine with a UBS, i just thought PCI is nicer and non complicated as it becomes part of the computer

thank you all

---

### Post by amityak on 2009-01-12
what nobody knows??!?!

weird... i guess it might be a mystery
well ill just get a USB and get it over with

---

### Post by Therion on 2009-01-12
The PCI-e 16x slot is ***strictly*** for graphics cards.

PCI connectors, on the other hand, are an entirely different type of connection and would be used for your wireless card.  PCI also supports any number of other cards (additional USB or Firewire ports for instance).  You could even use a PCI graphics card if you wanted to (even though it's about the worst possible scenario).  

Long story short though:  

Graphics card = PCI-e slot.
Wireless card = PCI slot.

---

### Post by Seq on 2009-01-12
According to [tp-link.com]("http://www.tp-link.com/products/product_fea.asp?id=17"):

[LIST]
[*]32-bit PCI connector 
[/LIST]

So it is a regular PCI card and will work in a regular PCI slot.


Somewhat unrelated now, but to correct Therion, you can use a pci-e 16x slot for a non graphics card (such as a pci-e 1x nic, etc). PCI-e is not specific to graphics (unlike AGP was). Though apparently some BIOSes disable onboard video based on the presence of a any card in that slot regardless of whether it is graphics or not, so YMMV (though not yours, as I said, this is unrelated to the original issue now).

---

### Post by amityak on 2009-01-12
thank you all for the replies, i was already thinking its a mystery so i ordered a USB, and i think eBay sellers dont like to be cancelled ):

so i'll just have to live with that I guess

10x again

---

### Post by Therion on 2009-01-12
> **Seq said:**
> ... you can use a pci-e 16x slot for a non graphics card (such as a pci-e 1x nic, etc). PCI-e is not specific to graphics (unlike AGP was).
Ugh.  You're right, of course, and that's what I get for posting before finishing my first cup of coffee in the morning.  I was vaguely recollecting that PCI-e is "card agnostic" as you point out, but it was mixing with my experience that, yes, some BIOS'es will disable onboard video if the slot is occupied...  

Lesson learned.  Coffee first, THEN post.  

And thanks for the correction/assist.

---

### Post by electrogeist on 2009-01-12
to make it even more fun and confusing: there *are* 64-bit PCI cards, and they are called PCI-X (not to be confused with PCI-e) if they have a speed of at least 100MHz bus.  Then there are differences in supported voltages, 5v vs 3.3v, and cards are keyed accordingly resulting in "WTF why don't it fit in the slot!?!"

Most PCI cards that most people will run into are 32-bit and run at a slow 33MHz bus speed.

---

### Post by Seq on 2009-01-12
> **electrogeist said:**
> to make it even more fun and confusing: there *are* 64-bit PCI cards, and they are called PCI-X (not to be confused with PCI-e) if they have a speed of at least 100MHz bus.  Then there are differences in supported voltages, 5v vs 3.3v, and cards are keyed accordingly resulting in "WTF why don't it fit in the slot!?!"

Most PCI cards that most people will run into are 32-bit and run at a slow 33MHz bus speed.

64-bit PCI-X cards CAN have a connector that is twice as long as a standard PCI connector. To make matters worse, Some cards like (my mortal enemy) the [Adaptec 29160LP]("http://www.adaptec.com/en-US/products/Controllers/Hardware/scsi/entry/ASC-29160LP/") card can be 64-bit PCI-X cards that are designed to work with 32-bit PCI slots ("64-bit PCI (32-bit compatible)").

I think the world will be a much better place if we all pretend PCI-X never happened.

---

