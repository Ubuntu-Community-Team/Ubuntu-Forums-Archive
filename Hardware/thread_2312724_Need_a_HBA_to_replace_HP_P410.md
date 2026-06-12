---
title: "Need a HBA to replace HP P410"
date: 2016-02-06
forum: Hardware
---

### Post by aronwalker on 2016-02-06
Hi there

I have a server which has a P410 in it. Its reached the end of its time, and I need a replacement. So basically does anyone have any recommendations for it.

Requirements:
[LIST]
[*]Don't need RAID Support - JBOD is enough
[*]Needs to connect to blackplate with 2 internal x4 wide port connectors (sff-8087 Connectors I think)
[*]Preferably under £200/$300
[*]Thats it
[/LIST]

Kind Regards,

Aaron

---

### Post by gordintoronto on 2016-02-06
You might get a useful response with fewer acronyms and more details. Do you want to continue using the existing drives? (But I'm not sure if that is an appropriate question.)

I've been in IT for a long time, and I don't entirely understand your question.

---

### Post by aronwalker on 2016-02-07
Sorry if I made the question too complicated:

Basically My current server has a HP P410 (a raid controller) inside of it. It is connected to the servers backplate (a board which connects the hard drives to the SAS cables (the cables which connect the backplate to the RAID card)) with some SFF-8087 SAS Cables (that is the name of the cables - they look like [this]("http://img.misco.eu/Resources/images/Modules/InformationBlocks/1210/SRH/SRH-1/173897-front2.jpg"))

I need a [HBA ]("https://en.wikipedia.org/wiki/Host_adapter")(A Host Bus Adapter - basically a device which allows me to add more Hard drives to a computer) instead of a RAID Card (a device which gets hard drives and groups them together (in a Redundant Array of Inexpensive Disks / RAID))
I don't need a RAID Card - aka I don't need Raid 0 or RAID 1 or RAID 5 etc... I just want each HDD (Hard drive) to be exposed to the Operating system, rather than creating a single [Logical Drive]("https://en.wikipedia.org/wiki/Logical_disk")
The Card needs to have 2 Internal Connectors SFF-8087 Connectors
It needs to be under £200/$300 - It shouldn't really be any more than this

I do want to continue to use the existing drives.

Maybe here isn't the correct place to ask such questions :/

Regards,

Aaron

---

### Post by gordintoronto on 2016-02-08
Would it be safe to say that what you want to do is attach several hard drives to your motherboard? If that's true, your existing setup is irrelevant, but identifying your motherboard is essential.

---

### Post by Yellow Pasque on 2016-02-09
[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007607%20600022733%20600022717%20600244153&IsNodeId=1&bop=And&Order=PRICE&PageSize=30](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007607%20600022733%20600022717%20600244153&IsNodeId=1&bop=And&Order=PRICE&PageSize=30)

---

