---
title: "Recommend SCSI card?"
date: 2007-01-01
forum: Hardware &amp; Laptops
---

### Post by btdown on 2007-01-01
I have never owned/used a scsi card or drive. But I am building a machine to be used as a home server where I will store my MP3 and other stuff I plan to keep long term. The server motherboards with onboard scsi seem way expensive, so I'd like to just put a scsi card in a regular motherboard and put 2 scsi drives in it. I know linux (ubuntu?) can sometimes be finicky about hardware, so could someone please recommend a scsi card (ultra320) that is known to be recognized in dapper and above? Anything else I need to look for, or know before buying?

Thanks!
BT

---

### Post by adaptr on 2007-01-01
Why on earth would you want to use real SCSI for a home server?

There is a very simple reason why server boards with on-board SCSI are expensive: a good Ultra320 SCSI card is expensive.

I have an Adaptec 29320LP PCI-X card in my "home" server, but only because I got it for free.
Were you to have to buy this card today, it would cost you at least $300.

And that's not because it is an expensive card - as SCSI goes, this is middle-of-the-road; no, it's because it is a good card.
Bad hardware is worse than useless.

A decent 4-port SATA card costs about $100~$150 , and SATA drives are at least twice as cheap as SCSI for the same size.

Get a few big SATA drives and knot them together in software RAID-5; you lose one drive for parity, but any one drive may fail without loss of data.
4 SATA 400GB drives would net you a 1.2 TB fileserver for rougly $800 or so.

If you had to buy this in SCSI, you would be paying upwards of $5000...

Apart from speed (which you won't need - not the sort of speed I'm talking about here) the only conceivable reason you would want SCSI in a home server is that SCSI drives are designed to operate 24/7 for 5 years.

But consider: say one of your cheap SATA drives dies in two years' time - who cares ? pay $150 and replace it.

Probably be $100 by then.

For a home server, SCSI just isn't worth it.

---

### Post by btdown on 2007-01-02
Thanks for the input...perhaps it would be overkill for my situation!
BT

---

