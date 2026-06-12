---
title: "Suggestions for upgraded video card for ATI Rage 128 on Ubuntu 14.04 LTS"
date: 2014-11-08
forum: Hardware
---

### Post by kidzstang on 2014-11-08
I'm running ubuntu 14.04 LTS on an old Dell Dimension 4400 with only 512megs of ram and the stock ATI Rage 128 video card. I've ordered 2GB of ram to juice it up a bit (who would have thought when this machine was new that you could buy 2mgs of ram for $15.00 USD at some point?).

The video is jumpy but usable for my purpose (Automatic Offsite Backup Machine), since this machine will just sit and purr along only to do an automatic backup of other drives each night. So the slow or jumpy video is not really an issue.

However, I have a few more of these machines and might dust them off to maybe use as support for a Customer Relationship Manager or Accounting System (both web based on my own servers). If I do this then I'm thinking that an upgraded video card (read: a card with an available driver) for these machines may make life a little better.  The problem is that I have been out of the hardware intelligence loop for many years (since this Dell 4400 was new) and I have forgotten what I used to know, to say nothing of the advancements that I have missed.

The specs of this motherboard is:
Manufacturer: Intel Corporation
Product Name: D845PT
Version: AAA67834-304
With onboard sound (which is working fine).

I don't think that the PCI slots are PCI-E but am not sure. I know that this limits me greatly.
I was thinking of maybe using a lighter flavor of lynux but haven't tested any of those and I like ubuntu.

My question is: Does anyone know of a video card that would fit in this machine and that might have an available driver that ubuntu 14.04 LTS would support?

Thanks in advance,
Jack

---

### Post by Mark Phelps on 2014-11-09
Can't state this for certain, but I would guess that all the recent AMD video cards are PCI-e, not PCI.  

If you do find a PCI card, it's most likely to be one of the ATI "legacy" cards (HD 2x/3x/4x-series card) and while those will work with the default Radeon driver in Ubuntu 14.04, they will not work with the AMD driver in any Ubuntu newer than 12.04.1.

---

### Post by Yellow Pasque on 2014-11-09
The PCI bus is really limiting because all the devices share the bandwidth of the bus. Something like this is about the best thing you can slap in there: [http://www.newegg.com/Product/Product.aspx?Item=N82E16814187213](http://www.newegg.com/Product/Product.aspx?Item=N82E16814187213)

---

### Post by SeijiSensei on 2014-11-10
The manual suggests these machines have an AGP slot.  You could try one of the cards [listed here](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007709%20600007850&IsNodeId=1&bop=And&Order=PRICE&PageSize=30).

Personally I much prefer NVIDIA hardware over AMD/ATI.  AMD has improved its support for Linux in the past year or two, but NVIDIA cards have always worked well for me.

That said, even with the AGP bus you'll have limitations, especially with high-definition streaming video.  If that's not one of your requirements, then most any of those ~$40 cards at NewEgg are probably fine.

---

### Post by kidzstang on 2014-11-10
Hey thanks guys. I think I'll go with a NVIDIA from NewEgg and see how that flies. You're right SeijiSensei, it is an AGP bus, my bad.

---

### Post by dannyboy79 on 2014-11-10
pick up the best nvidia AGP card you can afford would be my recommendation.

---

