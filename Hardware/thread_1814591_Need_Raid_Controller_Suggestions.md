---
title: "Need Raid Controller Suggestions"
date: 2011-07-29
forum: Hardware
---

### Post by oxsyn on 2011-07-29
Hello All,

I have a NAS powered by Ubuntu 11.04 x64 server.  It's in a Norco case which supports 20 SATA II drives in groups of 4 connected to 5 SAS backplanes, each with an 8087 connector.

I currently have four samsung 2tb spin points connected via a reverse 8087 to SATA breakout cable.  They work perfectly.

In order to connect the additional 16 drives, I need 4x 8087 connections.

The motherboard is an EVGA SLI 590.  It has 2x PCIe 1.0 x 16 slots.

I have already tried this card: [Intel SASUC8I PCI-Express x8 SATA / SAS (Serial Attached SCSI) Controller Card ]("http://www.newegg.com/Product/Product.aspx?Item=N82E16816117157") ... which simply didn't work.  I tried two of these cards and tested both cards in three different computers, in all cases the computer wouldn't post to bios (speculating, the card firmware may be trying to unload to the same place in memory as the bios firmware).

I need to order a new card now, and am looking for suggestions.  

The card must support JBOD (I'm using mdadm to manage the raid volumes for specific reasons), must have 2x 8087 internal connectors, work in a PCIe 1.0 x16 slot, and work with Ubuntu 11.04x64 server.

---

### Post by oxsyn on 2011-07-29
Technically, I could use cards with 8x SATA II connections/card and use reverse 8087-sata breakout cables on those as well.

---

