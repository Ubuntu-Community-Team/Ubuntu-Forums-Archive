---
title: "Missing half my memory"
date: 2016-09-10
forum: Hardware
---

### Post by jason13 on 2016-09-10
[SIZE=2]I've just gone through a big hardware upgrade (MB/CPU/RAM/PSU). I am now using a  ASUS Z170-P LGA 1151 Intel Z170 with  GeIL EVO POTENZA 16GB (2 x 8GB) 288-Pin DDR4 SDRAM.[FONT=Open Sans]
[/FONT][/SIZE]I haven't changed my drives at all, in fact I'm running off the same installation I was before, though the next step is to upgrade to 16.04. Both Ubuntu and my BIOS are missing half of the ram and only registering 8 GB. In the bios menu it lists which slots register memory, I was following the manufacturers recommendations and putting them in slots A2 and B2, it recognizes memory in slot A2 but not B2, there don't seem to be any tools in bios to debug it.
I tried reseating the [empty] memory dimm with no effect. I will try swapping them as soon as rsync finishes. Has anyone got any recommendations or steps to get more information?

---

### Post by 1clue on 2016-09-10
Try switching the sticks, as you suggested. Were you using B2 before you upgraded?

This is a bios or hardware problem, not an Ubuntu problem.  If the bios doesn't recognize it then it surely will not show up in Ubuntu.

Also try one of your old sticks in the B2 slot. Try mixing other slots, one stick in An and one in Bn, where n is always the same number.

It may be a hardware issue, if the same stick is unrecognised every time then you'll have to contact your seller and get an RMA.

---

### Post by jason13 on 2016-09-11
I swapped the memory dimms and it resulted in a no-boot scenario, the MB speaker is telling me it's because of the memory issue. Swapping them back to their original position did not restore it to bootable. At this point I think I have bad Dimms, and I don't have any other DDR4 memory to test out.

---

### Post by jason13 on 2016-09-20
Ok, so I've gotten an exchange on the memory dimms, and now I'm in the same scenario, except it is now recognizing only the memory in slot B2. Again this is using a [COLOR=#000000]ASUS Z170-P MB with DDR4 memory. I'm going to continue researching the issue, and try and contact ASUS tomorrow, but this is telling me it's most likely a configuration issue rather than a hardware issue. At the very least I know the MB slots are both good.[/COLOR]

---

### Post by 1clue on 2016-09-21
I'm missing half my memory too.  When you get to be my age maybe you'll understand.





Sorry, I've been wanting to post that since this thread originally showed up. I was a good boy for a few days, but the temptation was just too much to resist. Please chuckle and ignore.

---

