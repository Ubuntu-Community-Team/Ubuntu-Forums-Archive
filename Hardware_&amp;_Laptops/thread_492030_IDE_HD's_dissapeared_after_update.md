---
title: "IDE HD's dissapeared after update"
date: 2007-07-04
forum: Hardware &amp; Laptops
---

### Post by azkabaz on 2007-07-04
Hello all, 

What's happened is that I have not switched on my Ubuntu 7.04 for a few months, came over, turned it on and my IDE HD's are showing up fine and are accessible. 

They exist in /dev/hda and /dev/hdb. 

Installed a few months worth of available updates, restarted when prompted and my drives have both disappeared I've checked in /dev and they no longer exist.

They show in BIOS and if I poke a Windows hard drive in, they register fine.

Drive set up is ->
1x SATA/multiple partitions (Ubuntu lives here)
2x IDE

SATA registers as /dev/sda1, /dev/sda2, /dev/sda3, /dev/sda4 and /dev/sda5 as it originally did but no /dev/hda or /dev/hdb exists.

Any clues whats going on?

Cheers

---

