---
title: "I am just unable to find the driver I need no matter how much I search."
date: 2009-07-16
forum: Installation &amp; Upgrades
---

### Post by noahgelman on 2009-07-16
I just set my computer up to dual boot with Ubuntu 9.04 (which I already had) and Windows XP (which I just put on). My computer isn't new enough for vista unfortunately. Anyways, I for the life of me cannot for the proper network driver so I can connect to the internet on XP. I have a "Texas Instruments ACX 111 54mbps Wireless Interface". If you guys could help me find a driver for it for Windows XP, it would be a super big help.

---

### Post by starcraft.man on 2009-07-16
This isn't really in the per view of the forum, but as a Windows user who's had such trouble I'll give you help.

How'd you get this computer? It's an OEM built one or custom build? If it's OEM built (you bought from a store), you should visit the maker's website and look for the model you bought (even if it didn't come with XP, they often list drivers if you desire). If it's custom built, you should know the make and model of the motherboard (for built in networking) as well as this additional NIC you bought then go to manufacturers website of both, and search for your product in support/downloads section. 

You won't find the drivers at TI, they are just a chip maker and don't to my knowledge support customers, you'd be looking for an interim company in between like Netgear who took TI's chips and put em in a NIC. For this, it's important know the make and model of the wireless card. I'd just pull it out and look on it's surface. Without fail, every manufacturer puts a s/n on there with the company, model and usually a bit more somewhere.

That's about it, so just pull out the card and see who made it. If you bought it from a store, just get the box, it should have come with drivers.

Edit: Oh and I just remembered, even easier to that you could open a terminal (applications > accessories > terminal) and use the command:

```
lspci
```

That will list all the pci devices installed, you should see somewhere listed there the name of your nic. If your uncertain, use pastebin.ca and put a link here.

---

