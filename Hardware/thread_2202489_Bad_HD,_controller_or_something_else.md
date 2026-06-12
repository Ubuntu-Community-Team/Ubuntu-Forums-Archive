---
title: "Bad HD, controller or something else?"
date: 2014-01-29
forum: Hardware
---

### Post by cle-ziskind on 2014-01-29
I have a Dell PowerEdge 1950 server, which I put a Dell Cheetah 146GB drive into (second drive) in August. Lately, it's been failing - giving lots of end request: i/o errors, and disappearing from the mount table. So, I bought another (similar) drive and replacement off of eBay.

Replacement drive is giving the same errors., Now, do I:

a) try my luck with a third drive (both drives had similar problems);
b) Replace the server (my errors are really MB/controller related);
c) some diagnostics (SMART stuff says it's ok);
d) 42

?

---

### Post by ventrical on 2014-01-29
> **cle-ziskind said:**
> I have a Dell PowerEdge 1950 server, which I put a Dell Cheetah 146GB drive into (second drive) in August. Lately, it's been failing - giving lots of end request: i/o errors, and disappearing from the mount table. So, I bought another (similar) drive and replacement off of eBay.

Replacement drive is giving the same errors., Now, do I:

a) try my luck with a third drive (both drives had similar problems);
b) Replace the server (my errors are really MB/controller related);
c) some diagnostics (SMART stuff says it's ok);
d) 42

?

What software are you using?

---

### Post by cle-ziskind on 2014-01-29
The OS is Precise 12.04.4. LTS.

---

### Post by tgalati4 on 2014-01-30
Do you have an LSI PERC RAID controller?  I would upgrade the RAID BIOS from Dell, then burn yourself a CD of Dell Server Diagnostics and run through the entire panel.  Check the voltages with a meter.  If you have two power supplies, disconnect one and just use one (in case one is injecting noise).  Check the motherboard's capacitors using a magnifying glass for leakage or bulging.  One bad capacitor will cause problems.

Clean out the machine with compressed air--thoroughly and reseat all of the cables and connections.  In a way, you are rebuilding the machine to see if you can get a reliable server going again.  Run memtest to make sure the RAM is good.  Try some different models of drives--these old ones are now getting hard to find.

Otherwise, put in a slim PCIe SATA card and put in some newer drives.

---

### Post by cle-ziskind on 2014-02-03
> **tgalati4 said:**
> Do you have an LSI PERC RAID controller?  I would upgrade the RAID BIOS from Dell, then burn yourself a CD of Dell Server Diagnostics and run through the entire panel.  Check the voltages with a meter.  If you have two power supplies, disconnect one and just use one (in case one is injecting noise).  Check the motherboard's capacitors using a magnifying glass for leakage or bulging.  One bad capacitor will cause problems.

Clean out the machine with compressed air--thoroughly and reseat all of the cables and connections.  In a way, you are rebuilding the machine to see if you can get a reliable server going again.  Run memtest to make sure the RAM is good.  Try some different models of drives--these old ones are now getting hard to find.

Otherwise, put in a slim PCIe SATA card and put in some newer drives.

Ok, 3rd hard drive went in, similar errors. So, it can't really be the hard drive. :-(

I don't think it has the PERC controller - who can tell from reading Dell's hieroglyphics? - but the tag no. is J2G1WB1.

Nothing you suggested particularly helped. Remember, machine has two hard drives, one works fine, the other errors out no matter which drive I put in it. So, I guess my next step is new controller. Or, maybe a new server - looks like $250 on Tiger.

Which controller/drives would fit in this machine with a minimum of fuss?

Thanks again.

---

