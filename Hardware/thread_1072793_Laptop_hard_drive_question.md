---
title: "Laptop hard drive question"
date: 2009-02-17
forum: Hardware
---

### Post by dbbolton on 2009-02-17
I am trying to revive my old laptop (and hopefully get Debian running on it :D ). I believe that the hard drive is kaput. The hard drive with it now is:

```

Fujitsu
Model MHV2080AT PL

```

From what I have read, the interface for this drive is ATA-7. I haven't had much luck finding a replacement. Is this interface the same as SATA 1.5Gb/s or SATA 150? These seem to be much more common than ATA-7 at various online retailers.

(The reason that I'm not just ordering an identical replacement from Fujitsu is that I have had better luck with WD and Seagate in the past.)

---

### Post by cbtengr on 2009-02-17
> **dbbolton said:**
> I am trying to revive my old laptop (and hopefully get Debian running on it :D ). I believe that the hard drive is kaput. The hard drive with it now is:

```

Fujitsu
Model MHV2080AT PL

```

From what I have read, the interface for this drive is ATA-7. I haven't had much luck finding a replacement. Is this interface the same as SATA 1.5Gb/s or SATA 150? These seem to be much more common than ATA-7 at various online retailers.

(The reason that I'm not just ordering an identical replacement from Fujitsu is that I have had better luck with WD and Seagate in the past.)

I found a replacement for my old Dell here:

[http://www.drivesolutions.com/index.shtml](http://www.drivesolutions.com/index.shtml)

---

### Post by dbbolton on 2009-02-17
> **cbtengr said:**
> I found a replacement for my old Dell here:

[http://www.drivesolutions.com/index.shtml](http://www.drivesolutions.com/index.shtml)
They don't seem to have any with the "ATA-7" interface. 

It would be really helpful if I could figure out the terminology. According to Wikipedia, "SATA/150" is actually a "Transfer Mode", not an interface:

[http://en.wikipedia.org/wiki/Advanced_Technology_Attachment#ATA_standards_versions.2C_transfer_rates.2C_and_features](http://en.wikipedia.org/wiki/Advanced_Technology_Attachment#ATA_standards_versions.2C_transfer_rates.2C_and_features)

---

### Post by cbtengr on 2009-02-17
> **dbbolton said:**
> They don't seem to have any with the "ATA-7" interface. 

It would be really helpful if I could figure out the terminology. According to Wikipedia, "SATA/150" is actually a "Transfer Mode", not an interface:

[http://en.wikipedia.org/wiki/Advanced_Technology_Attachment#ATA_standards_versions.2C_transfer_rates.2C_and_features](http://en.wikipedia.org/wiki/Advanced_Technology_Attachment#ATA_standards_versions.2C_transfer_rates.2C_and_features)

Is this the drive you currently have?

[http://www.drivesolutions.com/cgi-bin/shop/store.cgi?command=listitems&kind=laptop&pos=&type=itemid&itemid=l46](http://www.drivesolutions.com/cgi-bin/shop/store.cgi?command=listitems&kind=laptop&pos=&type=itemid&itemid=l46)

Might be worth giving them a phone call.

---

### Post by dbbolton on 2009-02-17
> **cbtengr said:**
> Is this the drive you currently have?

[http://www.drivesolutions.com/cgi-bin/shop/store.cgi?command=listitems&kind=laptop&pos=&type=itemid&itemid=l46](http://www.drivesolutions.com/cgi-bin/shop/store.cgi?command=listitems&kind=laptop&pos=&type=itemid&itemid=l46)

Might be worth giving them a phone call.
That one is MHT but mine is MHV. 

I might just get another one on ebay :lol:

---

### Post by Bablefish on 2009-02-17
There is this Hard Drive tool, called Spin Rite it costs a bit. But it is an amazing tool. I personally seen it bring hard drives back from the dead. You may want to give it a try.

---

### Post by Therion on 2009-02-17
> **dbbolton said:**
> ... Is this interface the same as SATA 1.5Gb/s or SATA 150?
Absolutely NOT.  ATA 7 is a type IDE interface.  

In short, ATA 7 = "Round Peg", SATA = "Square Peg".

---

### Post by dbbolton on 2009-02-17
> **Therion said:**
> Absolutely NOT.  ATA 7 is a type IDE interface.  

In short, ATA 7 = "Round Peg", SATA = "Square Peg".
So then is SATA/150 the name of an interface as well as a transfer mode?

---

### Post by cbtengr on 2009-02-17
> **dbbolton said:**
> So then is SATA/150 the name of an interface as well as a transfer mode?

Here's some info:

[http://www.harddrivereport.com/pata_vs_ata_vs_sata_vs_ide.html](http://www.harddrivereport.com/pata_vs_ata_vs_sata_vs_ide.html)

---

### Post by Therion on 2009-02-17
> **dbbolton said:**
> So then is SATA/150 the name of an interface as well as a transfer mode?
Short answer: Yes.

SATA is a serial ATA pat/transfer mode, IDE is also called Parallel ATA or PATA because it's a Parallel path/transfer mode.  

Simply put, SATA uses one type of connector, PATA (or IDE or ATA 7 (those are all names for the same thing)) use another connector which is altogether different.  

It's like Firewire and USB.  Different connectors and ways of doing things even though they basically do the same thing: transfer data.  You still can'tuse a USB cable with a Firewire port or vice versa.  Same-same with serial (SATA) vs. parallel (PATA).  Clear as mud?

---

