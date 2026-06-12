---
title: "Hardware suggestions please"
date: 2016-04-22
forum: Hardware
---

### Post by splatt2 on 2016-04-22
I'm trying to procure a Ubuntu platform with the following:

Skylake CPU
Support for simultaneous use of 2 M.2 PCIe SSD cards (cards will be separately procured)
2x PCIe x4 slots for 10Gb Ethernet cards
A few spare PCIe x4 or larger slots
Primary hard drive or SSD (~250GB)
Support for >16GB RAM (ECC would be nice but not required)
Video is a don't care
Prefer Ubuntu pre-installed

I could part this out and build it myself but I'd prefer to buy an off-the-shelf system that meets these requirements.

Any suggestions?

Thanks,
Steve

---

### Post by TheFu on 2016-04-23
Have the Skylake issues all been solved?  One of them: [https://www.phoronix.com/scan.php?page=news_item&px=intel-skl-prelim-support](https://www.phoronix.com/scan.php?page=news_item&px=intel-skl-prelim-support), but I seem to recall a few others.

PC Part Picker will help to find a MB + CPU, then you can add whatever else is needed and search for Linux compatibility. 
[https://pcpartpicker.com/](https://pcpartpicker.com/)  - I've not found their prices or deal links to be very useful, but the compatibility and search by feature stuff has made life easier, if what you want is in their DB.  Sometimes they don't have the MB I know exists (running 2 ft from me now), so finding compatible parts requires manual research.  For newer systems, I haven't seen that.

---

### Post by pqwoerituytrueiwoq on 2016-04-23
This is to be a headless server right?
id start checking on newegg for a motherboard that suites your needs
id suggest building it yourself, it is not hard to do

---

### Post by splatt2 on 2016-04-24
Thank you for the responses. I did not know about pcpartpicker.com
I will look into the potential SkyLake issues and yes, I am strongly now considering building from scratch.
Thanks again.
Steve

---

### Post by TheFu on 2016-04-24
The best answers will depend on where you are in the world.  There are systems available in the USA that aren't sold to end-users in the EU, for example.  

For a system like you specified, finding that directly from a major vendor will be next to impossible - that means finding a local computer shop. If you go that direction, why not build it yourself - takes about 30 min.  The connections are all "keyed" these days, so it is hard to plug things in wrong.

Also, are there a specific performance and budget targets?  9000 passmarks for $350 - something like that?

Why so much RAM?  Seems like a waste unless you run 10 Windows VMs or do geospatial work.  I suppose java devs always need 32G+ RAM, but that's Java, not for end users. ;)

Really, we don't know the purpose for the system, so any improvements to the selection (where to save money for unneeded stuff) cannot be suggested.  For example, 10G networking?  Really?  Would a FC SAN connection be better or Infiniband if closer?  If a server, something from SuperMicro is where I'd start with Xeon CPUs.

Is it OK if there isn't **any** GPU at all?  Are you good with console only access to start?

---

