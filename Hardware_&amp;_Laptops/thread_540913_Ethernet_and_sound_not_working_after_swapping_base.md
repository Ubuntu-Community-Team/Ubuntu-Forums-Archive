---
title: "Ethernet and sound not working after swapping base board"
date: 2007-09-02
forum: Hardware &amp; Laptops
---

### Post by sola on 2007-09-02
Hi All,

Recently I had to swap the base board of my HTPC box which runs Dapper. 

Originally, I had an ASUS A8N-E board with Nvidia nforce4 ultra chipset. I couldn't get the same board when the old on stopped working so I bought an Asrock 939NF6G-VSTA board with nforce 430 chipset.

When I restarted the system with the new board, ethernet and audio didn't work.

The hardware information tool shows a couple of unknown devices.

Is it possible to fix this without reinstalling my Dapper Box?

Any help is appreciated,
Andras

---

### Post by overdrank on 2007-09-03
> **sola said:**
> Hi All,

Recently I had to swap the base board of my HTPC box which runs Dapper. 

Originally, I had an ASUS A8N-E board with Nvidia nforce4 ultra chipset. I couldn't get the same board when the old on stopped working so I bought an Asrock 939NF6G-VSTA board with nforce 430 chipset.

When I restarted the system with the new board, ethernet and audio didn't work.

The hardware information tool shows a couple of unknown devices.

Is it possible to fix this without reinstalling my Dapper Box?

Any help is appreciated,
Andras

Hi if you have not solved your issue yet then if you run the command in the terminal
```
sudo update-pciids
```
Then you can post back with the output of the command lspci and we may can help. Goo luck

---

