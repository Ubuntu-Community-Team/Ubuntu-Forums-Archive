---
title: "PCIe x8 slot used for GeForce 6610 XL and seen as 1x"
date: 2009-04-27
forum: Hardware
---

### Post by manveru.pl on 2009-04-27
Hello,

I have following problem:
I have a HP small server ML110 which do not have PCIe16x slot, only one 8x available. So I bought some GeForce 6610 XL - it has PCI 16x according to the documentation - and cut the plastic edge of the slot to mechanically fit the card. I read that it should work.
With the proprietary nVidia drivers card is nicely detected and it works at 1680x1050. But the [FONT=Courier New]nvidia-settings[/FONT] reports the bus type as **PCI Express 1x**.

So, now my question is is there any way to force it to x4 or x8? Maybe there is a way to check why nvidia detects it as x1?

Any helpful hints and solutions are very appreciated. I was looking for any configuration options for this, but I do not find nothing useful.

---

### Post by jerrrys on 2009-04-28
interesting hack...

yes pinout is the same until you get to HSOp(8)...pin 50...from then on HSOp and HSOn are shooting off into space...makes me think that mobo is seeing the card ok, but the card cannot detect pass HSOp(8) so it has (the card) a default built in of PCI-E 1x...I have tried to locate a schematic of an PCI-E 1x-4x-8x-16x, but cannot find one...with a schematic, a further hack may be possible...good luck...

faces not intended, trying to print HSOp8 with ()...

---

### Post by manveru.pl on 2009-04-30
> **jerrrys said:**
> interesting hack...

yes pinout is the same until you get to HSOp(8)...pin 50...from then on HSOp and HSOn are shooting off into space...makes me think that mobo is seeing the card ok, but the card cannot detect pass HSOp(8) so it hasReally interesting what you've written. Could you tell me more about it? Are the card should work on all available serial lanes?

> **jerrrys said:**
>  (the card) a default built in of PCI-E 1x...I have tried to locate a schematic of an PCI-E 1x-4x-8x-16x, but cannot find one...with a schematic, a further hack may be possible...good luck...

faces not intended, trying to print HSOp8 with ()...
About this kind of schematics are thinking: [http://www.allpinouts.org/index.php/PCI_Express_16x](http://www.allpinouts.org/index.php/PCI_Express_16x)

I've just look at differences between 16x and 8x and there is no HSOp and HSOn number 8 on 8x. Any other suggestions?

All the articles I found about hacking the slot tells only about the removing end of the slot. Is it possible that **GF 6610 **is too stupid for this? Most people writes about different **GF 9xxx**.

---

### Post by jerrrys on 2009-04-30
Hello manveru.pl...

wellll, i did some more digging and finally made a hit...there is a possibility that a bios change can be made...and most agree that this hack should work...checkout these links...

[http://forums.cnet.com/5208-7591_102-0.html?threadID=233965](http://forums.cnet.com/5208-7591_102-0.html?threadID=233965)

[http://www.hardforum.com/showthread.php?t=1175156](http://www.hardforum.com/showthread.php?t=1175156)

[http://forums.whirlpool.net.au/forum-replies-archive.cfm/862907.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/862907.html)

[http://www.urbelausdemall.de/pcie_en.php](http://www.urbelausdemall.de/pcie_en.php)

[http://www.mvktech.net/index.php?option=com_joomlaboard&func=view&catid=13&id=51606](http://www.mvktech.net/index.php?option=com_joomlaboard&func=view&catid=13&id=51606)

[http://www.sudhian.com/index.php?/forums/viewthread/105026/#909908](http://www.sudhian.com/index.php?/forums/viewthread/105026/#909908)

on the downside was this...

A PCIe card will fit into a slot of its physical size or bigger, but may not fit into a smaller PCIe slot. Some slots use open-ended sockets to permit physically longer cards and will negotiate the best available electrical connection. The number of lanes actually connected to a slot may also be less than the number supported by the physical slot size. An example is a x8 slot that actually only runs at x1; these slots will allow any x1, x2, x4 or x8 card to be used, though only running at the x1 speed. This type of socket is described as a "x8 (x1 mode)" slot, meaning it physically accepts up to x8 cards but only runs at x1 speed. 
[http://en.wikipedia.org/wiki/PCI_Express](http://en.wikipedia.org/wiki/PCI_Express)

and i even found a guy with the exact same problem..
[http://www.nvnews.net/vbulletin/showthread.php?t=132226](http://www.nvnews.net/vbulletin/showthread.php?t=132226)
you got a twin brother??

and there is more for your reading pleasure at...

[http://www.google.com/search?hl=en&rlz=1G1GGLQ_ENUS279&num=50&q=pci+express+16x+backwards+compatible+8x&btnG=Search&cts=1241123503353](http://www.google.com/search?hl=en&rlz=1G1GGLQ_ENUS279&num=50&q=pci+express+16x+backwards+compatible+8x&btnG=Search&cts=1241123503353)

this is about all i can do on the subject...hope it helps...good luck...

---

### Post by manveru.pl on 2009-06-22
I've solved the problem partially. I removed the 6610XL and put 8400GS instead - drivers are still reporting PCIe x1, but the full screen videos have much better performance.

---

