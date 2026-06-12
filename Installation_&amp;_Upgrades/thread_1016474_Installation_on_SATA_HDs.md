---
title: "Installation on SATA HDs"
date: 2008-12-19
forum: Installation &amp; Upgrades
---

### Post by TonyFordz on 2008-12-19
I have tried many times with no luck to get Ubuntu to notice my 2 new SATA 500GB HDs in which work fine with Windows XP when I download the drivers from ASUS for my motherboard & the RAID for SATA to work but to no end cant get Ubuntu to even notice or list my SATAs on it to install. I have looked all over the net for "Ubuntu SATA Support", "Ubuntu on SATA", and many other types of searches on  google.com but came up with nothing so I thought I would ask here if anyone knows of a way to make it possible to install on an SATA because I have ditched all IDE devices other then my 2 22x DVD Writers which are EIDE devices.

Any ideas?

Happy Holidays!

---

### Post by infamous-online on 2008-12-20
> **TonyFordz said:**
> I have tried many times with no luck to get Ubuntu to notice my 2 new SATA 500GB HDs in which work fine with Windows XP when I download the drivers from ASUS for my motherboard & the RAID for SATA to work but to no end cant get Ubuntu to even notice or list my SATAs on it to install. I have looked all over the net for "Ubuntu SATA Support", "Ubuntu on SATA", and many other types of searches on  google.com but came up with nothing so I thought I would ask here if anyone knows of a way to make it possible to install on an SATA because I have ditched all IDE devices other then my 2 22x DVD Writers which are EIDE devices.

Any ideas?

Happy Holidays!


I had this problem before whenever I tried to install Ubuntu on my scsi hd, and this is what caused it.

My system is a Dell 650 with a built-in scsi controller and I was thinking I could just install Ubuntu onto the scsi with no issues, WRONG! For whatever reason, the controller would never recognize it and I just happen to have an old pci scsi controller card lying around.

Just like that the scsi drive was found and I was able to install Ubuntu onto the scsi drive with no issues. So here's what I think it could be. Software makers I believe write their programs mostly for windows, so that could be the problem. However if you're willing to experiment, purchase an add-on sata II pci or better card and see if that helps out.

---

