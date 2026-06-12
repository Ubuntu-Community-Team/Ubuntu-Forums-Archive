---
title: "SuperMicro compatability"
date: 2009-12-21
forum: Hardware
---

### Post by maudigan on 2009-12-21
I'm getting close to building my own server, and I have scraped together about 2 grand. I'm terrified about purchasing the parts to put everything together. I've built 5 or 6 PC's at home, and I would consider myself pretty familiar with hardware. However because of the ammount of moola i'm spending on this im terribly scared This stuff wont be compatible with ubuntu 9.10 **server edition**, or with the hardware i've selected.
 
I called supermicro and asked about 9.10 and they tell me they haven't tested any boards with 9.10, and most of them haven't been tested with ubuntu at all. Can anyone tell me if it is compatible with this....
 
Chassis & Motherboard : [http://www.newegg.com/Product/Product.aspx?Item=N82E16816101246](http://www.newegg.com/Product/Product.aspx?Item=N82E16816101246)
 
The gentleman at supermicro did postulate that if there we're any problems it would be with the lan drivers and/or raid controller. The raid would be an issue as I intended on 10'ing 4 drives.
 
Secondary, and nobody has to answer this since it really has nothing to do with ubuntu, but should I have any concerns using the following hardware setup with the board/chassis above
 
HD x 4 : [http://www.newegg.com/Product/Product.aspx?Item=N82E16822136113](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136113)
RAM x 2: [http://www.newegg.com/Product/Product.aspx?Item=N82E16820134943](http://www.newegg.com/Product/Product.aspx?Item=N82E16820134943)
CPU x 2: [http://www.newegg.com/Product/Product.aspx?Item=N82E16819117185](http://www.newegg.com/Product/Product.aspx?Item=N82E16819117185)

---

### Post by Fire_Chief on 2009-12-21
So that server you linked to on Newegg uses this motherboard [http://www.supermicro.com/products/motherboard/QPI/5500/X8DTL-i.cfm]("http://www.supermicro.com/products/motherboard/QPI/5500/X8DTL-i.cfm")
Just glancing a the specs, the NICs will be fine and I think the SATA chipset will work (says it supports RAID10 under Linux).

The other hardware looks fine.

Cheers!

---

