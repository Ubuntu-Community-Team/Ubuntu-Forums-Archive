---
title: "hard drive fails to start after reinstalling ubuntu"
date: 2009-10-07
forum: Installation &amp; Upgrades
---

### Post by gencive on 2009-10-07
Hello everyone,

here comes the sad story of the old fujitsu siemens amilo pro, centrino processor, windows XP on one partition (20 G) and I had ubuntu hardy heron on the rest of it.

I downloaded the latest ubuntu (9.04 i think it is) and installed it. 

I used the old partitions but changed the sizes of both swap and /. Swap I gave 2 g instead of one.
/ I gave 8 instead of 6.
I reduced the /home accordingly.

that probably was my stupid mistake, anyway, I rebooted and everything worked fine, I had some adjustments to make, but the windows part and the new ubuntu part worked. grub and all.

that was yesterday. today, my computer won't start. the screen stays black, the lights show: little light bulb (so it receives electricity I guess) and then the little hard disk symbol light turns on and ... immediatly off and stays that way.

so the hard drive is broken ?
has it something to do with my lousy install skills ? (my computer is probably as full as an egg)
why did it work and suddenly fail me ?
this computer is my work tool, how deep in *** am I ?

any kind of advice is welcome, thanx in advance !

---

### Post by dstew on 2009-10-07
The problem suggests a hardware problem, or possibly disk corruption. First, do you get the usual BIOS splash screen (i.e., is the BIOS fried?). If so, then you can be pretty sure the BIOS and motherboard are working OK. Do you get the grub menu? If not, then either grub is mis-installed, or the disk file system is corrupted, or the MBR is corrupted.

Can you boot a Live CD? Can you access the hard disk from a Live CD boot? If so, that will reassure us that the disk is intact, and that we only need to re-install or re-configure things.

Even if the disk seems to be failing, there are good tools available to fix it, if it is fixable. But sometimes disks fail and cannot be retrieved.

---

### Post by gencive on 2009-11-04
hello dstew,

well absolutely nothing happens. no bios screen, no grub no nothing. impossible to boot a live cd, etc. i think all is fried. 

since my last post i paid people to retrieve my perso data, they managed to do so and i was told the hard drive seemed ok, so i guess :

the mother board (my laptop is old) ;

magic (an evel kind) ;

or is it possible (like i suggest in my first post) that when i installed ubuntu and modified the partition sizes a little, not taking into account that my computer was as full as an egg, i wrecked the hard drive ? are such things possible ?

I ask again because i bought an empty laptop and installed xp on a part of it and now i want to install ubuntu on the rest of it.

by the way thanx for the answer !

---

