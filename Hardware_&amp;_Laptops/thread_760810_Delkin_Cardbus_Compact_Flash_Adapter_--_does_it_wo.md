---
title: "Delkin Cardbus Compact Flash Adapter -- does it work?"
date: 2008-04-20
forum: Hardware &amp; Laptops
---

### Post by rcoconnell on 2008-04-20
My Special Lady recently upgraded to a DSLR, and so is switching from SD cards to CompactFlash (just ordered an 8GB 133x card).  One question of particular interest is how to quickly transfer pictures from the card to her laptop.

Here's the rub -- she's using an oldish Thinkpad T30 (running Gutsy), with blazing USB 1 connection.  I think this means that a USB reader will be no faster than directly connecting the camera.  One intriguing possibility is a cardbus adapter, like [this one]("http://www.amazon.com/Delkin-Devices-CARDBUS-32-BIT-DDCARDBUS-AD/dp/tech-data/B0000ET7JF/ref=de_a_smtd").  This is not to be confused with an ordinary PCMCIA adapter, which transfers at significantly lower rates.  Anyway, this brings us to the questions:

1.  Are there drivers in Ubuntu for the Delkin (or similar devices from Lexar, Viking)?  I ran across this thread,

[http://ubuntuforums.org/showthread.php?t=242971](http://ubuntuforums.org/showthread.php?t=242971)

but the link doesn't include the purported driver, and there's a later complaint that it wouldn't build anyway.  This is to be contrasted with rumblings like [this]("http://lkml.org/lkml/2007/1/13/44"), which make me think the matter isn't entirely hopeless.

2.  Is anybody actually using one of these devices in linux?  Does your machine boot normally etc when it's inserted?  

3.  Is there another fast way to transfer these files?

Thanks!

-ross

---

### Post by kwacka on 2008-04-20
Idon't know about the Delkin, but I bought an adaptor via ebay - 99 cents for adapter, $5 postage from China.  Its labelled "Enjoy adapter" & 'PCMCIA'. (Can a CF card transfer data at Cardbus rates?)

Immediately recognised when plugged into this laptop (running Gutsy) with 8 GB CF card.

Another possibility - I have a Trust HU-6100P USB2 2-port hub card - again plugs straight in and a usb memory stick is picked up.

---

### Post by rcoconnell on 2008-04-20
What kind of transfer rates do you get?  How long does it take you to dump the card?

-ross

---

### Post by kwacka on 2008-04-22
No idea of actual rates.

The Trust card (uses NEC chipset) is full USB2.

---

### Post by JPorter on 2008-04-30
I got an email response from Mark Lord, the developer of the original linux driver package for the Delkin Cardbus CF adapter.

> The 2.6.25 Linux kernel now contains a new **libata "pata_ninja32"** driver for this.

So with that kernel, and with that driver configured/installed,
flash cards should just automatically show up as /dev/sdX devices.

Just like USB drives do.

I am no longer maintaining or updating the ide delkin_cb driver now.

Cheers
-- 
Mark Lord

I hope this helps.

---

