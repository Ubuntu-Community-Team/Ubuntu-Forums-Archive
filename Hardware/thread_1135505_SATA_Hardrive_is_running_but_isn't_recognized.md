---
title: "SATA Hardrive is running but isn't recognized"
date: 2009-04-24
forum: Hardware
---

### Post by winrowc on 2009-04-24
I bought a new 1TB Western Digital SATA harddrive for my computer. I have an ASRock 775Dual-880Pro motherboard, with 2 IDE hard drives, an 80GB which is my primary master, and a 160GB which is my slave drive. I connected the new SATA drive and it isn't recognized. Holding it, I can feel it running in my hand, so its getting power, but it isn't recognized by the Bios. When I have the other two drives connected it boots normally, but the SATA drive isn't recognized. When I disconnect those drives, the computer freezes in the start up screen after a few lines before displaying hard drives, and after displaying the CPU type and amount of ram.

I'm a complete noob to SATA drives, can anyone help get my computer to recognize this?

---

### Post by Barry Carroll on 2009-04-24
I don't want to insult your intelligence but I have to ask:  Is the sata data cable connected firmly to both drive and motherboard?  Another thing to try might be using a different sata cable.

Have you tried the different sata ports on the motherboard to see if they all act the same?  I also recall that some WD Sata drives had both the newer sata style power connector and the older molex style.  If this is the case it's very important that you use one or the other, not both.

I'd also recommend to have a look in your BIOS to see if the sata ports are enabled and set to your preferred mode which is usually 'legacy / ide' or 'ahci'.

I had a look at the bios update history for your board but I couldn't see anything specific to a sata recognition bug ([http://www.asrock.com/mb/download.asp?Model=775Dual-880Pro&s=775](http://www.asrock.com/mb/download.asp?Model=775Dual-880Pro&s=775))

---

