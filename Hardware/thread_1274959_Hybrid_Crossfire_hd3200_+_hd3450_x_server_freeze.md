---
title: "Hybrid Crossfire hd3200 + hd3450 x server freeze"
date: 2009-09-25
forum: Hardware
---

### Post by hanbin973 on 2009-09-25
I didn't know that Ati had a crossfire support in linux. 

But it had a hybrid crossfire support from 9.1 driver. 

And I knew this a weak ago. 

What ever, I configured the bios setup to put IGFX as the primary ( The guide of the mainboard said 'put the IGFX as primary to use hybrid graphics ' ) and booted in recovery mode and ran

aticonfig --initial -f; sudo aticonfig --adapter=0,1 --cfa; aticonfig --adapter=0,1 --crossfire=on

And I booted the computer again and it worked fine but..

I ended up freezing. And I rebooted but again and again after about a min. 

My driver is 8.660 ( launchpad had a beta version of 9.10 driver ... So I compiled it. ) And kernel, 2.6.30 from [http://kernel.ubuntu.com/~kernel-ppa/mainline](http://kernel.ubuntu.com/~kernel-ppa/mainline).

My gpu is, hd3200 and hd3450.

help me please!

---

