---
title: "Installing Ubuntu &amp; RAID"
date: 2009-06-04
forum: Installation &amp; Upgrades
---

### Post by Literati on 2009-06-04
Alright, so I'm a bit new to RAID game, and need to know if a few things are possible.

I have 3 HDDs:

2 500GB
1 1TB

I was the 2 500GB drives to be setup in RAID0, to allow for faster access times and I want it to be mounted on /, and I want the 1TB drive to just act on it's own mounted on /home. 

First question, is that setup possible? Can I mount a single drive "inside" a RAID array? Or is that not something that is feasible?

Also, I'm reading around about the Alternate CD Installer, and I see that I might need to make /boot a RAID1, or else it won't boot. Is that still the case for 9.04? I'd prefer it to be RAID0, to help with faster boot times. If it MUST be RAID1, then how do I go about making a RAID1 and a RAID0 co-exist on my 500GB drives? 

Thanks so much for the help,
Literati

---

### Post by Literati on 2009-06-04
Anybody? :P Just need a point in the right direction. All the RAID How-To's seem to be very outdated (8.04 or earlier!)

---

### Post by Claus7 on 2009-06-04
Hello,

I used a new pci raid card, which enables me to have a sata on in combination to an old ide outside the raid configuration. I installed ubuntu in my new sata drive and everything is ok. Just experiment a little and find out which configuration is best for you.

For example your hardware specs might be such, that for example the ext4 might improve a lot your boot times. Yet, it might not. Just have a backup before you try any tests.

You might already know it, yet this was the first place I started to look about raid technology. It is very comprehensible.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)

Also I do not think that RAID has to do specifically with an ubuntu version.  

Regards!

---

