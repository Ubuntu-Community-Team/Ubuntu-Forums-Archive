---
title: "HDD Utility?"
date: 2007-08-15
forum: Hardware &amp; Laptops
---

### Post by bliffle on 2007-08-15
I've got a HDD here that it's claimed has been refurbished, but when I put it in a USB box nothing happens on Feisty. The lED light comes on at the box.

Is there something I can test or probe this thing with? Maybe a standalone program to test?

Gparted doesn't see it. Nothing seems to see it.

---

### Post by dougfractal on 2007-08-15
put it in the pc and see if the bios can see it.

Is it getting enough power?

---

### Post by 1/0 on 2007-08-15
I would go with the tool from the factory. What brand is it? 

[This page]("http://www.tacktech.com/display.cfm?ttid=287") links to some further info on tools to use.

---

### Post by bliffle on 2007-08-15
> **1/0 said:**
> I would go with the tool from the factory. What brand is it? 

[This page]("http://www.tacktech.com/display.cfm?ttid=287") links to some further info on tools to use.

It's a Hitachi. They say that their DTF utility only works internal, not in USB, so my next step is to put this HDD in the internal drive and try it out.  Hitachi has a utility I can DL and run from a floppy.

---

### Post by 1/0 on 2007-08-16
That's probably your best shot. Its usually a regular 3,5" HDD so you shouldn't have any problems.

---

### Post by bliffle on 2007-08-16
I tried it quickly in the Docking Station of my thinkpad 570 with win2K but that didn't work, so after breakfast I'll try it in the main system bay of a TP570.

---

### Post by bliffle on 2007-08-16
Finally, I got the HDD partitioned with Gparted. Then I tried copying the old winXP system to the new disk, but it always failed at the very end.

Well, I'm going to try Knoppix next as well as rescuecd.

---

