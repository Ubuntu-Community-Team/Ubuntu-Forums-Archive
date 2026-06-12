---
title: "PCI SATA Card Issues"
date: 2009-03-15
forum: Hardware
---

### Post by sch21c on 2009-03-15
Hello all.  I'm running a Dell Dimension 4550.  The IDE drive crashed in it and I purchased a 1TB SATA drive (Seagate Barracuda) and a PCI Serial ATA adapter card (CP Technologies CP-SP-01) so I can use the drive in the system (since it had no motherboard capabilities for SATA drives). 

I booted Ubuntu from the CD and chose Install.  It found the hard drive and partitioned it. The installation appeared to go without any problems.  When I rebooted the system the hard drive is not seen by the bios, and when I select the "Boot from first hard disk" option the following is displayed on the screen:
```

Booting from local disk...
isolinux: Disk error 01, AX = 0201, drive 80

Boot failed: press a key to retry...

```

Anyone have any experience or ideas on using a PCI SATA adapter card?  The BIOS is the newest version I found on Dell's support site (A08).  Any thoughts or options?

Thanks in advance,
--Sam

---

### Post by sch21c on 2009-03-17
Bump

---

### Post by markbuntu on 2009-03-18
I used a SIIG SATA PCI card for a while. It had its own bios which booted after the mobo and rearranged my drives for me in the process. It worked though I don't think I ever tried to boot directly from one of the drives on it.

Can you get the live cd to see the drive?

---

### Post by sch21c on 2009-03-21
When I was installing off the live CD it could see the drive, but if I try to "Boot from hard disk" with the Live CD, it doesn't see the drive.

---

### Post by rodney757 on 2009-04-05
I'm having the same problem, anyone have any ideas?

---

