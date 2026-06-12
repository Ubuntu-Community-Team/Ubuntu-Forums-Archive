---
title: "nvidia killed my monitor"
date: 2005-08-09
forum: Hardware &amp; Laptops
---

### Post by elpresidente on 2005-08-09
Just did a fresh install after wiping my debian sid box. (I tried upgrading to hoary but it broke apt and did want to spend the time to fix it - clean install is better). Before I installed hoary, I switch my ati video card for a geforce 2 I was using in another pc. Eveything went ok except I was getting some nasty shadows in X (not the monitor - I use the same monitor with other pcs over a kvm). I didn't have the time to sort out the problem so I left it like it was. Now 2 days later, my monitor burnt out, there's a nasty smell in the air, and I'm still getting shadows on this other monitor I threw on there. I figure either the monitor ranges in xorg.conf are wrong or the video card is bad. There was no indication that the card was going bad before this. There were no monitor ranges in xorg (I choose the simple route - there is now).

```
Section "Device"
        Identifier      "NVIDIA Corporation NV11DDR [GeForce2 MX 100 DDR/200 DD$
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-65
        VertRefresh     50-75
EndSection
``` 

Any suggestions?

---

### Post by linuxlover on 2005-08-17
Need to get the specs of the monitor for the sync settings, if not correct monitor will be damaged.  Do a search on the model.

---

