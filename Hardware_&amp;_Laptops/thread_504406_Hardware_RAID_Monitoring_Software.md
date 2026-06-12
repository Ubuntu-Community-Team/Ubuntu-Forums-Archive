---
title: "Hardware RAID Monitoring Software?"
date: 2007-07-19
forum: Hardware &amp; Laptops
---

### Post by KrisWillis on 2007-07-19
Hi there,

I have a hardware RAID controller, reported by *lspci* as:
```
00:09.0 RAID bus controller: Silicon Image, Inc. PCI0680 Ultra ATA-133 Host Controller (rev 02)
```
When I was running Windows XP I had some software called Medley that sat in the task bar and monitored my RAID array(s), it would tell me their status and report the progress if the array was being rebuilt, and I'd assume it would report if a disc failed, luckily I hadn't experienced that yet!

Is there anything like this available for Ubuntu? I have a poke around the add/remove programs and Synaptic, but everything related to RAID appeared to be for software based arrays.

I'm a little concerned that one (or more) of my arrays are 'out of sync' (they're mirrored) as every time I boot the machine the cards BIOS tells me so and that they are not being rebuilt while in Ubuntu.

Any advice welcome :)

---

### Post by Ted_Smith on 2008-03-23
I am seeking the same thing. There's loads for software RAIDS, but not hardware (it seems). I'd like a simple taskbar type GUI that has a green light for OK, amber for a problem and red for serious. Along with the opportunity to click it and obtain stats relating to performance etc.

---

