---
title: "Which motherboard for Intel Core 2 Duo"
date: 2006-11-07
forum: Hardware &amp; Laptops
---

### Post by graffoo on 2006-11-07
Hi folks

I'm planning to buy a new computer and I'd like to know which motherboard is working out of the box under Ubuntu Edgy. I need a motherboard which support Intel Core 2 Duo E6300 processor and has integrated graphics (and sound), preferably from Intel too (GMA3000 or GMA X3000 would be perfect).

Thanks in advance.

---

### Post by graffoo on 2006-11-09
No suggestions? Please...

---

### Post by thoughts on 2006-11-15
I just bought an Intel motherboard (DG965WH) that has the x3000 graphics chip, along with a Core 2 Duo E6600 (2.4GHz) processor.  I'm running Edgy on it.  The onboard sound and network are working fine; the onboard video works fine with the i810 driver but it does not support 3D, so it's fine for anything except games and 3D screensavers, etc.  Apparently a full driver specifically for this chip is in the works though (watch [www.intellinuxgraphics.org](www.intellinuxgraphics.org)) which will be in the 2.6.18 or 2.6.19 kernel (Edgy is 2.6.17 and I don't think the driver will show up in any later version of this kernel, but I could be wrong).

The only problem I had with Edgy on this motherboard is that the 2.6.17 kernel does not seem to support the onboard PATA IDE controller.  I have a Promise Ultra100 TX2 PCI IDE controller laying around so I'm using that instead.  Of course if you are using an SATA drive then this issue doesn't matter (though I don't have any SATA drives so I can't say whether the drivers for the onboard SATA controllers work).

--
Anthony DiSante
Encodable Industries
[http://encodable.com/](http://encodable.com/)

---

### Post by Cuppa-Chino on 2006-11-24
slightly different problem here but this is the right thread I think

want to replace my cpu (old p4) with a conroe. i currently run of an asrock p4dual880 (via 880 chipset) mobo which still uses ddr1 but has an pci-e slot (my gfx is pci-e), I have 2 sata HDDs but my DVD-Rom and DVD-RW are both IDE.

I am looking at the following options:

[LIST]
[*]Asrock 775 Dual VSTA (Via 880 based)- 
Pro Cheap upgrade, can use my DDR Ram, plug and play from my current mobo? 
Contra CHEAP, overclocking performance ?, will need to be replaced sometime again
[*]Intel 965P Chipset mobo - 
Pro good clocks, lots of flex, 4 slots for DDR2, lots of options to choose from 
Contra more expensive and **[COLOR="Red"]SEEING that people have installation problems[/COLOR]** in the forum
[*]Intel 965P Chipset mobo WITHOUT JMICRON IDE???
Pro good clocks, lots of flex, 4 slots for DDR2, lots of options to choose from 
Contra more expensive and **[COLOR="Red"]SEEING that people have installation problems[/COLOR]** in the forum
[*]Nvidia based board either nforce 4 or 5 Pro ok quality Contra pricey, not perfect
[*]Nvidia based board nforce 6 
Pro good flex, lots of options and performance, SLI potential Contra is this supported yet?, expensive, not avail for several weeks
[/LIST]

especially the **intel 965p installation problems** really **worry me**, I found ubuntu not straightforward to install and it took a good while to get everything running (wireles, graphics, etc etc). some threads seem to indicate that no kernel upgrade is expected before 7.04 but that seems an awful long way away. is there anyway I can upgrade the kernel on the installation disc? is there a solution where I just plug my HD with ubuntu on it in and run (and find the DVD drives)....

_UPDATE_
Have just seen that Biostar T965 does not use JMicron controller for IDE drives but a Via controller - I would guess that this board will not suffer the Intel 965P / JMicron problems, correct? anybody tried that board?
[Tom's hardware check on it]("http://www.tomshardware.co.uk/2006/11/13/shootout_at_the_core_2_corral_uk/page6.html")



slightly confused about the issue and would appreciate your help

PS please do not recommend an amd I have kind of set my mind on the conroe 

PPS please do not flame me for wanting to buy the conroe and asking not be recommend AMD - I have been pondering this for somewhile

---

### Post by wilsonywx on 2006-11-25
Hello. Does anyone have the Intel DP965LT board who has successfully installed ubuntu? If so I would appreciate sharing of the settings you used.

---

### Post by Cuppa-Chino on 2006-11-25
> **wilsonywx said:**
> Hello. Does anyone have the Intel DP965LT board who has successfully installed ubuntu? If so I would appreciate sharing of the settings you used.

please tell us where your boot / install fails.

if you cannot get your IDE DVD/CD drive recognised and the boot fails therefore, this is the issue I am concerned about - some posts suggested using the USB stick installation method

---

