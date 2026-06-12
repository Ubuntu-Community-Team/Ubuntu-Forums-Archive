---
title: "Brother HL-2040"
date: 2010-05-19
forum: Hardware
---

### Post by Pan Sloboda on 2010-05-19
I am trying to get my HL-2040 working in 10.04.  I have it on a network print server device, but the system seems to find the device just fine with the IP address.

The problem is that I cannot, for the life of me, get the Brother HL-2040 Print drivers to show up.  I have them showing in Synaptic.  I installed the most current lpr and CUPS (i that order) for the Deb.  System seemed ot pick it up and process it via Alien.  No big deal.

Except it NEVER shows up as a driver in the system.  I have tried from multiple angles and there is no PPD at linuxprinting for the HL-2040.

Anyone find a way to do this?  I am not going to buy a new printer, that would be ridiculous.  If I cannot get this working, does another driver version work?

Thank you,
Chris

---

### Post by plucky on 2010-05-20
Post output from a terminal ```
dpkg -l | grep brother
```

The drivers for your printer are packaged in **Synaptic Package Manager**, just search for **hl-2040** and you should find ```
brother-cups-wrapper-laser
brother-lpr-drivers-laser
```,just select and install.


Good Luck

---

### Post by Pan Sloboda on 2010-05-20
Worked like a charm.  Not sure how I managed to not do that.  I think I may have had two driver sets installed simultaneously.  Maybe they were conflicting?  Or one set did not install properly with the other one in?

In any case, we're rolling!

Thanks!

Chris

---

### Post by Chirpz on 2010-12-20
I have two brother printers, a 2040, and a 5250 and both work with 10.04 very well.  They were practically plug and play.  I just clicked on Add printer and it found them and they worked great.
Highly recommended.

---

