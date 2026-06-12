---
title: "Memory Problems..."
date: 2008-03-21
forum: Hardware &amp; Laptops
---

### Post by the beak on 2008-03-21
Hi,

I wondered if anyone could give me some advice please. This is purely a hardware question.

I'm trying to upgrade an ancient Dell cpx 750 from 128 ram with an extra 256. The RAM I bought was SDRAM PC133 SODIMM (SAMSUNG). However when I install the RAM it doesnt seem to work. 

If I take out the existing RAM and replace it doesnt boot.

If I keep both in it boots, tells me after GRUB that theres new memory either skip or setup and some kenal errors appear, or it tells me it's gonna ignore the new ram and boot normally.

The only difference I can see is that its PC133MHZ rather than PC100MHZ and I was told that thats ok.

So either its the wrong type?
Or it's faulty? baring in mind its brand new 


ANy advice would be magic, ta.

---

### Post by FuturePilot on 2008-03-21
Being faulty is definitely a possibility. Have you run Memtest with the new RAM plugged in?

---

### Post by the beak on 2008-03-21
I'm running the memtest in GRUB at the moment and it's coming back with ebndless failiing errors.

I take it that means the trash can then?

---

### Post by cprofitt on 2008-03-21
> **the beak said:**
> I'm running the memtest in GRUB at the moment and it's coming back with ebndless failiing errors.

I take it that means the trash can then?

Or returning the ram...

The other option is to remove the PC100 ram and put the 133 ram in the slot it was in...

A)  You might only be able to run one type of memory...

B)  Your bios may only support 256mb of ram (though I doubt that)

What does Dell's support say?

Found [this]("http://support.dell.com/support/edocs/systems/pcpxhj/sm/64ptn_en.pdf") ... not sure if it is really your model or not... there is apparently an H and a J variant of your laptop series. There is also [this]("http://support.dell.com/support/edocs/systems/pcpxhj/sig_amf/86efpamf.pdf") documentation; hope it helps.

The first one says the modules (192mb) are made for either A or B slot and have to go in the slot they are made for... which I have never heard of.

---

### Post by the beak on 2008-03-21
I've tried it on its own and it doesn't boot and all sort of combinations.

I got it shipped from Hong Kong I didn't go through Dell, I thought it was a bargain: false economy i think. :(

---

### Post by popch on 2008-03-21
> **the beak said:**
> If I keep both in it boots, tells me after GRUB that theres new memory either skip or setup and some kenal errors appear, or it tells me it's gonna ignore the new ram and boot normally.

I find it a bit unexpected that you are told after GRUB that there is new memory. 

I would expect a message of that sort after POST where you are then given the option to enter setup and configure your newly installed memory, presumably by pressing F1 or some such.

---

### Post by the beak on 2008-03-21
Your right.

But when i press F1 itenters the BIOS and all I seem to be able to do is view the system harware, not set anything up.

---

### Post by popch on 2008-03-21
What you enter on pressing F1 is the BIOS's setup. You scroll or otherwise navigate from there to the place where memory (or RAM) is mentioned and enter the amount of RAM installed in whatever form the BIOS expects there.

Sorry, I can not be more specific as I do not have any Dells at home and have never seen one of the kind you have.

---

### Post by the beak on 2008-03-21
Thanks. I'll have a look around the Bios

---

### Post by p_quarles on 2008-03-21
Thread moved to Hardware & Laptops.

---

