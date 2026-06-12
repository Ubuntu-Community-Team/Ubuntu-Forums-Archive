---
title: "Intel SE7505VB2 Mainboard and Via  vt6421a SATA Raid Controller"
date: 2009-02-15
forum: Hardware
---

### Post by drake22 on 2009-02-15
Hello all! I just got myself a new server, and I am trying to set up a SATA RAID. The motherboard is an Intel SE7505VB2. I have two western digital 320gb HDDs that I want to set up in a RAID 0 configuration. I bought a vt6421a SATA RAID controller to do the trick. It works fine in non-RAID configuration (it finds the drives and uses them independantly just fine). Problem is that I have no idea how to set up the RAID. The onboard RAID controller and the installed Mylex AcceleRAID 253 (PCI-X) boots up its BIOS on system boot, but the VT6421A does not.

Can someone help me out? Thanks.

David

---

### Post by ployber on 2009-06-11
got any luck on this?

I'm stuck with the same problem, the os see the card and then the disks, but I have no idea how to config the RAID.

TIA
Pablo

---

### Post by drake22 on 2009-06-12
I gave up an configured a software raid...it works very well and so I suggest you do the same.

---

