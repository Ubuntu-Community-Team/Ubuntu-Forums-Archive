---
title: "RAID In Ubuntu"
date: 2007-11-13
forum: Hardware &amp; Laptops
---

### Post by xelapond on 2007-11-13
So, I am building a new computer, and I had a few questions about RAID and Ubuntu, as I am very new to raid.

Here is the scheme I want to set up, if its even possible:

40 Gig SATA Drive(For Actually Installing Ubuntu, and Holding the stuff on my desktop, and swap, Not in RAID Array)

320 Gig SATA in RAID 1(For Data)
320 Gig SATA in RAID 1(For Data)

40 Gig PATA(For Gaming, Until they make HL2 and Crysis for Linux, Ill need a windoze drive:^(

Can I have a dual boot with the Two 40 gig drives, that just hold my OS, and Still have the RAID drives, but as ext3, for holding my linux data.

Also, should I use Hardware or Software RAID?

Alex

---

### Post by RTrev on 2007-11-13
> **xelapond said:**
> So, I am building a new computer, and I had a few questions about RAID and Ubuntu, as I am very new to raid.

Here is the scheme I want to set up, if its even possible:

40 Gig SATA Drive(For Actually Installing Ubuntu, and Holding the stuff on my desktop, and swap, Not in RAID Array)

320 Gig SATA in RAID 1(For Data)
320 Gig SATA in RAID 1(For Data)

40 Gig PATA(For Gaming, Until they make HL2 and Crysis for Linux, Ill need a windoze drive:^(

Can I have a dual boot with the Two 40 gig drives, that just hold my OS, and Still have the RAID drives, but as ext3, for holding my linux data.

Also, should I use Hardware or Software RAID?

Alex

Hi.  Sounds pretty close to what I have, actually.  I've got Ubuntu on a 74G drive, and various other things come and go on another 74G drive, and from both of them I access a RAID-1 array composed of two 500G drives.  I have the ext3 file system on all of the drives, because I only use Windows rarely, and when I need it to answer someone's question about it I boot it in a virtual machine.

If you have a *real* hardware RAID controller, as opposed to a "fakeraid" controller which requires a driver for the OS, then that would be good.  But if you have to ask, you probably don't have one and don't want to buy one.. they're pricey!  I have my BIOS fakeraid turned off and use mdadm for the RAID.  I think the consensus is that the fakeraid is simply not worth using, and that mdadm, due to code maturity if nothing else, is faster and more reliable.  I back up the RAID array to an external 500G USB drive, and to a couple of off-site machines.

HTH,
Bob

---

