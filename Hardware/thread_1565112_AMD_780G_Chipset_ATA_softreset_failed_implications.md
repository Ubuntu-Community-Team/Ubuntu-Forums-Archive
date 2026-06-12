---
title: "AMD 780G Chipset ATA softreset failed implications"
date: 2010-08-31
forum: Hardware
---

### Post by mattlach on 2010-08-31
Hi all,

I recently picked up a cheap Dell Zino HD mini computer to use as a file server for my home.  

My plan was to attach a "Drobo S" array to it via eSATA and use it as a file server via SSHFS.

My research has - however - concluded that the Drobo S requires Port Multiplier in order to function over eSATA.   My AMD 780G chipset displays the "ATA softreset failed" message during boot.

A post on the wikipedia page for the AMD 7x0 southbridge chipsets suggests that this would be a problem:

> 
SATA soft reset fails when PMP is enabled and attached devices will not be detected

Can anyone clarify?  Is the above statement still true, or is there a workaround or patch?

Thank you,
Matt

---

